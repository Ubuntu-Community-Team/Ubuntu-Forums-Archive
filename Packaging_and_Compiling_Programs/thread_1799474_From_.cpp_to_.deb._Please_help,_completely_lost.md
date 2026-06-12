---
title: "From .cpp to .deb. Please help, completely lost"
date: 2011-07-07
forum: Packaging and Compiling Programs
---

### Post by iamnotloggedon on 2011-07-07
Over the past two weeks or so I've managed to teach myself a good amount of C++ programming using Code::Blocks and have used it to create a console-based D&D 4e character builder but when I tried to share a few copies I found the "executable" file to only function on the computer on which it was created.

Needless to say I've realized that I must create a debian installer if I want my friends and the rest of the Ubuntu community at large to be able to use this program but every time I go to a tutorial on how to create one I wind up more lost than I began, often with several new folders I'm not sure what to do with, if they're debanized,or what files I need to be putting into the terminal.

So can ANYBODY... 
1) give me step-by-step instructions on how to change a simple "HelloWorld" executable file into a .deb package.

2) Explain how these instructions would be different in a project with multiple header files?

Also, I understand creating a tar.gz file is included somehow but I don't know which files to specify when I type in the command to create it. Do I just use the executable or does it need the main.cpp as well?

---

### Post by cgroza on 2011-07-07
I think there is a sticky in Programming Talk that explains how to make a basic deb.

---

### Post by gordintoronto on 2011-07-07
Indeed:
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)

---

### Post by iamnotloggedon on 2011-07-07
> **gordintoronto said:**
> Indeed:
[http://ubuntuforums.org/showthread.php?t=910717](http://ubuntuforums.org/showthread.php?t=910717)


Thank you! Finally, something simple but I still wanna clarify one more thing before I go on:

Pretend that the packaging directory is actually the root of the file  system. Put the files of your program where they would be installed to  on a system.
 	Code:
 	mkdir helloworld_1.0-1/usr mkdir helloworld_1.0-1/usr/local mkdir helloworld_1.0-1/usr/local/bin cp "~/Projects/Hello World/helloworld" helloworld_1.0-1/usr/local/bin 
Does this mean I will actually need to create 3 directories within each other? and what does "cp" do in the command line? It looks like within the quotation marks is where my helloworld executable lay and after that you're typing in the last directory created but why do you need ...usr/local/bin after it? 

I may have missed something in my first read-over so I'm gonna read it again, a bit more carefully but I find this particular step confounding.

---

### Post by iamnotloggedon on 2011-07-08
Never mind, sorry I got it and even managed to create a deb file on my home folder for HelloWorld so I know I'm close to my ultimate goal but now I'm having an issue with creating a control file for my project: 

How do I find what dependencies go with my projects and what is the proper format for entering them when there's more than one?

---

