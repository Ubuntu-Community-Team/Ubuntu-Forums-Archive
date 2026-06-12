---
title: "Installation problem"
date: 2012-04-15
forum: New to Ubuntu
---

### Post by shad686 on 2012-04-15
I created an Ubuntu iso cd to install on my extra hdd. I've tried installing a few times, and can't seem to get it working on its own. It works fine if I run it from the cd, but when I install, and restart all I get is a purple flashing screen. Could someone please help? I'm new to linux, and have no idea what i'm doing wrong.

---

### Post by 23dornot23d on 2012-04-15
Probably nothing you are doing wrong - but it may be having problems with your
graphics card or something similar

What graphics card is it .... and can you get in using the second menu option .... 
usually a safe-mode .....

also pressing

Ctrl + Alt + f2 together - when you see the flashing screen .... does it let you get to a console screen ?

---

### Post by shad686 on 2012-04-15
> **23dornot23d said:**
> Probably nothing you are doing wrong - but it may be having problems with your
graphics card or something similar
 
What graphics card is it .... and can you get in using the second menu option .... 
usually a safe-mode .....
 
also pressing
 
Ctrl + Alt + f2 together - when you see the flashing screen .... does it let you get to a console screen ?
 
 
My graphics card is an asus hd 6670. When i was searching threw the hardware it said gpu unknown, or something like that. Havent tried ctrl/alt/f2. I'll give it a go, and see what happens

---

### Post by 23dornot23d on 2012-04-15
Check some of the solved links .... for that Graphics card ....

[https://www.google.com/search?client=ubuntu&channel=fs&q=asus+hd+6670+ubuntu+solved&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=asus+hd+6670+ubuntu+solved&ie=utf-8&oe=utf-8)

Someone else may pick up on this but .... that graphics card is not one
that I know much about .... but by how you describe the start up
it sounds like that will be the reason why ....

[]("http://www.zoringroup.com/forum/viewtopic.php?f=4&t=1011")

---

### Post by shad686 on 2012-04-15
> **23dornot23d said:**
> Check some of the solved links .... for that Graphics card ....
 
[https://www.google.com/search?client=ubuntu&channel=fs&q=asus+hd+6670+ubuntu+solved&ie=utf-8&oe=utf-8](https://www.google.com/search?client=ubuntu&channel=fs&q=asus+hd+6670+ubuntu+solved&ie=utf-8&oe=utf-8)
 
Someone else may pick up on this but .... that graphics card is not one
that I know much about .... but by how you describe the start up
it sounds like that will be the reason why ....
 

 Thanks for the help. ctrl/alt/f2 just truns the screen from purple to black. seems like it is just a graphics issue Hopefully I'll be able to find some info on it.

---

### Post by QIII on 2012-04-15
Does you motherboard also have an integrated graphics chipset?
 
 If so, is it also an ATI product (if you know)?
 
 Is your BIOS set to use PCI-E graphics or integrated?

---

### Post by shad686 on 2012-04-15
> **QIII said:**
> Does you motherboard also have an integrated graphics chipset?
 
If so, is it also an ATI product (if you know)?
 
Is your BIOS set to use PCI-E graphics or integrated?
 
No intergrated graphics on the mobo. Kinda wish there was now. Bios is set to use the pcie.
 
I believe I found a driver for it in one of the links 23dornot23d suggested. Question now is how to install it when I can't see what i'm doing? 
 
I'm runnin win7 on one hd, and installed the ubuntu 11.1 to my seccond hd. Would it be possible to install the driver from win7 to the other hd?

---

### Post by QIII on 2012-04-15
No, you can't install the driver that way.

<snip>  I see the version now.  I'm surprised you are having a problem with this, but things happen.  Generally when things run in a live session, they run on boot with the default open source driver.

I'm going to try to recreate the issue on another machine, so that may take a bit.  And it's also midnight ...

There are a couple of things we can do here, but rather than firing off a series of "Try this and try that" posts, let me check a couple of things out.

---

### Post by shad686 on 2012-04-15
> **QIII said:**
> No, you can't install the driver that way.
 
<snip> I see the version now.
 Is there a nother version that would work better?
Or would flashing the driver update into the set up work?

---

### Post by QIII on 2012-04-15
The default, open source driver (which is used before you install the proprietary ATI driver) is not "flashed", but updated.  What is a bit unusual here is that the open source driver should generally work for your card at this point without harsh words and a riding crop.  Which means it may be something other than the driver, but we're going to go with that right now as a step in troubleshooting.

Instead of reinstalling (which I call the "Nuke 'em from orbit" approach), let's try to fix what you have.  You're going to have to get cozy with the command line for just a bit.  No need for fear.

When you boot, you probably don't see the GRUB screen because you haven't updated GRUB.  So, just as your BIOS is finishing up, hold the space bar down to get the GRUB menu to display.

Choose "Recovery" and then "Root with networking" (or, if 11.10 doesn't have that option, choose "enable networking" first and then choose "Root")

Issue the following commands in order  (I don't think you should have to, but if you get some complaints you may have to preface each of these commands with the word sudo):

```
apt-get update
```  ```
apt-get dist-upgrade
```(If you are asked "yes or no", answer yes.  If you are asked for your password, type the password you set up when you installed.)



That will catch all the updates between October and now.  There will be a lot, a lot of text will scroll by quickly and that will all be unintelligible to you.  And it will take a while.  Grab the beverage of your choice and relax.


Try to reboot and see if that helps.  There may have been a bug that was corrected along the way.



If that doesn't work, get back to root with networking and do:



```
apt-get install fglrx && apt-get install amdcccle
```  ```
aticonfig --initial
```  ```
reboot
```If that still does not solve the problem, I have a couple of other things to try.

---

### Post by shad686 on 2012-04-15
> **QIII said:**
> The default, open source driver (which is used before you install the proprietary ATI driver) is not "flashed", but updated. What is a bit unusual here is that the open source driver should work. Which means it may be something other than the driver, but we're going to go with that right now as a step in troubleshooting.
 
Instead of reinstalling (which I call the "Nuke 'em from orbit" approach), let's try to fix what you have. You're going to have to get cozy with the command line for just a bit. No need for fear.
 
When you boot, you probably don't see the GRUB screen because you haven't updated GRUB. So, just as your BIOS is finishing up, hold the space bar down to get the GRUB menu to display.
 
Choose "Recovery" and then "Root with networking" (or, if 11.10 doesn't have that option, choose "enable networking" first and then choose "Root")
 
Issue the following commands in order (I don't think you should have to, but if you get some complaints you may have to preface each of these commands with the word sudo):
 
```
apt-get update
``` ```
apt-get dist-upgrade
```(If you are asked "yes or no", answer yes. If you are asked for your password, type the password you set up when you installed.)
 
 
 
That will catch all the updates between October and now. There will be a lot, a lot of text will scroll by quickly and that will all be unintelligible to you. And it will take a while. Grab the beverage of your choice and relax.
 
 
Try to reboot and see if that helps. There may have been a bug that was corrected along the way.
 
 
 
If that doesn't work, get back to root with networking and do:
 
 
 
```
apt-get install fglrx && apt-get install amdcccle
``` ```
aticonfig --initial
``` ```
reboot
```If that still does not solve the problem, I have a couple of other things to try.
 Thanks. I'll try it out first thing in the morning. Its late here I'm getting tired now. 
 
Thanks again. Will keep posted if it works or not.

---

### Post by shad686 on 2012-04-15
Couldn't get those codes to work. Found one that did in another section of the forums. Seems to be running well now. Thanks for the info though.

---

