---
title: "Java, C and C++ in Ubuntu"
date: 2013-05-10
forum: New to Ubuntu
---

### Post by saribeiro on 2013-05-10
Hey guys! I've used Ubuntu in the past (and absolutely loved the environment) but last time I used it, I was more or less just playing around with it. Recently I've been taking a programming class in Java and I've had so much fun with it. I do have a few quick questions about the Ubuntu platform and writing code though.

1. Does is automatically come with a JVM and C/C++ Compiler?
2. What IDE would you recommend for writing code on Ubuntu? (I am using Netbeans on Windows and Mac OS X)
3. What scripting language do you prefer? Python, Ruby or Perl? I haven't done any scripting yet, but plan to do so in the future.

As I was saying, before I was more or less playing with Ubuntu, but now I have put serious thought into doing open source development on the side as a hobby. I love the open source community and would like to see it thrive and I would like to be a contributing member. I also have one more thing. What books would you recommend I buy to learn C/C++ and scripting languages? I am thinking of doing some serious development and writing code for the Ubuntu community. By the way, what kind of code is the Ubuntu community looking for? What do you guys really want as a general user? Are you looking for games, music, movies, various multimedia editors? I just want to know what is popular so that I can be writing code where it is really needed/wanted.

Thank you!

---

### Post by squakie on 2013-05-10
I can't help you with the first 3 questions (I use C and C++ -> you should have gcc, but there are other things needed as well (all free).  Some people say it's not needed because it's for package development, but the build-essential package includes lots of things in the way of dependencies, and those things make things easier.  There are many IDE's out there - I use CodeBlocks, but I don't know if you can use it for Java or not.  Linux also has many libraries you may at one time or another need depending on what you are developing.  The beauty is that you can just Synaptic package manaer or the Software Center to install those as needed.

As far as what to develop, you may want to check and see what you can do to help support Ubuntu.  Sometimes there are programming things that need to be done, sometimes scripting, etc..  It would be a way to give back to the community as your skills increase.

---

### Post by saribeiro on 2013-05-10
I also have another question that I just thought of. I really love the Ubuntu font and I want to get the Ubuntu font in my installation of LaTeX. I have a MacBook Pro, it runs Mac OS X Version 10.8.2 and I have TexStudio running on my Mac. Is there any way I can import the Ubuntu font to TeX?

---

### Post by saribeiro on 2013-05-10
Oh ok! Thanks a lot! Are you a developer for the Ubuntu community? I'm just trying to gain as much coding experience as I can. I find coding and programming experiences invaluable because I use programs for so much of my work.

---

### Post by Petro Dawg on 2013-05-10
Netbeans is available in the software center for Ubuntu, and  Code::Blocks is as well.  Both are powerful and work well with Ubuntu.  

Many people prefer just using something simple like Geany, which is also excellent.  Just try them and see which you are most comfortable with.

Also, write code for things you are interested in, you'll have much better quality of work and it will much more fun.  Chances are if you are interested in it, others will be too.

---

### Post by saribeiro on 2013-05-10
Does the Code::Blocks IDE come with a compilers bundled with the software, or will I need to install those separately?

---

### Post by Petro Dawg on 2013-05-10
It's been a while since I've used it, but it seemed to me code compiled right out of the box with that program.  I wrote a couple C++ programs with it, but can't remember exactly what I did now.  ](*,)

May have been a couple Z factor solvers or something.

Just download it and try to create a simple "Hello World" program to see if its working for you.

Most programming I do now is in VBA unfortunately, or BASH script if I need to do something silly in Linux.

---

### Post by squakie on 2013-05-11
> **saribeiro said:**
> Oh ok! Thanks a lot! Are you a developer for the Ubuntu community? I'm just trying to gain as much coding experience as I can. I find coding and programming experiences invaluable because I use programs for so much of my work.

I haven't been yet.  I keep trying to decide if I know enough to be helpful.

---

### Post by Zerochilli on 2013-05-11
I recently took up Java, I downloaded Open JDK 7 to run my Java apps and a IDE called IntelliJ IDEA Community Edition. I find it is the best IDE for Java I have used. You can install both from software centre to.

Personally I would go for python as a scripting language :)

---

### Post by xoomer.ap on 2013-05-11
*>    Does the Code::Blocks IDE come with a compilers bundled with the software, or will I need to install those separately? *


It depends from IDE packet dependences. Generally for C++  your system needs have g++ installed, which goes with libstdc++ (stdlib) alongside. Just watch to compiler' terminal - it determine what you are not install yet.

---

### Post by Cheesemill on 2013-05-11
> **saribeiro said:**
> I also have another question that I just thought of. I really love the Ubuntu font and I want to get the Ubuntu font in my installation of LaTeX. I have a MacBook Pro, it runs Mac OS X Version 10.8.2 and I have TexStudio running on my Mac. Is there any way I can import the Ubuntu font to TeX?

You can download the Ubuntu fonts from the website...

[http://font.ubuntu.com/](http://font.ubuntu.com/)

---

### Post by Archit88 on 2013-05-11
[COLOR=#000000]1. Does is automatically come with a JVM and C/C++ Compiler?
[/COLOR]C/C++ Yes got GCC by default, JVM no need to install OpenJDK Java runtime.
[COLOR=#000000]2. What IDE would you recommend for writing code on Ubuntu? (I am using Netbeans on Windows and Mac OS X)
[/COLOR]C/C++: Eclipse Or Qt , Java : Eclipse
[COLOR=#000000]3. What scripting language do you prefer? Python, Ruby or Perl? I haven't done any scripting yet, but plan to do so in the future.
Python (all 3 are some what similar , you can also try learning alongside. [/COLOR]

---

### Post by saribeiro on 2013-05-11
I've seen where you can download it from, but how do I import it into TexStudio?

---

### Post by Cheesemill on 2013-05-11
> **saribeiro said:**
> I've seen where you can download it from, but how do I import it into TexStudio?

I've never used OS X myself, but a quick search came up with this...
[http://support.apple.com/kb/ht2435](http://support.apple.com/kb/ht2435)

Just extract the downloaded fonts to one of these locations and it should be available from any installed application.

---

### Post by KARNVORbeefRAGE on 2013-05-11
*READ THIS ONLY IF YOU WANT TO KNOW HOW TO **_RUN_** A C++ PROGRAM ON UBUNTU*

Ok, here is the complete explanation of how to run a program in C++.  After you write the program you want in a text pad, save it as "_____.cpp", then save it in a directory you want (for simplicity say "Documents").  Next open the command prompt and "cd" to Documents, finally type "g++ -o [name you want to give the executable version] _____.cpp".  For example:

cd Documents
g++ -o hello HelloWorld.cpp

Remember, the part after the -o is the name you WANT to give the executable program.  Now to run it:

./hello

This should work for all C++ programs, I hope this helped you with the compiling piece.

---

### Post by marianoa on 2013-05-11
After installing the fonts using the links Cheesemill gave you and checking that the new fonts are correctly installed (try to use it in Office/LibreOffice or any other similar software) using them with latex requires you to use xelatex to compile your tex file in order to be able to access the system fonts. Here's a link with some infos and an example 

[http://en.wikipedia.org/wiki/XeTeX](http://en.wikipedia.org/wiki/XeTeX)

Using xelatex instead of latex requires only some changes in the document preamble, as far as I know most of the latex packages work with xelatex too.

---

### Post by saribeiro on 2013-05-11
Ok, thank you guys for all your help! It's been really good having you guys around to help me around with my questions.

---

