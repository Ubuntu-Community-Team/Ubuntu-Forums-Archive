---
title: "int=0 &amp; bool=false equates to NULL in C++"
date: 2008-11-07
forum: Programming Talk
---

### Post by bluedalmatian on 2008-11-07
Ive started experiencing something weird which Im sure hasnt held true in the past

if i have an int variable = 0 or a bool = false and I test it like this

if (myVar != NULL)
{

}
else
{

}

the else statement is executed, surely thats not right? :confused:

---

### Post by CptPicard on 2008-11-07
Well, NULL is just another name for zero, and in C++ I don't even really see NULL being used much, it's stylistically preferred to use 0.

---

### Post by dwhitney67 on 2008-11-07
If myVar is declared as an int, then
[php]
if (myVar)    // or if (myVar != 0)
{
  // continue here if myVar is NOT 0
}
[/php]

If myVar is a bool, then
[php]
if (myVar)    // or if (myVar == true)
{
  // continue here if myVar is true
}
[/php]

Some programmers prefer to use NULL when checking a pointer, to see if it has been assigned a proper address.  I prefer to use 0 (looks cleaner, less typing).

When declaring a variable, whether int, bool, or even a pointer, always initialize it when it is declared.  For example:
[php]
int value     = 0;
bool flag     = false;
MyObject* obj = 0;        // or MyObject* obj = new MyObject;
[/php]

---

### Post by bluedalmatian on 2008-11-07
Ok thanks, now I know its me and not the the machine being strange :) maybe its my Java past surfacing but I always thought NULL was a completely distinct value from 0 or false

---

### Post by CptPicard on 2008-11-07
Oh, Java null certainly is a value of its own... C NULL is just a subtitution for 0.

---

