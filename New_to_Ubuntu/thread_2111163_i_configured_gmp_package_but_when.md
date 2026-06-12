---
title: "i configured gmp package but when"
date: 2013-02-01
forum: New to Ubuntu
---

### Post by sense12 on 2013-02-01
I'm beginner in using Ubuntu Linux , and before two days i configured gmp package but when i compiled my program (ssss.c) by using this command 

(gcc ssss.c -o ssss.o -L/gmp_install/usr/local/lib -lgmp)

it doesn't give me any error commands or attention

then when i execute it by (./ssss) it says there is no such file or directory

plz help me

---

### Post by von Corax on 2013-02-01
Take a closer look at your compiler flags. Specifically, the -o flag specifies the name of the output file, which in this case is the final executable. (By default, the executable would be named a.out "for historical reasons," whatever that means... :P)

In this case, you are naming your executable ssss.o, so when you try to run ./ssss, you're trying to run a program with a different name from the one you just compiled.

By convention the suffix .o is used for _un_linked object files, while the executable has no suffix. Change the bit that says "-o ssss.o" to just "-o ssss" and you should be shiny.

---

### Post by sense12 on 2013-02-01
thanks for help

but when applied your advice i got this statement

(Combine shares using Shamir's Secret Sharing Scheme.

ssss-combine -t threshold [-x] [-q] [-Q] [-D])

i do not know  if that related to my code that is about secret sharing scheme, or error in some place .

---

### Post by squakie on 2013-02-02
I'm assuming you mean that you got that result after you compiled the program and executed it via ./ssss

That being said - just exactly what does ssss do?  Is it source you created - and if so - can you post the source so we might try to see what is going on?

---

### Post by squakie on 2013-02-02
Just found the source on the net.  I have no clue what the program is supposed to do outside of something mathematical, and didn't see any runtime syntax, but I can note the following:

in the notes in the top portion of the code are instructions telling you what the gcc line should look like as well as some other things

in the code, in the main function, it appears that it is dumping out a syntax list thinking you have either asked for help or to show the version.

I would suggest you find some more documentation for this and see if it doesn't mention the syntax of actually executing the program.

---

### Post by squakie on 2013-02-02
Did  you also read [this]("http://point-at-infinity.org/ssss/") page?  It shows the syntax you have to use - you don't just execute it, you have to provide the parameters at the command line.  The examples are on that page.  I don't know anything about coding or decoding encryption keys like this, so I can only go by what I read.

---

