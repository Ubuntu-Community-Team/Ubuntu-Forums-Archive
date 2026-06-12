---
title: "C++ help"
date: 2011-01-04
forum: Programming Talk
---

### Post by Mr Nemo on 2011-01-04
So I started teaching myself C++ and I wrote a small program to convert either Fahrenheit to Celsius or the other way around (I know it's lame, but I have to start somewhere). It works pretty well except for one small problem. If calculating for Celcius the answer is always some number in the 18000 or so, and I can't figure out why. Calculating for Fahrenheit works fine. I don't know if this is the right place to post this, but if anyone can help I'd appreciate it. It's probably a mess of a program and not efficient, but remember i'm a beginner. Here ya go:

```

#include <iostream>

using namespace std;
//Will calculate celcius with a given fahrenheit
//Celcius = (Ferenheight - 32) / 1.8
void cel()
{
unsigned short int fahrenheit, x;
fahrenheit = x;

unsigned short int celcius;
celcius = ((fahrenheit - 32) / 1.8);


cout << "Please enter a Temperature in Fahrenheit..." << endl;
cin >> x;
cout << "The temperature in celcius is:" << celcius << endl;
return;
}
//Will calculate fahrenheit with a give celcius
void fahr()
{
unsigned short int celcius;
int x;
celcius = x;
unsigned short int fahrenheit;
fahrenheit = (celcius / 0.555555556) + 32;

cout << "Please enter a value for celcius..." << endl;
cin >> x;
cout << fahrenheit << endl;
return;
}
//Introduction to program
void opening()
{
    cout << "This program will change fahrenheit to celcius or vice versa. Press enter to continue..." << endl;
    cin.get();
}

int main()
{
    opening();

enum CONVERT { Celcius, Fahrenheit };
CONVERT CONVERTS;
int y;
cout << "What would you like to convert to?" << endl;
cin >> y;
CONVERTS = CONVERT(y);

if (CONVERTS == Fahrenheit)
fahr();
else

cel();

return 0;
}

```

---

### Post by GabrielYYZ on 2011-01-04
this might not be the right answer but try adding #include <cmath> and see if that helps with the handling of operations.

also, it seems all your variables are ints but you're working with some floats.

i'm a c++ beginner too, but those are the 2 things that stand out for me.

---

### Post by Mr Nemo on 2011-01-04
Nope, #include <cmath> didn't have any effect.

The numbers I'm calculating should be small enough to define as int. If i'm misunderstanding something, could you expand on what floats i'm using?

---

### Post by mips on 2011-01-04
Have a look at [http://www.dreamincode.net/forums/topic/19161-celsius-to-fahrenheit-conversion/](http://www.dreamincode.net/forums/topic/19161-celsius-to-fahrenheit-conversion/)

---

### Post by Mr Nemo on 2011-01-04
Thanks for the link, but I still can't see where my program is going wrong.

---

### Post by drumsticks on 2011-01-04
When you define variables in a function, they are created uninitalised.  In cel(), "celcius" was calculated based on an uninitalised "fahrenheit", which in turn was calculated based on an uninitialised "x".  Similarly for fahr().  Neither are right.  

Try reordering the steps, such that you get from the user an input, perform the calculation, then output the result.

---

### Post by Mr Nemo on 2011-01-04
Thanks a lot drumsticks, it's working now. Here's my still sloppy, but functional program:

```

#include <iostream>

using namespace std;
//Will calculate celcius with a given fahrenheit
//Celcius = (Ferenheight - 32) / 1.8
void cel()
{
int x;
cout << "Please enter a Temperature in Fahrenheit..." << endl;
cin >> x;

unsigned short int fahrenheit;
fahrenheit = x;

unsigned short int celcius;
celcius = (fahrenheit - 32) / 1.8;



cout << "The temperature in celcius is:" << celcius << endl;
return;
}
//Will calculate fahrenheit with a give celcius
void fahr()
{
int x;
cout << "Please enter a value for celcius..." << endl;
cin >> x;
unsigned short int celcius;
celcius = x;
unsigned short int fahrenheit;
fahrenheit = (celcius * 9/5 + 32);


cout << fahrenheit << endl;
return;
}
//Introduction to program
void opening()
{
    cout << "This program will change fahrenheit to celcius or vice versa. Press enter to continue..." << endl;
    cin.get();
}

int main()
{
    opening();

enum CONVERT { Celcius = 1, Fahrenheit };
CONVERT CONVERTS;
int y;
cout << "What would you like to convert to?" << endl;
cout << "To Celcius = 1, To Fahrenheit = 2" << endl;
cin >> y;
CONVERTS = CONVERT(y);

if (CONVERTS == Fahrenheit)
fahr();
else

cel();

return 0;
}

```

---

### Post by drumsticks on 2011-01-04
Glad you worked it out.  This looks logically more correct, but there are still a few subtle flaws.  Be careful with integer division, as it truncates towards zero.  Also, operations are usually evaluated from left to right.

Thus:
fahrenheit = celcius * 9 / 5 + 32 == ((celcius * 9) / 5) + 32

which is quite different to:
fahrenheit = celcius * (9/5) + 32 == celcius * 1 + 32

For example, try it with celcius = 6!

---

### Post by koenn on 2011-01-04
> **Mr Nemo said:**
> 
The numbers I'm calculating should be small enough to define as int. 
It's not just about size. You're doing divisions, and int has no romm for decimals, so all your results will be rounded down ~ what drumsticks said
If you, at some point,  would use intermediate results for further calculations, the cumulative effect of these round-downs can be rather significant.

---

