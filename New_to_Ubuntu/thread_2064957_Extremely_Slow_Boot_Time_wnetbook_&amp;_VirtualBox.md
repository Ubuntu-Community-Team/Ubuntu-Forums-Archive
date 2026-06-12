---
title: "Extremely Slow Boot Time w/netbook &amp; VirtualBox"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by jeremydfleck on 2012-09-30
For the college program that I'm enrolled in, I have to be able to use Linux and Windows essentially at the same time. I was advised to install VirtualBox inside my Windows 7 OS, and then Ubuntu inside VirtualBox. VirtualBox opens fairly quickly, but it takes over 5 minutes to boot Ubuntu to the point of the login page, and then another 3 minutes to get to the Ubuntu desktop (not sure if that's what it's actually called). Once in, simply opening Terminal and Text Editor (gedit) is painfully slow. In the meantime, if I click back over to Windows, I don't seem to have any tangible performance issues with Windows. I've installed all available updates and guest additions. 
 
Please help, as I'm getting farther and farther behind in my classes as a result. 
 
I'm using a Dell Mini 1012, running Windows 7 Starter, with 2gb of RAM, and version 11.10 of Ubuntu inside VirtualBox. 
 
Thanks...

---

### Post by DaGeek247 on 2012-09-30
Judging from the specs/review at **[http://www.notebookcheck.net/Review-Dell-Mini-1012-Netbook.25429.0.html](http://www.notebookcheck.net/Review-Dell-Mini-1012-Netbook.25429.0.html)** your netbook has a fairly small processor, and in effect, not much ability to run cpu intensive programs. According to the review, the windows experiance index on your processor is a 2.3 and it has 1.66Ghz processor. This is not good.

The Virtualbox System requirements that are located [here]("https://www.virtualbox.org/wiki/End-user_documentation"), have stated this:
> 
In order to run VirtualBox on your machine, you need:
...
Reasonably powerful x86 hardware. Any recent Intel or AMD processor should do.


This all means your netbook cannot handle two operating system at the same time.

I had this same experience on my old 2.4Ghz Intel processor, so the people at virtualbox probably mean it when they say they want a 64bit processor to run.

To fix this, I would suggest installing ubuntu alongside windows here:
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) and here:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
The only issue with this is that you dont get to switch between windows and virtual box by the click of a mouse, you have to restart the pc to switch.

Or maybe [getting a 64bit laptop instead]("http://www.newegg.com/Store/SubCategory.aspx?SubCategory=32&name=Laptops-Notebooks"). The issue with this is; you have to buy a new laptop, which is usually (in the needs you mentioned) about 400$+.

Lastly, you could drop the class. i don't know how important your class is, but if its causing you issues like this, and my previously stated suggestions aren't right for you, maybe this one is.

---

### Post by jeremydfleck on 2012-09-30
DaGeek247, thanks for your expedient response, I feel like I'm drowning here.  
 
Even considering I'm a bit of a novice, everything that you're saying makes complete sense to me, except...  
 
If this is a processor issue (which I don't doubt), why does Windows 7 seem to run fine even with VirtualBox/Ubuntu open?  
 
Ultimately, a new, much faster machine will be replacing my netbook, but that may be 2-3 months away, and I have to take these classes for my program/major, so dropping them is not an option.  
 
Thanks...

---

### Post by DaGeek247 on 2012-09-30
I honestly do not know for sure why it does not work in the way you described.

However, going into the realm of *guesswork* based on past experience and knowledge, this is what *might* be happening.

VirtualBox was first released on 04 September, 2007 and as such, the developers have had plenty of time to test debug and get user input. *Perhaps* when they released or tested in development the original virtual box did split the processor evenly so both operating systems would run at the same speed. However, this is a very bad idea as those systems that could not handle it would freeze the whole computer and cause major frustration. Instead the better option is to give the host operating system full CPU priority, then give the extras to the guest system.

If say, the processor has multiple cores, then Virtualbox could simply appropriate one of the cores for itself and use that. This is *probably* why Virtualbox wants users to have a 64bit system.

Guesswork aside, I hope this gives some insight into how it all works.

---

### Post by ixtok on 2012-09-30
I have a HPmini110 with similar specs to your netbook. It runs  ubuntu and has windows xp in virtual box. It runs xp fine but is slow with Windows 7. You might try to tweak the memory allocated to virtual box to improve the performance. You might also try a different version such as lubuntu to run in the virtual box.

---

### Post by DaGeek247 on 2012-10-07
also, dont forget to mark your threads as "solved" when they have been solved.

---

