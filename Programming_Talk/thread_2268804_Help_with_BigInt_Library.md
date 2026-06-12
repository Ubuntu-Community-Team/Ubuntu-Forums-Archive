---
title: "Help with BigInt Library"
date: 2015-03-11
forum: Programming Talk
---

### Post by Bresser on 2015-03-11
Hello so I want to start off this is not Homework.

But I am in a c++ class and we were going over recursion and a Factorial equation:

Quick sum if you don't know what a factorial is. Its like this Factorial of 6 is = 6 * 5 * 4 * 3 * 2 * 1 or 720 

7 is = 7 * 6 * 5 * 4 * 3 * 2 * 1 or 5040.

So as you can imagine you hit the limits of C++ datatypes pretty fast. At 20 is the biggest you can do with int16_t and size 170 is the biggest you can do with double. 

My teacher was telling us about the limitation of this and I thought I would use the bigInt library. But every time it only outputs one can anyone tell where I messed up?


[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]```
// This program tests a recursive algorithm for the factorial 

// function  

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2][COLOR=#000000]
[/COLOR][/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<iostream>[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<sstream>[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<stdint.h>[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<string>[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]<iomanip>[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]#include
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"BigIntegerLibrary.hh"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]using
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]namespace[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] std; [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]

BigInteger Factorial (BigInteger number);        
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Function prototype[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]int
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] main() [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
{ 

	

	string theNumber;

	BigInteger bigNumber;

	bigNumber = stringToBigInteger(theNumber);


    cout << 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"Enter whole number for factorial operation: "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]; [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
    cin >> theNumber; 

    cout << endl << endl; 

    cout << theNumber << 
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"! = "[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] << Factorial(bigNumber) << endl; [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
	

	system(
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515][FONT=Consolas][SIZE=2][COLOR=#a31515]"pause"[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]);[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
    
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] 0; [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
}  


[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// This function receives an integer and calculates the  

// factorial of that integer using a recursive algorithm 

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]BigInteger Factorial (BigInteger number)         

[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// Pre: number is assigned and number >= 0. 

[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]{ 

   
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]if[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]  ( number == 0)          [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]//  base case [/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]        
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]  1 ; [/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
   
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]else[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]                        [/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]// general case[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000][FONT=Consolas][SIZE=2][COLOR=#008000]
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]   {

        
[/SIZE][/FONT][/SIZE][/FONT][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff][FONT=Consolas][SIZE=2][COLOR=#0000ff]return[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT][FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2] number * Factorial(number - 1);[/SIZE][/FONT][/SIZE][/FONT]
[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
   }

  

} 
```


&#12288;
[/SIZE][/FONT][/SIZE][/FONT]

---

### Post by spjackson on 2015-03-11
This line
```

[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]    bigNumber = stringToBigInteger(theNumber);

[/SIZE][/FONT][/SIZE][/FONT]
```[FONT=Consolas][SIZE=2][FONT=Consolas][SIZE=2]
should appear **after** you have read the value into theNumber, not before.
[/SIZE][/FONT][/SIZE][/FONT]

---

