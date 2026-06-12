---
title: "C code segmentation faulting -_-"
date: 2011-11-06
forum: Programming Talk
---

### Post by compiz addict on 2011-11-06
I really don't get why this isn't working. No warnings appear when compiling.

```

#include <stdlib.h>
#include <stdio.h>
void main() {

int shade[10]; //10 different shades to be averaged every 10 loops
int count=0;
int shades;
int average;
int epicint;

for (int i=0;i>-1;i++) {
  count++;
  // ^ Because for loops make your code look smarter
  shade[count]=rand()%40+1;
  
  if (count==10) {
    count=0;
    shades=0;
    for (int j=1;j<=10;j++) {
      shades=shades+shade[j];
    }
    average=shades/10;
    printf("%d\n",average);
    epicint=average*0.80;
  }
}


}

```

---

### Post by ve4cib on 2011-11-06
I just compiled and ran it with no issue:

```
$ gcc -std=c99 -Wall foo.c
$ ./a.out
```

I didn't get any segfaults.  There is an infinite loop, but no segmentation fault.

---

### Post by compiz addict on 2011-11-06
Well, that's just plain weird. Even when I compile it using -Wall (I wasn't before), it still seg faults. The infinite loop is intentional; I'm going to run code based on this on the NXT's (lego robots) at my school, where rand()%40+1 will be replaced with a function to get input from light sensors. Fun stuff.

---

### Post by nickleboyblue on 2011-11-06
Side note:  it's generally not considered good form to write code that doesn't do what it looks like it does.  Eventually, with a signed int for i, the for loop COULD terminate.

Instead, do something like this:

```
while(true)
```

or

```
while(1)
```

That does exactly what it looks like it does, which makes revisions and bug fixes all that much easier.

---

### Post by davetv on 2011-11-07
Its this line

    for (int j=1;j<=10;j++) {

should be 

    for (int j=0;j<10;j++) {

---

### Post by Bachstelze on 2011-11-07
main returns int, not void. Game over, get a better book.

---

### Post by lisati on 2011-11-07
> **davetv said:**
> Its this line

    for (int j=1;j<=10;j++) {

should be 

    for (int j=0;j<10;j++) {
Why did I miss that? :D
> **Bachstelze said:**
> main returns int, not void. Game over, get a better book.
I hear what you're saying. IMO in this context the usage should be fine.

---

### Post by Bachstelze on 2011-11-07
> **lisati said:**
> 
I hear what you're saying. IMO in this context the usage should be fine.

No. main returns int, not void. It is never fine to do as if it returned void. If you do that, your code is not C.

---

### Post by lisati on 2011-11-07
> **Bachstelze said:**
> No. main returns int, not void. It is never fine to do as if it returned void. If you do that, your code is not C.

This thread was about a segfault, which, unless I am mistaken, has been addressed by an adjustment to the conditions one of the loops.

I agree that it's usually good form to return "int" for main. All I'm saying is that if I read the OP's description of the program correctly, the final version is unlikely to end of its own accord, making what main returns (if anything) irrelevant. There's an interesting discussion here: [http://stackoverflow.com/questions/204476/what-should-main-return-in-c-c](http://stackoverflow.com/questions/204476/what-should-main-return-in-c-c)

edit: I have a vague recollection of reading somewhere that the requirement to return "int" wasn't in the original definition of C.

---

### Post by schauerlich on 2011-11-07
> **lisati said:**
> edit: I have a vague recollection of reading somewhere that the requirement to return "int" wasn't in the original definition of C.

Prior to C99, it was also acceptable to have "main()" with no arguments or return type specified. Functions with no given return types are assumed to return int. void main() has never been allowed.

---

### Post by Arndt on 2011-11-07
> **compiz addict said:**
> Well, that's just plain weird. Even when I compile it using -Wall (I wasn't before), it still seg faults. The infinite loop is intentional; I'm going to run code based on this on the NXT's (lego robots) at my school, where rand()%40+1 will be replaced with a function to get input from light sensors. Fun stuff.

Try running it under gdb.

---

### Post by davetv on 2011-11-07
I use gdb without knowing any of its nuances. I use code::blocks 10.05 as an ide (kubuntu 8.04) set to use gdb as default debugger. I also use this with wxWidgets 2.8 but that is irrelevant. I can set stop points - press f8 for debug map/build/execute- and edit "watches" (under debugging windows) at a stop point.

Whether or not you use wxWidgets ... it is the painlesstness (is that a word?) way to use gdb I reckon. Works fine with a c "hello world" ... or the c++ openGL thingy I'm writing

---

### Post by karlson on 2011-11-07
> **compiz addict said:**
> I really don't get why this isn't working. No warnings appear when compiling.

```

int shade[10];
int count=0;

for (int i=0;i>-1;i++) {
  count++;
  // ^ Because for loops make your code look smarter
  shade[count]=rand()%40+1;
  
  if (count==10) {
}

```

Deleted most of the irrelevant code:

The last index in the array of shade is 9.  The last index that count can present according to this code is 10.

Adding other comments posted you should be able to get his working correctly.

---

### Post by Arndt on 2011-11-07
> **karlson said:**
> Deleted most of the irrelevant code:

The last index in the array of shade is 9.  The last index that count can present according to this code is 10.

Adding other comments posted you should be able to get his working correctly.

Good catch. I guess that the reason it crashes in some places and not in others (for example for me), is whether the processor is 64-bit or not. It seems gcc puts four bytes between shade[10] and count here, but if it doesn't, count will be overwritten with for example 11 and then assignments to shade will trample over the rest of the stack. Output from gdb might be confusing in situations like this. But debug print statements are helpful.

I just tried valgrind, and was somewhat surprised that it doesn't catch the error on my machine.

---

