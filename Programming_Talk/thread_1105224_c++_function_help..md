---
title: "c++ function help."
date: 2009-03-24
forum: Programming Talk
---

### Post by Vandorin on 2009-03-24
I need to write a function, that accepts a string and returns true if the string contains a valid floating point number using the at and length methods. I am still really confused on how to do this, and I've been having trouble writing functions, this is what I have so far.

```


#include <iostream>
#include <string>
using namespace std;

int num ( int a = 12.3 )
{
      return (a)
}

int main ()
{
     int i




```


and i'm really stuck there, I have no idea what to do next, in the second part of the code that will reference to it. I've googled and found guides, but none of it makes since, can someone do an example, like something not related to mine (since i'm trying to learn and not get you guys to do my homework for me) just so I can see how this would even be done?

---

### Post by namegame on 2009-03-24
First of all...

the assignment "int a = 12.3" will truncate to just 12. You would need to use a double or float type to support decimal numbers. And your function num is slighty trivial, not sure if that's your goal or not.

---

### Post by kjohansen on 2009-03-24
for starters you have a function that accepts and returns an int, not a string and a boolean

```

#include <iostream>
#include <string>
using namespace std;

bool num ( string a )
{
    if(a valid float) //this is not REAL code
       return true;
    else
       return false;
}

int main ()
{
     int i
}

```

---

### Post by kjohansen on 2009-03-24
As for the using the at and length methods, you should start by writing out what constitutes a valid float.  what characters are you looking for to make a float?

One case might be just a number: 1 or maybe 1.0 etc.

Lenght and at are not how most people would do this, but if you are required too...

---

### Post by albandy on 2009-03-24
well, the first I see it's that you are defining floats as integers.
another thing: I supose you can't use atof funtion so I think you should compare the lenght of the string to the float type size to avoid a buffer overflow and then ensure that the string is something like 0.00

then you can do a stream redirection like if the number was typed in keyboard

---

### Post by namegame on 2009-03-24
I would also recommend looking at string::find

---

### Post by Vandorin on 2009-03-24
I'm also confused about how I would pass data in and out, without using cin and cout, do I just assain the letter a to a number?

---

### Post by Sockerdrickan on 2009-03-24
you assign number to variable "a"

---

### Post by dwhitney67 on 2009-03-24
> **Vandorin said:**
> I'm also confused about how I would pass data in and out, without using cin and cout, do I just assain the letter a to a number?

Read your textbook!  Surely there are plentiful examples on how to define a function and pass a parameter, either by value or by reference.

If you are in a class, what have you been doing... skipping it?

---

