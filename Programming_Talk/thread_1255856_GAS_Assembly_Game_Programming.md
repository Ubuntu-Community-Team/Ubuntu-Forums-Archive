---
title: "GAS Assembly Game Programming"
date: 2009-09-02
forum: Programming Talk
---

### Post by socool274 on 2009-09-02
Call me crazy, but I would like to revive assembly, and use assembly for game programming. It is possible to create somewhat of a library in GAS assembly. If at all possible, I would like to simplify assembly game programming with my own library. But, to make a library, I do, first, need to learn assembly game programming. This is just a hobby project.

---

### Post by escapee on 2009-09-02
Any particular reason for this interest?  And was there a question - I'm not sure.

---

### Post by Chronon on 2009-09-02
This seems most useful on embedded systems.

---

### Post by socool274 on 2009-09-02
No particular reason, I just wanted to learn GUI in assembly. I just got an interest in assembly language.

---

### Post by socool274 on 2009-09-04
From the enormous amount of replies I got, I am assuming that assembly is (almost) a completely lost art. I suppose I don't see the use of creating something from pure assembly. But it would have been fun.

---

### Post by dangerdrew on 2009-09-04
It would be a good experience, but would be pretty tough. Assembly isn't dead, especially for embedded devices as mentioned above. The thing is that assembly is very difficult to write, very difficult to maintain, and not portable. You can write some very fast code with assembly, but that kind of speed is rarely needed in these days of GHz CPU's.

I say go for it, but you might want to set your sights a bit lower, initially at least. Why not try to do a graphics demo in assembly and work your way up from there? It'll give you a good taste of what you're in for!

---

### Post by socool274 on 2009-09-04
That would be nice, although, I really do need to learn how to make a window, draw things on it, etc. I'm a c++ game programmer. Game programming is what I like to do, and I just thought that it would be nice to learn it in assembly, sure, I'll learn graphics first, but my ultimate goal is to learn game programming, and API making. Right now, in assembly, I am stuck at the resizing of variables. I have an ascii array, and I need to change the size of it. I have looked to allocation, but there are no really good tutorials that I can turn to (for anything in assembly, really). It was very hard to obtain the information on the really simple stuff (printing system calls).

---

### Post by socool274 on 2009-09-04
But, yeah, I should learn graphics first. Do you know of any tutorials, or do you know GAS assembly personally.

---

### Post by GoS_ on 2009-09-04
Have you considered programming games for a vintage computer?  Programming games for computers like the Commodore 64, Vic 20, Atari 2600, etc. is really fun and immensely satisfying compared to modern x86 assembly language.  Not only is the processor much simpler (you don't have to worry about the pipeline, cache, or anything like that), but the memory maps on most machines also make it extremely simple to draw graphics to the screen.  

If you have considered vintage computers, but would prefer to go the x86 route, I suggest learning to use whichever graphic library you would like to in C/C++, and then switch to assembly to program the game library once you know the graphics library well enough.  I know you stated that you'd like to learn game programming in assembly, but it will be a lot less frustrating and faster if you learn first in a high level language. 

Learning to use the GAS assembler is really not an issue if you already know x86 assembly.  Just look at either some assembly output by gcc, or some example programs written for GAS if you can find any.  If you really want example source code you could alternatively use NASM, FASM, or any other assembler more geared towards hand-written assembly.

---

### Post by wmcbrine on 2009-09-04
Nowadays, I think that assembly is still worth learning, but not worth actually using. It can teach you a lot about how the machine really works. But, having acquired that knowledge... move on. Trying to actually "revive" it is indeed crazy.

They say that modern C compilers produce more efficient code than the average ASM programmer. I'm skeptical of that, but I do know that the code you wrote in C, you could simply recompile for x86, x86-64, PPC, or whatever else might be needed, while your x86 ASM would have to be totally rewritten. You'd also have an easier time maintaining the C code.

---

### Post by nvteighen on 2009-09-05
Hm... If you're going to do this on a modern computer, forget this... Assembly is not a language meant for this sort of things. There's a reason why C and C++ are used, even when sometimes even higher-level languages should be used instead.

Ok, yes, Assembly is Turing-complete and allows you to do this, but not because it allows you to do it, it'll be the best solution.

---

### Post by socool274 on 2009-09-05
I actually do know many higher level languages, and many API's. Java, python, c, c++ are languages that I know well. OpenGL is the graphics library I use. OpenGL is the one I will stick with. Although, I know many other API's, including a basic knowledge of SDL, pygame(python's binding of SDL), GLUT, Carbon, Cocoa, WinAPI. I do like to learn things so they will work on a majority of computers, which is why I know so many of them. But, my point is that I already know higher level game programming, and would like to try it with assembly.

---

### Post by socool274 on 2009-09-05
I understand that it is MUCH more useful to use c and c++, but I just had a sudden impulse to learn assembly. My goal is also to gain a general knowledge on many things. Not necessarily to learn one thing really well.

---

### Post by jimi_hendrix on 2009-09-05
> **GoS_ said:**
> Have you considered programming games for a vintage computer?  Programming games for computers like the Commodore 64, Vic 20, Atari 2600, etc. is really fun and immensely satisfying compared to modern x86 assembly language.  Not only is the processor much simpler (you don't have to worry about the pipeline, cache, or anything like that), but the memory maps on most machines also make it extremely simple to draw graphics to the screen.  


this sounds mildly interesting, how would one do this today without a Commodore 64 or something similar

---

### Post by socool274 on 2009-09-05
Hey, may the Ubuntu be with you. Ha ha ha ha, thats funny! Let us have, and use, the Ubuntu within us all!

---

### Post by GoS_ on 2009-09-05
> **jimi_hendrix said:**
> this sounds mildly interesting, how would one do this today without a Commodore 64 or something similar

Indeed, I find it extremely interesting.  Even if you have a real Commodore 64 or whatever machine you'd like to program, you'll want to develop and test with an emulator.  I've spent a lot of time programming the Commodore 64 and I don't own a functional one.  VICE is an emulator that emulates pretty much all the popular Commodore computers (from the PET to the Commodore 64).  Version 1.2 is in the repositories and is very accurate.  The most recent is 2.1, but I haven't found any significant improvements in emulation.

Then you have a couple options.  I started programming the C=64 by using VICE and a cartridge image that contained a machine language monitor (specifically the Retro Replay cartridge).  However, I'd recommend using a cross-assembler instead.  I use the assembler acme for all 6502 based machines (Atari 2600 and almost all 8-bit Commodores).  It's quite powerful, but also really simple to use.

Once you assemble the program, you can run it on an emulator.  This is usually a very simple process.  Testing a C=64 program with VICE is as simple as:
```
x64 programname.prg
```

Then you'll have to use the BASIC command "SYS" followed by the memory address the program was assembled at in decimal if you didn't put the BASIC tokenized version of this command in the assembly program.

It takes a little while to get going, but once you've figured out your development tools, it becomes a very rapid learning process.

---

### Post by nvteighen on 2009-09-06
> **socool274 said:**
> I understand that it is MUCH more useful to use c and c++, but I just had a sudden impulse to learn assembly. My goal is also to gain a general knowledge on many things. Not necessarily to learn one thing really well.

Hm... I understand your attitude, but this may be actually counterproductive, as it is almost forcing a language towards a task it is not optimal for. Ok, as an intellectual exercise it may be interesting, but be careful and measure the possibilities you have in getting the abstraction level you need.

But it'll be interesting to see your advances ;)

---

### Post by socool274 on 2009-09-06
I can't really advance well, unless there are resources on the internet, or in a book store that lists things like what functions there are within a specific library.

---

### Post by jimi_hendrix on 2009-09-06
> **GoS_ said:**
> Indeed, I find it extremely interesting.  Even if you have a real Commodore 64 or whatever machine you'd like to program, you'll want to develop and test with an emulator.  I've spent a lot of time programming the Commodore 64 and I don't own a functional one.  VICE is an emulator that emulates pretty much all the popular Commodore computers (from the PET to the Commodore 64).  Version 1.2 is in the repositories and is very accurate.  The most recent is 2.1, but I haven't found any significant improvements in emulation.

Then you have a couple options.  I started programming the C=64 by using VICE and a cartridge image that contained a machine language monitor (specifically the Retro Replay cartridge).  However, I'd recommend using a cross-assembler instead.  I use the assembler acme for all 6502 based machines (Atari 2600 and almost all 8-bit Commodores).  It's quite powerful, but also really simple to use.

Once you assemble the program, you can run it on an emulator.  This is usually a very simple process.  Testing a C=64 program with VICE is as simple as:
```
x64 programname.prg
```Then you'll have to use the BASIC command "SYS" followed by the memory address the program was assembled at in decimal if you didn't put the BASIC tokenized version of this command in the assembly program.

It takes a little while to get going, but once you've figured out your development tools, it becomes a very rapid learning process.

getting slightly off topic, but got a good tutorial for actually writting the programs? this sounds like a great weekend diversion

---

### Post by GoS_ on 2009-09-06
> **jimi_hendrix said:**
> getting slightly off topic, but got a good tutorial for actually writting the programs? this sounds like a great weekend diversion

The only general tutorial I've been able to find is this one:
[http://www.c64.ch/programming/]("http://www.c64.ch/programming/")
Sadly, it is really basic and short.

The best tutorial I've found is this one:
[http://ocaoimh.ie/wp-content/uploads/2008/01/intro-to-programming-c64-demos.html]("http://ocaoimh.ie/wp-content/uploads/2008/01/intro-to-programming-c64-demos.html")
It is geared towards programming demos, which makes it really interesting.  

Here's another one that looks similar.  It is by a person who is very active in the Commodore 64 scene right now:
[http://tnd64.unikat.sk/]("http://tnd64.unikat.sk/")
Click "Assemble It" on the left to get to the tutorial.  I've never actually gone through it, but it looks pretty in depth.

Here is the link to the source code of my cross-assembler of choice.  It builds really easily and comes with some great documentation, which is good because both of the above tutorials assume you're not using a cross-assembler.   QuickRef.txt will be especially handy, and it even has a short example program for the Commodore 64 at the top. 
[http://www.esw-heim.tu-clausthal.de/~marco/smorbrod/acme/current/acme091src.tar.bz2]("http://www.esw-heim.tu-clausthal.de/~marco/smorbrod/acme/current/acme091src.tar.bz2")

If you want to start programming with a monitor (not a bad idea), here is the download link to the cartridge image I used when I started:
[http://ar.c64.org/bin/rr-38a-64.zip]("http://ar.c64.org/bin/rr-38a-64.zip")
Note that there are two images in the archive.  One is for NTSC C64s and the other for PAL.  You can change the video standard to whatever you like in VICE.  To use the cartridge within VICE, find "Attach a cartridge image" in the menus, then select "Attach Retro Replay image", then select the image linked to above with the appropriate video standard at the end of the filename.  Press F7 when the cartridge's options appear, and then type "MON" and press return to enter the machine language monitor.

Best of luck to you, and sorry for derailing the thread :).

---

### Post by socool274 on 2009-09-06
It's all fine, thanks for the tutorials! I will look at them. Although, sadly, school starts day after tomorrow, and I may not have time.

---

### Post by NathanB on 2009-09-06
socool274,

You really should chat-up "Hostile Encounter" author Bogdan.  These people who have "been there, done that" are a fount of knowledge and are typically happy to share their experiences and resources with those willing to learn.

Hostile Encounter is a full-featured modern game written in ASM.  You can find it here:  [http://www.oby.ro/rts/](http://www.oby.ro/rts/)

You can sometimes find Bogdan at the MASM32 forum:
[http://www.masm32.com/board/index.php](http://www.masm32.com/board/index.php)

---

### Post by socool274 on 2009-09-06
I prefer somewhat cross platform things. I don't like Masm, because it only works on windows. I mean, that the assembler, is only for windows. GAS is a cross platform assembler. While, I understand that one piece of code, even with the GAS assembler cannot work on multiple platforms, it can still be changed, quite easily to fit each individual platform. Such as, you make the game specifically for linux, and it won't work on mac or windows. But with a small amount of code changes, you can make it fit on each individual platform. Masm code CAN'T be changed to fit any platform other than windows. But, I will look at this game.

---

### Post by socool274 on 2009-09-06
Wow, that game looks very good. It works very well with wine, also. So I was easily able to run it with wine. It's amazing the game was made with assembly.

---

