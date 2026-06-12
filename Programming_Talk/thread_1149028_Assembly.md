---
title: "Assembly"
date: 2009-05-04
forum: Programming Talk
---

### Post by asm_Coty on 2009-05-04
how and were do I get an assembler for Ubuntu? thanks in advance :)

---

### Post by jimi_hendrix on 2009-05-04
run ```
sudo apt-get install nasm
```

---

### Post by asm_Coty on 2009-05-04
Thank you much... Is there one for Fasm perhaps?

---

### Post by jimi_hendrix on 2009-05-04
not that i can tell from a repo search, but there may be a .deb out there on the internet...and compiling it should not be that hard if there isnt

---

### Post by asm_Coty on 2009-05-04
I found it here [http://flatassembler.net/download.php](http://flatassembler.net/download.php) how would I compile it?

---

### Post by samjh on 2009-05-05
> **asm_Coty said:**
> I found it here [http://flatassembler.net/download.php](http://flatassembler.net/download.php) how would I compile it?

If you are an assembly programmer, you should already know.

If you are not an assembly programmer, why do you want to start with FASM?

The most popular assemblers for Linux are NASM and GAS.  Take a look at this tutorial to get started: [http://asm.sourceforge.net/howto/Assembly-HOWTO.html](http://asm.sourceforge.net/howto/Assembly-HOWTO.html)

---

### Post by asm_Coty on 2009-05-05
I am not yet a very experienced assembly programmer.... fact, I just started last month :(
I do however like the setup of Fasm and use it to make small dinky programs on windows..
But, I switched to Linux because its plain better, so...

---

### Post by samjh on 2009-05-05
You should probably use NASM.  Its syntax is one of the simplest among assembly languages and there are huge masses of online tutorials, books, and other resources for it.  It's extremely popular and very well supported, not only on Linux, but also on Windows and BSD as well.  NASM is **the** assembler for x86 processors.

I personally use GAS, but only because it makes working with C easier because GCC uses GAS.

---

### Post by asm_Coty on 2009-05-05
OK, I shall play with NASM for a while... thank you all for your help :)

---

