---
title: "xubuntu vs ubuntu and wine"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by monkey10120 on 2013-03-05
So I am very new to ubuntu but I am getting used to it.  I have ubuntu at work and xubuntu at home on an ancient pc so I can mess with the os and ubuntu's ui does not display correctly on that pc. 

But I am mainly asking about wine.  I installed it on both and tested small programs like minecraft to make sure I could get wine to work. On ubuntu I installed java (windows) with wine and ran mc and it ran just fine. 
Then I went home on xubuntu and did the exact same steps and I get a java error- java virtual machine could not start. 
Is there any differences between the 2 distributions that can cause this error? Btw they are up to date and running 12.04

---

### Post by cthugha on 2013-03-05
You shouldn't need wine to run minecraft on Ubuntu, java runs natively in Linux.

Download the .jar file from minecraft.net instead of the .exe

---

### Post by papibe on 2013-03-05
Hi monkey10120. Welcome to the forums ):P

If your main concern is running Minecraft, I wouldn't worry about wine. MC runs directly under Java.

Install Java from the software Center, and run MC natively on (X)Ubuntu.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by monkey10120 on 2013-03-05
Oh sorry i think that I got the wrong pioint off. im not going to run minecraft I was just testing to see if I could get a windows program up and running. I was just mainly wondering if there are differences between the os that gives me the java error. We have a few java programs at work and it qould be nice to know of a fix ahead of time if I run into it.

Also I am liking ubuntu a lot after using for a few days. I might actually make a permanent switch:p

---

### Post by papibe on 2013-03-05
Are both your work and personal machines running the same bit version (32b or 64b)?

I don't have access to my Xubuntu machine right now, but you can check if you are using the same wine version by running:
```
apt-cache policy wine
```
Let us know how it goes.
Regards.

---

### Post by monkey10120 on 2013-03-05
Yeah they are both running 32bit and wine 1.4.1. I also tried 1.5.25 and still no luck

---

