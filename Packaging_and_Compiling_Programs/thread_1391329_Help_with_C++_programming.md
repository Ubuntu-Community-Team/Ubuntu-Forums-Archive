---
title: "Help with C++ programming"
date: 2010-01-26
forum: Packaging and Compiling Programs
---

### Post by jjones237 on 2010-01-26
Need help making a program.
Have typed up the whole program and have one syntax error.  What do i need to fix. The error occurs it says before the equals sign after distance.  The error says "Syntax error before '=' token"
What do i need to do to fix it?


#include <stdio.h>

//Constants.
#define PI = 3.1415926;
const int INCHES_IN_FEET = 12;
const int FEET_IN_MILE = 5280;

int main(void) {

  int revolutions;
  float radius;
  float miles;
  float distance;
  
  //Prompt the user to enter the radius of their tires in inches.
  printf("What is the radius of your tires, in inches?\n");
  
  //Read in the radius of the tires.
  scanf("%f", &radius);
  
  //Prompt the user to enter the amount of revolutions of their car tires.
  printf("How many revolutions did your car's tires make?\n");
  
  //Read in the amount of revolutions.
  scanf("%d", &revolutions);
  
  //Calculate the distance.
  distance = (2*PI*radius*10000/FEET_IN_MILE*INCHES_IN_FEET);
  
  //Print out the distance travelled.
  printf("Your car travelled %.2lf\n", miles);

	
	
    return 0;
}


Can someone please help me, thank you.

---

### Post by marin123 on 2010-01-26
printf("Your car travelled %.2lf\n", miles)

youre missing quotes in this line..

it should look like this:

printf("Your car travelled %.2lf\n, miles",distance);

---

### Post by jjones237 on 2010-01-26
Thanks for the help fixing that, but I am still receiving an syntax error message before the =.  What should I do?

---

### Post by marin123 on 2010-01-26
i got it... remove #define PI (i dont know is this a good syntax for DEFINE) and make it const int (or const float)...
works! :)

and edit the last printf (add a \n)...

---

### Post by jjones237 on 2010-01-26
Thank you, it finally worked!:D

---

### Post by Some Penguin on 2010-01-26
For reference:

#define BLAH<whitespace>STUFF

means that all occurrences of 'BLAH' will be replaced by STUFF, even if STUFF contains whitespace.   That's all.

In other words, your #define macro put "= 3.1415926" everywhere "PI" appeared. 


Also for reference, your /usr/include/math.h almost certainly already defines M_PI.

---

### Post by marin123 on 2010-01-26
and i barely passed (i cheated) my c++ college exam... i'll show this to my professor :D

---

