---
title: "(Java) Why does copying /w this copy() method that copies objects not take paramters?"
date: 2010-02-19
forum: Programming Talk
---

### Post by s3a on 2010-02-19
I am reading my text book and I am wondering why the copy() method that *copies the contents of objects* does not take parameters.

_**Here is source code from my text book:**_

**ObjectCopy class:**
```
/**

   This program uses the Stock class's copy method

   to create a copy of a Stock object.

*/



public class ObjectCopy

{

   public static void main(String[] args)

   {

      // Create a Stock object.

      Stock company1 = new Stock("XYZ", 9.62);

      

      // Declare a Stock variable

      Stock company2;

      

      // Make company2 reference a copy of the object

      // referenced by company1.

      company2 = company1.copy();

      

      // Display the contents of both objects.

      System.out.println("Company 1:\n" + company1);

      System.out.println();

      System.out.println("Company 2:\n" + company2);

      

      // Confirm that we actually have two objects.

      if (company1 == company2)

      {

         System.out.println("The company1 and company2 " +

                  "variables reference the same object.");

      }

      else

      {

         System.out.println("The company1 and company2 " +

                "variables reference different objects.");

      }

   }

}
```

**Stock Class Phase 3:**
```
/**

   The Stock class holds data about a stock.

*/



public class Stock

{

   private String symbol;     // Trading symbol of stock

   private double sharePrice; // Current price per share



   /**

      Constructor

      @param sym The stock's trading symbol.

      @param price The stock's share price.

   */



   public Stock(String sym, double price)

   {

      symbol = sym;

      sharePrice = price;

   }

   

   /**

      getSymbol method

      @return The stock's trading sysmbol.

   */

   

   public String getSymbol()

   {

      return symbol;

   }

   

   /**

      getSharePrice method

      @return The stock's share price

   */

   

   public double getSharePrice()

   {

      return sharePrice;

   }



   /**

      toString method

      @return A string indicating the object's

              trading symbol and share price.

   */

   

   public String toString()

   {

      // Create a string describing the stock.

      String str = "Trading symbol: " + symbol +

                   "\nShare price: " + sharePrice;

      

      // Return the string.

      return str;

   }



   /**

      The equals method compares two Stock objects.

      @param object2 A Stock object to compare to the

                     calling Stock object.

      @return true if the argument object is equal to

                   the calling object.

   */



   public boolean equals(Stock object2)

   {

      boolean status;

      

      // Determine whether this object's symbol and

      // sharePrice fields are equal to object2's

      // symbol and sharePrice fields.

      if (symbol.equals(object2.symbol) &&

          sharePrice == object2.sharePrice)

         status = true;  // Yes, the objects are equal.

      else

         status = false; // No, the objects are not equal.

      

      // Return the value in status.

      return status;

   }



   /**

      The copy method makes a copy of a Stock object.

      @return A reference to a copy of the calling object.

   */



   [B]public Stock copy()

   {

      // Create a new Stock object and initialize it

      // with the same data held by the calling object.

*      Stock copyObject = new Stock(symbol, sharePrice);*

      

      // Return a reference to the new object.

      return copyObject;

   }
[/B]
}

```

What I don't understand is why isn't the bold part of the *Stock Class Phase 3* taking any parameters? I ask this because, I do not understand how the line in italics in the same method, sends the *symbol* and *sharePrice* variables to the Stock class' constructor since I don't see it in the method at all.

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by era86 on 2010-02-19
Since the class has members that define the state of the object (symbol and sharePrice), and copy() is a method in the class usable by the object, all the copy() method does is create a NEW object of the same class with the same state variables as the calling object.

It's a rough explanation, but that is pretty much what happens.

---

### Post by falconindy on 2010-02-19
Is the constructor you're looking for not the first method defined in the class?
```
   private String symbol;     // Trading symbol of stock
   private double sharePrice; // Current price per share

   /**
      Constructor
      @param sym The stock's trading symbol.
      @param price The stock's share price.

   */   
   public Stock(String sym, double price)
   {
      symbol = sym;
      sharePrice = price;
   }
```
You're invoking a method which references a currently created object's attributes. Think of it as a constructor with pre-defined parameters. Consider the following:
```
...
Stock s = new Stock("GOOG", 542.24);
Stock s2 = new Stock(s.getSymbol(), s.getSharePrice());
Stock s3 = s.copy();
...
```
s2 and s3 are created in different ways, but contain the same data.

---

### Post by alexk82 on 2010-02-19
[B][I][B][I]symbol, sharePrice are instance variables which the method copy as access to,

if the author use the this.symbol and this.sharePrice it maybe easier to see
[/I][/B][/I][/B]

---

### Post by s3a on 2010-02-20
I think I didn't phrase my question right. I also think that I now get it though and it would be nice if someone could confirm that I am right. :)

The reason why it works is because

this happens:
// Create a Stock object.

Stock company1 = new Stock("XYZ", 9.62);

which assigns "contents" into the symbol and sharePrice variables and then the copy() method is in the same class as the location of the symbol and sharePrice variables so it can access their contents and make a new object. And finally, it returns the address of the new object.

Right?

---

