---
title: "My gcc is bad, how do I reset?"
date: 2007-10-10
forum: Programming Talk
---

### Post by osiris2258 on 2007-10-10
When I compile a program I am working on, it loses exactly 1 from the end of my ints after multiplication when run. No error messages, just incorrect math. 
But when I compile on another computer, the program works perfectly. This means my gcc has something wrong with it. is there some way to repair it?  :confused:

---

### Post by Wybiral on 2007-10-10
Can you post some code?

---

### Post by osiris2258 on 2007-10-10
```
/* Elliot Jenner	Programming Assignment 2
 Program to calculate the change for any given dollar amount. it is designed to take input from a file rather than the user, which is why there are no prompts. use with an input redirect or replace scanf with appripriate fscanf. */

#include <stdio.h>

int main(){

int quarters, dimes, nickels, pennies, active; float input;

	while (1){ /*loop to cycle until end of input. This will always be true. without break in else (at bottom of loop), genereates an infinte loop*/
	scanf("%f",&input);
		if (input>=0){ /* check for end of input*/
		active=100*input; /* convert input to an int without sacrificing any data*/
		quarters=active/25;
		active=active%25; /* the modulo will give the remaining change without the quarters*/ 
		dimes=active/10;
		active=active%10;
		nickels=active/5;
		active=active%5;
		pennies=active;
		
		printf("$%.2f: %d %s %d %s %d %s %d %s\n",input,quarters,((quarters==1)?"quarter":"quarters"),dimes,((dimes==1)?"dime":"dimes"),nickels,((nickels==1)?"nickel":"nickels"),pennies,((pennies==1)?"penny":"pennies"));} /* in order to be gramatical, check to see if the plural is needed. (x==y)?l:m if the statement is parenthesis is true, then replace this string with l, otherewise replace with m.*/
		else {
		break;} /* nothing to do here since the end of input has beeen reached, so exit the loop*/
	} 
}
```

when compiled on my computer, the resulting program looses exactly 1 penny sometimes (1.01 is only four quarters, but 1.10 is 4 quarters and a dime). When compiled on my school's unix server or my teacher's mac, the program works perfectly.

---

### Post by ryno519 on 2007-10-10
Could you post your test data and results so we could run through the math in our heads?

Missed the bottom of your post, sorry.

---

### Post by osiris2258 on 2007-10-10
here's some output.

1
$1.00: 4 quarters 0 dimes 0 nickels 0 pennies
1.01
$1.01: 4 quarters 0 dimes 0 nickels 0 pennies
1.02
$1.02: 4 quarters 0 dimes 0 nickels 1 penny
1.03
$1.03: 4 quarters 0 dimes 0 nickels 2 pennies
1.04
$1.04: 4 quarters 0 dimes 0 nickels 3 pennies
1.05
$1.05: 4 quarters 0 dimes 0 nickels 4 pennies
1.06
$1.06: 4 quarters 0 dimes 1 nickel 0 pennies
1.07
$1.07: 4 quarters 0 dimes 1 nickel 2 pennies
1.08
$1.08: 4 quarters 0 dimes 1 nickel 3 pennies
1.09
$1.09: 4 quarters 0 dimes 1 nickel 4 pennies
1.10
$1.10: 4 quarters 1 dime 0 nickels 0 pennies
1.67
$1.67: 6 quarters 1 dime 1 nickel 1 penny
1.68
$1.68: 6 quarters 1 dime 1 nickel 2 pennies
1.69
$1.69: 6 quarters 1 dime 1 nickel 4 pennies
1.70
$1.70: 6 quarters 2 dimes 0 nickels 0 pennies
1002.68
$1002.68: 4010 quarters 1 dime 1 nickel 2 pennies
1.58
$1.58: 6 quarters 0 dimes 1 nickel 3 pennies
9.01
$9.01: 36 quarters 0 dimes 0 nickels 1 penny
8.01
$8.01: 32 quarters 0 dimes 0 nickels 1 penny
7.01
$7.01: 28 quarters 0 dimes 0 nickels 1 penny
6.01
$6.01: 24 quarters 0 dimes 0 nickels 1 penny
5.01
$5.01: 20 quarters 0 dimes 0 nickels 1 penny
4.01
$4.01: 16 quarters 0 dimes 0 nickels 1 penny
.41
$0.41: 1 quarter 1 dime 1 nickel 0 pennies

---

### Post by ryno519 on 2007-10-10
Ignore.

---

### Post by osiris2258 on 2007-10-11
It looks like it is not my gcc, but rather something odd going on in the c language. Something screwy is happening when I multiply on line 13, making it lose the cent. I have no idea what could be causing it though; losing a cent isn't truncation and besides I am way to small to have to worry about that.

---

### Post by dwhitney67 on 2007-10-11
When you convert the floating number (e.g. 1.01) to an integer value with the multiplication by 100, you lost the precision you were after due to mixing integers and floats.

Try multiplying by 100 into a temporary float value; then assign that result to active.

In other words:

```

float adjust_input = 100 * input;    // preserves float value
active = adj_input;                  // now converts to integer

```

P.S.  There's a huge key on your keyboard, generally referred to as the "space bar".  Try to use it sometime; your code is awfully difficult to read.  Also try to declare your variables and initialize them at the same time.

---

### Post by Wybiral on 2007-10-11
Floating point arithmetic is notoriously inaccurate. Consider asking for dollars and cents separately or parse the decimal into the two values. Relying on a multiplication and a cast to integer isn't going to give you an accurate result.

---

### Post by dwhitney67 on 2007-10-11
The problem posted piqued my interest, therefore I tried the program not only on my ubuntu system, which has gcc 4.1.2, but also on my Fedora Core 5 system which has gcc 4.1.1.

The program originally posted worked the same, with the error occurring with the 1.01 input; however with the changes I suggested earlier, the problem was resolved.

Here's yet another approach (note that 'active' is declared as a float):

[PHP]#include <stdio.h>

int main()
{
  while (1)
  {
    float input = 0.0;

    printf( "Enter a US$ amount: " );
    scanf( "%f", &input );

    if ( input <= 0.0 )
    {
      break;
    }

    float active = 100.0 * input;

    int quarters = active / 25;
    active -= (quarters * 25);

    int dimes = active / 10;
    active -= (dimes * 10);

    int nickels = active / 5;
    active -= (nickels * 5);

    int pennies = active;

    printf( "$%.2f: %d %s %d %s %d %s %d %s\n",
            input,
            quarters, ((quarters == 1) ? "quarter" : "quarters"),
            dimes, ((dimes == 1) ? "dime" : "dimes"),
            nickels, ((nickels == 1) ? "nickel" : "nickels"),
            pennies, ((pennies == 1) ? "penny" : "pennies"));
  }
}
[/PHP]

---

