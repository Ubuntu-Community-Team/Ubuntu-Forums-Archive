---
title: "Compiling Windows Code Under Linux!"
date: 2008-01-04
forum: Packaging and Compiling Programs
---

### Post by Zeliwin on 2008-01-04
Hello everyone,
     Well, I am a long term windows user. Switched to Linux to expand my programming knowledge base. So I have a simple stright forward question.

I downloaded Ubuntu Server Edition, but sense  I been working on a windows machine. all my code i wrote is in windows formate (C code). Is there somthing which will let me compile the code as if it was on windows and still run it? And sense I suck with Linux still I have no idea how I would go about this without recreateing the makefile etc etc.

---

### Post by LaRoza on 2008-01-05
If you used ANSII C you can compile it. 

If you used libraries not available for Linux, you can't.

---

### Post by Zeliwin on 2008-01-05
Is any windows enviroment available for Linux? Kinda of like Cygwin? Except for windows? Better yet, is it possible to make it so Linux can run exe executable files? If so I can just compile on my windows machine and still have Linux run the program.

---

### Post by NathanB on 2008-01-05
First, you can use the tools available here...

[http://www.mingw.org/](http://www.mingw.org/)

...to create a cross-compiler environment that will let you create Windows-style executables from your Linux machine.

Second, you can use this...

[http://www.winehq.com/](http://www.winehq.com/)

...to run those Windows applications on a Linux machine.

However, it seems to me that you are trying to defeat yourself.  If it is true that you "Switched to Linux" with the stated intent "to expand my programming knowledge base", then the above items will not be of assistance.  Shouldn't you be seeking information on how to build "Linux" executables??  ...and learning the "Linux approach" to programming?  If you continue to just do "Windows programming", then you nullify the benefit of using Linux.

Nathan.

---

### Post by chammy on 2008-01-07
In Ubuntu apt-get install mingw32* to get the cross compiler. From there just use i586-mingw32msvc-gcc in place of gcc to compile. Be careful that you link against all the libraries you used in the original program!

---

