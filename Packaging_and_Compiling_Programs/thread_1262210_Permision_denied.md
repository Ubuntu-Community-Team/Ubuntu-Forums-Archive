---
title: "Permision denied"
date: 2009-09-09
forum: Packaging and Compiling Programs
---

### Post by Extol11 on 2009-09-09
I keep getting a message from Codeblocks when I try to run code that says "Permision Denied" The exact output in the console is this: 
> sh /home/blix/Programs/C++/Forfun: Permission denied
I tried right-cliking the file and messing with its properties to let Codeblocks execute the file as a program and changing the ownership permissions but it's still not working. Anyone knows what I'm doing wrong?

---

### Post by Tclarkie on 2009-09-09
write click/properties/permission

right dow the bottom is a thing that says "allow to execute' or something, tick that b

---

### Post by apmcd47 on 2009-09-09
Looks like a permissions problem to me. Start up a terminal emulator and check every directory in the path of /home/blix/Programs/C++/Forfun.

What is Forfun - a shell-script or some program compiled from C++? If it is a C++ program why is codeblocks trying to use sh on it?

Andrew

---

### Post by Extol11 on 2009-09-09
Ok. I finally solved it. I had to click the "allow to execute" thing. I had already done so, but for some reason, when I checked it again... it was not marked. I made sure I marked it, run the thing, and made sure it was still marked after I ran it. It tried to run and told it me it was missing G++. I installed it using synaptic and then everything worked as it should. 

Forfun is a cpp file I wrote inside codeblock just to dust off my C++ skillz. I added .cpp at the end although I don't know if that's mandatory in linux. Also, why wasn't G++ selected when I installed codeblocks from synaptics and what is it exactly? I had never heard about it when I used Codeblocks in windows. Thanks for the help, guys.

---

### Post by apmcd47 on 2009-09-10
> **Extol11 said:**
> 

Forfun is a cpp file I wrote inside codeblock just to dust off my C++ skillz. I added .cpp at the end although I don't know if that's mandatory in linux. Also, why wasn't G++ selected when I installed codeblocks from synaptics and what is it exactly? I had never heard about it when I used Codeblocks in windows. Thanks for the help, guys.

I imagine G++ is the Gnu C++ compiler and it should be accessible using c++ and CC as well as G++. Having said that I don't have a G++ package in the repositories. Presumably codeblock for windows came with a compiler (or you had already installed one) so you didn't notice it.

As for why it wasn't selected, I don't know, but I would guess that codeblock can be used for several languages making it difficult to put a dependency on a single language.

Andrew

---

