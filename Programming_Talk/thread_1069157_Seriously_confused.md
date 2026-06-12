---
title: "Seriously confused"
date: 2009-02-13
forum: Programming Talk
---

### Post by Epeeman on 2009-02-13
Ok, I'm doing a coding assignment for a Java programming class and I'm asking users for input when selecting a car option (1 or 2) if they enter anything else it's supposed to send them into a while loop until they enter a valid number. But the error check isn't working for the transmission option, even though I cant see anything wrong with it.

Radio error check code (working) and Transmission error check code (not working)

```

            //Get Radio Options

            options = JOptionPane.showInputDialog(null, "If you would like the standard radio press 1.\n" + "If you would like only the basic AM/FM radio press 2. " );

            radioOptions = Integer.parseInt(options);


            //Radio Errors

            while(intOptions != 1 && intOptions != 2)
               {
                  errorMessage ="Incorrect value for radio type";
                  JOptionPane.showMessageDialog(null, errorMessage);
                  options = JOptionPane.showInputDialog(null,
                     "Enter 1 if you want the standard radio\n" +
                     "Enter 2 if you want the AM/FM radio");
                     intOptions = Integer.parseInt(options);
               }



            //Subtract the cost of AM FM radio from car options cost if radio option is 2

            if (radioOptions == 2)

               optionsCost += AMFM_RADIO_ONLY ;



            //Get Transmission Options

            options = JOptionPane.showInputDialog(null, "If you would like the automatic transmission press 1.\n" + "If you would like the manual transmission press 2. " );

            transmissionOptions = Integer.parseInt(options);


            //transmission Errors

            while(intOptions != 1 && intOptions != 2)
               {
                  errorMessage ="Incorrect value for transmission type";
                  JOptionPane.showMessageDialog(null, errorMessage);
                  options = JOptionPane.showInputDialog(null,
                     "Enter 1 if you want the automatic transmission\n" +
                     "Enter 2 if you want the manual transmission");
                     intOptions = Integer.parseInt(options);
               }



            //Subtract the cost of manual transmission from car options cost if transmission option is 2

            if (transmissionOptions  == 2)

               optionsCost += STANDARD_TRANSMISSION;


```

Yes, I know curly brackets, baaaw

Here's the rest of the program if that helps:

```

//Lab4Winter09.java

//MY NAME
//Lab Section 06



import java.io.*;

import java.util.Scanner;

import javax.swing.JOptionPane;

import java.text.DecimalFormat;



/**

This program is designed for a car dealership to determine which options a customer might want on his/her car. It will allow the customer to generate up to five (5) pricing quotes.

*/

public class Lab4Winter09

{



   /**

   This program is designed for a car dealership to calculate the cost of a car to be purchased, after taking into account the customer's chioces of options.

   */

   public static void main(String[] args)

   {



      //Declare Variables

      DecimalFormat dollar = new DecimalFormat("$#,##0.00");

      int intOptions = 0;

      int seatingOptions = 0;              //customer's choice of seating

      int flooringOptions = 0;             //customer's choice of flooring

      int radioOptions = 0;                //customer's choice of radio

      int transmissionOptions = 0;         //customer's choice of transmission

      int tryCount = 1;                    //counts the number of quote attempts

      int stop = 0;                        //Stops the program
      int miles = 0;                       //miles entered each time prompted
      int milesDrivenAnnually = 0;         //Number of miles driven per year
      String options = " ";
      String errorMessage = " ";           //Error message string
      double lifeCycleCost = 0.0;          //Cost of car + options + driving for 5yrs

      double costOfDrivingPerYear = 0.0;   //Cost of driving car per year

      double optionsCost = 0.0;            //Cost of the desired options

      double totalCost = 0.0;              //Total cost of the car



      //Declare constants

      final double COST_PER_MILE = .40;              //Cost of driving one mile

      final double BASE_CAR = 20000.00;              //cost of the basic car

      final double SEATS_CLOTH = 300.50;             //Cost of cloth seats

      final double SEATS_SPLIT = 400.50;             //cost of split seats (as opposed to bench-style)

      final double SEATS_BASIC = 0.0;                //Cost of basic seats

      final double DELUX_CARPET = 500.00;            //cost of heavy-duty carpeting

      final double AMFM_RADIO_ONLY = -200.00;        //cost of cheap radio

      final double STANDARD_TRANSMISSION = -500.00;  //cost of manual transmission

      final double TAX_RATE = .0725;                 //Tax rate (7.25%)

      final double PROFIT_RATE = .1;                 //Profit margin (10%)

      final double SHIPPING_COST = 300.00;           //Cost of Shipping and handling



      //Declare input value

      Scanner input = new Scanner (System.in);



      //Announcemt pane; Declaration of program purpose

      JOptionPane.showMessageDialog(null, "This program will give you up to five (5) attempts to get a price quote that you like for the car you are planning to buy. \n" + "It will calculate the cost of the car and it's options (transmission, radio, flooring material, seating type). \n" + "It will then ask for the approximate number of miles that you will drive in five (5) years and calculate the \n" + "approximate cost of operating the vehicle over that period of time.");

      //Begin do-while loop to gather user input

      do

      {   

         //Ask for base car

         options = JOptionPane.showInputDialog(null, " This is try number " + tryCount + "\n" + " If you would like the standard car press 1.\n " + "If you would like a car with options press 2. " );

         intOptions = Integer.parseInt(options);



         //Check for errors

         while(intOptions != 1 && intOptions != 2)
            {
               errorMessage ="Incorrect value for car type";
               JOptionPane.showMessageDialog(null, errorMessage);
               options = JOptionPane.showInputDialog(null,
                  "Enter 1 if you want the base car\n" +
                  "Enter 2 if you want the car with options");
                  intOptions = Integer.parseInt(options);
            }
         if (intOptions == 1)
         {



            //Output Message if BASE CAR chosen

            if (intOptions == 1) 

            {

               totalCost = BASE_CAR + (BASE_CAR * TAX_RATE) + (BASE_CAR * PROFIT_RATE) + SHIPPING_COST;

               JOptionPane.showMessageDialog(null, "The cost of the base car you've chosen is\n " + dollar.format(totalCost));

            } 

         }

         //Car with options 

         else if (intOptions == 2)

         {

            //Get Seat Options

            options = JOptionPane.showInputDialog(null, " If you would like Cloth bench-style seats press 1.\n " + "If you would like cloth split seats press 2.\n " + "If you would like the basic seats press 3 " );

            seatingOptions = Integer.parseInt(options);

            switch (seatingOptions)

            {

               case 1: //bench seats chosen

                  optionsCost += SEATS_CLOTH;

               break;

               case 2: //cloth seats chosen

                  optionsCost += SEATS_SPLIT;

               break;

                  case 3: //basic seats chosen

                  optionsCost += SEATS_BASIC;

               break;
               default: //Check for seating errors
                     errorMessage ="Incorrect value for seat type";
                     JOptionPane.showMessageDialog(null, errorMessage);
                     options = JOptionPane.showInputDialog(null,
                        "Enter 1 if you want the bench seats\n" +
                        "Enter 2 if you want the cloth seats\n" +
                        "Enter 3 if you want the basic seats");
                        intOptions = Integer.parseInt(options);

            }
            
            //Get Flooring options

            options = JOptionPane.showInputDialog(null, " If you would like the delux heavy-duty carpeting press 1.\n " + "If you would like standard carpeting press any other number. " );

            flooringOptions = Integer.parseInt(options);



            //Add the cost of deluxe carpet to car options cost if flooring option is 1

            if (flooringOptions == 1)

               optionsCost += DELUX_CARPET ;



            //Get Radio Options

            options = JOptionPane.showInputDialog(null, "If you would like the standard radio press 1.\n" + "If you would like only the basic AM/FM radio press 2. " );

            radioOptions = Integer.parseInt(options);


            //Radio Errors

            while(intOptions != 1 && intOptions != 2)
               {
                  errorMessage ="Incorrect value for radio type";
                  JOptionPane.showMessageDialog(null, errorMessage);
                  options = JOptionPane.showInputDialog(null,
                     "Enter 1 if you want the standard radio\n" +
                     "Enter 2 if you want the AM/FM radio");
                     intOptions = Integer.parseInt(options);
               }



            //Subtract the cost of AM FM radio from car options cost if radio option is 2

            if (radioOptions == 2)

               optionsCost += AMFM_RADIO_ONLY ;



            //Get Transmission Options

            options = JOptionPane.showInputDialog(null, "If you would like the automatic transmission press 1.\n" + "If you would like the manual transmission press 2. " );

            transmissionOptions = Integer.parseInt(options);


            //transmission Errors

            while(intOptions != 1 && intOptions != 2)
               {
                  errorMessage ="Incorrect value for transmission type";
                  JOptionPane.showMessageDialog(null, errorMessage);
                  options = JOptionPane.showInputDialog(null,
                     "Enter 1 if you want the automatic transmission\n" +
                     "Enter 2 if you want the manual transmission");
                     intOptions = Integer.parseInt(options);
               }



            //Subtract the cost of manual transmission from car options cost if transmission option is 2

            if (transmissionOptions  == 2)

               optionsCost += STANDARD_TRANSMISSION;



            //Compute cost here of automobile with options

            totalCost = (BASE_CAR + optionsCost) + ((BASE_CAR + optionsCost) * TAX_RATE) + ((BASE_CAR + optionsCost) * PROFIT_RATE) + SHIPPING_COST;



            //Output the cost for automobile with options

            JOptionPane.showMessageDialog(null, "The cost of the car with options you've chosen is\n " + dollar.format(totalCost));

         }
         tryCount++; //Increment variable tryCount

	 //ask for more quotes --> stop

         options = JOptionPane.showInputDialog(null, "If you would like another quote enter 1, if not enter any other number");
         stop = Integer.parseInt(options);



      } while (stop == 1 && tryCount < 6);   //End do-while loop after 5 tries or user termination
     

      //Ask user for number of miles driven annually

      for (int yearCount = 1; yearCount <= 5; ++yearCount)

        {

           options = JOptionPane.showInputDialog(null, "Please enter the number of miles you will drive in year " + yearCount);

           miles = Integer.parseInt(options);
           milesDrivenAnnually = (milesDrivenAnnually + miles);

        }

      //Calculate the life cycle cost of the car
      costOfDrivingPerYear = (COST_PER_MILE * milesDrivenAnnually);
      lifeCycleCost = totalCost + costOfDrivingPerYear;

      //Output cost to user
      JOptionPane.showMessageDialog(null, " The cost of the Car you chose is " + dollar.format(totalCost) + "\n The approximate cost of driving for five years is " +  dollar.format(costOfDrivingPerYear) + "\n The number of miles you drove in five years was " + milesDrivenAnnually + "\n The life cycle cost of your car is " +  dollar.format(lifeCycleCost));

   } //End main method

} //End class

```

---

### Post by Tony Flury on 2009-02-13
I don't really know java - but look at the names of the variables you are using to store your input data, and compare that with the name of the variables that you are actually testing in the if statement.

Unless java is far more horrribly esoteric than i think it is, then i think your problem lies there.

---

