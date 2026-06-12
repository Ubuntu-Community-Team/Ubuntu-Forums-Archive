---
title: "Little Help in Java"
date: 2012-10-06
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-06
Little help i don't understand where the error is.. 

The Task is 
  

[COLOR=Red]A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 [IMG]http://projecteuler.net/images/symbol_times.gif[/IMG] 99.[/COLOR]
 [COLOR=Red]Find the largest palindrome made from the product of two 3-digit numbers.[/COLOR]
  

class Prpal 
{
    public static void main(String[] args) 
    {
        int i,j;
        long a,k;
        long rev=0;
        //Repeating the Loop itself from 999 to 100
        for ( i=100; i>1000 ; i-- ) 
        {
        // Repeating the loop to multiply i with numbers from 999 to 100 Each time i value is increased
            for (j =100; j<i; j++) 
            {
                k=i*j;
        // Logic for Reversing The Number
                a=k%10;
                k=k/10;
                rev=rev*10+a;

        // Checking weather the given number is palindrome or not??
                if (k==rev)
                {
                    System.out.println("The Number "+k+"is Palindrome");
                }
                
            }
        }
    }
}

It is compiling without Errors yet no output is displaying.. :(
I can't understand where the error is....

---

### Post by albandy on 2012-10-06
The first for loop condition never works:

for (i=100; i>1000; i--)

if i=100 and the condition to enter the loop is i > 1000, this never will enter the loop.

---

### Post by Mohan1289 on 2012-10-06
> **albandy said:**
> The first for loop condition never works:

for (i=100; i>1000; i--)

if i=100 and the condition to enter the loop is i > 1000, this never will enter the loop.

Nope no result same as Blank........ :(

i changed for loop like

for(i=100;i<1000;i++)
{
   for(j=100;j<i;j++)
     {
           k=i*j;
           a=k%10;
           k=k/10;
           rev=rev*10+a;
           if (k==rev)
            {
             System.out.println("The Number "+k+"is Palindrome");
             }
         }
}

yet no avail

---

### Post by spjackson on 2012-10-06
That implementation of the test for a palindromic number is not what was discussed before. It is simply wrong. Go back to the previous thread and implement that - if you are still minded not to use a string. Hint - you need another loop.

Here's an example of what your code is doing:
```

k = 423324
a=4
k=42332
rev=0*10+4
if (42332 == 4)

```Put your algorithm for testing the palindromic number into a separate function that you can test. Test it.

Also, your inner loop means that you will never multiply a number by itself. I don't know whether that is your intent or not. Perhaps there are no squares that are palindromic in the given range - I don't know.

---

### Post by Mohan1289 on 2012-10-06
> **spjackson said:**
> That implementation of the test for a palindromic number is not what was discussed before. It is simply wrong. Go back to the previous thread and implement that - if you are still minded not to use a string. Hint - you need another loop.

Here's an example of what your code is doing:
```

k = 423324
a=4
k=42332
rev=0*10+4
if (42332 == 4)

```Put your algorithm for testing the palindromic number into a separate function that you can test. Test it.

Also, your inner loop means that you will never multiply a number by itself. I don't know whether that is your intent or not. Perhaps there are no squares that are palindromic in the given range - I don't know.

yes yes i see my flaw now.. i have to stop the loop when it reaches to Zero... I mean when all the numbers are over.. now it is just doing only once right???

---

