---
title: "Somehow I keep messing up my installation"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by brockolicosmique on 2013-02-05
Hello everyone, this is my 1st post.

I decided to use Ubuntu last week and got it installed on my Dell XPS 17 L702x. I have installed 12.10 but I'm unsure if maybe I should downgrade to 12.04 instead. I'm all new to Linux and don't really have a clue as to what I'm doing, previously I was using Macs.

After installing 12.10, my Broadcom 4322 is recognized, but after the automatic update it stops being recognized. I have found a workaround for it and it works again after that. I have also installed Bumblebee for my Optimus setup and got it to work.

The next step I want to achieve is to get Ardour to work with my Rocksmith USB guitar cable, but I can't get it to work with it. QjackCtl will not list it, but when going in the sound settings it is showing up, and the meter will even display my instrument being plugged in. Then after opening and closing Ardour/QjackCtl a few times, I lose all audio, and after a reboot I am greeted by a grey menu that says none of my hardware is detected. Another reboot and then it works fine.

Should a first time user stick with 12.04 or can I use 12.10 safely? Anyway, I think I'll get the install disk in again for the 6th time...

Thanks!

JF

---

### Post by collisionystm on 2013-02-05
Okay so as far as your broadcom card and the updates....

Broadcom and linux sucks. When your system updates, its grabbing the latest kernel available to it. In the kernel are the device drivers. Essentially the kernel that comes packaged off the cd is compatible but the updated one is not. Its a strange world, I know. 
You can try 12.04. You shouldnt really have this problem as long as the card works when you boot the live cd. 12.04 is an LTS and they keep very minor kernel revisions so that is maintains the stability.

As for your guitar...no idea.

---

### Post by Petro Dawg on 2013-02-05
Stick with Long Term Support (LTS) versions unless you like working extra to get everything running correctly.  I would suggest using 12.04 (especially if you are new to Ubuntu).

---

### Post by elgordodude on 2013-02-05
Welcome to the forums, 12.04 is the long term support edition, in theory it's a little more stable than 12.10. but really it doesn't make much of a difference. The good news, is that it sounds like your installation went just fine, absent a compelling reason (someone says their guitar works fine with 12.04) I wouldn't reinstall. The bad news is I'm not a musician and don't know how to sort the guitar, hopefully you get lucky and a musician comes through here, but that looks like a question for the manufacturer's forum. You're probably more likely to find a guitar owner with linux, than a linux user with the guitar...

---

### Post by brockolicosmique on 2013-02-05
> **collisionystm said:**
> Okay so as far as your broadcom card and the updates....

Broadcom and linux sucks. When your system updates, its grabbing the latest kernel available to it. In the kernel are the device drivers. Essentially the kernel that comes packaged off the cd is compatible but the updated one is not. Its a strange world, I know. 
You can try 12.04. You shouldnt really have this problem as long as the card works when you boot the live cd. 12.04 is an LTS and they keep very minor kernel revisions so that is maintains the stability.

As for your guitar...no idea.

I have a spare Intel Centrino Wireless-N 1000 wifi card I could use instead, but after searching on Google a bit, people seem to be having issues with that one too... I'm unsure if I should open up my laptop for it.

---

### Post by collisionystm on 2013-02-06
I believe the only issue with the Wireless-N series cards was power related but that should have been patched in the later kernel that 12.04/12.10 brings. Swapping out the wireless is easy as long as it is accessible through a panel on the bottom of the laptop. The black and white wires just pull off and clip back on the new card.

---

### Post by brockolicosmique on 2013-02-08
Whew, I've learned quite a bit about Linux in the last few days. I've reinstalled multiple times, tried Mint for a few hours for the heck of it, and came back on Ubuntu 12.10.

I would say all of my issues are fixed: 

The message I got on boot about no hardware detected (Low Graphics Mode) was fixed with this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1070150)

My problems with Ardour have been fixed with this: [http://ubuntuforums.org/showthread.php?t=1902027](http://ubuntuforums.org/showthread.php?t=1902027).

Now that everything is running smoothly, I'll stay on 12.10 for a while, see what else I can do.

JF

-edit: oh and I swapped the wifi card and everything was so much easier during reinstalls and all, no more messing around...

---

### Post by landersohn on 2013-02-08
+1 to "broadcom and linux sucks".
I ended up using a USB wireless dongle, tried for days to get my BCM4313 to work properly.

Having said that, does anybody have a recommendation for a wireless card I should get instead?

---

### Post by brockolicosmique on 2013-02-10
> **landersohn said:**
> +1 to "broadcom and linux sucks".
I ended up using a USB wireless dongle, tried for days to get my BCM4313 to work properly.

Having said that, does anybody have a recommendation for a wireless card I should get instead?

My Dell Mini Wireless N 1000 works great!

JF

-Edit: Sorry I meant my Intel Centrino Wireless-N 1000... I got mistaken with the Broadcom one I had in before.

---

### Post by sandyd on 2013-02-10
> **landersohn said:**
> +1 to "broadcom and linux sucks".
I ended up using a USB wireless dongle, tried for days to get my BCM4313 to work properly.

Having said that, does anybody have a recommendation for a wireless card I should get instead?

Intel Centrino Advanced* series. Most of them work out of the box

---

### Post by landersohn on 2013-02-10
Thanks all for your for the help. I will report what I'll be trying and end up using.

---

### Post by Bucky Ball on 2013-02-10
> **petro dawg said:**
> stick with long term support (lts) versions unless you like working extra to get everything running correctly.  I would suggest using 12.04 (especially if you are new to ubuntu).

+1.

You are asking about more than one issue here which makes things confusing. For the wirless issue you should post in ***Networking & Wireless*** and for the guitar issue possibly ***Multimedia & Video*** or ***General Help***.

Use descriptive thread titles which give some information about your problem (the current one gives none about either issue) and include where you are at, what you've done to get there and as much relevant information as you can muster. Good luck.

---

### Post by landersohn on 2013-02-12
Bucky Balls comment notwithstanding, just wanted to close out the wireless issue:
Intel Advanced N-6235 works peachy.
I had to enable it with rfkill unblock all since on my laptop the Fn-F12 wireless key does not work

---

### Post by Bucky Ball on 2013-02-13
Thanks for sharing the fix and well done. You should probably mark this thread as solved and move on to the guitar issue. How's it going? Post a thread about that and a link back here if you like.

***Multimedia & Video*** might be a good section for it. My previous advice still stands; your thread title really doesn't have anything to do with the guitar issue if that is what you have left. ;)

PS: Have you tried Ubuntu Studio and jackaudio? Might help. You can install the Studio audio with ubuntustudio-audio.

Good luck.

---

