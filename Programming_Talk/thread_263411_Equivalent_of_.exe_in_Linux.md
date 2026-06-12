---
title: "Equivalent of .exe in Linux?"
date: 2006-09-23
forum: Programming Talk
---

### Post by iONiK on 2006-09-23
What is the equivalent of an executable in linux? How would I go about programming tools for Linux? What tools and knowledge do I need? I have programmed on every system I have owned except for Linux...

Please help.

---

### Post by wildseven on 2006-09-23
for programming tools, you can search the repositories for c++, java, python, jython and other languages.

---

### Post by iONiK on 2006-09-23
and if I compile something, I can just run it?

---

### Post by wildseven on 2006-09-23
yeh, in terminal, just type the name.

---

### Post by iONiK on 2006-09-23
Thanks.

---

### Post by wildseven on 2006-09-23
yup.

---

### Post by junglepeanut on 2006-09-23
I am very new to programming, but

if you compile it, you can call it whatever you want then if your path is special you can just type the name. If not put ./name where name is you know what.

If it is a script (read an interpreted language) you will probably/may have to make the file executable. Read I think... "man chmod" I cheat and use chmod 755 for anything I think I may need to execute but I don't know if that is a good thing.

---

### Post by Engnome on 2006-09-23
> **junglepeanut said:**
> I am very new to programming, but

if you compile it, you can call it whatever you want then if your path is special you can just type the name. If not put ./name where name is you know what.

If it is a script (read an interpreted language) you will probably/may have to make the file executable. Read I think... "man chmod" I cheat and use chmod 755 for anything I think I may need to execute but I don't know if that is a good thing.

Right click the file --> properties --> permissions
Set to whatever you want.

If a file is set to be executable you can just double click and choose run instead of using the terminal.

---

### Post by tht00 on 2006-09-23
> **iONiK said:**
> What is the equivalent of an executable in linux? How would I go about programming tools for Linux? What tools and knowledge do I need? I have programmed on every system I have owned except for Linux...

Please help.

For a base set of compilers, install 'build-essential' from Synaptic.

Use 'gcc' to compile C programs and 'g++' for C++.  Without extra arguements, the compiled program will be named a.out, so the command './a.out' will run the resulting program.

For Java, install Sun's JDK 1.5 and compile/run with javac/java.

What specifically are you looking at?

---

### Post by SuperMike on 2006-09-24
> **iONiK said:**
> What is the equivalent of an executable in linux? How would I go about programming tools for Linux? What tools and knowledge do I need? I have programmed on every system I have owned except for Linux...


1. Any file that has had one of the following commands applied to it...

chmod u+x myfile
chmod g+x myfile
chmod a+x myfile

...and which the user qualifies for this security permission, may execute the file. If the file is a script, and the first line uses a syntax like...

#!/path to my binary ELF executable file


...such as...

#!/bin/bash

...then it will run that executable file to run this script.

However, if you want a TRUE executable file on Linux, it's much more than permissions. It requires compiling something down to an ELF executable file. This doesn't mean the file ends with ".ELF" -- there is no comparison to Windows with its requirement for 3 letter file extensions like ".EXE". Instead, it means "Executable and Linking Format".

The ELF format is a machine language format (think 1s and 0s) of instructions that the microprocessor can process via interaction with the kernel and its modules. In order to make an ELF executable, you need either a language that can convert your software/code into assembler code and then machine code, or you need a third-party tool that can convert a scripting language script into machine code in the ELF format.

To build an ELF, read this tutorial:

[http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html]("http://www.muppetlabs.com/~breadbox/software/tiny/teensy.html")

To see if a file is in ELF format or not, do this with it:

file /bin/bash

...here I see that the bash file inside the /bin directory has been compiled into machine language in the ELF format. The 'file' command shows me this result.

Another bit of trivia you might want to know is that the equivalent of a Windows DLL on Linux is closely related to a Linux .so file, which stands for Shared Object. However, there are lot of advantages of SO files over Windows DLLs. One of these is that it means you can upgrade software without needing to reboot, but that's an entirely different topic altogther.

2. You don't actually need to build tools for Linux by compiling ELF executables. You can use scripting languages and interpreters in order to create script programs. These require no compilation or linking, or require  some minimal compilation into something called "bytecode" (or something close to it) so that it runs faster. Some scripting languages compile "bytecode" (or something close to it) on the fly for you so that you don't have to do this. Many people find that compiling programs from code into machine language is a slow, tedious process because you have to do it over and over as you work on an application. That's why they choose scripting languages. This comes at a cost, however. Scripting languages are a bit slower. Sometimes, however, the speed difference is acceptable -- especially with today's faster computers.

Personally, I use PHP to do most of what I want in web pages or on a command line. However, when you mention "tools for Linux", it sounds a bit to me like you don't want to make a web app or something that runs in a command line. I would reason to bet you might be interested in building something sort of like a "control panel" such as something to configure a database or firewall. For that, it seems that those who manage the Linux distributions have a staff mostly focused in using Python and PyGTK or PyQT in order to build the control panel tools. Python and PHP are both scripting languages. However, Python has had a lot more developers invested in it as a scripting language that can drive a fast GUI. PHP hasn't come along very far with PHP-GTK, last I checked.

Some people have also experimented recently with building rich client applications on Linux using PHP, thttpd, SQLite3, and Mozilla XUL. For this, Mozilla Firefox becomes the client and a new chrome (or GUI) is loaded instead of the normal browser window. This then connects to a local web server port hosted by a tiny web server called thttpd. This thttpd then uses a gateway interface called CGI to launch sub-processes of PHP scripts for the PHP intrepreter to process. As database connectivity is necessary, SQLite3 can be reached from PHP. The combination of this is called XTPS.

However, should you want to build ELF executables directly, your best bet is to learn either C++ using the free Linux G++ (aka GC++) program, or learn another fast, easier to use language that compiles down to ELF. Just look up languages for Linux on the web and you'll probably find an article that compares compiled to interpreted (scripting) languages.

3. What tools do you need? You need a file editor and either an interpreter  or compiler. With PHP, you use an interpreter called 'php'. With C++, you use GCC to create an executable file.

What skills do you need? You'll need some programming skills and a way to ask a lot of questions to grow your knowledge over many years. Your best bet, however, is to curl up with a book and a laptop, learning something easy like PHP, then moving to something tougher later on.

---

