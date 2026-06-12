---
title: "Ubuntu mobile phone?"
date: 2008-04-13
forum: Programming Talk
---

### Post by RedPandaFox on 2008-04-13
I own a [[COLOR="Blue"]UTSTARcom DV007 smart phone [/COLOR]]("http://www.intomobile.com/2007/06/13/utstarcom-dv007-swivel-camcorder-phone-does-linux.html")which runs on a Linux OS by default, I’m not sure what OS it is running but I know it is Linux, I was at a LAN the other night and a guy I know in IT told me it would even be possible to hack it to run on Ubuntu, given the correct programming.
At the moment Telstra (My service provider in Australia) will not offer support for my phone which it does not recognise the settings for, I know it is possible to hack the phone to run MMS which will not work currently. So I was thinking, while I’m trying to get MMS working, why not look into this Ubuntu mobile?
Is there currently a mobile version of Ubuntu which I could install, or is there any programs which allow me to make calls, sms and mms?
If I need to I can easily put in a flash card to run off as I know I will require more memory to install it on.
If I can’t get Ubuntu on it, is there a more customisable version of mobile Linux I can use on it?

---

### Post by xelapond on 2008-04-14
What kind of processor does that have?  You might have a chance at getting Debian to run on it, but there is a small change for Ubuntu.  You will have to know a ton about JTAG and Flash Flashing, you might even have you write your own bootloader for it.

---

### Post by RedPandaFox on 2008-04-14
Im not sure what kind of processor, iv been looking around doing some research but i worked out there is a mobile version of Ubuntu, but it is for mobile internet devices not mobile phones. And I cant find anywhere to get Mobilinux 5.0
I'm only new at Linux and programing but if someone can give me a hand, i don't mind mucking around with it a bit if someone can help me.

---

### Post by zubu on 2008-04-16
i was also thinking about loading ubuntu on a mobile phone . it would be nice if you could share some info about what you have got upto now.

---

### Post by xelapond on 2008-04-16
You will probably spend hours of time, hundreds of dollars on debug quipemnt, and hours more learning how to program.  There is no ARM port of Ubuntu, so you would have to make that youreself.  What you would end up with is a hardly usable slow cellphone that can't make calls.  It could be as easy as porting and flashing over USB, or you might have to open it up, pop some JTAG traces of the board, solder to them, and flash over JTAG. I would recommend either trying to load OpenMoko, Android or QTopia on it.  Or just go buy a Neo FreeRunner.

It *could* be done, but it is not for the faint of heart.

---

### Post by Ferrat on 2008-04-16
> **xelapond said:**
> You will probably spend hours of time, hundreds of dollars on debug quipemnt, and hours more learning how to program.  There is no ARM port of Ubuntu, so you would have to make that youreself.  What you would end up with is a hardly usable slow cellphone that can't make calls.  It could be as easy as porting and flashing over USB, or you might have to open it up, pop some JTAG traces of the board, solder to them, and flash over JTAG. I would recommend either trying to load OpenMoko, Android or QTopia on it.  Or just go buy a Neo FreeRunner.

It *could* be done, but it is not for the faint of heart.

There is an ARM port of Ubuntu 
[https://wiki.ubuntu.com/EmbeddedUbuntu](https://wiki.ubuntu.com/EmbeddedUbuntu)

---

### Post by xelapond on 2008-04-16
> There is an ARM port of Ubuntu 

Sorry, I had no idea.  It would still be a big chore though, because they don't want you to reflash the phone.  What OS is on it now?  Does is support booting off SD Cards?  Can users write programs for it?

---

### Post by RedPandaFox on 2008-07-03
The phone runs on a PXA270 processor iv been told, [http://www.howardforums.com/showthread.php?t=1146508&page=16&pp=15](http://www.howardforums.com/showthread.php?t=1146508&page=16&pp=15) is a good forum iv been going on regarding this phone, it has lots of info on the phone and some people have access to the console, im not the most tech savy person in the world, but I learn through trial and error if someone is prepared to help me

---

