---
title: "Need help with a method for converting a double to an int in C# !"
date: 2012-10-20
forum: Programming Talk
---

### Post by Egonosaur on 2012-10-20
Hello fellas!

Does anyone here know how to make a method in C# for converting a double input lets say 0.73 to make it return the int 73 ?

Thanks in advance!

---

### Post by trent.josephsen on 2012-10-20
I don't understand your question. Is it

1) What is the syntax to write a method in C#?

or

2) What algorithm would convert a floating point number, say 0.73, to the integer 73?

1) is a homework question, just a Google search away. 2) may be pretty simple or moderately complex depending on exactly what you want to do with other numbers (e.g., what about 0.7? 0.725? 0.729999999999?)

---

### Post by Egonosaur on 2012-10-20
I wonder what the algorithm would be to convert the floating point number 0.73 to integer 73. 
I want to make a method to do the operation, for example if I call my method Program.ToPercentage(0,73) the console will print just 73.

Is it possible to start the method with:

static int ToPercentage(double floatingpointnmbr)


I'm very new to programming and I'm learning how to make methods in C# at the moment.
I appreciate any help I can get!

---

### Post by Odexios on 2012-10-20
> **Egonosaur said:**
> I wonder what the algorithm would be to convert the floating point number 0.73 to integer 73. 
I want to make a method to do the operation, for example if I call my method Program.ToPercentage(0,73) the console will print just 73.

Is it possible to start the method with:

static int ToPercentage(double floatingpointnmbr)


I'm very new to programming and I'm learning how to make methods in C# at the moment.
I appreciate any help I can get!
What should be the output of Program.ToPercentage(0.731)? Should it print 731, 73, or the non integer number 73.1? The name of the function would suggest that what you need is to multiply the number by 100.

---

### Post by Egonosaur on 2012-10-20
> **Odexios said:**
> What should be the output of Program.ToPercentage(0.731)? Should it print 731, 73, or the non integer number 73.1? The name of the function would suggest that what you need is to multiply the number by 100.


I want the program to print out the integer 73

---

### Post by trent.josephsen on 2012-10-20
You'll get better responses if you start by trying to write code and post what you have when you run into problems. Even if it doesn't work, it shows you're serious about putting in the effort and aren't just trying to get free answers for your homework.

---

### Post by Egonosaur on 2012-10-20
> **trent.josephsen said:**
> You'll get better responses if you start by trying to write code and post what you have when you run into problems. Even if it doesn't work, it shows you're serious about putting in the effort and aren't just trying to get free answers for your homework.

Yeah, sorry guys for confusing you so much, my first time asking for help about programming on a forum. This problem was a exercise from my book that wanted me to create the method "ToPercentage" however I think "ToInt" would be a better name for it. I finally figured out how to do it and I will post the code so it might come to use for others with similar problems.

```

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace ToInt
{
    class Program
    {
        static int ToInt(double doubleFloatingPoint) //The method that converts doubles to ints.
        {
            double dblOneHundred = 100;
            double theCalculation = (dblOneHundred * doubleFloatingPoint);
            int calculation = Convert.ToInt32(theCalculation);
            return calculation;

        }
        static void Main(string[] args)
        {
            int mainCalculation = ToInt(0.73); 
            Console.WriteLine(mainCalculation); //To Print out the number.

            Console.WriteLine();
            Console.WriteLine();
            Console.WriteLine("Press ENTER to exit...");
            Console.ReadLine(); //To be able to take a look at your number.


        }
    }
}


```

Thanks alot for your help guys I really appreciate it! :)

---

