---
title: "C dynamic string problem"
date: 2009-04-26
forum: Programming Talk
---

### Post by xboxbman on 2009-04-26
I am making a simple program that takes user input in the form of a string.  Because it asks for input which could be of variable length, the strings are allocated dynamic memory.  At the end of the program, it displays a menu that user is supposed to select an option from, but it doesn't ask the user for input.  Here's the code and the output, if anyone can help me figure out what the problem, it would be appreciated.

```
#include <stdio.h>

#include <math.h>

#include <stdlib.h>



int main(){



	int age, i, choice;

	long height, weight;

	char *name, *homeTown, *style, *nick, temp[25];



	

	name = (char *) malloc (sizeof(char));

	homeTown = (char *) malloc (sizeof(char));

	style = (char *) malloc (sizeof(char));

	nick = (char *) malloc (sizeof(char));

	name = NULL;

	homeTown = NULL;
	style = NULL;
	nick = NULL;

	choice = 3;

	printf("Welcome to the Fighter Creater!!\n");

	printf("Please fill in the information below\n\n");



	printf("Fighter Name -> ");

	scanf("%s",&temp);
	name = temp;

	printf("\n");

	printf("Fighter NickName -> ");
	scanf("%s",&temp);
	nick = temp;
	printf("\n");

	printf("Fighter Age -> ");

	scanf("%d",&age);

	printf("\n");

	printf("Fighter Height -> ");

	scanf("%lf",&height);

	printf("\n");

	printf("Fighter Weight -> ");

	scanf("%lf",&weight);

	printf("\n");

	printf("Fighter Home Town -> ");

	scanf("%homeTown",&temp);
	homeTown = temp;

	printf("\n");

	

	printf("You may select a style from the list, or enter a custom style\n");



	printf("\t1.  BJJ\n");

	printf("\t2.  Muay Thai\n");

	printf("\t3.  Wrestler\n");

	printf("\t4.  Karate\n");

	printf("\t5.  Boxing\n");

	printf("\t6.  Custom Style\n");



	printf("Your choice -> ");

	scanf("%d", &choice);

	printf("/n");



		switch(choice){

			case 1:

				style = "BJJ";

				break;

			case 2:

				style = "Muay Thai";

				break;

			case 3:

				style = "Wrestler";

				break;

			case 4:

				style = "Karate";

				break;

			case 5:

				style = "Boxing";

				break;

			case 6:

				printf("Enter your custom style:  ");

				scanf("%s",&style);

				printf("/n");

				break;

			default:

				printf("Wrong answer, try again dillhole\n");

				break;

			}

	




	printf("Fighter Name -> %s",&name);

	printf("\n");

	printf("Fighter Age -> %d",age);

	printf("\n");

	printf("Fighter Height -> %.lf",height);

	printf("\n");

	printf("Fighter Weight -> %lf",weight);

	printf("\n");

	printf("Fighter Home Town -> %homeTown",&homeTown);

	printf("\n");



return(0);

}
```

OUTPUT

```
Welcome to the Fighter Creater!!
Please fill in the information below

Fighter Name -> Brendan

Fighter NickName -> bman

Fighter Age -> 22

Fighter Height -> 185

Fighter Weight -> 88

Fighter Home Town -> guelph

You may select a style from the list, or enter a custom style
	1.  BJJ
	2.  Muay Thai
	3.  Wrestler
	4.  Karate
	5.  Boxing
	6.  Custom Style
Your choice -> /nWrong answer, try again dillhole
Fighter Name -> &#65533;&#65533;
Fighter Age -> 22
Fighter Height -> 0
Fighter Weight -> 0.000000
Fighter Home Town -> 115610meTown

```

thanks everyone for the help

---

### Post by monkeyking on 2009-04-26
You need a loop in you main somehting like

[PHP]
int main(){
while(user hasnt pressed q)
  YOUR PROGRAM

}
[/PHP]

---

### Post by dwhitney67 on 2009-04-26
> **xboxbman said:**
> ....Because it asks for input which could be of variable length, the strings are allocated dynamic memory.

You should have a better reason to allocate memory than this.  In fact, this is a case where allocating memory would not buy you anything over defining a fixed array; unless of course you plan to read in one character at a time using non-blocking I/O, and reallocate more memory should the user input more data than you first anticipated.

With respect to using scanf() to read strings, avoid using this function.  Use fgets() instead, since it is easier to convey to the function the length of the string that you are expecting.

If you insist in using scanf(), then at least use it properly when reading a string.  Passing the address of an array that is already treated as an address is overkill.

The proper syntax is:
```

char string[20];

scanf("%s", string);   // note that the & is not required

// or better yet...

fgets(string, sizeof(string), stdin);

```
The only caveat with fgets() is that it will include the terminating carriage-return (space permitting) in your string.  scanf() will not do this, but will leave the carriage return in the stream for your next scanf() to come across.

Countless people have been bitten when attempting to read an int, followed by an attempt to read a string, and then wonder why the program doesn't pause to allow the user to input the string.  Well, it is because of the carriage return sitting in the stdin stream.

> **xboxbman said:**
> 
At the end of the program, it displays a menu that user is supposed to select an option from, but it doesn't ask the user for input.  Here's the code and the output, if anyone can help me figure out what the problem, it would be appreciated.
Perhaps following monkeyking's advice is what is needed; but hopefully the information above will assist you too.

---

