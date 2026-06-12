---
title: "Making change using for and while loops"
date: 2011-03-12
forum: Programming Talk
---

### Post by BrockStrongo on 2011-03-12
Here is another homework assignment that I am missing part of.
The program is a basic change calculator, but it includes a new coin called a "jonnie" valued at $1.21. The program is structured to first make standard change for the amount entered, it then uses a "for" loop to make change using 1 "jonnie", then 2 "jonnies" etc.. up to the maximum "jonnies" the amount entered could have. 
My problem is, the program is always going to display the last iteration of the "for" loop. 
I need a way to store each combination of change and only output the most efficient one.
I have got this program to work using strictly "while" loops but there is supposed to be a way using a "for" loop as well. 
Thank you very much to anyone who reads this.

here is what I have so far if anyone wants to look
[PHP]
#include <stdio.h>

int main()
{
    //set constants for value of coins
    int numCoins;
    int numJonnies,numToonies,numLoonies,numQuarters,numDimes,numNickles,numPennies;
    int maxJonnies;
    float input;
    float currentAmt;
    int maxCoins=1000;
    
   
    
   
    printf ("please input the a value between 0.00, and 100.00 \n");
    scanf ("%f", &input);
    currentAmt=input*100;
    maxJonnies =(input*100)/121;
    printf ("max Jonnies are: %d\n", maxJonnies);
    printf ("input: %5.2f\n",input);
    
    //start first loop, take out  n jonnies
for (numJonnies=0; numJonnies<=maxJonnies; numJonnies++)
          {
           numToonies=0;
           numLoonies=0;
           numQuarters=0;
           numDimes=0;
           numNickles=0; 
           numPennies=0;
                       
                                     
              currentAmt=input*100;
              currentAmt=currentAmt-(numJonnies*121);
              while (currentAmt>=200)
              {
                    currentAmt=currentAmt-200;
                    numToonies++;
              }
              
              while (currentAmt>=100)
              {
                    currentAmt=currentAmt-100;      
                    numLoonies++;
              } 
              while (currentAmt>=25)
              {
                    currentAmt=currentAmt-25;
                    numQuarters++;
              }
              while (currentAmt>=10)
              {
                    currentAmt=currentAmt-10;
                    numDimes++;
              }
              while (currentAmt>=5)
              {
                    currentAmt=currentAmt-5;
                    numNickles++;
              }
              while (currentAmt>=1)
              {
                    currentAmt=currentAmt-1;
                    numPennies++;
              }
              numCoins=numJonnies+numToonies+numLoonies+numQuarters+numDimes+
              numNickles+numPennies;
              
              
              if (numCoins<maxCoins)
                 maxCoins=numCoins;
             
                        
                 
                 
                 
    }// end forloop
                    
               
   numJonnies=numJonnies-1;     
   printf("current amount: %d\n",currentAmt);      
   printf("number of coins: %d\n",maxCoins);           
   printf("number of jonnies: %d\n",numJonnies);
   printf("number of toonies: %d\n",numToonies);
   printf("number of loonies: %d\n",numLoonies);
   printf("number of quarters: %d\n",numQuarters);
   printf("number of dimes: %d\n",numDimes);
   printf("number of nickles: %d\n",numNickles);
   printf("number of pennies: %d\n",numPennies);
              
         
   

    getchar();
    getchar();
    return 0;

}[/PHP]

---

### Post by Vaphell on 2011-03-13
you don't have to store all combinations, only the best one up to that moment and replace data if new one is better. You store number of coins already (if (numCoins<maxCoins) ...), just do the same with all the values for individual coins.

btw, do you know arrays? because you could get rid of all those while loops for each coin and do this with one universal construct. Array would store values of coins in a descending order (eg coin[0]=121; coin[1]=50; coin[2]=25;...) and calculating for 1 element of array would mean shifting to the next one and repeating the whole thing, until all elements are used.
Also you don't need to increase the counter by 1 coin at a time in your while loops. For example when you have 34 to fill you go with integer/modulo arithmetic where 34/10=3 with the remainder of 4 (and where % is modulus operator returning remainder 34%10=4). 3 will be the number of dimes - it's that simple :).

---

### Post by BrockStrongo on 2011-03-13
> **Vaphell said:**
> you don't have to store all combinations, only the best one up to that moment and replace data if new one is better. You store number of coins already (if (numCoins<maxCoins) ...), just do the same with all the values for individual coins.

:).


Thanks for the help. I was trying to use this approach, but at some point in the loops the numQuarters..... is going to be zero. When I put all these if statements in the loop I end up with an output of all zero's. 

Again, thanks for the help :)

---

### Post by Vaphell on 2011-03-13
is it about finding the combination with the lowest number of coins? if so, then nothing but numCoins should be able to trigger the subroutine storing the values. What you are saying suggests that you test each individual coin for the lowest number - no wonder you'd almost always get 0s... Or you had code that was parsed improperly and dumping the value for each coin was executed each time, not only when it met condition.
You simply need to expand THEN section of that SINGLE if (numCoins<maxCoins) condition to include not only new, lower number of coins (maxCoins) but also temporary values of individual nominals in similar way ( maxQuarters=numQuarters; ...). When loop ends you are guaranteed to have lowest number and precise combination of coins that matched that lowest number in these variables.

```

if (numCoins<maxCoins)
{
  maxCoins=numCoins;
//  max... for all kinds coins listed here too
}

```

---

### Post by BrockStrongo on 2011-03-13
thanks, I will work on this and post the result when I get it.
I really appreciate you ,Vaphell, taking the time to help me with this.

---

### Post by BrockStrongo on 2011-03-14
Here is what I got.  It seems to be working properly and returning the proper values.
 If anyone has any suggestions please let me know.
Thanks very much,
[PHP]
#include <stdio.h>

int main()
{
    //set constants for value of coins
    int numCoins;
    int numJonnies, jonniesUsed, numToonies,numLoonies,numQuarters,numDimes,numNickles,numPennies;
    int maxJonnies;
    float input;
    float currentAmt;
    int maxCoins=1000;
    int tooniesUsed,looniesUsed,quartersUsed,nicklesUsed,dimesUsed,penniesUsed;
    
    
   
    printf ("please input the a value between 0.00, and 100.00 \n");
    scanf ("%f", &input);
   
    maxJonnies = (int)(input*100)/121;
    

 
    //start first loop, take out  n jonnies
for (numJonnies=0; numJonnies<=maxJonnies; numJonnies++)
{
           numToonies=0;
           numLoonies=0;
           numQuarters=0;
           numDimes=0;
           numNickles=0; 
           numPennies=0;
                      
                                     
              currentAmt=input*100;
              
              currentAmt=currentAmt-(numJonnies*121);
              while (currentAmt>=200)
              {
                    currentAmt=currentAmt-200;
                    numToonies++;
              }
              
              while (currentAmt>=100)
              {
                    currentAmt=currentAmt-100;      
                    numLoonies++;
              } 
              while (currentAmt>=25)
              {
                    currentAmt=currentAmt-25;
                    numQuarters++;
              }
              while (currentAmt>=10)
              {
                    currentAmt=currentAmt-10;
                    numDimes++;
              }
              while (currentAmt>=5)
              {
                    currentAmt=currentAmt-5;
                    numNickles++;
              }
              while (currentAmt>=1)
              {
                    currentAmt=currentAmt-1;
                    numPennies++;
              }
              
              numCoins=numJonnies+numToonies+numLoonies+numQuarters+numDimes+
              numNickles+numPennies;
              
          //if lower number of coins is found save values    
              if (numCoins<maxCoins)
              {
                 maxCoins=numCoins;
                 jonniesUsed = numJonnies;
                 tooniesUsed=numToonies;
                 looniesUsed=numLoonies;
                 quartersUsed=numQuarters;
                 dimesUsed=numDimes;
                 nicklesUsed=numNickles;
                 penniesUsed=numPennies;
                 
              }
}  // end forloop            
  
      
         
   printf("number of coins: %d\n",maxCoins);
   
   if (jonniesUsed > 0 )
   {
       printf("number of jonnies: %d\n",jonniesUsed);           
   }
                             
   if (tooniesUsed > 0 )
   {
       printf("number of toonies: %d\n",tooniesUsed);           
   }
   
   if (looniesUsed > 0 )
   {
       printf("number of loonies: %d\n",looniesUsed);           
   }
   
   if (quartersUsed > 0 )
   {
       printf("number of quarters: %d\n",quartersUsed);           
   }
   
   if (dimesUsed > 0 )
   {
       printf("number of dimes: %d\n",dimesUsed);           
   }
   
   if (nicklesUsed > 0 )
   {
       printf("number of nickles: %d\n",nicklesUsed);           
   }
   
   if (penniesUsed > 0 )
   {
       printf("number of pennies: %d\n",penniesUsed);           
   }
   
         
   

    getchar();
    getchar();
    return 0;

}[/PHP]

---

