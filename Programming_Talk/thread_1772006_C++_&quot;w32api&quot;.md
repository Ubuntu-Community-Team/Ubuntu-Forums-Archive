---
title: "C++ &quot;w32api&quot;"
date: 2011-05-31
forum: Programming Talk
---

### Post by ThatCoolGuy220 on 2011-05-31
Hi so im interested on developing for windows from linux for later develop on this one...

Im using NetBeans IDE and i downloaded Cygwin32 also installed 
gcc (I think)

I added this to the libraries

and also on options > C++ 

But im not able to build the project it keeps saying that it couldn't

Find the library.




Any fix for this or a way that i could be able to include win32 api on my project? 
:guitar:


Thx....

---

### Post by NovaAesa on 2011-05-31
I'm confused, are you programming in a Windows environment or a Linux environment?

---

### Post by ThatCoolGuy220 on 2011-05-31
On Linux environment

I've created an application that can sum:

it ask you for 1st number and for the second one and gives the the result very friendly though...

I'm using Netbeans I Build the Release i see a File that is executable though is not .exe

though using the win32api I would be able to do so and it could run on Windows...


Its very simple is just one library though i couldn't include the windows ones..


like:

- iostream.h
- windows.h
- w32api

---

### Post by NovaAesa on 2011-05-31
So if I understand correctly, you have written a summing application and it compiles and runs on Linux. Am I correct in understanding that you also wish to compile the program to produce an exe file that will run on Windows?

To do this, you have two options. You can either install Mingw (or any other compiler) on a Windows machine and compile there, or you can do what is known as "cross compiling". Cross compiling is where you compile the source code on a Linux machine and the output is an .exe file that will run on Windows.

---

### Post by ThatCoolGuy220 on 2011-05-31
Yes how i do that i have  the libraries cause auto-completion gives me the word.

This is what happens.

[IMG]http://img825.imageshack.us/img825/5299/screenshotspl.png[/IMG]

I get a build error

---

### Post by Zugzwang on 2011-05-31
Ah ok,

so what you are trying to do is to build a Windows executable that can make use of the Win32 API in a Linux environment. It was confusing that you mentioned "Cygwin32", because that is for the other way around: having a Linux-like build/compile/shell/etc. environment in a Windows world. Also, your sentence "im interested on developing for windows from linux for later develop on this one" makes no sense, so everyone was guessing, as "for later develop this one" makes grammatically no sense.

What you essentially want to do is to cross-compile for Windows (this is the technical term you might want to use for google searches). You can use "mingw" to do so. Search google or this forum for tutorials, etc.

You will need to run executables that use the Win32 API through Wine in Linux.

Note that it is highly likely that you won't find anyone who knows how to configure Netbeans to use mingw, so you are strongly advised to compile on the terminal before using an IDE. Only this way, you acquire the necessary knowledge of the compilation process to configure Netbeans accordingly without further help. Also, it avoids problems when getting started.

---

### Post by ThatCoolGuy220 on 2011-05-31
Well not much sense actually sorry english is not my best skill.

yes i will look for what you told me

---

