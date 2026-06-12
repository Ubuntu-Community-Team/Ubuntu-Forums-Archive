---
title: "How Do I Download/Install Mondevelop?????"
date: 2006-09-17
forum: Programming Talk
---

### Post by Avenue on 2006-09-17
Hello, 

I'm a TOTAL newbie here with Linux and i'm trying to install Monodevelop.  I got it from the repository but it kept crashing on me, then I read somewhere on this forum that the version in the repository is outdated.  

Fine.  I went to the Monodev site and frankly...I don't understand it.  I can't seem to figure out what I need to do to install it.  I have downloaded everything into the Archive Manager but all i'm doing at this point is staring at a bunch of files, nothing looks familiar and I have absolutely no idea what to do.  

SO...I did another search in this forum and came across an APT-GET (or something like that) command for the bash and I pasted it in and it seemed to work - a bunch of returns stating that Monodev was "unpacking" and the final line states: 

[B]Setting up monodoc (1.0.6-3ubuntu1) ...
chad@Avenue:~$[/B]

What the hell am I supposed to do now?? (humor, of course)

As stated above i'm very new to Linux and just don't get it right now. It'll take some practice and some reading.  

Can someone help me finish off my install?

Your help is greatly appreciated.

Thanks!!********

---

### Post by grim918 on 2006-09-17
Try using the following command:
> 
sudo apt-get install mono mono-gmcs mono-gac mono-utils monodevelop

To launch mono just issue the following command in a shell:
> monodevelop

---

### Post by Avenue on 2006-09-18
GREAT!!!  Thanks for the reply, that really helped.  

I'm still having an issue, though.  Please allow me to explain:

After I run the commands listed in the post above, Monodevelop launches a window that says it's loading, then....NOTHING.  It just doesn't open.  

I went up to the Applications menu and Monodevelop does show up under the Programming sub-menu, so I do know that it is installed and on my system.  

The question:  Just how do I get it to run?

My god - this is really confusing, HA HA HA...Can someone help?

Thank you!!

Ave

---

### Post by grim918 on 2006-09-23
I'm not sure what could be the problem since I am also new to using mono, and linux. The truth though is that I don't use the monodevelop ide anyways. I compile my programs on the command line. I think its easier that way. you should try runnin the command > mcs
if you get an error saying that theres no input file then the C# compiler is installed and you should be able to write your programs and compile them.

To compile a program> mcs filename.cs

To execute a program> mono filename.exe
mcs will create an executeable .exe

---

