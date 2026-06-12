---
title: "Basic C issue with EOF"
date: 2009-10-01
forum: Programming Talk
---

### Post by Tdraket on 2009-10-01
I just started with C using The C Programming Language(2nd ed) by K&R.  Anyway, I have the program
> #include <stdio.h>

main()
{
  long nc;
  
  nc = 0;
  while (getchar() != EOF)
		++nc;
	printf("%ld\n", nc);
}

It's directly from the book, but when I compile it with gcc and run it it gets stuck in an endless loop of letting me enter characters. It never even gets to the printf statement.  I understand that EOF is basically equal to -1. Not sure how to get it to terminate the loop/get getchar() to return a statement that is equal to EOF so it will terminate.  Just trying to get it to display the way the book intends.

---

### Post by chrisjsmith on 2009-10-01
Your assumption is wrong - it's not stuck in a loop.  It simply depends how you run it:

The following will appear to get stuck:

./a.out file.txt

Actually it's ignoring the file.txt and is waiting for keyboard input (from stdin stream).  To issue an EOF manually, do Ctrl+D

Try running it as:

./a.out < file.txt

That should work.  It pipes the contents of the file into the stdin stream :)

---

### Post by MadCow108 on 2009-10-01
your code waits for getchar to return an EOF (end of file).
until this happens it will continue
so either pipe in a file (which will issue an EOF when getchar reaches the end) or type ctrl D into the prompt of the terminal which is equivalent to EOF

---

### Post by Tdraket on 2009-10-01
Thank you very much. :)  I've got it working now.

---

### Post by nvteighen on 2009-10-01
K&R C is an outdated version of C; nowadays it has a historical value only senseful to people that already have learned modern C. Look at [http://crasseux.com/books/ctutorial/](http://crasseux.com/books/ctutorial/) for a great C tutorial.

For instance, your code in ANSI C would look like this:
```

#include <stdio.h>

int main(void)
{
    long nc = 0;

    while (getchar() != EOF)
        ++nc;

    printf("%ld\n", nc);

    return 0;
} 

```

---

### Post by wmcbrine on 2009-10-02
> **nvteighen said:**
> K&R C is an outdated version of CYes, but the K&R *book* isn't outdated at all. It was updated to ANSI C in the second edition.

---

### Post by Arndt on 2009-10-02
> **chrisjsmith said:**
> Your assumption is wrong - it's not stuck in a loop.  It simply depends how you run it:

The following will appear to get stuck:

./a.out file.txt

Actually it's ignoring the file.txt and is waiting for keyboard input (from stdin stream).  To issue an EOF manually, do Ctrl+D

Try running it as:

./a.out < file.txt

That should work.  It pipes the contents of the file into the stdin stream :)

EOF is usually issued by Ctrl-D, but it can be changed. To see the terminal settings (and to change them), use the program 'stty':

```
$ stty -a
speed 38400 baud; rows 36; columns 80; line = 0;
intr = ^C; quit = ^\; erase = ^?; kill = ^U; eof = ^D; eol = M-^?; eol2 = M-^?;
swtch = M-^?; start = ^Q; stop = ^S; susp = ^Z; rprnt = ^R; werase = ^W;
lnext = ^V; flush = ^O; min = 1; time = 0;
-parenb -parodd cs8 hupcl -cstopb cread -clocal -crtscts
-ignbrk brkint -ignpar -parmrk -inpck -istrip -inlcr -igncr icrnl ixon -ixoff
-iuclc ixany imaxbel iutf8
opost -olcuc -ocrnl onlcr -onocr -onlret -ofill -ofdel nl0 cr0 tab0 bs0 vt0 ff0
isig icanon iexten echo echoe echok -echonl -noflsh -xcase -tostop -echoprt
echoctl echoke
```

There it says eof = ^D.

---

### Post by A_Fiachra on 2009-10-02
Learning C from K&R is like learning Perl from manpages (ok --- maybe that is an exaggeration).

K&R is, for me, more of a reference, like Stroustrup's book is for C++.

Depending on your programming experience and knowledge of systems, there are gentler tutorials out there.

I like C Primer Plus as a teaching/tutorial book.

---

### Post by nvteighen on 2009-10-02
> **wmcbrine said:**
> Yes, but the K&R *book* isn't outdated at all. It was updated to ANSI C in the second edition.

Ok, but the OP is writing K&R C, or am I wrong?

---

### Post by Bachstelze on 2009-10-02
> **nvteighen said:**
> Ok, but the OP is writing K&R C, or am I wrong?

This code is perfectly valid ANSI C. I would agree that it's not best practice, but it's valid.

(The code looks like this in the second edition of the book, btw, apart from the indentation)

---

### Post by chrisjsmith on 2009-10-02
Either K&R book is fine for learning C.

The 2nd edition will only gain you more respect as a programmer, not get the job done any better.

---

### Post by magistar on 2010-04-17
yeah i have the same problem and nothing happens when i hit the ctrl+d. Is there any other way you can issue an EOF?

---

### Post by MadCow108 on 2010-04-17
maybe its bound to a different key on your terminal
type
stty -a
and look under eof

if it does not work you probably have a error in your code in which case we would need a working example code snippet.

---

### Post by pbrane on 2010-04-17
> **magistar said:**
> yeah i have the same problem and nothing happens when i hit the ctrl+d. Is there any other way you can issue an EOF?

You may have to hit the ENTER key after you finish typing. Then type CTRL+D.

---

