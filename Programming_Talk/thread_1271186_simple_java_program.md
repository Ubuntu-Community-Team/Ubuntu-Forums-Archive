---
title: "simple java program"
date: 2009-09-20
forum: Programming Talk
---

### Post by nathang1392 on 2009-09-20
im writing a program that tries to simulate the flipping of a coin. it generates a random number and then uses that number to indicate if it is a head or a tail. i have that part working, but the program is supposed to output like this:[http://tinypic.com/view.php?pic=2z8vl78&s=4](http://tinypic.com/view.php?pic=2z8vl78&s=4)
any help would be appreciated. 

```

 /** 
  * Write a description of class HeadsOrTailsV1 here. 
  *  
  * @author (your name)  
  * @version (a version number or a date) 
  */  
 import java.util.Scanner;  
 public class HeadsOrTailsV1  
 {  
   public static void main(String [] args)  
     {  
         Scanner in;  
         in = new Scanner(System.in);  
           
         System.out.println("Enter the number of flips: ");  
         int numberOfFlips = in.nextInt();  
         int numberOfHeads = 0;  
         int numberOfTails = numberOfFlips - numberOfHeads;
         System.out.println("\n");  
           
         double randomNumber = 0;  
         int counter = 0;             
         while(counter < numberOfFlips)  
         {  
               
             randomNumber = Math.random();  
             counter ++;  
               
               
             boolean isTails = randomNumber > .5;  
               
             if (isTails)  {  
                 System.out.print("\nT " + randomNumber);  
                 numberOfTails++;
                 
             }  
             else {   
                 System.out.print("\nH " + randomNumber);  
                 numberOfHeads++; 
                 
                 
                 
             }  
             System.out.println("\nNumber of Heads: " + numberOfHeads);
             System.out.println("\nNumber of Tails: " + numberOfTails);
               
               
         }  
          
         
           
     }  
}

```

---

### Post by Renée Jade on 2009-09-20
I'm an a brand new Ubuntu install and I haven't installed JDK yet so I can't compile it. Can you tell me what it outputs as it is?

---

### Post by Renée Jade on 2009-09-20
Also, numberOfTails should be initialised to zero and you should be using a bounded (i.e. for) loop, not an unbounded (i.e. while) loop. I suggest you have a look at System.out.printf() for a much more powerful and flexible print function too - you'll never look back.

---

### Post by nathang1392 on 2009-09-20
> Number of Tails: 11

T 0.8145386864009515
Number of Heads: 1

Number of Tails: 13

T 0.5256666045038697
Number of Heads: 2

Number of Tails: 15

T 0.5797177749625496
Number of Heads: 3

Number of Tails: 17

H 0.09433232148290327
Number of Heads: 5

Number of Tails: 18

T 0.5798698367636074
Number of Heads: 6

Number of Tails: 20

T 0.6579312191200797
Number of Heads: 7

Number of Tails: 22

T 0.5671814995772273
Number of Heads: 8

Number of Tails: 24

H 0.29725882610632626
Number of Heads: 10

Number of Tails: 25

T 0.6941613183640829
Number of Heads: 11

Number of Tails: 27
it is pretty rambled. at one point i had it all correct, except that i wanted it to tell me the number of heads and tails in the output, and then it just turned into a mess.

---

### Post by sunchiqua on 2009-09-20
Does this look better ( can't compile it, so .. not sure if it works the way you want ) ?

[php]/** 
  * Write a description of class HeadsOrTailsV1 here. 
  *  
  * @author (your name)  
  * @version (a version number or a date) 
  */  
 import java.util.Scanner;  
 public class HeadsOrTailsV1  
 {  
   public static void main(String [] args)  
     {  
         Scanner in;  
         in = new Scanner(System.in);  
           
         System.out.println("Enter the number of flips: ");  
         int numberOfFlips = in.nextInt();  
         int numberOfHeads = 0;  
         int numberOfTails = numberOfFlips - numberOfHeads;
         System.out.println("\n");  
           
         double randomNumber = 0;  
         int counter = 0;             
         while(counter < numberOfFlips)  
         {  
               
             randomNumber = Math.random();  
             counter ++;  
               
               
             boolean isTails = randomNumber > .5;  
               
             if (isTails)  {  
                 System.out.print("\nT " + randomNumber);  
                 numberOfTails++;
             }  
             else {   
                 System.out.print("\nH " + randomNumber);  
                 numberOfHeads++; 
             }  
                  
         }  
          
         System.out.println("\nNumber of Heads: " + numberOfHeads);
         System.out.println("\nNumber of Tails: " + numberOfTails);
           
     }  
}[/php]

Oh, and .. don't touch tails before you enter the loop - if you set flips to 10, tails will be defaulted to -10, which means, it can end up with being zero.

---

### Post by Renée Jade on 2009-09-20
Yikes. Well, in addition to what I said in my earlier post, you also need to move your "print(numberOf...)" calls. I'm sure you can work out where they're meant to be.

---

### Post by nathang1392 on 2009-09-20
thanks jade and sun. you guys helped me out alot.

---

### Post by Renée Jade on 2009-09-20
That's alright mate. Have fun learning Java! :D

---

