---
title: "Installing Ubuntu on HP g-60 with a newly replaced hard drive"
date: 2017-05-13
forum: New to Ubuntu
---

### Post by pamlicopanther on 2017-05-13
Hello.  I am brand new to Ubuntu and wanted to prepare myself for potential difficulty I may encounter doing my first installation.  

I have a HP G-60 458 DX laptop with a dead hard drive.  I wanted to replace the hard drive and install Ubuntu in it.  I wanted this laptop to be exclusively Ubuntu with no Windows on it.  I have another laptop with Windows 10.  From what I have read so far is I download Ubuntu and either install by the DVD drive or USB.  Being this machine once had Windows on it, will it cause any conflicts with the other installed hardware?  Are there any potential conflicts I should be prepared for?

Thanks for any help with this.

---

### Post by Geoffrey_Arndt on 2017-05-14
It uses Intel cpu and Intel graphics, so that's a plus for a better linux experience.    The wireless chipset is not specified in the specs that I saw, but may be broadcom which means wireless may not work out the box, but can easily be installed via an ethernet connection via the "additional drivers" utility.   (click on the dash (top icon in launcher panel) and then just search for "additional drivers.)

As you said Ubuntu (or any other excellent Linux distro (such as Antergos, Solus, etc.) should install easily . . . but I suggest simplifying by enabling "Legacy" mode in the bios.   You will still have GPT partitioning versus MBR but not have the overhead of UEFI.   Of course - if the system is older than about 2010, maybe it is already Legacy BIOS which means you can have Ubuntu take over the whole drive during install - - - saving you a couple steps in the setup process.

---

### Post by pamlicopanther on 2017-05-14
Awesome - Thanks so much for your help.  I plan to dive into this later this week.  I am excited to see how this goes.

---

### Post by RobGoss on 2017-05-14
Hello and welcome to the forum, if you want this to be a Ubuntu only machine you should not have any problems installing Ubuntu, you are correct about burning the **ISO** file to a** USB or DVD**, I would recommend using a **"USB"** it's seems to be much easier. Once you have your USB ready, run the live installer to see how things work

When you're ready to begin your installation choose the **entire disk,** option this will use the whole hard drive for Ubuntu

---

### Post by pamlicopanther on 2017-05-16
> **RobGoss said:**
> Hello and welcome to the forum, if you want this to be a Ubuntu only machine you should not have any problems installing Ubuntu, you are correct about burning the **ISO** file to a** USB or DVD**, I would recommend using a **"USB"** it's seems to be much easier. Once you have your USB ready, run the live installer to see how things work

When you're ready to begin your installation choose the **entire disk,** option this will use the whole hard drive for Ubuntu

Thanks for the welcome and thanks for the information.  I should have my new hard drive here soon and I plan for this to be my weekend project.

---

### Post by RobGoss on 2017-05-17
If you have any more questions we'll be glad to answer them

Have a great day

---

### Post by gordintoronto on 2017-05-17
One of the ways to create a working USB is pendrive linux.

Since the machine is seven years old, it might be better to use Xubuntu, Ubuntu Mate or Lubuntu. You could try each of them from a Live USB to see which one tickles your fancy. The 16.04 LTS would probably be best for you.

---

### Post by pamlicopanther on 2017-05-21
Ok - So I received my new hard drive and installed it yesterday.  Today I installed Ubuntu on it via USB.  I had no problems at all.  I am actually posting using this older laptop with Ubuntu.  I did plug in my wired connection anticipating a possible problem with wireless.  I am trying to get the wireless going, but so far I have not been able to.  I will keep researching this and see what I can find out.  I just wanted to say thanks to everyone for their help.  I have wanted to play with Linux for a long time and it is cool to finally be doing it.

---

### Post by RobGoss on 2017-05-21
If you're having issues with your WiFi you should open another thread to get the help needed

---

### Post by pamlicopanther on 2017-05-21
That was going to be my next thing to do.  Right now I am researching it and hoping I can figure it out..

---

### Post by RobGoss on 2017-05-21
Post your question about your WiFi issue I'm sure someone should be able to figure out what's going on with it

---

