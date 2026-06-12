---
title: "need help with universal IDE problem"
date: 2009-10-19
forum: Programming Talk
---

### Post by jessiebrownjr on 2009-10-19
hey hey! Ok, I have tried several Linux IDEs to compile my code. They kept giving me errors from perfect code, and its quite annoying. 

For instance I just tried "Geany" and got it set up.. I typed out hello world, and hit execute and this is what the terminal showed up as.
```

./geany_run_script.sh: ./rawr: not found

_____________
(program executed with code:127)
Press return to continue.
```

What is causing this? It has done it on... four IDEs now? 

I can type a code out and go to terminal and gcc compile it myself now... is this a permissions problem? halp! Thanks :-)

---

### Post by jpkotta on 2009-10-20
Does rawr exist?  What directory is it in?  What exactly is geany_run_script.sh trying to do with it?

---

### Post by jessiebrownjr on 2009-10-20
yes rawr does exist.  My question is more or less geared towards how is that IDE trying to run/compile my program?

I don't know what that geany etc line means either.. is it running some type of virtual machine, or what?

---

### Post by jpkotta on 2009-10-21
OK, it seems like you were hitting "compile" instead of "build".  "Compile" just compiles, it converts source into object code.  Object code is machine code, but it is not executable.  "Build" compiles *and* links.  Linking converts object code into executable code.

---

### Post by hessiess on 2009-10-21
Learn how to use make and how the underlying build system works (how to compile manually with the CLI), it will make your life easier in the long run.

---

### Post by Zugzwang on 2009-10-21
@OP: For using IDEs correctly, you should read some kind of tutorial or something. I've recently written one for KDevelop which might get you started: [http://ubuntuforums.org/showthread.php?t=1258665](http://ubuntuforums.org/showthread.php?t=1258665)

---

### Post by jessiebrownjr on 2009-10-21
> **jpkotta said:**
> OK, it seems like you were hitting "compile" instead of "build".  "Compile" just compiles, it converts source into object code.  Object code is machine code, but it is not executable.  "Build" compiles *and* links.  Linking converts object code into executable code.

I hit compile, it compiles without error. I then hit execute and it gave me the same error that it didn't exist. It is showing that it compiles with the following options. -Wall -c
I always use gcc name.c -o name and go with that

Still errored out, so I think what you said is something different then my problem.

---

### Post by jessiebrownjr on 2009-10-21
> **hessiess said:**
> Learn how to use make and how the underlying build system works (how to compile manually with the CLI), it will make your life easier in the long run.

This is probably good advice but im still learning C and Linux simultaneously, and what you said sounds like *another* project, and not a solution to this problem. I mean, it might be, but it sounds more like another project :-)

---

### Post by hessiess on 2009-10-22
> **jessiebrownjr said:**
> This is probably good advice but im still learning C and Linux simultaneously, and what you said sounds like *another* project, and not a solution to this problem. I mean, it might be, but it sounds more like another project :-)

GCC isnt that complicated

```

gcc -c main.c
gcc -c file2.c
gcc main.o file2.o -o application_name

```

The first two lines compile the two files main.c and file2.c into linkable objects, and the last line links everything into a executable binary. Just replace the example file names with the names of your source files.

Personally I hate IDE's because they add unneeded levels of abstraction and make everything more complicated. Plus they all have there own `project' file format which is a pain for portability.

---

### Post by jpkotta on 2009-10-22
> **jessiebrownjr said:**
> I hit compile, it compiles without error. I then hit execute and it gave me the same error that it didn't exist. It is showing that it compiles with the following options. -Wall -c
I always use gcc name.c -o name and go with that

Still errored out, so I think what you said is something different then my problem.

Read my post again.  Compiling is not the same as producing an executable, which is usually called "building".  Building implies *both* compiling and linking.  Googling or reading about these these terms in the documentation should be fruitful.

---

### Post by jessiebrownjr on 2009-10-22
> **hessiess said:**
> GCC isnt that complicated...
Personally I hate IDE's because they add unneeded levels of abstraction and make everything more complicated. Plus they all have there own `project' file format which is a pain for portability.

1) This isn't about GCC
2) This post is about an IDE, if you don't like them, why are you posting in an IDE help thread?
3)

I didn't ask how to compile off the command line, I asked if anybody could diagnose the IDE error that I get off multiple IDEs. If you can't answer that particular question, then please don't tell me to do it another way... A way that I'm already familiar with and not interested in learning about.

A list of notes to recap. I can compile source off the command prompt, no problem.  I have tried 4+ IDEs and they give me the **same** error when they try to run. Im assuming its either a permissions issue or a pathing issue or the rest I have no idea im just making up. I checked the command line syntax that the compiler compiles and links with, and its correct. Something else over my head is happening, and THAT is my question. Sorry if I am obnoxious, but im a to-the-point guy and I don't ask questions that I don't want to know the answer to.

---

### Post by jessiebrownjr on 2009-10-22
> **jpkotta said:**
> Read my post again.  Compiling is not the same as producing an executable, which is usually called "building".  Building implies *both* compiling and linking.  Googling or reading about these these terms in the documentation should be fruitful.

I have already done this, and looked at what the compiler does on the command line when I hit each button..

That.. is not..the issue...

One of my commands goes to compile ( -c) , the other compiles and links IE builds (-o)... Not hard to figure that part out.. I don't know why you guys think I'm hung up on that.  

Im asking why the IDE errors out, when I attempt to COMPILE and LINK saved and correct code, with the error I posted about earlier.. this is getting frustrating...

That little window the compiler pops up to show me my code.... How is it created..? Is it a virtual terminal ran through something magic in the IDE, is it a regular terminal that they made look all shiny for my benefit?  From what I can assume.. The code is correct, the compiler is* attempting* to compile and link correctly, but after that point is when the error is happening.. 

./geany_run_script.sh: ./rawr: not found

_____________
(program executed with code:127)
Press return to continue.
Geany is the name of the compiler im using, "rawr" was the name of the test c code I had typed.

---

### Post by jessiebrownjr on 2009-10-22
[http://ubuntuforums.org/showthread.php?t=1162133](http://ubuntuforums.org/showthread.php?t=1162133)

Seems another person having this same issue, and it went unanswered as well, odd. :-/

---

### Post by jpkotta on 2009-10-23
> **jessiebrownjr said:**
> 
One of my commands goes to compile ( -c) , the other compiles and links IE builds (-o)... Not hard to figure that part out.. I don't know why you guys think I'm hung up on that.  

Im asking why the IDE errors out, when I attempt to COMPILE and LINK saved and correct code, with the error I posted about earlier.. this is getting frustrating...


You didn't say anything about building before.  You've only said compile, and the error you get is exactly what happens when you compile but neglect to link.

> **jessiebrownjr said:**
> 
That little window the compiler pops up to show me my code.... How is it created..? Is it a virtual terminal ran through something magic in the IDE, is it a regular terminal that they made look all shiny for my benefit?  From what I can assume.. The code is correct, the compiler is* attempting* to compile and link correctly, but after that point is when the error is happening.. 

./geany_run_script.sh: ./rawr: not found

_____________
(program executed with code:127)
Press return to continue.
Geany is the name of the compiler im using, "rawr" was the name of the test c code I had typed.

The compiler is gcc, geany is the IDE, rawr is the executable, rawr.o is the unlinked object code, rawr.c is the C code.

It looks like geany is creating a shell script to run the program, running it (inside a terminal emulator, xterm on my system), and immediately deleting it.  So who knows what's in the script. 

You need to post the contents of the compiler log at the bottom of geany, and the contents of the directory where your code is.

---

### Post by jessiebrownjr on 2009-10-23
> **jpkotta said:**
> You didn't say anything about building before.  You've only said compile, and the error you get is exactly what happens when you compile but neglect to link.



The compiler is gcc, geany is the IDE, rawr is the executable, rawr.o is the unlinked object code, rawr.c is the C code.

It looks like geany is creating a shell script to run the program, running it (inside a terminal emulator, xterm on my system), and immediately deleting it.  So who knows what's in the script. 

You need to post the contents of the compiler log at the bottom of geany, and the contents of the directory where your code is.

Is there anything buggy about xterm/vte anything along those lines that would make 4 IDEs error out the same way? I tried googling what error code 127 was, didn't really find anything definitive. I tried to download some libraries that had to do with vte out of synaptic but it didn't work. Im hoping it was a configuration issue and when I install karmic it just goes away.. :-/

later when I get to work, ill post what you asked for. It does say it compiles it properly on the bottom of the IDE, but when I go to execute, thats when xterm pops up erroring out.

---

### Post by jessiebrownjr on 2009-10-24
Moving this thread to solved, im going to be a pharmacist. :guitar:

---

