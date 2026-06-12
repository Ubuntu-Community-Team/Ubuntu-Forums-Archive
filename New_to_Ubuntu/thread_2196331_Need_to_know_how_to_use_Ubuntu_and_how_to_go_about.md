---
title: "Need to know how to use Ubuntu and how to go about gaming"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by alaricmercier on 2013-12-28
I am running Ubuntu 12.04 on an Alienware 17, Intel i7-4700MQ CPU, Nvidia 765m GPU, 16GB RAM, 120GB SSD, 750GB HDD. I mainly only play Minecraft and Skyrim and Dark Souls so I need help with setting up Skyrim and Dark Souls. I am brand new to Linux, just installed it, and need help with how to go about getting all of the correct drivers I need to play my games and such.

---

### Post by Bucky Ball on 2013-12-29
Skyrim appears to run in Wine, although how well, not sure. Read this:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749](http://appdb.winehq.org/objectManager.php?sClass=version&iId=24749)

Dark Souls has a gold rating on WineHQ so that's looking good:

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=14458](http://appdb.winehq.org/objectManager.php?sClass=application&iId=14458)

Getting them up and running in Wine is about as straightforward as install Wine>Install the game in Wine as you would in Windows.

The game will either work or not. Dig around for tweaks with something like a search for:

'ubuntu install dark souls'

Correct drivers? Not sure what you mean. If your Ubuntu 12.04 LTS install is running without issues unsure what drivers you need. :-k

If 12.04 is running without issue then this thread should probably be moved to ***Gaming & Leisure*** or ***Wine ***as the games seem to be your main issue.

---

### Post by alaricmercier on 2013-12-29
do i need nvidia drivers for my linux at all is what i mean as my gpu is nvidia 765m

---

### Post by Bucky Ball on 2013-12-29
Possibly not. If you're running Ubuntu fine at the moment, then to run Ubuntu you don't need them (I don't use them on this install myself). To run your games efficiently, that's a completely different matter which is going to take some research. Look for system requirements, particularly graphics, for the games you're looking to run. 

The other option is to install and run them, if they look under par, try with the nvidia drivers.

You should find some clues in the comments on WineHQ for each game.

You do have another option. Install Virtualbox (it's in Software Centre) and install Windows as a virtual machine, then just install the games in that. Or dual-boot with Windows.

---

### Post by 3rdalbum on 2013-12-29
> **Bucky Ball said:**
> Possibly not. If you're running Ubuntu fine at the moment, then to run Ubuntu you don't need them (I don't use them on this install myself). To run your games efficiently, that's a completely different matter which is going to take some research. Look for system requirements, particularly graphics, for the games you're looking to run. 

The other option is to install and run them, if they look under par, try with the nvidia drivers.

You should find some clues in the comments on WineHQ for each game.

You do have another option. Install Virtualbox (it's in Software Centre) and install Windows as a virtual machine, then just install the games in that. Or dual-boot with Windows.

Hi Buckyball, sorry to be a downer but your advice in this message is not good.

If you want to play games, you **need** the Nvidia driver. Click the Ubuntu button and type "drivers" - the first result will be the Additional Drivers program, so click that. You'll be given the option to download and install the Nvidia driver for your card. If it doesn't give the option, then your card might be newer than 12.04 and you'd need to install the driver from a PPA - but we'll cross that bridge if the Additional Drivers thing doesn't work. Let us know how it goes.

Playing games in a virtualised Windows simply isn't a reality; too much overhead, and insufficient 3D support within a virtual machine.

The "dual boot" idea is fine. That's what I do, I have a cheap copy of Windows Vista installed on my disk, and I only boot it occasionally for a game. Most of my real work and browsing happens in Ubuntu.

---

### Post by Bucky Ball on 2013-12-29
> **3rdalbum said:**
> Hi Buckyball, sorry to be a downer but your advice in this message is not good.



All good. Not a gamer so don't know what's required for gaming on Linux or any other OS. ;)

---

### Post by alaricmercier on 2013-12-29
thank you so much man, and i would dual boot but I do not like Microsoft anymore, I am not trying to hate on them it's just, with all they have done in the past 2 years to their OS and the Xbox, I want nothing to do with them, and maybe I will use Windows Vista the last review for gaming I saw for Vista was when Vista came out and then everyone avoided it like the it was the Black Death, and I just installed the drivers but anytime in the past 3 hours I have restarted my PC I have had to forcefully shut it down by holding the power button down until it shut off, I have just reinstalled Ubuntu and I am going to try and restart it, hopefully it works, will keep you posted on what happens.

---

### Post by Bucky Ball on 2013-12-29
Please do not post duplicates. You are already being helped with the same here.

Creating multiple posts on the same topic reduces your chances of help. If you want the thread title changed, just ask.

---

### Post by alaricmercier on 2013-12-29
alright

---

### Post by alaricmercier on 2013-12-29
I checked the update info for nvidia 319 and it says it doesnt support my 765m

---

### Post by Bucky Ball on 2013-12-29
See the answer with the green tick here:

[http://askubuntu.com/questions/351404/nvidia-gtx-765m-with-optimus-unclamed](http://askubuntu.com/questions/351404/nvidia-gtx-765m-with-optimus-unclamed)

Appears you need to add the xorg-edgers ppa for this card.

The second one here might also give some clues:

[https://duckduckgo.com/?q=Nvidia+765m+ubuntu](https://duckduckgo.com/?q=Nvidia+765m+ubuntu)

* Tip: do a search for your issue and see what you dig up. 

'ubuntu 12.04 nvidia 765m'

---

### Post by 3rdalbum on 2013-12-29
Agreed :-)  You might also need to install the nvidia-current package:

```
sudo apt-get install nvidia-current nvidia-settings
```

If it doesn't work, try this page:

[http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

### Post by alaricmercier on 2013-12-29
I don;t know what I am doing...anytime now my resolution is at 1024x768 instead of 1600x900... can you please post a step by step guide?

---

### Post by alaricmercier on 2013-12-29
Okay so the nvidia 319 driver doesnt support my gpu but  its what steam recommended, how would i go about installing the 325 driver?

---

