---
title: "C programming stumbling block"
date: 2009-05-16
forum: Programming Talk
---

### Post by davidpeace on 2009-05-16
I'm using *C for Dummies* to teach myself programming. In one exercise, the book says to use getchar() to read a keyboard input.

**snip**
printf("Which character is greater?\n");
printf("Type a single character: ");
a = getchar();
printf("Type another character: ");
b = getchar();

**snip**

The author knows that the first getchar() will will read in the values for both variables. Later in the lesson, he says to insert this line just after the first use of getchar():

fflush(stdin);

That didn't work. The author then says it might not work on all systems and to try:

fpurge(stdin);

There are no further instructions on what to try if that doesn't work, and sure enough it didn't. I have tried various things to get the getchar() to clear and nothing works.(yet...) Can anyone point me to where I might find information on reading just a single character from the keyboard or to otherwise clear that first getchar()? The author mentions "Curses" for Linux but a man curses turned up 0. I don't know if this will help, but I'm using a netbook, with the remix version of Ubuntu (my regular laptop is broken :(   ), gcc version is 4.3.3, and I'm using Emacs to type in the programs and compiling from the command line. Thanks for any help, in advance.

---

### Post by slavik on 2009-05-16
umm, flushing inputs is undefined according to the standard, since you can only flush outputs ...

as for Curses, search synaptic for the library.

---

### Post by hanniph on 2009-05-16
getchar() returns only one character from stream, so in cour code if you enter single character and press enter, the first character is assigned to a and line feed is assigned to b. If you want to read characters in this way - enter two character and then press enter.

The other way to read characters that comes to mind is to create buffer (char array) and read into that buffer first and assign the first character of buffer to a:
```
#include <stdio.h>
#define BUFSIZE 10
int main()
{
    char buf[BUFSIZE];
    char a,b;

    printf("Which character is greater?\n");
    printf("Type a single character: ");
    fgets(buf, BUFSIZE, stdin);
    a = buf[0]; 
    printf("Type another character: ");
    fgets(buf, BUFSIZE, stdin);
    b = buf[0];

    printf("%c\n", a);
    printf("%c\n", b);

    return(0);
}

```

If you want to use curses, you may be interested in [*this*]("http://tldp.org/HOWTO/NCURSES-Programming-HOWTO/") document.

---

