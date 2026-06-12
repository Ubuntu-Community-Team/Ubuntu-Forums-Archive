---
title: "Programming Services?"
date: 2011-01-13
forum: Programming Talk
---

### Post by Xplat on 2011-01-13
Hi. I have an idea for an application programmed in assembly.

I don't know a thing about assembly, so I need someone to create it for me.

Is there any ubuntu-related service or something where people program my application?

---

### Post by Barrucadu on 2011-01-13
What is it and why should it be done in assembly? If you're absolutely certain it must be done in assembly:

1) Learn assembly
2) Write program
3) ????
4) PROFIT!

---

### Post by shadylookin on 2011-01-13
You can post a job offering lots of places, but expect to pay top dollar for anyone willing to write in assembly.

---

### Post by Xplat on 2011-01-13
> **Barrucadu said:**
> What is it and why should it be done in assembly? If you're absolutely certain it must be done in assembly:

1) Learn assembly
2) Write program
3) ????
4) PROFIT!

I'll describe the program:

This is a program that reads the low-level code of files and runs them if written in an executable format. If a program is missing a file, this application will recreate a file it is missing based on the "request" a program gives when executed. In other words, if a program is missing a file, this application will make a file with the needed parts of the missing file.

Sort of like if I compiled a file, instead of an error such as: "No such file or directory", this application would create the missing file with dummy functions named after the function being called. (for example). If the dummy functions are not recognized, this application will recreate the needed function parts based on the call and the code it is referring to.

It is supposed to run files (including games) from other platforms perfectly.

If there is some way to write this at all, let alone Assembly language, I would be pretty amazed.

---

### Post by unknownPoster on 2011-01-13
> **Xplat said:**
> 
It is supposed to run files (including games) from other platforms perfectly.

If there is some way to write this at all, let alone Assembly language, I would be pretty amazed.

Good luck with that. I'm fairly certain what you're wanting to do is impossible, that being said, if it were possible, why would you choose Assembly as that is platform/hardware specific?

---

### Post by myrtle1908 on 2011-01-13
> **Xplat said:**
> If a program is missing a file, this application will recreate a file it is missing based on the "request" a program gives when executed. In other words, if a program is missing a file, this application will make a file with the needed parts of the missing file.

Huh?  How would this magical program know what's supposed to be in these missing files?

---

### Post by worksofcraft on 2011-01-13
> **Xplat said:**
> ...
It is supposed to run files (including games) from other platforms perfectly.


Computer's may seem incredibly magical at times but sadly there is no magic involved. No matter how sophisticated, a computer is little more than a programmable calculator: You give it instructions and it does what they say.

If you give it instructions for hardware and system software that it doesn't have... it can't create them for you.

---

### Post by Yownanymous on 2011-01-13
> **myrtle1908 said:**
> Huh?  How would this magical program know what's supposed to be in these missing files?

If you manage to figure that out I'm sure you'd solve a lot of problems in computing. In other words it's more or less impossible.

---

### Post by Xplat on 2011-01-13
> **worksofcraft said:**
> Computer's may seem incredibly magical at times but sadly there is no magic involved. No matter how sophisticated, a computer is little more than a programmable calculator: You give it instructions and it does what they say.

If you give it instructions for hardware and system software that it doesn't have... it can't create them for you.

That's not what I meant. I meant that a program (maybe even an OS) would be written so that it would copy an instruction put into it by a foreign program and create something that does the instruction. An example would be: You are asked a question. You don't know the answer or want to give the answer, so you make up an answer that satisfies the asker.

Same concept.

---

### Post by CptPicard on 2011-01-14
So you're saying that if, for example, my program is missing a function for determining if some other given program ever halts with some given input, it will actually create that function for me?

*Cool.* I can see how this will revolutionize *everything!*

I also can't wait to apply this to things like find_prime_factors_real_fast(int)...

---

### Post by jerenept on 2011-01-14
[IMG]http://ubuntuforums.org/customavatars/avatar148462_7.gif[/IMG]

---

### Post by worksofcraft on 2011-01-14
> **Xplat said:**
> That's not what I meant. I meant that a program (maybe even an OS) would be written so that it would copy an instruction put into it by a foreign program and create something that does the instruction. An example would be: You are asked a question. You don't know the answer or want to give the answer, so you make up an answer that satisfies the asker.

Same concept.

So like say the image of Coco Bandicoot is missing from my game... then the computer just makes up something that looks like her in action?

Well that is not possible with the current state of technology.

I gather they are working on new quantum logic technology which in theory could one day have the capability to test all possible solutions simultaneously and retain only the "successful" ones, but even then it still needs some way to determine what constitutes success and what would be failure :shock:

---

### Post by Xplat on 2011-01-14
> **worksofcraft said:**
> So like say the image of Coco Bandicoot is missing from my game... then the computer just makes up something that looks like her in action?

Well that is not possible with the current state of technology.

Why not? An image on a computer is just processed code that tells the computer to display colors on a monitor, even in small pixels.

Besides, even if the image is not completely recoverable, I think you can trust game developers to include all the images and textures.

---

### Post by unknownPoster on 2011-01-14
> **Xplat said:**
> Why not? An image on a computer is just processed code that tells the computer to display colors on a monitor, even in small pixels.

Besides, even if the image is not completely recoverable, I think you can trust game developers to include all the images and textures.

Please tell me you are joking. What you're suggesting is an extremely advanced AI that can somehow determine the desires of a human at runtime. If you have any insight as to how to go about making this happen, I'm sure you'd be up for a Nobel Peace Prize.

---

### Post by worksofcraft on 2011-01-14
> **Xplat said:**
> Why not? An image on a computer is just processed code that tells the computer to display colors on a monitor, even in small pixels.

Besides, even if the image is not completely recoverable, I think you can trust game developers to include all the images and textures.

As far as the computer is concerned it is just writing numbers in a particular area of memory. It has no idea what they mean, or which ones make Coco's eyes or even how many eyes she has and whether they belong in her head or her toes and whether they move about or not :shock:

---

### Post by Xplat on 2011-01-14
> **worksofcraft said:**
> As far as the computer is concerned it is just writing numbers in a particular area of memory. It has no idea what they mean, or which ones make Coco's eyes or even how many eyes she has and whether they belong in her head or her toes and whether they move about or not :shock:


The intention of this concept application is it will recreate all the functions it can based on the main executable's request. The goal is for all the files to be recreated perfectly. That's why it needs to be written in a low level language.

So yes, although it won't know, it will recreate everything (at least, that is my goal).

---

### Post by schauerlich on 2011-01-14
I just want to post in this thread so that when I tell my grandkids about it, I have proof I was here.

---

### Post by worksofcraft on 2011-01-14
> **Xplat said:**
> ... That's why it needs to be written in a low level language.


Hummm... well... yes I think it would help you quite a lot to become familiar with a low level language like assembler.

That way you will understand the level of instructions that teh processor is performing.
Once you know just how primitive the internal mechanisms of a digital computer actually are, then you can learn about the fascinating art of computer programming and all the intelligent design of algorithms and data structures that make it possible for the computer to do what it can do :popcorn:

---

### Post by slavik on 2011-01-14
> **schauerlich said:**
> I just want to post in this thread so that when I tell my grandkids about it, I have proof I was here.

And I have proof of closing this thread.

I am sorry but this 'idea' is _VERY_ naive. What you are suggesting is basically what WINE does without actually implementing any functions.

Here's an actual solution to do what you want:
Replace function call (jump and save instruction) with a noop and you're done.

If you think this thread deserves to live, open a thread in the resolution center.

---

