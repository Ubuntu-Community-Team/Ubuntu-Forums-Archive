---
title: "Base failed ?"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by scottjge on 2008-07-23
Hi, I am new to the forum and am new to Linux. I am a windows long time user and just got tired of all the viruses and crashes and slow performance,so I decided to install Ubuntu.

Unfortunately, I am not having very good luck. This is day three of trying to install the program. Everything seems to go alright for a while then I come up with the message, " base failed to install". I have tried two or three different cd's, I have written the Ubuntu on the cd's at different speeds.(4x, 24x, 48x, etc) Nothing seems to work.

I have completely erased the hard drive but I still get the same results.

Any advise that you could give me would be greatly appreciated. Just keep in mind that I know absolutely nothing about Linux.

Thanks,
Glenn

---

### Post by halitech on 2008-07-23
Hello and welcome to the forum :)

a little info about your computer may help in fixing things up for you. Do you know the brand/CPU speed/amount of RAM/speed of CD/video card/previous version of windows?

---

### Post by Potatoj316 on 2008-07-23
Did you check the MD5 of the iso before burning to verify integrity?  Either way you could use the verify disk integrity thing before you try to install.

---

### Post by scottjge on 2008-07-23
thank you for your quick response.

I have a Compaq Presario 1200-XL105, 475Mhz processor, 160 meg Ram.
The original OS was Windows 98SE, then I installed Windows Xp and everything installed alright but I just got sick the hassles with windows.

How do I check the checksum ? I apologize for such a stuoid question but I am a true beginner at this.

---

### Post by halitech on 2008-07-23
with that machine and only 160 meg of ram I would recommend using the alternate install cd and probably Xubuntu as opposed to Ubuntu if you want Ubuntu. Otherwise I'd probably say go with Puppy LInux, DSL or Zen as they are better for lower end machiens.

---

### Post by Potatoj316 on 2008-07-23
You would have to check the MD5 before burning but its a pain on windows, in ubuntu you can do this
```
md5sum FILENAME
```
but since you already burned it it would be best to use the check disk integrity thing (or whatever its called), boot with your cd and when you get to the menu look for one to check the CD for defects (that might be what its called)

I agree with halitech, you probably cant even run ubuntu, you dont have enough RAM.  You could upgrade your ram to atleast 256MB or maybe try xubuntu.  But best to go with Puppy or DSL.

---

### Post by scottjge on 2008-07-23
Which system would you recommend for my application. My main concern is to be able to surf the web and get my email for now. Then I can dive in and learn Linux and all it's features later.

thanks,
Glenn

---

### Post by halitech on 2008-07-23
any modern distro will allow you to browse the web and get your email, heck even the old ones will that are command line only if you are that brave starting off  ;)

I would probably go with puppy ( [http://www.puppylinux.com/](http://www.puppylinux.com/) ) I've run it on my laptop before and as a virtual machine inside windows and it is pretty easy to use.

---

### Post by scottjge on 2008-07-23
Okay I will check out Puppy. I no longer have windows on the machine so what ever Linux that I put on it will be the only OS.

I checked the integrity of the cd and there were errors. I have burnt two more and they still have errors. I even tried two different mirrors.

thanks again,
Glenn

---

### Post by halitech on 2008-07-23
good luck and I'm sure it should work for you as long as your burns are okay.

one thing you may want to try before downloading and burnign another cd, boot the Ubuntu cd and when it gives you the menu, there is an option to run memtest, run that to check and make sure its not a ram problem.

---

### Post by scottjge on 2008-07-23
I did run the memory test and it check out ok.

---

### Post by halitech on 2008-07-23
ok, so that is at least 1 less thing to worry about. :) go grab the puppy iso and burn that and I'm sure you will be up and runnign in linux shortly :D

---

