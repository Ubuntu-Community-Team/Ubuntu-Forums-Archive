---
title: "some help with create a c program to find SQUARE-FREE NUMBERS!!!"
date: 2008-11-05
forum: Programming Talk
---

### Post by fibonacci87 on 2008-11-05
hallo.i want to create a program to find square-free numbers.      my thought is this:all numbers can be represented like a unique prime factoriazation..if in this factorial a prime number appears more than once,then,this number is not a square-free number.        e.x.:4=2.2 its not a square-free                                    :8=2.2.2 its not a square-free                                      :10=2.5 its a sqare-free                                            :18=2.3.3 its not a square-free                                     :30=2.3.5 its a square-free                                         ....                                                                 {{{a square-free integer is one divisible by no perfect square except one..for example:10 is a sqare-free but 18 its not,as its divisible by 9=3^2}}}                                               Can anybody help with the construction of this algorithm??thank you a priori..

---

### Post by LaRoza on 2008-11-05
First read this: [http://ubuntuforums.org/showthread.php?t=717011](http://ubuntuforums.org/showthread.php?t=717011)

If it looks like a duck...

---

### Post by fibonacci87 on 2008-11-05
i am sorry.you are right,my false.i didnt want to cheat or anything like this.its a homework obviously i will not deny it,but i wanted to have an opinion about how to start working on this.the thought i described before is all mine and i think the most quick..i prove that i know how to solve it with mathematics but i have some problems with the program creation..i will try harder and then you may help me with the code..i am really sorry,i didnt want to fool you..

---

### Post by Lux Perpetua on 2008-11-05
If you're familiar with the Sieve of Eratosthenes, then it's not very hard to modify it to filter squarefree numbers instead of prime numbers. If you're not familiar with it, then it's worth learning about it.

---

### Post by Luggy on 2008-11-06
So if I understand you correctly, you are looking for numbers that, when square rooted, do NOT produce integer values.

The cmath library has a function to calculate the square root of a number.
I'd compare the square of a number verses the integer cast of the square of a number. If they don't match then you have a square-free number.

---

### Post by Lux Perpetua on 2008-11-06
You're thinking of perfect squares. A squarefree number is one that is not even *divisible* by any perfect square (besides 1). For example, 12 is not a perfect square, but it is not squarefree, either, since it is divisible by 4. It's very easy to check whether an integer is a perfect square, as you point out, but it's comparatively difficult to determine if a number is squarefree.

---

### Post by Luggy on 2008-11-06
> **Lux Perpetua said:**
> You're thinking of perfect squares. A squarefree number is one that is not even *divisible* by any perfect square (besides 1). For example, 12 is not a perfect square, but it is not squarefree, either, since it is divisible by 4. It's very easy to check whether an integer is a perfect square, as you point out, but it's comparatively difficult to determine if a number is squarefree.

Ah, I see. I understand now why this problem would take a little bit more thought.

---

### Post by fibonacci87 on 2008-11-07
this is not a c code,i know it,its just a code that i learn at high-school.i think(if its correct)it is the sieve of eratosthenis,can you help me modify it to find square-free numbers?                                ```

flag = true
if (&#925; mod 2 = 0 and &#925; !=2) 
         flag = false
else
    if (&#925; mod 3 = 0 and &#925; != 3) 
         flag = false
    else
         x = integer part of(sqr(&#925;))
         i = 5
         while (i <= x and flag = true)
               if (&#925; mod i = 0 or &#925; mod (i + 2) = 0) 
                       flag = false
               endif
               i = i + 6
         wend
     endif
endif
if flag = true 
          write 'is prime'
else
          write 'it is not prime'
andif
```

---

### Post by Tony Flury on 2008-11-07
Well you have that - make it in to a function that returns a true or false if the input is a prime.

You can then use that function to find the prime factors of your input.

Does not sound that difficult - but then again - this is your homework not ours.

I think you will find that nobody is going to write your code for you - but we might help in giving you some pointers to the write direction.

---

### Post by fibonacci87 on 2008-11-13
```
#include <stdio.h>
#include <math.h>
#define NUMBER 
main()
{
      int m,n,i,count2=0,count3=0,count4=0,count5=00;
      n=NUMBER;
      
      while (n%2==0)      
      {
            count2+=1; 
            n/=2;
       }
     
     while (n%3==0)
     {
           count3+=1;
           n/=3;
     }
     if ((count2>1) || (count3 >1))  printf(" %d is not square-free\n",NUMBER);
     
     m=floor(sqrt(n))+1;
     i=6;
     
     while(i<m+1)
     {
                while((n%(i-1))==0) 
           {
               count4+=1;
               n/=(i-1);
           }
            while((n%(i+1))==0)
           {
                count5+=1;
                printf("%d %d %d %d\n",count5,n,i,m);
                n/=(i+1);
           }
            i+=6;
           if ((count4>1) || (count5>1)) printf(" %d is not square-free\n",NUMBER);
           }
           
           if ((count2<=1)&& (count3<=1)&& (count4<=1)&& (count5<=1))
     printf("%d is square-free\n",NUMBER);
     system("PAUSE");
     return 0;
     }

                 

```
this is my code.but i have a litle problem:when i insert a big number which its not  square free,it print's, once that "is not square-free" and once that"is square-free".what happening???for numbers that its square free its working fine.plz some help...

---

### Post by Tony Flury on 2008-11-13
Without comments or meaningful variable names it is very difficult to debug your code.

a good tip is to learn to use gbd (a debugger) so you can step through your code line by line, and identify the values of your variables as your code runs.

The other way to do it is to work it out on paper, and pretend you are the computer.

---

### Post by fibonacci87 on 2008-11-13
my problem is when the program finds a number ,which is not square-free ,to stop  checking it anymore..probably the mistake is with some 'if'.i try to use the command break; but i make it worse..anyway thanks,and if you have any new idea i will gladly to hear it

---

### Post by Tony Flury on 2008-11-13
The problem is it is very difficult for anyone else to help with your code because it is not clear what it is doing i.e. what do all the variables do etc.

why not at least try to add in some comments to your code, and use some consistent formatting - i might help you find the bug, or at least help us to help you.

When commenting - try to describe what the code is doing and why.

---

### Post by fibonacci87 on 2008-11-13
you are right.sorry.i will try to fix it and have some comments.i forgot it at all that its difficult to understand without comments.i will post later again.thanks!

---

### Post by Strike4!! on 2008-12-12
Oh boy someone just played a joke on you... there is no known polynomial time algorithm for recognizing squarefree integers or for computing the squarefree part of an integer.
In fact, if you solve this problem you can think about the Fields Medal, because you would have solved the problem of computing the ring of integers of an arbitrary algebraic number field. And that leads to some very interesting stuff...

So i guess what you're really looking for is an algorithm for finding, **within a certain range of values!!!**, if an integer is squarefree or not.
Well, then you can take some different paths. 
You can have a file with a sieve, and the problem gets trivial. 
You can not have a sieve on a file, but generate it when running your program, and check out against your number -this is the classic exercise-. 
You can generate not the sieve, but all of the non-squarefree numbers in the range, and match against your number -a different version of the previous possibility-. 
Or you can jump-start into the abyssal mysteries of mathematics, and try to generate a decent Mobius function, and check about processing time having in mind that the asymptotic number of freesquare integers =< n is given by Q(n)=(6n/pi**2)+O(sqrt(n)), so is around 0,61... -a pretty filled package of numbers no matter what range you're looking through-

Good luck on your research, and about the program, well, the code you wrote will give wrong results with numbers starting at very low values -that is it's usefull in a veeeery short range-, so i guess you better write a Sieve, then a program using it, and only after that you will be able to deal properly with the dinamical checking of properties like this in a given number.

Now it's up to you to deal with the information in this post. You are the one running the show in your education now.
Have fun!!!!!!!!!!!!!


PS: Before coding anything else, please feel free to post what is the ALGORITHM you're planning to use. I went through the painful experience of hacking your code. Is not just not commented and blah blah blah... is basically wrong, it will give you lots of wrong results. And the flaws -there are more than one- are in the algorithm you are trying to use. So post a proper algorithm for whatever you want to do, and we can check it to see if and on what range it works :popcorn:
Come on, do it. Maths are fun!!

---

