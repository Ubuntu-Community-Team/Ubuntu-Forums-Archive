---
title: "getting a C program to print out to screen using gcc"
date: 2006-10-31
forum: Programming Talk
---

### Post by Coffee_Time on 2006-10-31
Could anyone help,

I have installed all the gcc packages up to the latest gcc4.0 and the build-essential which was recommended.  I have done a basic program to see if it work

I executed using gcc -o test test.c (see below)

Nothing happens

can some please help ](*,) 

Regards


#include <stdio.h>

int main (void)
{
  printf("\n Hello linux World");
  return 0;
}

---

### Post by red_Marvin on 2006-10-31
you have to run the program first:
./test

gcc just *compiles* the code into a machine readable format, and then (IIRC) it calls ld to link the code to the library/libraries, In your case that would be stdio.
so when you call gcc like above there should appear a file called test in the same directory and that is the program...

---

### Post by Coffee_Time on 2006-10-31
Yes thanks for that, it works:D  new to programming C in linux ( final yr uni) is there a quicker way instead of using the ./test to run the program on the screen?

---

### Post by red_Marvin on 2006-10-31
If you want to do it all in one line you could type
*gcc [parameters 'n stuff] && ./[programname]*

Explanation:
"*command_1 && command_2*"
Executes command_1 and waits for it to return, if the return value is zero (standard value for "no problems occured") execute command_2

EDIT: Also, if you didn't know; by pressing up in the terminal you can get the commands you typed before, so you don't have to retype things that you use often as much.

---

### Post by Arndt on 2006-10-31
> **Coffee_Time said:**
> Could anyone help,

I have installed all the gcc packages up to the latest gcc4.0 and the build-essential which was recommended.  I have done a basic program to see if it work

I executed using gcc -o test test.c (see below)

Nothing happens

can some please help ](*,) 

Regards


#include <stdio.h>

int main (void)
{
  printf("\n Hello linux World");
  return 0;
}

Now that the issue of running the program is resolved, I'd recommend printing a newline _after_ lines, not before them. Depending on what shell you use, the line above might not appear for that reason.

---

