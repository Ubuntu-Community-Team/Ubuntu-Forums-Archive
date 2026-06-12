---
title: "[C/C++] Set char array using pass by reference"
date: 2009-07-16
forum: Programming Talk
---

### Post by wbest on 2009-07-16
I have an array, that I need to set as a string (char ar[5] = "TEST") and long story short, I can't actually use the string class.

Now what I want to do is pass an empty array and fill it up.  Fortunately, I am certain of the size of the array, so that is not a worry.

Here is the code I have now:
(NOTE: This is C++ code, I'm using printf for another bit of code that is not important to this problem, but it is important to the rest of the code)
```

#include <iostream>
using namespace std;

void textcolor(char color[]);
void charray(char test[]);

int main() {
    char test[7];
    charray(test);
    printf("Text in %s!\n", test);
    return 0;
}

void charray(char test[]) {
    test = "COLOR";
}
```


I keep getting junk output, I assume due to bad pointer use; but I can't figure out where I messed up.  Pointers are my only weakness :(.

Thanks in advance for your help.

---

### Post by MadCow108 on 2009-07-16
test="string"
is illegal. you can't assign values to an array. you can only do that in declarations (char * str = "test")
use strncpy(dest,source,size) defined in <cstring>
```

(...)
char test[7];
charray(test,7);
(...)

void charray(char *test,int size) {
    strncpy(test,"test",size);
}

```
[http://www.cplusplus.com/reference/clibrary/cstring/strncpy/](http://www.cplusplus.com/reference/clibrary/cstring/strncpy/)

btw you can convert a c++ stgring to a c string by calling its c_str() method.
so maybe you can use the c++ strings

(out of curiosity why do you need printf? c++ streams have the same capabilities)

---

### Post by wbest on 2009-07-16
Yeah, your code worked.
I could have sworn I assigned values to arrays outside of the declarations...

Anyway, yeah I'll probably just use that code.

I'm not sure I can use strings because I'm pretty sure I need to use printf (Thus I also can't use cout).

This is because, as is hinted in my code, I'm changing the color of text.  To do this I need the escape character.

I don't know, now that I think about it, maybe I can do it.  I'll have to see.

---

### Post by MadCow108 on 2009-07-16
of course you can also change the color with streams:
```

std::cout <<char(0x1B)<<"["<<1<<";"<<31<<";"<<40<<"m" << std::endl;

```
but I admit its harder to read :)

---

### Post by wbest on 2009-07-17
Yeah, well, that just gave me a good idea.
 I'd already set all the colors, as char arrays (I left it out of my example code as it looked messy): 

```
#define BLACK         "[2;30m"
#define RED        "[0;31m"
#define GREEN        "[0;32m"
#define YELLOW        "[0;33m"
#define BLUE        "[0;34m"
#define MAGENTA        "[0;35m"
#define CYAN        "[0;36m"
#define    WHITE        "[0;37m"
```

So what I can do then is also have:
char ESC = 0x1B;

So I can pull this off:
```
void textcolor(char color[])
{
    cout << ESC << color << "HELLO!" << endl;
}
```

Which is really quite easy to read (especially if I change thos char[] arrays into strings!):D

---

### Post by dwhitney67 on 2009-07-17
> **wbest said:**
> ...

I'm not sure I can use strings because I'm pretty sure I need to use printf (Thus I also can't use cout).


What does the usage of STL string and printf() have to do with each other?

```

std::string msg("Hello World!");

printf("%s\n", msg.c_str());

```

---

### Post by dribeas on 2009-07-18
> **wbest said:**
> 
```

void charray(char test[]) {
    test = "COLOR";
}
```


In C/C++ arrays decay into pointers when passed to a function. That means that the actual  function you have defined is:

```

void charray( char *test ) {
   test = "COLOR";
}

```

The function is receiving a pointer to the first element of the array by value (a copy of the pointer is being made). Your code is changing the value of the pointer (local variable to the function) to point to the "COLOR" literal. No change is being made to the array passed as reference.

As others pointed before, you do not want to change the pointer, but rather the value, and that can be achieved with strcpy set of functions:

```

void charray( char *test ) { // must assume that the buffer is big enough
   strcpy( test, "COLOR" );
}

```

But then again, this code is fragile in that you can only assume the size of the passed buffer and some user code could call the function with too short a buffer.

[B]The best advice is using std::strings, as dwhitney suggested.
[/B]
```

void chstring( std::string & str )
{
   str = "COLOR";
}
int main()
{
   std::string str;
   chstring( str );
   printf( "%s\n", str.c_str() );
}

```

---

### Post by MindSz on 2009-07-20
Or you can use the fact that whenever you declare a string, you are really declaring a pointer to a set of consecutive characters:

(This is written in C, but it should be almost the same for C++)

```
#include <stdio.h>

int charray(char test[]);

int main() {
    char test[7];
    charray(test);
    printf("Text in %s!\n", test);
    return 0;
}

int charray(char test[]) {
  test[0] = 'C';
  test[1] = 'O';
  test[2] = 'L';
  test[3] = 'O';
  test[4] = 'R';
  test[5] = '\0';

  return 0;
}
```

---

### Post by wbest on 2009-07-20
Yeah, I'm actually using code like dribeas's
 
> void charray( char *test ) { // must assume that the buffer is big enough
   strcpy( test, "COLOR" );
}
 
And that's working pretty well.
 
I do, however, send the result elsewhere as such:
 
```
 
void printTest(char test[]) {
  std::cout << color;
}

```
 
That method seems to work fine

---

### Post by MadCow108 on 2009-07-20
dribas solution is very dangerous in certain cases as it doesn't check for boundaries.
if color doesn't fit in the allocated space you get undefined behaviour and this is also a potential security hole if you allow for user input!

if using C strings always check the length.
One possibility is to use str**n**copy(char*ch,size_t n) instead of strcpy
this will only copy n chars into the array and stop at n if ch is to long. (although this again can lead to problems if further processing requires not truncated input)

keep to std::string in c++ to avoid these (and other) problems of char arrays.

---

### Post by wbest on 2009-07-20
Well, I know the size.
All the different things I'm going to ACTUALLY be writing to it are the same length (6 chars, if I recall correctly).
So that's never going to change, so I don't need to worry about size issues with the array.

---

