---
title: "Sementation fault in GCC when using pointer"
date: 2011-12-03
forum: Programming Talk
---

### Post by k_mp on 2011-12-03
Hi every body.I'm working on GCC for writing my program. But I encountered a problem after I ran my program. I mean it's compiled but in run time it gives me segmentation fault error. here is my code::
[PHP]
#include<stdio.h>
#include<string.h>
int main()
{
  char *string="";
  char *string1="";
  scanf("%s",string);
  scanf("%s",string1);
  printf("%s",string);
  printf("%s",string1);
  return 0;
}
[/PHP]
Finally when I've changed the definition of string of my code with below code it works fine
[PHP]
char string[1000];
char string1[1000];
[/PHP]
I just wanna know I can use pointer for string or not????
My machine runs in ubuntu 11.04 X64

---

### Post by ofnuts on 2011-12-03
> **k_mp said:**
> Hi every body.I'm working on GCC for writing my program. But I encountered a problem after I ran my program. I mean it's compiled but in run time it gives me segmentation fault error. here is my code::
[PHP]
#include<stdio.h>
#include<string.h>
int main()
{
  char *string="";
  char *string1="";
  scanf("%s",string);
  scanf("%s",string1);
  printf("%s",string);
  printf("%s",string1);
  return 0;
}
[/PHP]Finally when I've changed the definition of string of my code with below code it works fine
[PHP]
char string[1000];
char string1[1000];
[/PHP]I just wanna know I can use pointer for string or not????
My machine runs in ubuntu 11.04 X64You can use a pointer but you have to make it point to some allocated memory. [FONT=Courier New]char *string=""[/FONT] makes it point to one byte ('\0'). You would have to use:
```

#include <malloc.h>

char *string;
string=malloc(1000);

```

But in C, pointers and arrays are the same concept. When you declare an array, the variable that holds the array is really a pointer to the first element of the array, so this is valid:
```

#include <stdio.h>
#include <stdlib.h>

int main(int argc, char **argv){
    char x1,x2;
    char *string1="abcdefgh";
    x1=string1[5]; 
    x2=*(string1+5); 
    printf("%c =? %c\n",x1,x2);

    char string2[]="abcdefgh";
    x1=string2[6]; 
    x2=*(string2+6); 
    printf("%c =? %c\n",x1,x2);

    return 0;
}
```

---

### Post by MadCow108 on 2011-12-03
> **ofnuts said:**
> You can use a pointer but you have to make it point to some allocated memory. [FONT=Courier New]char *string=""[/FONT] makes it point to one byte ('\0').

more even, it points to a read only memory location containing a null byte. 
any attempt to write to that memory will result in a segmentation fault.

```
const char * str = "blabla"; // pointer to read only memory
bla[4]='s'; // segfault

char str[] = "blabla"; // copy content of read only memory onto the read/write stack and get pointer to that
bla[4]='s'; // ok

char *str = malloc(10); // get 10 byts of read/write memory
bla[4]='s'; // ok

```

---

### Post by dagoth_pie on 2011-12-03
ofnuts explained it prettty well.

But you can also initialise your char pointers to 0, then declare a dynamic array of the size you need.
```

char* pcString = 0;

pcString = new char[iStringSize];

delete[] pcString;

```
Declaring the array dynamically lets you set the array to any size you want, rather than having to set it to a constant value. Just remember to delete it afterwards, or else you'll end up with a memory leak.

If you aren't comfortable with using free store memory yet, just declare the char array to be a nice big number, like 1000, and use that. It's a bit of a waste of memory, but to be honest it's actually a better way to do things sometimes.

I'm assuming here that you're only just learning C or C++. For understanding how you can use char pointers as strings, perhaps you could #include <string> to get access to the std::string, then write your own class that implements the functionality you want.

I can't quite remember how I learned to understand pointers.

---

### Post by k_mp on 2011-12-04
Thank you very much everyone in advance for your quick answers. I think that I have long way to be professional in C/C++ :D

---

