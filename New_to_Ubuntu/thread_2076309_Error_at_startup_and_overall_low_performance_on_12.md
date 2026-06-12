---
title: "Error at startup and overall low performance on 12.04"
date: 2012-10-25
forum: New to Ubuntu
---

### Post by hansnn on 2012-10-25
When i am booting ubuntu it appears an error message for a couple of seconds.
Something like "disk not ready yet or not available".

I have searched the web for answers, but my problem seems to differ from everyone else as the error message disappears in a couple of seconds and Ubuntu boots just fine.

I am curious as to what this could be and how i can manually check for system errors or something like that.


Also, the startup is much slower then my windows startup (dualboot), and generally Ubuntu seems to be working kind of slowly when I'm opening folders and such. Compared to windows, that is. Which is not what my reading on Linux has taught me it should be.

Some applications also crash from time to time, like the software center.
I also got an internal ValueError the first time i booted Ubuntu.


The system is working "just fine", but as you might understand i want it running all clean and smooth before i really get into it. 


Computer specs:

CPU: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz

GPU: Nvidia Geforce GFX 580

RAM: 8gb

MOTHERBOARD: How do you check this (and other system specs) in Ubuntu?

I have a SSD drive which Ubuntu don't seem to recognize. But judging the speed difference from windows to Ubuntu, i do not think that's the reason for it to be so slow. Not that i would know :)

---

### Post by hansnn on 2012-10-27
Also noticed a playmouth error at startup.

Can i troubleshoot the boot or something?

---

### Post by krustenBrot on 2012-10-27
> **hansnn said:**
> When i am booting ubuntu it appears an error message for a couple of seconds.
Something like "disk not ready yet or not available".


This may refers to your boot table - given that your 1st boot device is set to usb or disk - it checks them, sees that there is nothing to boot from and then jumps to booting from HDD.
> 
I have searched the web for answers, but my problem seems to differ from everyone else as the error message disappears in a couple of seconds and Ubuntu boots just fine.

I am curious as to what this could be and how i can manually check for system errors or something like that.


Also, the startup is much slower then my windows startup (dualboot), and generally Ubuntu seems to be working kind of slowly when I'm opening folders and such. Compared to windows, that is. Which is not what my reading on Linux has taught me it should be.

At my system it is a couple of seconds faster then booting a clean Windows 7 system. 
Please try to post a few more informations. How did you install it? Are all Drivers isntalled correctly - especially graphic drivers can be crucial when it comes to Unitys performance.

> 
Some applications also crash from time to time, like the software center.
I also got an internal ValueError the first time i booted Ubuntu.


The system is working "just fine", but as you might understand i want it running all clean and smooth before i really get into it. 


I had those problems too, especially with randomly popping up crash messages - but since i installed it again - it works just fine. So if everything else fails - check the installation medium again ( MD5 sum!) and isntall it again it may help a lot.

> Computer specs:

CPU: Intel(R) Core(TM) i7-3770 CPU @ 3.40GHz

GPU: Nvidia Geforce GFX 580

RAM: 8gb

MOTHERBOARD: How do you check this (and other system specs) in Ubuntu?

I have a SSD drive which Ubuntu don't seem to recognize. But judging the speed difference from windows to Ubuntu, i do not think that's the reason for it to be so slow. Not that i would know

For displaying Hardware specs there are several tools - I am just posting a link here which explains it pretty nice: [How to get Hardware Information]("http://www.webupd8.org/2011/07/how-to-get-hardware-information-in.html")

Your SSD should be recognized just fine. + it is using a new kernel there are no necessary tweaks it just "runs" out of the box and doesn't need any 3rd party software like Samsung SSD Magacian

---

### Post by hansnn on 2012-10-27
Thank you for answering!
I was afraid i was asking too dumb a question to get a response.


I installed it with a live CD with an ISO downloaded from ubuntu.com
I used a CD, not a DVD, with 700MB space, compared to the around 680MB ISO file.
When i was dealing with the disks during the install, splitting my main disk to the two OS' , i could not find my SSD. Nor could i install Ubuntu on it. I haven't really looked around for my SSD so maybe it's there and nothing is wrong.

I had to set nomodeset to make the boot work without crashing.

What is md5 sum?
How can i check my installation medium? :) I assume you mean the CD
You think i should re-install Ubuntu?


Thanks.

---

### Post by sffvba[e0rt on 2012-10-27
You need to install the correct drivers for your graphics card (to stop having to use nomodeset) at boot time.  This should also help make the whole system more responsive.

In dash search for "additional drivers" and run it, choose the proprietary nvidia drivers and you should be good to go (unless you have some issues with using proprietary drivers).


404

---

### Post by krustenBrot on 2012-10-27
> **hansnn said:**
> Thank you for answering!
I was afraid i was asking too dumb a question to get a response.


There are no dumb questions, just dumb answers. ;)
> 
I installed it with a live CD with an ISO downloaded from ubuntu.com
I used a CD, not a DVD, with 700MB space, compared to the around 680MB ISO file.
When i was dealing with the disks during the install, splitting my main disk to the two OS' , i could not find my SSD. Nor could i install Ubuntu on it. I haven't really looked around for my SSD so maybe it's there and nothing is wrong.

I had to set nomodeset to make the boot work without crashing.

Alright I have to admit I am hoping someone else is taking a look at this thread because i cant help you with this. But it is always a good idea to post the specs of your SSD. Especially which model, there may have been issues with this particular one before.
> 
What is md5 sum?
How can i check my installation medium? :) I assume you mean the CD
You think i should re-install Ubuntu?
You can use the md5 sum to verify your downloaded file isn't corrupted. This can be useful to exclude the installation medium from the source of errors and especially when it comes to OS Images it is very important to make sure everything is alright.
Take a look at the Ubuntu Wiki for further details on [How to md5sum]("https://help.ubuntu.com/community/HowToMD5SUM"). 

Dont reinstall it right away - let us sort out the SSD issues first. :)

---

### Post by hansnn on 2012-10-27
> **not found said:**
> You need to install the correct drivers for your graphics card (to stop having to use nomodeset) at boot time.  This should also help make the whole system more responsive.

In dash search for "additional drivers" and run it, choose the proprietary nvidia drivers and you should be good to go (unless you have some issues with using proprietary drivers).


404

I forgot to mention this in my last post. I have installed the latest drivers.
I did some commands in the terminal which i found online to install drivers, and i allready have the proprietary drivers chosen. I.E the version current, recommended ones.

So i don't think that's the problem.

Please excuse my late responses today.

EDIT: Also, in the bios my 1st boot device is my main hard drive (like it should be).
On a second note, on my pc, before i enter the actual bios, i get a list of boot devices. I don't know if they really mean anything, but the top one is "UEFI, Built in shell"

---

### Post by hansnn on 2012-10-27
There are several error messages appearing during boot. (3-5)
It's hard to catch them all as they only appear for a couple of seconds.
At least one of them is: 
*Starting crash report submission daemon

This could be the reason for the slow boot

---

### Post by hansnn on 2012-10-27
I am simply going for a re-install :) Thanks for all the help!

I will be back :)


EDIT: I have now reinstalled ubuntu and there are no error messages.

---

### Post by krustenBrot on 2012-10-28
Did it work out for your SSD? I hardly recommend installing i on the SSD. :)

---

### Post by Wim Sturkenboom on 2012-10-28
You can not compare the bootup time of Windows on SSD versus Ubuntu on normal HD, if that is what you are doing.

> 
I was afraid i was asking too dumb a question to get a response.

Or a far too difficult question that nobody here knows the answer to ;) Oh ja, and dumb questions don't exist.

---

### Post by hansnn on 2012-11-08
> **krustenBrot said:**
> Did it work out for your SSD? I hardly recommend installing i on the SSD. :)

Why don't you recommend installing on SSD?

I just re installed my 3rd time today, cause of a partitioning problem. I installed it on my SSD and made my 1TB disk /home.

It is all working smoothly now and the computer restarts in about 24 seconds.

---

