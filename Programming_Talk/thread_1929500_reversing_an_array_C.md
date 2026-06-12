---
title: "reversing an array C"
date: 2012-02-22
forum: Programming Talk
---

### Post by jon zendatta on 2012-02-22
Hi
I wish to reverse input. Compiles with EOF marker but gives no output.'\n' compiles & outputs. Problem is the text will be longer than one line.:KS
```
#include <stdio.h>
#define MAX 500

int main()
{
   char phrase[MAX];
   int i,c;
   printf("enter your phrase?\n");
   for(i=0;(c = getchar()) != EOF; ++i)
      phrase[i] = c;
   for (--i; i >=0; --i)
   putchar(phrase[i]);
   putchar('\n');

   return 0;
}
```

---

### Post by Tony Flury on 2012-02-22
when you run the code with the EOF marker - you have to ask yourself what will cause getchar to return EOF ?

On Linux the answer is normally CTRL-D, so try typing your input and then afte the last return - press CTRL-D

---

### Post by jon zendatta on 2012-02-22
Cheers Tony
CTRL-D returns nothing.Did you try this? Sorry for the lame question.:KS

---

### Post by dwhitney67 on 2012-02-22
> **jon zendatta said:**
> Cheers Tony
CTRL-D returns nothing.Did you try this? Sorry for the lame question.:KS

Try inputting your phrase (which btw is not a question), followed by a newline (return) and a ctrl-d.  Or enter ctrl-d twice.

If you input will merely consist of a single line of input, where only one newline will be present, then I would suggest that in lieu of checking for EOF that you check for '\n'.

---

### Post by Tony Flury on 2012-02-22
I do CTRL-D most days - not on your code though.

When you hit CTRL-D it must be the first character on the line - i.e. hit return and then hit CTRL-D

---

### Post by jon zendatta on 2012-02-22
Firstly, thanks for the advice. <return> <ctrl-d>(either once or twice),returns nothing.

---

### Post by surfer on 2012-02-22
i just compiled and ran it; <return> <crtl-d> as final input. this was the output:
```
$ ./a.out 
enter your phrase?
hello world

dlrow olleh

```
looking good, i'd say!

---

### Post by jon zendatta on 2012-02-22
yes that works fine, but not if it exceeds EOF:KS

error I meant end of line.

---

### Post by dwhitney67 on 2012-02-22
> **jon zendatta said:**
> yes that works fine, but not if it exceeds EOF:KS

What do you mean by EOF in the context discussed above?

---

### Post by jon zendatta on 2012-02-22
what I'm saying is if I use EOF as marker & it exceeds newline, I get no ouput.regardless of <return> <ctrl-d>

---

### Post by Arndt on 2012-02-22
> **jon zendatta said:**
> what I'm saying is if I use EOF as marker & it exceeds newline, I get no ouput.regardless of <return> <ctrl-d>

It works for me:

```
$ gcc -o rrev rrev.c
$ ./rrev
enter your phrase?
ippli bippli
voffel vaffel

leffav leffov
ilppib ilppi

```

Now, you can have EOF assigned to other keys than Ctrl-D. What does the command "stty -a" show? Somewhere in the middle of the output, you will find the setting for eof.

This talk about EOF and Ctrl-D assumes you are running in a normal terminal emulator. Maybe you are inside some kind of integrated development environment instead?

---

### Post by jon zendatta on 2012-02-22
cool Arndt, I hope I grasp it now. Should be straight forward

---

### Post by trent.josephsen on 2012-02-22
> **dwhitney67 said:**
> Try inputting your phrase (which btw is not a question), followed by a newline (return) and a ctrl-d.  Or enter ctrl-d twice.

And here I was thinking that ending input without a terminating newline was impossible.  How did I never know about this before?

---

