---
title: "Having trouble running 32-bit binary on Ubuntu subsystem"
date: 2018-01-13
forum: New to Ubuntu
---

### Post by jenchi on 2018-01-13
Hello, I am very much a noob so please help me

I am running an ubuntu subsystem on my windows 10 and I cannot get this program to run. 

The program file is ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.2.5, not stripped

When I try running it I get this error: Syntax error: "(" unexpected

I tried following these instructions already: [https://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit](https://askubuntu.com/questions/454253/how-to-run-32-bit-app-in-ubuntu-64-bit) 

but I am still having the same issue. I don't know if this is true, but when I open the file in nano it says "Converted from Mac format," so that would mean the file is written for MacOS? 

Can anyone please help me get the program running?

---

### Post by Holger_Gehrke on 2018-01-14
What program are you trying to run and what was the exact command you used to try and run it ? The error message you got might actually have nothing to do with the program itself. It might be issued by the shell trying to process your command or it might be the program you're running complaining about the contents of some file you gave it. And what file where you trying to open in nano ? If you're trying to open a binary executable file in a text editor, you can consider any and all error messages it gives you due to the fact that that editor is not meant to edit binary files. If it was a text file, then it's basically complaining about the end-of-line characters (Linux uses the "line feed" control character, Windows uses "carriage return" and "line feed", old MacOS used "carriage return")

Holger

---

