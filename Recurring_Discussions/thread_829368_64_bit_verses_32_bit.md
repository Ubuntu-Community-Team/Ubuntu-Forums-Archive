---
title: "64 bit verses 32 bit"
date: 2008-06-14
forum: Recurring Discussions
---

### Post by kalesh7 on 2008-06-14
so I have 32 bit ubuntu 7.10 running, I want to upgrade to 8.04, but I am thinking what to do just upgrade? or to installed 64 bit?
so I would like to know some advantages(or disadvantages) of 64 bit over 32 bit(or vice versa)? from experience please.

---

### Post by Kilz on 2008-06-14
> **kalesh7 said:**
> so I have 32 bit ubuntu 7.10 running, I want to upgrade to 8.04, but I am thinking what to do just upgrade? or to installed 64 bit?
so I would like to know some advantages(or disadvantages) of 64 bit over 32 bit(or vice versa)? from experience please.

[Take a look here.]("http://ubuntuforums.org/showthread.php?t=765428") The 32bit vs 64bit question has been gone over, and over, and over.

---

### Post by Stolea on 2008-06-15
I have both the 32 and 64 bit versions installed on one of my computers. I had some weird problems with the 64 bit installation with graphics card not loading the ATI driver properly, some odd network problems and my UPS not being recognized.
After installing the 32 bit version, most of those problems were resolved. there is a difference in speed, but nothing that I would get exited about. I guess if you were to do lots of number crunching or compiling this would make a difference, but for what I have to do, it doesn't matter.
From what I have seen, 32 bit is older and therefore more stable. But the decision would have to be yours based on what hardware you have and what sort of work you do.

---

### Post by Sef on 2008-06-15
32-bit and 64-bit both go back to 1961 at least.

From [Wikipedia]("http://en.wikipedia.org/wiki/64-bit"):

>     * 1961: IBM delivers the IBM 7030 Stretch supercomputer, which uses 64-bit data words and 32 or 64-bit instruction words.


---

### Post by d0x! on 2008-06-15
im new to ubuntu (just last monday)
and chosen to use the 64 bit version.
i read all the guides on this forum, particulary the stickies ;)

so far so good and im really enjoying thr ubuntu experience thus far :D
nothing in wrong in trying 64 bit, if you dont like it jump to 32bit.

---

### Post by Arkold Thos on 2008-06-15
64 bits thingies are toooo old, as the example of Sef there is one quite old for now console know by all that had a 64 bits processor, the Nintendo 64 :D

---

### Post by Stolea on 2008-06-15
> **Sef said:**
> 32-bit and 64-bit both go back to 1961 at least.

From [Wikipedia]("http://en.wikipedia.org/wiki/64-bit"):

I can only base my assessment on my experience on my hardware, and by no way am saying that this is the same for everyone. 
This setup is an AMD 64/3000 on a Gigabyte GA-K8NSC-939 board with ATI 9550/128 graphics card, 2gig ram, 320gig SATA (WinXP), 200gig SATA (Ubuntu 8.04 64 bit) 40gig IDE (Ubuntu 32 bit).
I did 4 installs of the 64 bit version and always had the same odd problems, like the ATI driver not working or even the plain vanilla driver only functioning in basic mode only. The network setup had its own mind on how it should function and it took a fair bit of fiddling to get it to talk to my XP machines, and in the end sort of works. My MGE UPS point blank refused to install by adding the recommended repository to the list of repositories or for that matter even recognize the fact that there is a UPS connected.
The 32 bit install had the network working straight out of the box, the graphics card runs in all modes from setup, the ATI driver installs and works straight away, the UPS software installs but, for some reason that I haven't worked out yet, doesn't connect to the UPS.
Basing my assessment on those facts, I have to say that the 32 bit version is (at least on this configuration) better.

---

### Post by Kilz on 2008-06-15
> **Stolea said:**
> I can only base my assessment on my experience on my hardware, and by no way am saying that this is the same for everyone. 
This setup is an AMD 64/3000 on a Gigabyte GA-K8NSC-939 board with ATI 9550/128 graphics card, 2gig ram, 320gig SATA (WinXP), 200gig SATA (Ubuntu 8.04 64 bit) 40gig IDE (Ubuntu 32 bit).
I did 4 installs of the 64 bit version and always had the same odd problems, like the ATI driver not working or even the plain vanilla driver only functioning in basic mode only. The network setup had its own mind on how it should function and it took a fair bit of fiddling to get it to talk to my XP machines, and in the end sort of works. My MGE UPS point blank refused to install by adding the recommended repository to the list of repositories or for that matter even recognize the fact that there is a UPS connected.
The 32 bit install had the network working straight out of the box, the graphics card runs in all modes from setup, the ATI driver installs and works straight away, the UPS software installs but, for some reason that I haven't worked out yet, doesn't connect to the UPS.
Basing my assessment on those facts, I have to say that the 32 bit version is (at least on this configuration) better.

So because you couldn't get ati drivers working you prefer the 32bit version? I could probably find 30 posts from people using ati cards running the 32bit version with problems.
But thats the problem with these threads, they do nothing but give opinions of someone who may or may not have any experience with Linux and installing things. There is a learning curve, and if your idea of solving the problem is just to reinstall the operating system to see if multiple installs will fix it, you may need to learn  a little.

---

### Post by Stolea on 2008-06-15
I admit , I am a rookie if it comes to things Linux. 
I have found the Ubuntu community very generous in offering help and advice with solving my various problems, for which I am very greatful. I was simply reporting on my experience with the different flavours as I found them on my setup, and thought I made that pretty clear.
I was under the impression that forums are there to offer your finding/advice/feedback to those asking (at least that how it has worked for me). I didn't realize that it was the reserved domain of the very senior experienced users to offer opinions or advice.
I take note and will mend my errenous ways.

---

### Post by Kilz on 2008-06-15
> **Stolea said:**
> I admit , I am a rookie if it comes to things Linux. 
I have found the Ubuntu community very generous in offering help and advice with solving my various problems, for which I am very greatful. I was simply reporting on my experience with the different flavours as I found them on my setup, and thought I made that pretty clear.
I was under the impression that forums are there to offer your finding/advice/feedback to those asking (at least that how it has worked for me). I didn't realize that it was the reserved domain of the very senior experienced users to offer opinions or advice.
I take note and will mend my errenous ways.

The x86 64-bit Users section is a support section. Feel free to add comments that help people. This thread is not a support thread. Its an opinion piece, my comments were on the reliability of the opinions. 
Just as you would probably listen to a seasoned trained mechanic vs a back alley teenager who can do brakes if you want an opinion on what car to buy. So someone asking these questions should understand who is replying.

---

### Post by Jouke74 on 2008-06-17
To be honest, what is so difficult about simply trying the 64 bit first, before you use the 32 bit? It might cost about 2 to 3 evenings to fully install Ubuntu and set and test everything (at least that's my experience). Not to mention it is possible to simply use a 64 bit live CD and check it out. 

Given that you are going to use an OS for some time on a regular basis (or at least 6 months :-) ) some investment of time before the big install is not too much to ask for.

Furthermore the 64 bit experience is completely dependent on your hardware and how you are able to deal with any issues. The same goes for 32 bit. I can tell you it runs great on my computer, however if I plug in a different wireless network card it could run only without internet because for that particular card there is no linux or ndiswrapper support.

---

