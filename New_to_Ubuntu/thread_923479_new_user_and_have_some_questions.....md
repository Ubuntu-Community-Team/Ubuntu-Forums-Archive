---
title: "new user and have some questions...."
date: 2008-09-18
forum: New to Ubuntu
---

### Post by phoenix_snake on 2008-09-18
Hi, I am new here and would like to ask some questions before getting started.

I have a Dell Inspiron 1525 with these specs

Intel Core2Duo 2.10ghz
2gb ram
Sigmatel Audio
Intel 965 Express Chipset family vga card
Integrated laptop webcam from Creative don't know much else about it.
Conexant HDA D330 MDC V.92 Modem
Dell Wireless 1395 Broadcom 
Marvel Yukon 88e8040 Ethernet

Oh yeah and it has a remote control as well.

Will linux support all this stuff? Could I run in to any difficulty?

I have Vista right now and am satisfied with it, I just want to try something new.

I have downloaded ubuntu and kubuntu right now and I like kubuntu more, so is it possible to setup a dual boot?

how to partitions and stuff and what is swap?

I also read while surfing that a new version is coming out soon, anyone thinks I should wait for that instead?

Thanks for the help.

---

### Post by egalvan on 2008-09-18
> **phoenix_snake said:**
> Hi, I am new here and would like to ask some questions before getting started.

I have a Dell Inspiron 1525 with these specs

Intel Core2Duo 2.10ghz
...
I also read that a new version is coming out soon, anyone thinks I should wait for that instead?

Thanks for the help.

The  new version 8.10 will be called Intrepid Ibex (or sp?)

It is supposed to have superior 64-bit support, which is what I am waiting for...

But I am running 32-bit 8.4.01 right now.
i don't see any use wasting all that time, waiting for a new version,
when I can be having so much fun, and education, running Ubuntu/Kubuntu

---

### Post by phoenix_snake on 2008-09-18
> **egalvan said:**
> The  new version 8.10 will be called Intrepid Ibex (or sp?)

It is supposed to have superior 64-bit support, which is what I am waiting for...

But I am running 32-bit 8.4.01 right now.
i don't see any use wasting all that time, waiting for a new version,
when I can be having so much fun, and education, running Ubuntu/Kubuntu
Hi, thanks for your response. I want to run the 64 bit version as well, so will all my hardware be supported?

---

### Post by fourthofjuly on 2008-09-18
> **phoenix_snake said:**
> Hi, I am new here and would like to ask some questions before getting started.

I have a Dell Inspiron 1525 with these specs

Intel Core2Duo 2.10ghz
2gb ram
Sigmatel Audio
Intel 965 Express Chipset family vga card
Integrated laptop webcam from Creative don't know much else about it.
Conexant HDA D330 MDC V.92 Modem
Dell Wireless 1395 Broadcom 
Marvel Yukon 88e8040 Ethernet

Oh yeah and it has a remote control as well.

Will linux support all this stuff? Could I run in to any difficulty?

I have Vista right now and am satisfied with it, I just want to try something new.

I have downloaded ubuntu and kubuntu right now and I like kubuntu more, so is it possible to setup a dual boot?

how to partitions and stuff and what is swap?

I also read while surfing that a new version is coming out soon, anyone thinks I should wait for that instead?

Thanks for the help.
if you have vista installed, simply install wubi in vista:-

 [http://wubi-installer.org/]("http://wubi-installer.org/") 

then reboot from your *buntu disk... *buntu will install like any other program in vista

no need to partition

you can uninstall *buntu from vista just as any other program...

cheers!

devang.

---

### Post by aysiu on 2008-09-18
Probably the Broadcomm wireless will not work, but there may be usable workarounds.

In the meantime, if you want to play around, there are several things you can do apart from a full install: [list][*][Install Ubuntu or Kubuntu has a virtual machine inside Vista](http://www.psychocats.net/ubuntu/virtualbox).[*]Use the live CD of Ubuntu or Kubuntu to run a Ubuntu or Kubuntu operating system out of your computer's RAM and not affecting your hard drive at all. [*]Using the CD within Windows to install a dual-boot (otherwise known as a Wubi installation). No repartitioning necessary. Windows boot loader will be untouched.[/list]

---

### Post by phoenix_snake on 2008-09-18
yeah I tried the live cd for ubuntu just again and everything seems to work, except of wireless, I haven't tested the modem, actually I don't know how to test the modem?

bluetooth works, its light is on and closing lid puts it to sleep and stuff, how can I try hibernate?

can anyone tell me how to change brightness settings for the screen on ubuntu as well?

thanks :)

---

### Post by crazypenguin2008 on 2008-09-18
open a terminal and type this command.

$ xgamma -help

that should take u to where u can bump the gama up or down

you will probly have to run the command "cheese" in terminal to get the webcam to work in skype and amsn as well.

remove the quuotation marks around cheese first of course

---

### Post by phoenix_snake on 2008-09-18
thanks I will try the brightness thing right now :)

---

### Post by phoenix_snake on 2008-09-18
alright so I found out that fn + up and down keys adjust brightness as well but is there a way to configure brightness on AC power and battery like on Windows?

I am still seeing if I like the apps yet, webcam works :) but can I use a webcam on this app called pidgin?

---

### Post by aysiu on 2008-09-18
> **phoenix_snake said:**
> alright so I found out that fn + up and down keys adjust brightness as well but is there a way to configure brightness on AC power and battery like on Windows? According to this page, yes, but there are no instructions on how to set it up that way:
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525)

---

### Post by crazypenguin2008 on 2008-09-18
no,pidgin has no means to do voice or video. but you can gte skype or AMSN for ubuntu that will allow you voice and video for their respective protocalls

---

### Post by phoenix_snake on 2008-09-18
thanks everyone for the links as well, I will try to configure my wireless card now

---

### Post by phoenix_snake on 2008-09-18
everyone just one more thing I need help setting up, my media keys on the keyboard work for example the play stop and volume control keys but on the inspiron on the left of the power button I have a home key that opens up Dell Media Direct on Vista, can I configure it to do something on Ubuntu?

---

### Post by lolostich on 2008-09-18
this site will help...

[http://sikh.myminicity.com/tra/](http://sikh.myminicity.com/tra/)

good luck

---

### Post by vikram on 2008-09-18
Webcam works with Kopete. It should already be installed if you installed Kubuntu. If you installed Ubuntu you can easily install it since it is in the repos.

FYI I installed Kubuntu on my wifes Dell 1525. Wireless works with Ndiswrapper, no problems with webcam etc.

Funny thing hibernate works with Kubuntu but not Vista - and the laptop came installed with Vista ! how wierd is that ?

> **phoenix_snake said:**
> alright so I found out that fn + up and down keys adjust brightness as well but is there a way to configure brightness on AC power and battery like on Windows?

I am still seeing if I like the apps yet, webcam works :) but can I use a webcam on this app called pidgin?

---

### Post by phoenix_snake on 2008-09-18
> **vikram said:**
> Webcam works with Kopete. It should already be installed if you installed Kubuntu. If you installed Ubuntu you can easily install it since it is in the repos.

FYI I installed Kubuntu on my wifes Dell 1525. Wireless works with Ndiswrapper, no problems with webcam etc.

Funny thing hibernate works with Kubuntu but not Vista - and the laptop came installed with Vista ! how wierd is that ?
might be just your laptop cause hibernate works fine for me on Vista and its been hibernating for almost 4 days without problems, thanks for telling me about kopete though, I also read about this other msn clone called amsn and I managed to install Skype :)

---

