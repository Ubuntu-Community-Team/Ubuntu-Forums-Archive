---
title: "Problem with Ubuntu 8.04"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jfh on 2008-05-21
I am using XP Serv. Pack 2, 3.40Ghz Intel Pentium4, 197 G free HD space, 2GB memory.  I have installed previous versions of Ubuntu in VM and Virtual Box, but had uinstalled all of them before installing Ubuntu 8.04.  At one point during the long installation (as a Windows program) a small blue box appeared with the legend:  "Out of Range 46.4kHz/87 Hz".  The box went away and the installation seemed to be completed sucessfully.  However, when I tried to shut down Ubuntu, the blue box appeared again withe the same message.  This time, my computer froze, and I had to unplug it in order to free it up and reboot it in Windows.  Can anyone tell me the meaning and importance of the messge in the blue box and what, if anything, I can do to avoid a repeat of this problem.  I enjoy using Ubuntu, but certainly don't want to have my computer freeze up each time I try to exit it.

---

### Post by dark_harmonics on 2008-05-21
That error message and blue box is referring to your display actually and is not happing in your os but is actually from your monitor. What is happening in your installation process to cause it, im not totally sure. Are you installing this in a virtual machine like VirtualBox or are you installing using Hardy's Wubi feature? It should not cause any crashes (I've not personally read of any on here yet).

---

### Post by jfh on 2008-05-21
No, I did not install via any virtual machine this time.  Instead, I used the option on the Ubuntu CD to install it as a Windows program - I assume that is the Wbui (I'm not familiar with that term). I can't imagine what the blue box message means re my monitor.  I take it for granted that the "terminal type" screen that appears on my monitor when I boot up is normal - the one that asks me whether I want to use Win XP or Ubuntu.

---

### Post by dark_harmonics on 2008-05-21
Oh yes thats normal. Its the bootloader. More details about the exact process and problem would help us help you here. That blue box with the mention of HZ is definitely monitor related (and how i knew it was a desktop not a laptop) but may be a result of the OS trying to put something to your monitor that it cant handle. Like if you set your screen resolution to something weird and it cant handle the output from the video card. Do you use a graphics card like ATI or Nvidia? If so you may need install some proprietary drivers from a recovery prompts to get your ubuntu functioning correctly. 

With hardy heron i didnt have to do this on my computers though. In previous versions, i had to install drivers for video before i'd even get an initial display.

---

### Post by jfh on 2008-05-21
Yes, I have an ATI graphics card.  By scroogling the term "out of range" I saeem to be getting an education re graphics cards and display settings.  Gawd, I hate messing with the display and such stuff. I guess I will have to decide whether I want to use Ubuntu that badly.  This item seems to explain at least an aspect of the problem.:
[http://www.sharpened.net/helpcenter/answer.php?15](http://www.sharpened.net/helpcenter/answer.php?15)
Thanks, dark_harmonics, for your help.

---

### Post by dark_harmonics on 2008-05-22
Sure i hope you can get past your glitch and get it working well. In my opinion its worth it but then I am the sicko who LIKES configuring my computer.

---

### Post by kansasnoob on 2008-05-22
I tried Wubi when 8.04 was still in Beta stage and still prefer an actual dual boot, but there is some great documentation here:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

I notice regarding video they address a couple of potential issues, but I'm unsure what the real answer is.

---

