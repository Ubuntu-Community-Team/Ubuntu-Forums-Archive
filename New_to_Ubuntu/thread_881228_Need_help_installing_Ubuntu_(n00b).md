---
title: "Need help installing Ubuntu (n00b)"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Labombadog on 2008-08-05
Hi! Let me introduce myself. My name is Jay, and I am a windows user that is very interested into getting into Linux. I am specifically a heavy gamer, but I want to use Windows for gaming. Welcome to give me any PM to talk about gaming!

**Into business.**
Yesterday, I tried to install Ubuntu yesterday on my IDE 80GB HDD (I have Vista on my Raid 0 320GB x 2). So, when it finished installing it restarted, and then it said 'insert boot cd and press any button'. Linux never installed correctly and it kind of messed up my Windows OS, but thats ok since I repaired it. But what do I have to do in order to have two OS (Vista, Linux) on my two different HDD's?

Thanks alot and please be nice! ;-)

---

### Post by tuxxy on 2008-08-05
Youd should be able to select whihc one at bootup you would like to use, if there both connected that is.

---

### Post by ByteJuggler on 2008-08-05
Welcome Jay, hopefully we'll be able to help.  Can you be a bit more specific with regards to exactly how your hard drives are connected?  Is the RAID array in effect the primary boot drive and the 80GB secondary?  Did you change your hard drive config before or after installing Ubuntu?  When you say the Ubuntu install "messed up" your Windows what do you mean?  Just that the boot sequence didn't work anymore?

Suffice it to say what you want is very possible, I run a very similar setup on my main desktop, Dual boot Windows Vista with 3-way Raptor RAID0 and another disk with Ubuntu etc.  Even so, the RAID array complicates matters slightly wrt to installing and booting, so be patient while we try to understand what went wrong in your case and how to fix it.  What motherboard (make/model) do you by the way?

---

### Post by Labombadog on 2008-08-05
> **ByteJuggler said:**
>   Is the RAID array in effect the primary boot drive and the 80GB secondary?

 I am not sure. How can you find this out? 
> **byteJuggler said:**
> Did you change your hard drive config before or after installing Ubuntu? No
 > **byteJuggler said:**
> When you say the Ubuntu install "messed up" your Windows what do you mean?  Just that the boot sequence didn't work anymore? Yes, my boot did not work.

 > **byteJuggler said:**
> What motherboard (make/model) do you by the way?
I have an Asus P5n32 E sli Plus, E6600 2.4 (3.2ghz OC'ed), G.Skill 2 x 1GB DDR2 800 RAM, and a 8800GTS 320mb graphic card. Probably more than you wanted, but I am just making sure. Thanks for your help so far! :) :guitar:

---

### Post by Labombadog on 2008-08-05
bump

---

### Post by ByteJuggler on 2008-08-06
> **Labombadog said:**
> I am not sure. How can you find this out?


OK, boot with the Ubuntu CD, then when you're at the desktop, press alt-f2, and paste the following command line in there and press enter:

```
sudo fdisk -lu >~/fdisk.txt; gedit ~/fdisk.txt
```

A text editor with information should pop up.  Please post that back here. (I'm assuming your networking is starting up correctly so you can do that directly from the liveCD.)

> **Labombadog said:**
>  
I have an Asus P5n32 E sli Plus, E6600 2.4 (3.2ghz OC'ed), G.Skill 2 x 1GB DDR2 800 RAM, and a 8800GTS 320mb graphic card. Probably more than you wanted, but I am just making sure. Thanks for your help so far! :) :guitar:

OK, just to be clear, are you 100% sure your overclock is stable?  That is, did you stress test it properly with e.g. Orthos/Prime etc. and did all the tests pass for an extended period (8h+) with no failures?  Note: There is also a "memory test" option on the Ubuntu LiveCD.  You might want to run that for a bit just to make sure your machine is stable. (I'm just being careful here -- you'd be surprised at the number of problems you see on here where dodgy hardware or some sort of instability is the problem.)

Re your goal of a dual-boot setup: Broadly speaking what I'd suggest we aim for is we swap your boot priority around (if needed) so your single disk becomes the initial boot disk with the GRUB boot loader and have that then chainboot onto Vista (if booting Vista) etc.

Furthermore, what I'll suggest is that you intially (if possible) event disconnect your RAID array disks so that you can perform a clean install without the complications of the RAID array's presence, onto your 80GB disk, then check that works, then reconnect your RAID array to get the boot loaders set up.

But, before we try any of that: **Make a backup of everything that you can't afford to lose/reinstall.**  It makes sense before starting with messing about with disks and partitions and stuff.  Also post back with the above info and then I'll try to post some slightly more detailed steps to accomplish the above.

Also, be patient.  We're not here 24h a day, so this process is likely to take several days to work through.

---

### Post by Dedoimedo on 2008-08-06
Hello,

I've written a thorough tutorial, explaining how to get things done in detail. I've written for Kubuntu some time ago, but it applies well for current situations / distros.

If you're interested:

[http://www.dedoimedo.com/computers/install_kubuntu.html](http://www.dedoimedo.com/computers/install_kubuntu.html)

And other Linux related stuff...

Cheers,
Dedoimedo

---

