---
title: "[SOLVED] Problems installing Ubuntu"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by Vunutus on 2008-09-17
I've installed Ubuntu a handful of times and installed Fedora many times for a class, so it's not like I'm clueless here.

Whenever I boot from my Ubuntu (8.04) CD, it gives me the menu where I select my language and choose what I want to do. I choose to install Ubuntu, and it goes to the Ubuntu progress bar/bouncy thing. Stays there a while, then it loads some basic shell (TinyBox I think was the name) and sticks there without progressing. I looked through the command list for this shell and none of the provided commands seemed to allow me to continue installation. Thinking it may be a CD problem, I reboot and run the built-in media test. It does the exact same thing, progress bar then the shell. I'm fairly certain there is nothing wrong with my disc, however. I've installed off it onto another computer and it is 100% scratch free.

What could be the problem here?

---

### Post by Crafty Kisses on 2008-09-17
What are your system specs?

---

### Post by jken146 on 2008-09-17
Try the option for 'low-graphics mode' or some such, or use the Alternate CD.

---

### Post by Vunutus on 2008-09-17
> **Codename said:**
> What are your system specs?

Athlon 64 3200+ with 1GB memory 
gforce 6800 XT

---

### Post by Titan8990 on 2008-09-17
Some boards don't agree with Live CDs. Like mentioned earlier, try the alternate CD.

---

### Post by Vunutus on 2008-11-05
Bumping this with more information.

I held off on tinkering with Ubuntu for a while until this week. I still have the same problem with my official 8.04 CD. In an effort to track the problem down, I tried three additional versions of Linux.

First, I took the suggestions in this topic and downloaded the alternate 8.04 CD and burnt it on my own disc. It goes through keyboard and language configuration, then stops with an error saying that the cd drive cannot be mounted. 

Second, I had an old Ubuntu 5.10 Live CD sitting around and I tried it. It simply freezes up at the first menu.

Thirdly, I tried a Knoppix Live CD I had sitting around. Works like a charm, no problems.

Does Ubuntu hate my computer?

---

### Post by mapes12 on 2008-11-06
> Does Ubuntu hate my computer?

Could we have a look at the spec / configuration please. Could you post the output to:

```
sudo lshw
```

---

### Post by LowSky on 2008-11-06
did you build the computer yourself?
Make sure the CD drive has the correct 80 pin IDE cable and not a 40 pin cable. For some reason this issue pops up now and again. I used to suffer from something simular.

---

### Post by Vunutus on 2008-11-06
> **mapes12 said:**
> Could we have a look at the spec / configuration please. Could you post the output to:

```
sudo lshw
```

I'd love to oblige here but my problem here is not even being able to get Ubuntu running at all. I'm a ways away from being able to run commands :)

I posted my CPU/RAM/video card earlier. I forgot what motherboard I have, but I know it's an Asus model.

> **LowSky said:**
> did you build the computer yourself?
Make sure the CD drive has the correct 80 pin IDE cable and not a 40 pin cable. For some reason this issue pops up now and again. I used to suffer from something simular.

I did indeed build the computer myself, but my CD/HDD are on SATA , not IDE.

I've also done some more searching around and came up with more information. The shell it brings me to is called "BusyBox" not "TinyBox". It says nothing other than "(initramfs)". I searched the forums based on this and found a few people with potential solutions, and none of them seem to work for me. The only one I'm not sure about is adding "IRQPOLL" to the boot options. I tried this, but I'm not sure I did it right. I hit F6 on the CD menu and it brought up a string with some stuff ending in "--". I typed IRQPOLL there. Was that the correct way of doing it?

I'm really hoping somebody here knows a way to fix this, I'm anxious to give Ubuntu a serious spin.

---

### Post by bennachie on 2008-11-07
This is a common problem. For many people, the bug can be bypassed by hitting F6 when the boot dialogue appears, then adding:

all_generic_ide floppy=off irqpoll

at the end of the line of parameters that is presented. It worked for me, and my old backup computer seems to have much the same specifications as your own.

No harm in trying.

---

### Post by Vunutus on 2008-11-07
> **bennachie said:**
> This is a common problem. For many people, the bug can be bypassed by hitting F6 when the boot dialogue appears, then adding:

all_generic_ide floppy=off irqpoll

at the end of the line of parameters that is presented. It worked for me, and my old backup computer seems to have much the same specifications as your own.

No harm in trying.

Thanks! That seems to have solved it. I have Ubuntu up and running now. 

Thus begins a journey that brings up dozens of other questions, but that's for another time and another topic.

---

