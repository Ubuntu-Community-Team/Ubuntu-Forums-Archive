---
title: "From understanding code to designing complete applications"
date: 2010-08-28
forum: Programming Talk
---

### Post by nair on 2010-08-28
I have only used one programming language: Python.  I understand some of the syntax and can read it about as well as I can read spanish; I am not fluent, just moderately literate.  Now I want to know how to actually create an entire application written in Python, or any programming language for that matter.  I am familiar with the concept of compiling code as well as interpreting code.  I have heard that Python is not a language which is compiled, it is a language that is only interpreted by a Python interpreter, like the one installed by default on Ubuntu Linux or Mac OS X.

What I want to know is: How do I go from understanding Python code, for example (or any type of code), to creating an entire application?  What I mean by an "entire application" is something that is an executable ... something that can be installed as a standalone application (ex. click Next > Next > Next) ... and something that has a point-and-click GUI.  Any mainstream application you download from the web (ex. Skype, Firefox, OpenOffice) has an installer that actually installs the program on your harddrive, reserving the necessary space in some sort of organized fashion, and presents a GUI with which you interact to use the application.  This is clearly very different from using a Python interpreter to interpret a .py file.

I am a complete beginner at programming and designing software.  I do not know if compiling vs. interpreting languages is relevant to this discussion--I only mentioned it because I am not that informed about it and was expecting it to be related to the answer to my question.  I am also not that interested in keeping the discussion Python specific; Python is just all that I know.

---

### Post by kahumba on 2010-08-28
> **nair said:**
> 
What I want to know is: How do I go from understanding Python code, for example (or any type of code), to creating an entire application? .
Exactly the way you learn(ed) Spanish - you learn it bit by bit, you don't attend a lesson and then wake up in the morning knowing Spanish 100%, instead you keep learning for months and years, same with programming languages, you can't read something and then think that you're a lot closer to your mythical purpose of knowing anything you need to know to create robust medium and large size applications.
An application, unless you mean a hello-world like one, can be over hundred thousand lines of code, there's a lot of stuff to learn and there's no stipulated path to go, everyone learns individually.

---

### Post by Bachstelze on 2010-08-28
First, not all programs have a "Next > Next > Next" installer.  This is mostly only for Windows programs (and not even all of them), some OS X ones, and very, very few Linux ones.

So first you must get rid of this idea that all programs have such an installer. Did you see any when you installed programs on Ubuntu? Probably not.

Second, it is perfectly possible to create graphicals applications with a .py file, you just need a graphical toolkit. Several exist. There is Tkinter (based on Tk), that ships with Python. DEpending on what you want your application to do, it might or might not work for you, it is quite limited. Then there's GTK (the toolkit you are probably familiar with in Ubuntu, and Qt (the one used by KDE). You can use both GTK and Qt in Python. I don't know how good the various GTK resources are, but for Qt you can use [this book]("http://www.amazon.com/dp/0132354187/").

---

### Post by nair on 2010-08-28
I figured someone would mentioned the Next > Next > Next comment.  I am aware that is a very Windowsee characteristic of installing a program.  Synaptic and Ubuntu Software Center obviously lack this characteristic.  The only reason I mentioned it is because that characteristic generally deals a lot with where/how you store a program on your harddrive.  And that is a very important concept that I know nothing about which is directly related to installing applications.

---

### Post by Bachstelze on 2010-08-28
> **nair said:**
> I figured someone would mentioned the Next > Next > Next comment.  I am aware that is a very Windowsee characteristic of installing a program.  Synaptic and Ubuntu Software Center obviously lack this characteristic.  The only reason I mentioned it is because that characteristic generally deals a lot with where/how you store a program on your harddrive.  And that is a very important concept that I know nothing about which is directly related to installing applications.

If you want to see how a Python application is "installed" in Ubunu, have a look at the software-center package.  Basically, if your application is only one .py file you should:

-> Add the so-called [shebang line]("http://en.wikipedia.org/wiki/Shebang_%28Unix%29") on top of it

-> Rename it to remove the .py extension

-> Move it somewhere in your PATH, typically /usr/local/bin

-> Make it executable with [font=monospace]chmod +x /usr/local/bin/foo[/font]

And then you can run it by typing just the name of the file, either in a terminal, with Alt+F2 or from a launcher.  Of course when you install a Python program from the repos, you don't do all that, the package takes care of it.

---

### Post by nair on 2010-08-28
I came across PyInstaller today but have not spent any time trying to use it.  I would guess that some type of software like a PyInstaller would be able to handle certain commands like these automatically ... and would even know how to do similar commands for multiple platforms.  Those commands are not hard in the case of Ubuntu though.

Thanks a lot for sharing those.  That is one thing I wanted to know how to do since I am messing with Python on Ubuntu specifically.  I will ultimately want to know how to do those types of things for other programming languages and other platforms... I don't know if they will change in those cases.

---

### Post by maximinus_uk on 2010-08-29
I can tell you now that any kinda of auto-magic installer is essentially trivial to code compared to writing a program. So pick something interesting to write and get started. You learn programming by programming*, the same way you learn other things.

*also by reading other code and thinking about it in the shower, on the bus etc...

---

### Post by nair on 2010-08-29
I know that everyone refers to Python as a scripting language, but I recently (last night) realized that specifically means that it is an interpreted language.  Scripting language = interpreted language.  It is my understanding that an interpreted language does not compile into bytecode/assembly code and instead is interpreted by an interpreter at the time of execution.  This is exactly like the Java model of using runtime environments which are platform specific to interpret the code for that particular machine.

If Python is only interpreted, it would seem to me that a Python interpreter would be required on whatever system was using the Python application, in general.  I know there are exceptions to this rule in the case of Python (ex. py2exe for Windows) that enable one to build Python based executables while enabling users to use the executable without a Python interpreter.

My first question is: Do the commands you posted require a user to have Python installed on their machine (which it is by default in Ubuntu) in order to execute the code?

My second question is: Are there ways in linux to build complete executable applications using Python or any other interpreted language so that they are not actually using the interpreter of the OS to execute?  In other words, is there a way to mimic the process of actually compiling code, like you would in C or C++, but doing so using an interpreted language like Python so that the process of interpreting is done prior to the user actually using the application?

---

### Post by nvteighen on 2010-08-29
> **nair said:**
> I know that everyone refers to Python as a scripting language, but I recently (last night) realized that specifically means that it is an interpreted language.  Scripting language = interpreted language.  It is my understanding that an interpreted language does not compile into bytecode/assembly code and instead is interpreted by an interpreter at the time of execution.  This is exactly like the Java model of using runtime environments which are platform specific to interpret the code for that particular machine.

You're sort of right. Just that Python does compile to bytecode (.pyc files)... It actually works almost like Java, just that the compilation is done automatically from the source file and, usually, in the background. .pyc files are only generated when you import the code as a module in order to increase access speed.

> 
If Python is only interpreted, it would seem to me that a Python interpreter would be required on whatever system was using the Python application, in general.  I know there are exceptions to this rule in the case of Python (ex. py2exe for Windows) that enable one to build Python based executables while enabling users to use the executable without a Python interpreter.

My first question is: Do the commands you posted require a user to have Python installed on their machine (which it is by default in Ubuntu) in order to execute the code?


Yes, but Python is included in all major GNU/Linux distributions, so this is not an issue. And if it were, it's fairly easy to install. py2exe exists just because Windows makes it difficult to install and use Python... :P

> 
My second question is: Are there ways in linux to build complete executable applications using Python or any other interpreted language so that they are not actually using the interpreter of the OS to execute?  In other words, is there a way to mimic the process of actually compiling code, like you would in C or C++, but doing so using an interpreted language like Python so that the process of interpreting is done prior to the user actually using the application?

There aren't mainly because there's no need for them, at least yet: the shebang makes the file executable like it was a binary. If it was for speed, you'd probably do better using C or C++. But also, because compiling such a dynamic high-level language like Python to native code is terribly difficult. Of course it isn't impossible, but if you know ASM and C (or C++) you know that those languages require a lot of compile-time information Python doesn't need because of how the language is designed.

---

### Post by Bachstelze on 2010-08-29
> **nair said:**
> I know that everyone refers to Python as a scripting language, but I recently (last night) realized that specifically means that it is an interpreted language.  Scripting language = interpreted language.  It is my understanding that an interpreted language does not compile into bytecode/assembly code and instead is interpreted by an interpreter at the time of execution.  This is exactly like the Java model of using runtime environments which are platform specific to interpret the code for that particular machine.

To add to what nvteighen said, don't let the word "bytecode" fool you.  Python bytecode is not machine code: it is also interpreted, not executed by the CPU directly.

---

### Post by juancarlospaco on 2010-08-29
Let me see...

Algunas de esas cosas que mencionas las hacen los .DEB
Como dijeron TKinter es recomendado, por que es facil.
*Suerte my friend*

---

