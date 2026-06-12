---
title: "Difference in compilers?"
date: 2005-10-20
forum: Programming Talk
---

### Post by Coutsos on 2005-10-20
Hello, world!

For a lab in my systems programming course we are asked to download and compile an [example program](http://janus.newcs.uwindsor.ca/~hjin/256/labs/files/lab5/streamexample.c) and run it with a test file. However, when I tried to compile it on my laptop running Breezy (with build-essential package installed) I got a bunch of errors.

> niko@ubuntu:~/Desktop$ gcc streamexample.c
streamexample.c: In function &#8216;main&#8217;:
streamexample.c:10: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_file&#8217;
streamexample.c:11: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_base&#8217;
streamexample.c:17: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_file&#8217;
streamexample.c:18: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_base&#8217;
streamexample.c:19: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_cnt&#8217;
streamexample.c:20: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_ptr&#8217;
streamexample.c:26: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_file&#8217;
streamexample.c:27: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_base&#8217;
streamexample.c:28: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_cnt&#8217;
streamexample.c:29: error: &#8216;struct _IO_FILE&#8217; has no member named &#8216;_ptr&#8217;

Yet, compiling it from my account on the school's server was fine (also gcc). I guess that it's probably just a different version of gcc, but I was really hoping somebody could provide me with a better understanding of the problem. I'd really  prefer to do my programming work on my own computer than be forced to use the ridiculously outdated software they provide us with.

If this isn't enough information to help you figure out the problem, please let me know what else you need (and preferrably how to get it!).

Thanks in advance!

-Nick

---

### Post by David Marrs on 2005-10-20
I would guess that your school have added code to the stdio.h file that defines these member names. I get the same error message as you and a look through the stdio.h file confirms what the compiler says. Grep their stdio.h for _file, _base and the like and see what you find.

If their stdio is different, you could always copy it to your working directory and include it with the #include "stdio.h" line (ie. swap the <tags> for "quotes"). If it's not different then I'm as clueless as you are. :)

---

### Post by thumper on 2005-10-20
Is your school using Linux or some other UNIX OS?

---

### Post by Coutsos on 2005-10-20
Thanks for the help, David. This is pretty troubling that the stdio header seems to be... non standard?

As for the school, their servers are running Solaris. I don't know the details but it seems they've worked out a deal in which the university bends over and takes it from Sun in exchange for crappy equipment. :(

---

### Post by toojays on 2005-10-20
The header is standard, but your code is using nonstandard features of the FILE struct. All those _variable names you have used are non-standard, and should not be used in portable code. I don't think it's really fair to blame Sun for this.

---

### Post by LordHunter317 on 2005-10-20
[QUOTE=toojays] I don't think it's really fair to blame Sun for this.[/QUOTE]It's sun, so it's justified by their very nature. ;)

---

### Post by Coutsos on 2005-10-20
Well, the thing about Sun didn't really have all that much to do with anything. I guess I just don't like them.

More importantly though, are there some standard variable names I can use instead? And if so, why would anybody want to change it?

---

### Post by LordHunter317 on 2005-10-20
Nope.  The internals of FILE are a black box, AFAIK.

---

### Post by JmSchanck on 2005-10-20
How are the internals black box? Check out libio.h. Look for _IO_FILE.

---

### Post by LordHunter317 on 2005-10-20
As in, without a portability library, you're not guaranted by any standard what the contents of a FILE strucutre are.

---

### Post by toojays on 2005-10-21
To add to LordHunter317's comment: the fact that the structure members which you're trying to access start with an underscore should serve as a big "this is not portable" warning. It's conventional to name such things that way, because in C, you can't really hide them from the user without resorting to ugly casting tricks.

---

### Post by JmSchanck on 2005-10-21
Sorry, I should have been more clear. I completely agree with it not having guaranteed portability, it's just that black box implies that libio.h is not viewable when in fact it is. This is more of a White Box case, If he wanted to he could easily go look at his copy of libio.h and alter the variable names in his program to work with it.

Doesn't really matter what jargon we use though, the points been made, the code isn't portable.

---

### Post by LordHunter317 on 2005-10-21
[QUOTE=JmSchanck] it's just that black box implies that libio.h is not viewable when in fact it is.[/quote]No, it implies that you're not supposed to know or care about the contents of a FILE structure.  Just because you can find out what is inside the black box doesn't change the fact the box is black.

Libio.h isn't portable anyway, so any attempt to use it in the name of portability carries no weight.

---

