---
title: "Capitalization program"
date: 2011-07-18
forum: Programming Talk
---

### Post by stamatiou on 2011-07-18
Hey guys, I would like to create a program to capitalize the first letter of a given array, here's the code:

```
#include <stdio.h>

char *capitalise(char *array)
{
char *pointer;
pointer = array;
char capitalised;
char temp;
if(pointer >= 'A' && <= 'Z')
{
printf("This word is already capitalised!");
return;
}
else
{
capitalised = *pointer - 32;
temp = *pointer;
*pointer = capitalised;
}

int main(void)
{
char arrray[50];
gets(array);
capitalise(array);
return 0;
}
```
and the compiler has the following errors:
```
capitalise.c:9:12: warning: comparison between pointer and integer
capitalise.c:9:22: error: expected expression before ‘<=’ token
capitalise.c:27:1: error: expected declaration or statement at end of input

```
What is wrong?

---

### Post by cgroza on 2011-07-18
This line:
```
if(pointer >= 'A' && <= 'Z') //wrong
if(*pointer >= 'A' && *pointer <= 'Z') //right
```I know that in natural languages it makes sense, but not to computers...

---

### Post by Zugzwang on 2011-07-18
> **cgroza said:**
> if(pointer >= 'A' && <= 'Z') //wrong
if(pointer >= 'A' && pointer <= 'Z') //right

Actually, they are both wrong, since in these expressions you are comparing the *pointer* against some value and not what the pointer actually points to. ;-)

---

### Post by JupiterV2 on 2011-07-18
I may be missing the point of this exercise but have you looked into the standard library ctype.h? It has an isupper() function to test if a character is upper case and toupper() to change the character to upper case. Technically, you could skip testing entirely and simply use toupper() because it won't change a character which is already upper case or if it is not ascii. No point in reinventing the wheel.

---

### Post by stamatiou on 2011-07-18
Thank you, but there is one error left:

```
capitalise.c:27:1: error: expected declaration or statement at end of input
```

---

### Post by Zugzwang on 2011-07-18
> **stamatiou said:**
> Thank you, but there is one error left:

```
capitalise.c:27:1: error: expected declaration or statement at end of input
```

Try to format your code in a more readable way. As an example, try the tool "astyle" that comes in a Ubuntu package. Apply it to your code by entering "astyle <yourCFileName>" in the terminal, where you replace the latter part by the actual file name of your source code. Then see what it produced. You should see the error immediately and get to know the value of proper code formatting at the same time.

---

### Post by stamatiou on 2011-07-18
> **Zugzwang said:**
> Try to format your code in a more readable way. As an example, try the tool "astyle" that comes in a Ubuntu package. Apply it to your code by entering "astyle <yourCFileName>" in the terminal, where you replace the latter part by the actual file name of your source code. Then see what it produced. You should see the error immediately and get to know the value of proper code formatting at the same time.
What is astyle?

---

### Post by Zugzwang on 2011-07-18
> **stamatiou said:**
> What is astyle?

As written, it is a tool that comes in a Ubuntu package. It formats your code such that you have an overview about its curly braces and their induced scopes. See, e.g., [http://packages.ubuntu.com/natty/astyle]("http://packages.ubuntu.com/natty/astyle").

---

### Post by stamatiou on 2011-07-18
> **Zugzwang said:**
> As written, it is a tool that comes in a Ubuntu package. It formats your code such that you have an overview about its curly braces and their induced scopes. See, e.g., [http://packages.ubuntu.com/natty/astyle](http://packages.ubuntu.com/natty/astyle).
And how can I use it?

---

### Post by Zugzwang on 2011-07-19
> **stamatiou said:**
> And how can I use it?

As I've written in Post #6. Other than that, please refer to its manual page and/or documentation available on the internet.

---

