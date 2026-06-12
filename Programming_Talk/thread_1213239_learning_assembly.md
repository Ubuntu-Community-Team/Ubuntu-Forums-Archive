---
title: "learning assembly"
date: 2009-07-14
forum: Programming Talk
---

### Post by mosty friedman on 2009-07-14
hey everyone,

i know a bunch of programming languages such as C, Java, Haskell, Prolog and Python and i was really interested in learning assembly..so i'm kindly asking you guys to point me to some good books or tutorials and if you have any tips to share for learning assembly, i would really appreciate that

---

### Post by Finalfantasykid on 2009-07-14
I took a course about 68K assembly.  I don't know if it would have any practical use today(you might be better off learning x86 assembly), but 68K assembly was pretty easy and would be a good place to start.

Easy68K is the assembler/emulator that I used, but I don't know if it is supported on Linux...

---

### Post by mosty friedman on 2009-07-14
that's what i wanna do actually..i want to learn x86 assembly, but i dont really know any good sources to learn it from so i was wondering if someone could gimme a hand here

---

### Post by lisati on 2009-07-14
Among the things that helped me learn the basics of ASM were studying the code for simple programs others had published in computer magazines (it helps if it is well commented) and books from the library.

Note: I'd probably have to do some serious learning to program for Linux using ASM, since most of the x86 programming I've done has been for 16-bit MS-DOS systems!

---

### Post by Drone022 on 2009-07-14
A book entitled the "Art of Assembly" is available online.

Html link: [http://webster.cs.ucr.edu/AoA/Linux/HTML/AoATOC.html]("http://webster.cs.ucr.edu/AoA/Linux/HTML/AoATOC.html")

Pdf link: [http://webster.cs.ucr.edu/AoA/Linux/PDFs/0_PDFIndexLinux.html]("http://webster.cs.ucr.edu/AoA/Linux/PDFs/0_PDFIndexLinux.html")

As far as I understand you can get different versions depending on which platform your using. I have posted the linux 32-bit versions.

x86 is the way to go I reckon.

---

### Post by lisati on 2009-07-14
Afterthought for my previous post:

In interesting and potentially useful resource for programmers (in many programming languages) can be found at [http://www.programmersheaven.com/](http://www.programmersheaven.com/)

---

### Post by Can+~ on 2009-07-14
I personally learnt using SPIM the MIPS simulator:

```
sudo apt-get install spim
```

Here's a quick guide:
[https://www.cs.tcd.ie/~waldroj/itral/spim_ref.html](https://www.cs.tcd.ie/~waldroj/itral/spim_ref.html)

And the whole set of instructions:
[http://www.utdallas.edu/~cantrell/ee2310/spiminst.pdf](http://www.utdallas.edu/~cantrell/ee2310/spiminst.pdf)

And to test your applications on the simulator:

```
spim myfile.asm
```

---

### Post by rCXer on 2009-07-14
Since you want an x86 assembler, here is a NASM tutorial [Here](http://drpaulcarter.com/pcasm/).  NASM can be installed using...

```

sudo apt-get install nasm

```

The tutorial also comes with example code for Linux (See bottom of the page).

---

### Post by mosty friedman on 2009-07-15
alright thanks all for replying..i guess am gonna give nasm a shot :D

---

### Post by johnl on 2009-07-15
Hi,

Just a piece of advice when doing assembly and looking at tutorials/documentations: make sure what you are looking at is using the same syntax as the assembler you are using, or know how to convert between the two.

GNU Assembler ('as') uses the AT&T syntax, while NASM uses the Intel syntax.  The big thing is that source and destination are swapped between the two.

For example, AT&T:

```

pushl %ebp        # push ebp onto the stack
movl  %esp, %ebp  # mov esp to ebp
subl  $16,  %esp  # esp = esp - 16

```

is the same as intel:

```

push ebp       # push ebp onto the stack
mov  ebp, esp  # mov esp to ebp
sub  esp, 16   # esp = esp - 16

```

---

