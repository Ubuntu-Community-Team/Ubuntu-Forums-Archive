---
title: "C Help please :)"
date: 2008-12-17
forum: Programming Talk
---

### Post by feedmeh8 on 2008-12-17
C code for homework and im a little stuck :/ .. appreciate any help at all! ... The program is compiling fine but it runs all screwy. Program is supposed to accept two numbers and determine if both are greater than 0,
if so print the first number cubed followed by the second number squared. Otherwise print an error message.

```
/* accept two numbers and determine if both are greater than 0,
if so print the first number cubed followed by the second number
squared. Otherwize print an error message */
/* b_d */

#include<stdio.h>
#include<dos.h>

void main()

{

/* declare variables */
int num1, num2, num1cu, num2sq;

/* define variables */
num1cu=num1*num1*num1;
num2sq=num2*num2;

/* request and accept user input */
printf("Please enter a number:");
scanf("%d",&num1);
printf("Please enter another number:");
scanf("d",&num2);

/* calculate output */
if(num1,num2>0)

{
printf("%d %d",num1cu, num2sq);
}
else
{
printf("-----E R R O R-----");
}

sleep(10);

}


```

thanks :)

---

### Post by samjh on 2008-12-17
num1cu=num1*num1*num1;
num2sq=num2*num2;

You're doing those two calculations without first getting the values for num1 and num2.  They need to be done after you get the values from the user.

---

### Post by kjohansen on 2008-12-17
in one scanf statement you uses scanf("%d") in the second you have just scanf("d")  you want them both to be scanf("%d") since the %d is the format for reading.  just a d is meaningless as a format string...

---

### Post by Bakerconspiracy on 2008-12-17
#include<iostream>

using namespace std;

int main(){

int num1, num2, cubed1, squared2;

system("clear");

cout << "Please enter the first number" << endl;
cin >> num1;

cout << "Please enter the second number" << endl;
cin >> num2;

if(num1 > 0 && num2 > 0){
   cubed1 = num1 * num1 * num1;
   squared2 = num2 * num2;
   cout << Number 1 Cubed: " << cubed1 << endl;
   cout << Number 2 Squared: << squared2 << endl;
}
else if(num1 < 0)
   cout << "Error, Number 1 was less than 0... Exiting." << endl;
else
   cout << "Error, Number 2 was less than 0... Exiting." << endl;

return EXIT_SUCCESS;

}

//I remixed it a little bit haha, sorry i couldn't help with C
//but here is the C++ version.

---

### Post by |{urse on 2008-12-17
just add std:: in front of cout and cin should make it all happy.

---

### Post by Bakerconspiracy on 2008-12-17
I declared "using namespace std;" - no need to put std infront of cin and cout.

---

### Post by tyfius on 2008-12-17
There are several things wrong. Let's start at the beginning.

The use of "void main()" is not and has not ever been valid C or C++. Anyone to say so is wrong and if your teachers teaches you to use it he should be fired and replaced. Luckely for you most compilers will allow it but that doesn't make it right and a compiler is not required to implement it. It might work on your PC and compiler but fail on your neighbors PC and compiler. The use of "int main(), int main(int argc, char *argv[]) or int main(int argc, char **argv[])" is correct and also requires a return statement. Most likely this will be 0 (success) or 1 (failure). The header file "stdlib.h" defines EXIT_SUCCESS and EXIT_FAILURE which can also be used.

You do not initialize the variables when you declare them. This means that they will be filled with whatever is currently in memory. This might result in values like -2348485 or whatever you are seeing.

After you read in the first numerical value and you press the "return" or "enter" key that value is read into the second value. As a quick fix you can do something like:```
scanf("%d", &num1);
getchar();
scanf("%d", &num2);
getchar();
```

The order in which you process is also wrong. You declare the variables. Use them in operations and then read in values. This is not what you want. Let's say for example we write:```
int num1 = 0;
int num2 = 0;
int num1cu = 0;
int num2sq = 0;

num1cu = num1 * num1 * num1; // This will always be 0 because 0 * 0 * 0 = 0
num2sq = num2 * num2; // This will always be 0 because 0 * 0 = 0

// Here you call scanf stuff

/* calculate output */
if (num1,num2 > 0) {
  // The values of "num1cu" and "num2sq" will still be 0.
  printf("%d %d",num1cu, num2sq);
} else {
  printf("-----E R R O R-----");
}
```

---

### Post by |{urse on 2008-12-17
> **Bakerconspiracy said:**
> I declared "using namespace std;" - no need to put std infront of cin and cout.

Oh derrr =) I'm going blind i think.

---

### Post by feedmeh8 on 2008-12-17
Thanks a ton guys im going to try all of these and get back with what happened :) you guys are awesome!

---

### Post by Rocket2DMn on 2008-12-17
We don't do homework help here, sorry.  Thread closed.

---

