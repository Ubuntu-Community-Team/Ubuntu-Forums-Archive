---
title: "Need help with that problem variable-sized object ‘array’ may not be initialized"
date: 2012-06-28
forum: Programming Talk
---

### Post by timeout2575 on 2012-06-28
[FONT=Arial]Hello,

I am new to programming and kind of stuck on this assignment. 

This is the code that I wrote so far: 
#include <iostream>
using namespace std;

int Feld [11][11];
int main()
{
    for (int Reihe = 0; Reihe  <= 10; Reihe++)
    {
        for (int Zeile = 0; Zeile <= 10; Zeile++)
        {
            int Feld1[Reihe][Zeile] = Reihe * Zeile;
        }
    }
return 0;
}

and this results in the following error message:

tobias@Lonestar:~/c++$ g++ nl.cpp -Wall
nl.cpp: In function ‘int main()’:
nl.cpp:11:37: error: variable-sized object ‘Feld’ may not be initialized
nl.cpp:11:8: warning: unused variable ‘Feld’ [-Wunused-variable]

At the end of the day, I tried to work around that and declared the array in the following way:

const int AR = 11;
const int AZ = 11;
int Feld [AR][AZ];

This leads pretty much to the same error message. 

Any ideas? Help is appreciated :) Thanks!

Tobias




[/FONT]

---

### Post by cgroza on 2012-06-28
The problem is not the variable declaration. It is in the line inside the for loop.
You are defining another 2d array Feld1 (maybe you meant Field here).
If you meant Feld instead of Feld1, you should remove the int in front of it.
I could help you more, but I don't know what you are trying to do with this code.

---

