---
title: "error in compiling and running a C program"
date: 2013-10-30
forum: Packaging and Compiling Programs
---

### Post by mariya_nikova on 2013-10-30
I have just started learning C programming and yesterday I have compiled HelloWorld.

Today I finally got the book I have ordered on C-programming and there is an example of the program which I should compile. But there is some error (I checked it several times and it is the same as in the book) and I can't figure out what is wrong.

So this is what I put in my text editor (and save it as cards.c file):

#include<stdio.h>
#include<stdlib.h>
int main()
{
char card_name[3];
puts("Enter the card_name: ");
scanf("%2s", card_name);
int val = 0;
if (card_name[0] == 'K') {
   val = 10;
} esle if (card_name[0] == 'Q') {
   val = 10;
} else if (card_name[0] == 'J') {
   val = 10;
} else if (card_name[0] == 'A') {
   val = 11;
} else {
   val = atoi(card_name);
}
printf("The card value is: %i\n", val);
return 0;
}


Then I've tried to compile it in a command line with $ gcc cards.c -o cards

And as a result I see this in the command line:

cards.c: In function ‘main’:
cards.c:11:3: error: ‘esle’ undeclared (first use in this function)
cards.c:11:3: note: each undeclared identifier is reported only once for each function it appears in
cards.c:11:8: error: expected ‘;’ before ‘if’



What is the problem?

---

### Post by partloer on 2013-10-30
You have mispelled 'else' after the first if statement.  That should fix it.

---

### Post by mariya_nikova on 2013-10-30
oh yes! That was dumb :-s 

Thanks!

---

