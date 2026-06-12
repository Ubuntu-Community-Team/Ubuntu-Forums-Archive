---
title: "Java compiler error"
date: 2011-01-28
forum: Programming Talk
---

### Post by CaptainMark on 2011-01-28
Here the source for a real beginners java program i made, im pulling my hair out trying to spot my error, experienced users will probably
spot it straight away. The compiler tells me it cant find the symbol for the BufferedReader class but ive imported java.io.*

Ive already made a program that accepts user input and the syntax looks the same, obviously it isnt though, where have i slipped up??
```
// Tax Calculator
// Mark Skinner
// Created 28/01/2011

import java.text.DecimalFormat;
import java.io.*;

public class tax_calculator {
    
    public static void main(String args[]){

        // Declare and instantiate buffer
        BufferedReader reader;
        reader = new BufferedReader(new InputStreamReader(System.in));

        // Declare decimal precision
        DecimalFormat two_pnt = new DecimalFormat("0.00");

        // Declare Variables
        float amount = 0,
            tax_percent = 0,
            tax_amount = 0,
            total_amount = 0;
            
        String value = ""; 

        try{
            // Prompt input
            System.out.println("--------------£££ Tax Adder £££--------------");
            System.out.print("\nPlease enter your transaction amount: £");
            value = reader.readline();
            amount = Float.parseFloat(value);
            System.out.print("\nAnd please enter your tax percentage: ");
            value = reader.readline();
            tax_percent = Float.parseFloat(value);
            System.out.println("\n---------------------------------------------");
            System.out.print("\nYour bill of £" + two_pnt.format(amount));
            System.out.println(" plus a " + two_pnt.format(tax_amount) + "% tip:");
        } // End try
        catch (IOException ioe) {
            // Handle exceptions
            System.out.println("Input Output Error!");
        } // End Catch

        // Calculate Tax
        tax_amount = amount * (tax_percent /100);
        total_amount = amount + tax_amount;
        System.out.print("\nYou have to pay £" + two_pnt.format(tax_amount));
        System.out.print(" in tax.\n\n\tTotal Bill: £" + two_pnt.format(total_amount));
        System.out.print("\n\nPress enter to exit :");
        reader.readline();
    } // End main
} // End tax_calculator

```Error ```
mark@mark-desktop:~/Documents/programming/java/java_programming_for_absolute_beginners/chapter_2$ javac tax_calculator.java tax_calculator.java:31: cannot find symbol
symbol  : method readline()
location: class java.io.BufferedReader
            value = reader.readline();
                          ^
tax_calculator.java:34: cannot find symbol
symbol  : method readline()
location: class java.io.BufferedReader
            value = reader.readline();
                          ^
tax_calculator.java:51: cannot find symbol
symbol  : method readline()
location: class java.io.BufferedReader
        reader.readline();
              ^
3 errors

```

---

### Post by Some Penguin on 2011-01-28
read**L**ine

---

### Post by KdotJ on 2011-01-29
Some Penguin has you sorted there. 
Just some help, when you look at the error in the stack trace (printed out the the terminal when it won't compile) you can see it says cannot find symbol, and then explains what the symbol is. In your case it was the method readline() 
It's saying it can't find that method IN BufferedReader, not that it can't find BufferedReader itself

---

### Post by CaptainMark on 2011-01-30
Doh!! Thanks guys

---

