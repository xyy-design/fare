package DeLeon;
import java.text.DecimalFormat;
import java.util.Scanner;

public class fare {
    public static void main(String[] args) {
        int rate = 100;
        double discountRate = 0, businessCharge = 0;


        Scanner input = new Scanner(System.in);
        DecimalFormat df = new DecimalFormat("###,###.00");
        System.out.print("Enter Discount for Ordinary Passenger: ");

        double ordinaryPassengerDiscount = input.nextDouble();
        System.out.print("Business class additional Fare for Ordinary Passenger: ");
        double ordinaryBusinessCharge = input.nextDouble();
        System.out.println("");

        System.out.print("Enter Discount for Student Passenger: ");
        double studentPassengerDiscount = input.nextDouble();
        System.out.print("Business class additional Fare for Student Passenger: ");
        double studentBusinessCharge = input.nextDouble();
        System.out.println("");

        System.out.print("Enter Discount for Senior Citizen Passenger: ");
        double seniorPassengerDiscount = input.nextDouble();
        System.out.print("Business class additional Fare for Senior Citizen Passenger: ");
        double seniorBusinessCharge = input.nextDouble();
        System.out.println("");


        System.out.print("Enter fare: ");
        double fare = input.nextDouble();
        System.out.print("Passenger type [O,S,C]: " );
        char passengertype= input.next().charAt(0);
        passengertype = Character.toUpperCase(passengertype);

        System.out.print("Travelling in business class [Y/N]: ");
        char travellinginbusiness = input.next().charAt(0);
        travellinginbusiness = Character.toUpperCase(travellinginbusiness);

        switch(passengertype) {
            case 'O':
                discountRate = ordinaryPassengerDiscount / rate;
                businessCharge = ordinaryBusinessCharge;
                break;
            case 'S':
                discountRate = studentPassengerDiscount / rate;
                businessCharge = studentBusinessCharge;
                break;
            case 'C':
                discountRate = seniorPassengerDiscount / rate;
                businessCharge = seniorBusinessCharge;
                break;
            default:
                discountRate = 0;
                businessCharge = 0;
                break;
        }

        if (travellinginbusiness == 'Y') {
            businessCharge = businessCharge;
        } else if (travellinginbusiness == 'N') {
            businessCharge = 0;
        }

        double discount = fare * discountRate;
        System.out.println("Discount: " + df.format(discount) + " Pesos");
        System.out.println("Business class charge: " + df.format(businessCharge) + " Pesos");

        double newFare = fare - discount + businessCharge;
        System.out.print("New Fare: " + df.format(newFare));
    }
}
