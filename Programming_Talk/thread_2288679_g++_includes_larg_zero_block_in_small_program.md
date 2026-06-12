---
title: "g++ includes larg zero block in small program"
date: 2015-07-29
forum: Programming Talk
---

### Post by veddox on 2015-07-29
Hi everyone,

trying to learn something new, I just installed a hex editor (ghex) and was playing around with it. I took a peek at the binary file of a small C++ program I had written some time ago, and was rather surprised at how many zeros it contains. There's a big chunk full of zeros right in the middle of the file. So I'm wondering why the compiler inserts them? Isn't that inefficient? 

If you want to replicate, you'll find the source code at [www.launchpad.net/comp](www.launchpad.net/comp). I compiled it with g++, no extra options passed (as seen in the install.sh file).

---

### Post by dwhitney67 on 2015-08-01
Maybe the source code that you obtained was written by an amateur programmer, and it has a static string chock full of zeros.  Why not peer review the source code, and get back to UF if you see something in the code that warrants more interest.

---

### Post by xb12x2 on 2015-08-01
> **veddox said:**
> There's a big chunk full of zeros right in the middle of the file. So I'm wondering why the compiler inserts them? Isn't that inefficient? 


I suspect the culprit is the linker, etc, not the compiler.

---

### Post by veddox on 2015-09-23
Sorry guys, I missed your replies :-(

In case you still see this:

> Maybe the source code that you obtained was written by an amateur  programmer, and it has a static string chock full of zeros.  Why not  peer review the source code, and get back to UF if you see something in  the code that warrants more interest.

Yes, the source code was written by an amateur programmer - that would be me ;-) And I can guarantee you, I did not load if full of zeros...

> I suspect the culprit is the linker, etc, not the compiler.

Why that?

---

### Post by xb12x2 on 2015-09-25
> **veddox said:**
> Why that?

The compiler's job is to turn human readable/writable code into machine language. It's the linker's job to format the machine language file(s) into a loadable executable.

You can compile a source file without linking (g++ -c). You'll get a *.o file (object file). You can use the hex editor on the object file to see if that block of zeroes is there before linking.

If your interested in what the linker does, how it formats, etc, google 'Executable and Linkable Format' (ELF).

[https://en.wikipedia.org/wiki/Executable_and_Linkable_Format](https://en.wikipedia.org/wiki/Executable_and_Linkable_Format)

---

