---
title: "very slow boot"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by franco81 on 2008-10-14
I've been using Ubuntu for about a year, overall really happy with it. But lately I am having some problems:

really slow boot - this has been going on for a while. I have tried apt-get update and repairing broken packages etc. but hasn't resolved this problem for me so far. 

would like to know some general procedures, if there are any, to try and tackle this problem. or where I should look to get more information about the booting process.

it may be related to an error that pops up after shutting down ocassionally, I don't have the specifics but a fatal error in red I think to do with hlib?

ubuntu 8.04
toshiba satellite p200-1ee
dual boot with vista

Thanks for any feedback.

---

### Post by jemate18 on 2008-10-14
> **franco81 said:**
> I've been using Ubuntu for about a year, overall really happy with it. But lately I am having some problems:

really slow boot - this has been going on for a while. I have tried apt-get update and repairing broken packages etc. but hasn't resolved this problem for me so far. 

would like to know some general procedures, if there are any, to try and tackle this problem. or where I should look to get more information about the booting process.

it may be related to an error that pops up after shutting down ocassionally, I don't have the specifics but a fatal error in red I think to do with hlib?

ubuntu 8.04
toshiba satellite p200-1ee
dual boot with vista

Thanks for any feedback.

please post the message of

```
dmesg
```


The output are the contents or messages during bootstrap or simply boot

---

### Post by franco81 on 2008-10-14
Thanks, here are my bootup messages [attached]

---

### Post by jemate18 on 2008-10-14
I have checked your file and I found no error related to slow boot up...

So does the slow boot up take the time(slow) in the splash? the one with the black screen and ubuntu orange line loading? HOw many minutes?

---

### Post by jemate18 on 2008-10-14
can you give the exact error in that red thing hlib ?

---

### Post by franco81 on 2008-10-14
Its slow before the splash screen, just a blank (black) screen. A couple of minutes at least. 

One problem that came up recently was when I installed postfix and sendmail. But uninstalled those, and problem continued before and after this event. Also, I am changing location of the laptop between home and work, so I have to change network manually for each location if that has any effect?

Thanks for having a look through for me, much appreciated. I will try to get the error message thats triggered on shut down up on this thread soon.

cheers

---

### Post by franco81 on 2008-10-14
Okay, there was no error on shutdown that time. 

When I rebooted, without any input (keypresses, mouseclicks) from me it took just on 3 minutes for the login splash screen to appear.

Is this usual - should I expect that sort of booting time? in the early days it booted up right away. I have a few more programs installed now, like clamav, eclipse, amarok etc. but still not that many, and nothing unusual.

Attached is my latest dmesg output. 

Thanks!

---

### Post by jemate18 on 2008-10-14
> **franco81 said:**
> Its slow before the splash screen, just a blank (black) screen. A couple of minutes at least. 

One problem that came up recently was when I installed postfix and sendmail. But uninstalled those, and problem continued before and after this event. Also, I am changing location of the laptop between home and work, so I have to change network manually for each location if that has any effect?

Thanks for having a look through for me, much appreciated. I will try to get the error message thats triggered on shut down up on this thread soon.

cheers

did you try 
sudo dpkg --configure -a



or 

sudo apt-get check

and

sudo apt-get autoremove

?

Just to make sure you dont have broken packages or something that was left by your uninstalltion of postfix and sendmail..

---

### Post by philinux on 2008-10-14
Looks like a long wait here.
```
[   47.334781] lo: Disabled Privacy Extensions
[   47.335233] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  ** 47.335737**] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  **148.595362**] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  148.650698] r8169: eth0: link down
[  148.652993] ADDRCONF(NETDEV_UP): eth0: link is not ready
```

How is you net connected?

---

### Post by franco81 on 2008-10-14
Thanks, I did the auto remove and other apt-get/dpkg commands, but there didn't seem like much needed to be done.

The internet is wireless both at work and at home and I have a couple of network locations set up that I change between. 

But, before upgrading to 8.04 I implemented a hack for ensuring the system remembered my  network password, and actually I think this might be still there and causing issues as I always need to re-enter my password at home.

I'll try and find that and remove it I guess...

cheers

---

### Post by hyper_ch on 2008-10-14
install teh bootchart package. It will then put a .png file in /var/log/bootchart I think where you have a graphical overview when what process is being started and how long it takes to complete.

---

### Post by gnudriver on 2008-12-23
I recently loaded ubuntu onto a 3 year old toshiba satelite laptop. I chose to overwrite the old xp os. It works pretty well, wireless graphics etc, but it boots super slowly unless I hit the enter key several times. Any Suggestions?  Also How can I force the boot sequence to show in text instead of the update bar graphic?

---

