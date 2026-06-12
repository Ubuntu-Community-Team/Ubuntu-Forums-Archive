---
title: "Help with programming C++"
date: 2010-01-27
forum: Programming Talk
---

### Post by jjones237 on 2010-01-27
Here's my program which will run but will not give me the correct answer.  What am i doing wrong.  When you plug in 15 and then 10,000 I should get the answer 14.87 but I am getting a ridiculously big number.  What do I need to change?

#include <stdio.h>

#define PI 3.14159

//Constants.
const int INCHES_IN_MILE = 63360;

int main(void) {

  float revolutions;
  float radius;
  float circumference;
  float distance_inches;
  float distance;
  
  //Prompt the user to enter the radius of their tires in inches.
  printf("What is the radius of your tires, in inches?\n");
  
  //Read in the radius of the tires.
  scanf("%f", &radius);
  
  //Prompt the user to enter the amount of revolutions of their car tires.
  printf("How many revolutions did your car's tires make?\n");
  
  //Read in the amount of revolutions.
  scanf("%f", &revolutions);
  
  // Calculate the circumference of the tires.
  circumference = (2*PI*radius);
  
  //Calculate the distance in inches
  distance_inches = circumference*revolutions;
  
  //Calculate the distance in miles.
  distance = distance_inches/INCHES_IN_MILE;
  
  //Print out the distance travelled.
  printf("Your car travelled %.2f miles.\n", distance);

	return 0;
}

---

### Post by Zugzwang on 2010-01-27
Works fine here. How do you compile?

---

### Post by saulgoode on 2010-01-27
Your code is actually plain old C (no C++ specific statements) and seems to work fine on my computer (it also worked when compiled with g++). 

```
tesla:~ $ vim tst.c # <--- program text inserted 
tesla:~ $ gcc tst.c
tesla:~ $ ./a.out 
What is the radius of your tires, in inches?
15
How many revolutions did your car's tires make?
10000
Your car travelled 14.87 miles.

```

---

### Post by lisati on 2010-01-27
> **jjones237 said:**
> Here's my program which will run but will not give me the correct answer.  What am i doing wrong.  When you plug in 15 and then 10,000 I should get the answer 14.87 but I am getting a ridiculously big number.  What do I need to change?
```

#include <stdio.h>

#define PI 3.14159

//Constants.
const int INCHES_IN_MILE = 63360;

int main(void) {

  float revolutions;
  float radius;
  float circumference;
  float distance_inches;
  float distance;
  
  //Prompt the user to enter the radius of their tires in inches.
  printf("What is the radius of your tires, in inches?\n");
  
  //Read in the radius of the tires.
  scanf("%f", &radius);
  
  //Prompt the user to enter the amount of revolutions of their car tires.
  printf("How many revolutions did your car's tires make?\n");
  
  //Read in the amount of revolutions.
  scanf("%f", &revolutions);
  
  // Calculate the circumference of the tires.
  circumference = (2*PI*radius);
  
  //Calculate the distance in inches
  distance_inches = circumference*revolutions;
  
  //Calculate the distance in miles.
  distance = distance_inches/INCHES_IN_MILE;
  
  //Print out the distance travelled.
  printf("Your car travelled %.2f miles.\n", distance);

	return 0;
}
```
Are you putting in "10,000" with a comma, or "10000" without a comma?

---

### Post by The Men on 2010-01-27
```
What is the radius of your tires, in inches?
15
How many revolutions did your car's tires make?
10000
Your car travelled 14.87 miles.

```

Works just fine. How big exactly is the *ridiculously big number* ?

---

### Post by jjones237 on 2010-01-27
i'm running it on a mac with xcode and it gives me the number 396000000.00.  Is it the software or what?

---

### Post by dwhitney67 on 2010-01-27
> **jjones237 said:**
> i'm running it on a mac with xcode and it gives me the number 396000000.00.  Is it the software or what?

I just ran your code on my MacBook Pro with OSX 10.5.8 (Leopard); it works as the others have described.

---

### Post by johnl on 2010-01-27
Edit: nevermind, I borked the copy paste.  Ignore me.

---

