---
title: "Need drivers and info"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by ian60 on 2014-08-22
Hello,  ):P  I'm totally new to Linux and Ubuntu so please go easy with me.

Ok, I have a Ubuntu installation disc, but where do I get the drivers for my Asus M4A87TD motherboard?

At the moment I'm using win xp, with ms outlook express, can you recommend an email program to replace it?  

Is there a good alternative for windows media player?  

How do I play my old games, Silent Hunter 3, Call of duty, Risk2 etc?


Pleas keep all answers in plain English and un-technical  
Thank you for your help.

---

### Post by anchitsingh9 on 2014-08-22
You don't need to get drivers from somewhere else for Ubuntu, atleast that has been my experience.(except specific cases like graphics drivers, where the proprietary drivers may be better)
Besides, other drivers needed by Ubuntu can be download via Ubuntu-Software-Center>Edit>Software-Sources>Additional-Drivers.
Mozilla Thunderbird, the default mail client is an alternative to MS-Outlook.
The default player for music is Rhythmbox, which is fine, but if you need options, there are others such as 'Clementine', 'Audacious' available in the sofware-center.
Also Vlc is available from the software-center.
As far as the games you mentioned, you need windows :(
So I suggest you to have a dual-boot system.
Hope this helps

---

### Post by ian60 on 2014-08-22
Thank you for your reply.

So do you think the drivers install from the Ubuntu disc, or are drivers just not bothered with? As we know windows will work without driver installation, but not very well at all.

Can you give me the link to the software center please I can't find it.

---

### Post by anchitsingh9 on 2014-08-22
Drivers get installed from the disk.
Ubuntu-Software-Center is itself a software, you'll see it when you install Ubuntu.(You'll need internet connection to install softwares).

:)

---

### Post by ian-weisser on 2014-08-22
> **ian60 said:**
> where do I get the drivers for my Asus M4A87TD motherboard?

Does the Live environment on the install disc not work already with your motherboard? Have you tried it? Exactly what happens?


> **ian60 said:**
> can you recommend an email program?

Ubuntu comes with an e-mail program, Thunderbird. Why not try that first?


> **ian60 said:**
> Is there a good alternative for windows media player?

Several...including the one that included with Ubuntu. Why not try that first?


> **ian60 said:**
> How do I play my old games, Silent Hunter 3, Call of duty, Risk2 etc?

You don't. Learn to love Linux games. Most Windows games are are written for...Windows, of course. They are often incompatible with Ubuntu.


> **ian60 said:**
> windows will work without driver installation, but not very well at all.

Ubuntu is not a free clone of Windows. It's not based on Windows. The way it handles hardware (drivers) is completely different from the way Windows handles hardware.


Look,if you have an install disk that you downloaded from Ubuntu.com (instead of some random website), then it includes a risk-free Live environment to try without touching the hard drive. 
If the Live environment works with your hardware (wifi, USB, ethernet, keyboard, display, etc), then the installed version will work with your hardware. 
Open up Software Center and see the media applications, e-mail clients, and games that are available.
That's why it's there - to answer questions like yours. So stick it in the drive and boot from it.

If you have an install disk that you got from some other place on the random internet, delete it. Get a real, supported, tested, free install disk at Ubuntu.com.

---

### Post by coffeecat on 2014-08-22
> **ian60 said:**
> 
So do you think the drivers install from the Ubuntu disc, or are drivers just not bothered with? 

If drivers were not bothered with, nothing would work! :wink: In Linux-based operating systems, most of the drivers are in the Linux kernel and are activated if necessary. They are so comprehensive that if you find that something on your motherboard doesn't work, then you will be very unlucky. If you do find a piece of hardware that does not work by default, then start a thread here describing your problem and the piece of hardware and in most cases someone will be able to help you.

For your graphics card there are open source drivers as default for AMD, nvidia and Intel graphics devices. If you need extra performance for games and you have either AMD or nvidia graphics, you can install proprietary drivers, but the system will work satisfactorily with the default open source video driver. 

What might be a good idea for you is to get a feel of the Ubuntu desktop before you install if you have never used it before. Boot the live disc and after a minute or so you will be presentes with a choice of Install Ubuntu and Try Ubuntu. Choose Try Ubuntu and it will boot into a live desktop session. This will be sluggish - don't judge performance of a proper installation on the live session - but it will give you a chance to make sure all your hardware is working.

---

### Post by ian60 on 2014-08-22
Aha! Thank you. 
I'm so used to adding drivers to my Windows install that it's just the next progression, before adding other programs. It's become second nature.


All questions answered 

Thank you for your time  :D

---

### Post by Mike_Walsh on 2014-08-22
@ian60:

Drivers are not something you need to install for Linux.....coffeecat's perfectly correct about this (and he DOES know what he's talking about; I've received good advice  on more than one occasion); nearly half the Linux kernel is nothing BUT drivers, and with each kernel update, more and more open source equivalents for proprietary drivers (the type you are used to searching the web for) are added to it.

As one XP refugee to another, I, too, will echo the advice given by everybody else; if the LiveCD runs satisfactorily on your machine, and everything works as you would expect it to, then the installation itself WILL work; only considerably faster. Optical disc data transfer speeds are several times lower than that achieved even by older IDE PATA hard drives like my own; modern SATA hard drives will be considerably quicker still.

Regards,

Mike.

---

### Post by mastablasta on 2014-08-23
Regarding windows games - you can check which can be forced to work under linux here: [https://appdb.winehq.org/](https://appdb.winehq.org/)
everything below gold rating i susualyl not works looking at.

dualboot with windows XP is easy to do.

---

### Post by dave131 on 2014-08-23
If you dual-boot with XP so you can game, remember to turn off your networking in XP.  Things just aren't as safe as they used to be.  Also, I don't know what hardware you have, but if you have sufficient hardware you may want to try running a virtual machine with something like virtualbox and install XP in it.  Doing so would mean you wouldn't have to shutdown and reboot.  However, I believe there are also limits on the graphics, etc., that may impact the gaming in virtualbox.  I'm just a newbie myself, so I'll leave it to others to tell you about gaming and a virtual machine.

---

