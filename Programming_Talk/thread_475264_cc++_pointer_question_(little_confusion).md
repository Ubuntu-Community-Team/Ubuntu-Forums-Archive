---
title: "c/c++ pointer question (little confusion)"
date: 2007-06-15
forum: Programming Talk
---

### Post by rbprogrammer on 2007-06-15
here is some sample code:
```

#include <iostream>
using namespace std;

void foo( char* str1, char*& str2 )
{
    cout << "char*  == " << &str1 << endl;
    cout << "char*& == " << &str2 << endl;
}

int main(int argc, char *argv[])
{
    char* str = "oh yea!";

    cout << "char   == " << str << endl;
    cout << "&char  == " << &str << endl;

    cout << endl;
    foo( str, str );
    cout << endl;

    return EXIT_SUCCESS;
}

```
with some sample output:
```

char   == oh yea!
&char  == 0xbf84026c

char*  == 0xbf840250
char*& == 0xbf84026c

```
**so my question is what is really happening with the pointers in the function?**

i just dont know which variable (str1 or str2) holds the address that points to the character array, and which one holds the address of the original pointer that holds the address of the character array

i hope i explained that as clearly as possible..

---

### Post by brooksbp on 2007-06-15
Pointer basics here:

A) pointers are variables that essentially store a memory address as a data type.
B) The '&' (reference) operator returns the memory address of a variable.  

The Reference Operator:

int myInt = 4;
int* myInt_Address = &myInt;

myInt_Address now has the value of the memory address that myInt is located at.

Your example:

the first line of code in foo() prints out the memory address of the origional pointer that holds the address of the char*
the second line 'hold's the address that points to the char*

Hope that helps.

---

### Post by Modred on 2007-06-15
Alright, the first two lines of output are pretty obvious.  It creates a string with the appropriate text, then creates a pointer called **str** and assigns the address of the string to this pointer.  The address that you're outputting is ***not the address of the string***, but the *address of the pointer*.  This happens because cout is overloaded such that a pointer to a cstring passed to cout will result in printing the text, not the address of the string.

Clear so far?  **str** holds a (currently unknown) address for the text you entered, and what's displayed is the address of **str**.

**str1** is passed to the function by value, so you get a *new pointer* that points to the string "oh yea!".  You could still access "oh yea!" through **str1**, but you have a new pointer, so when you display the *address of this pointer*, you have a different value than before.

**str2** is passed by reference, so you really just have a new handle on the exact same pointer.  Thus when you display the address of **str2**, it matches the address of the pointer from your main function.

Hope that was clear.  Ask some questions if it wasn't.

---

### Post by rbprogrammer on 2007-06-16
> **Modred said:**
> 
The address that you're outputting is ***not the address of the string***, but the *address of the pointer*.


just so i understand what was posted, in this code example, [FONT="Courier New"] 0xbf84026c[/FONT] is the address of the original variable in main(), while the actual address of the beginning of the string is not being displayed?

---

### Post by WW on 2007-06-16
Exactly.  Here is a variation of your program:

**ptrtest.cpp**
```

#include <iostream>

using namespace std;

int main(int argc, char *argv[])
{
    char* str = "oh yea!";
    int dummy;

    cout << "The string is \"" << str << "\"" << endl;
    cout << "The address of the string \"" << str << "\" is       " << (void *)str << endl;
    cout << "The address of the pointer to the string is " << &str << endl;
    cout << "The address of the integer dummy is         " << &dummy << endl;

    return EXIT_SUCCESS;
}

```
and here is the result of compiling and running it:
```

$ g++ ptrtest.cpp -o ptrtest
$ ./ptrtest
The string is "oh yea!"
The address of the string "oh yea!" is       0x80488e4
The address of the pointer to the string is 0xbfcff9fc
The address of the integer dummy is         0xbfcff9f8
$

```
I included the address of another variable, dummy, for comparison.

---

### Post by rbprogrammer on 2007-06-16
sweet, thanks for the explanation.. my confusion is cleared up

thanks again

---

