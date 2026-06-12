---
title: "C++ help plz :)"
date: 2008-12-01
forum: Programming Talk
---

### Post by feedmeh8 on 2008-12-01
So im a little stuck on a few programs i have to do by december 13. I got so much help from this community in setting up my first Linux OS, i figured i would ask here :p 

I am using Borland C++ 

_Question : Write a C program to accept three numbers from the user and print the smallest, largest and sum._

What I have done (that's not quite working out) :

```
#include<stdio.h>

#include<dos.h>



void main()

{



/* Declare Variables */

int numone, numtwo, numthree;



/* Print message to screen and accept user input */

printf("\n Enter a number : ");

scanf("%d",&numone);



printf("\n Enter another : ");

scanf("%d",&numtwo);



printf("\n One more : ");

scanf("%d",&numthree);



for(numone > numtwo, numthree)

{

  printf("\n The Largest number is : %d",numone);

}

for(numtwo > numone, numthree)

{

  printf("\n The Largest number is : %d",numtwo);

}

for(numthree > numone, numtwo);

{

  printf("\n The Largest number is : %d",numthree);

}



sleep(10);



}  

```

I know that all i have (incorrectly) so far is the 'largest' part, but i figured if i got that down i can manage the rest. ty :)

---

### Post by dribeas on 2008-12-01
Start reading a tutorial on either C or C++ (your code is plain C, not really C++). You need quite some learning with the basics, control structures in the language...

---

### Post by albandy on 2008-12-01
If we do your homework you'll never learn.
I recomend you read the bubble sort algorithm, and sort it using a loop, I think the objective of this program is to learn how to sort things.

Imagine that you have to sort 1000 numbers. you cant do it by hand.

[http://en.wikipedia.org/wiki/Bubble_sort](http://en.wikipedia.org/wiki/Bubble_sort)

and why are you using de "for" instruction? "for" works like "while" (well a bit diferent)

and if you want to compare 2 numbers use if:

if (a>b) printf("\na is greater");
else printf("b is greater or equal");

---

### Post by feedmeh8 on 2008-12-01
If anyone knows of any online tutorials i would appreciate a link :) I have been on google for a few hours now and seem to only be able to find answers that are not quite answering my question :p

---

### Post by albandy on 2008-12-01
for me this The best book of C: "The Ansi C" by Kerningan & Ritchie

C was designed by Dennis Ritchie

[http://www.docstoc.com/docs/293282/Kerningan-y--Ritchie---The-C-programming-language](http://www.docstoc.com/docs/293282/Kerningan-y--Ritchie---The-C-programming-language)

---

### Post by EV500B on 2008-12-01
> **feedmeh8 said:**
> If anyone knows of any online tutorials i would appreciate a link :) I have been on google for a few hours now and seem to only be able to find answers that are not quite answering my question :p
You can try this site [http://www.cprogramming.com/tutorial.html](http://www.cprogramming.com/tutorial.html)
or if you know french, you can use the tutorial which I'm hosting
 :arrow: [http://ev500b.co.cc/Cours_cpp/book1.html ]("http://ev500b.co.cc/Cours_cpp/book1.html")[]("http://ev500b.co.cc/Tutorials/C%20for%20Dummies,%202nd%20Edition.pdf")

---

