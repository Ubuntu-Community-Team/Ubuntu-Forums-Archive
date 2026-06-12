---
title: "C programming: getchar() bug"
date: 2009-06-28
forum: Programming Talk
---

### Post by dwalker0044 on 2009-06-28
Hi everyone,

I have a really annoying bug in a program I'm writing at the moment.

What I would like to happen is for the main menu of the program to be displayed initially and after the user is ask to enter a number which corresponds to an action. Actions available are currently only: **0 = run program** and **1 = quit**. If the user chooses to run the program, then after execution of "**Function_1**" the we exit the switch statement and the function is called again due to the while(1) loop in main - this is give the user possibility of running the program again or quitting.

However, on second entering of the "**Program_Start**" function, the getchar() doesn't seem to work. It appears not to wait for user input (or accepts NULL?) which forces the switch statement to enter its default state. On third entry it then works as expected.You can see this happening in the terminal output when it says: "User response was: **(blank)**"

In line 27 of the program sample, I provide a 'workaround' (uncomment it and then compile and run the program, the output will now be correct apart from **c** is reassigned as '\0') by calling getchar() a second time to get the fault out of the system, but I don't want to do this and hope someone could enlighten me to this strange behaviour.

```
#include<stdio.h>
#include<stdlib.h>

void Program_Start(void);
void Print_Menu(void);
void Function_1(void);

int main(void) {
	
	while(1) {
		Program_Start();
	}
}

void Program_Start(void) {
	
	static char c;

	Print_Menu();

	c = getchar();
		
	switch( c ) {
		case '0':
			Function_1();
			// this next line is a workaround to 'correct' the getchar			
			//c = getchar();
			break;
		case '1':
                        exit(0);
			break;
		default:
			printf("Bad program state, try again: \n");
			break;
	}
	printf("User response was: %c\n\n", c);
}

void Print_Menu(void) {

	printf("What would you like to do?: \n");
	printf("\t0. Run Program\n\t1. Quit\n");
	printf("\nPlease enter a number which corresponds to your decision: \n");
}

void Function_1(void) {

	printf("\nRun Program from here\n");
	printf("*** Program finishes here*** \n\n");
}
```

A silly little problem, but I'd really appreciate any help!

---

### Post by monraaf on 2009-06-28
> **dwalker0044 said:**
> 
However, on second entering of the "**Program_Start**" function, the getchar() doesn't seem to work. It appears not to wait for user input (or accepts NULL?)

Or it gets the newline that's still in the buffer?

---

### Post by dwalker0044 on 2009-06-28
Hi monraaf,

How would be the correct way of handling the input so I don't take the newline character?

Many thanks

---

### Post by monraaf on 2009-06-28
Just flush the buffer, e.g. calling getchar till you get a newline.

---

### Post by dwalker0044 on 2009-06-28
Ah ok, so I've just inserted: 

getchar(); after 

c = getchar();

which seems to work. Also found [http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392]("http://faq.cprogramming.com/cgi-bin/smartfaq.cgi?answer=1044873249&id=1043284392") which may be useful for other beginners.

Thanks again monraaf

---

