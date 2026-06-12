---
title: "C# Programming With Mono"
date: 2011-11-02
forum: New to Ubuntu
---

### Post by Tarast on 2011-11-02
Hi guys i need some help with a bit of coding, i cannot finish my simple assignment program can someone help me to finish off please

here is my task:

  	 	 	 	 	 	   The bookstore has 3 books costing £9.99, £0.50 and £3.45.
  Add £2.50 for postage.
  Give the customer a loyalty bonus by subtracting £0.30p per book.
  Use variables for all values.
  Provide a variable table and write the code to calculate the total cost of the books
 
here is my program and what i done so far but i cant figure out how to finish it off:

// This is a simple program that calculates the total cost of the books

// Namespace Declaration
using System;

// Program start class
class Bookstore
{
    // Main begins program execution
    public static void Main()
    {
        /* 
           Declaring 3 variables   ( "book1" "book2" "book3" )
           Assigning a data type   ( "double" ) 
           Givining initial values ( "9.99" "0.50" "3.45" )
        */
                 
        double book1 = 9.99; 
        double book2 = 0.50;
        double book3 = 3.45;
    
        // Using extra variable for "loyalty bonus"
        
        double loyaltyBonus = 0.30;
        double loyaltyBonus = double.Parse("0.30");

---

### Post by hailtothethief on 2011-11-02
First of all, ABT is not the place to post for programming homework help.

Beyond that, you haven't provided enough information for us to properly help you. Specifically, how are the quantities of books purchased passed to your program? I doubt you'd be parsing command line arguments, but it's possible.

Anyway, something like:

```
public static double totalCost(double count1, double count2, double count3) {
   double cost = 0;

   double book1 = 9.99; 
   double book2 = 0.50;
   double book3 = 3.45;

   double loyaltyBonus = 0.30;

   double postage = 2.50;

   cost = count1 * book1 + count2 * book2 + count3 * book3;
   cost -= loyaltyBonus * (count1 + count2 + count3);
   cost += postage;
   
   return cost;
}
```

would return the value given the number of books of each type. _Pay more attention in class!_ This is very trivial stuff which should give you no trouble if you listen to your instructor.

---

### Post by coffeecat on 2011-11-02
> **hailtothethief said:**
> First of all, ABT is not the place to post for programming homework help.

@Tarast, nor is any part of the forum. 

Thread closed.

---

