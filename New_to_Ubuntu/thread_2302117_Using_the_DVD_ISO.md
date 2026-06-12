---
title: "Using the DVD ISO"
date: 2015-11-07
forum: New to Ubuntu
---

### Post by rdb3 on 2015-11-07
Hi guys,  nubie here.  I installed Ubuntu on computer 1 via creating DVD with ISO.

I want to install Ubuntu on computer 2 now.  Can I use that same DVD from above to do it?

As always, thanks in advance.

---

### Post by sammiev on 2015-11-07
You can use that DVD to install ubuntu on as many computers as you wish.

---

### Post by Bashing-om on 2015-11-07
rdb3; Hello;

If computer 2 is same architecture (64 bit ) and same platform (AMD/Intel) -
Then, most assuredly !

[INDENT][INDENT]install away 
[/INDENT][/INDENT]

---

### Post by rdb3 on 2015-11-07
Thank you..... will give it a try!!

---

### Post by Sweet_Baby_Jamie on 2015-11-08
Let us know how you did!  My computer is 32-bit and my parents' is 64-bit.  While a 32-bit OS works on a 64-bit machine, it doesn't make use of all that 64-bit power.  So I needed a separate DVD for my parents' computer.

---

### Post by rdb3 on 2015-11-09
I have 3 computers.  They are all 32-bit.  Computer 1 was installed with a DVD.
Computer 2 was installed with a USB flash drive.
Computer 3 is giving me a problem.  I tried to install it with the DVD from computer 1.  When I get to the install options, it tells me that Vista exists on that computer.  
But it does not give me the option to install side-by-side with the Vista partition.  It will only allow me to erase everything and install Ubuntu.  I'm not sure what to do now because 
I need both operating systems on that pc.

Also, earlier I tried to boot pc 3  from the flash drive used in pc 2, but I can't get the boot order to recognize the flash drive as first on that old Dell.  That's where I'm at with
the third install now.

---

### Post by Bashing-om on 2015-11-09
rdb3rdb3l Well ..

I hazard to guess;
Machines 1 & 2 are bios based
Machine 3 is UEFI ?
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

UEFI makes us
[INDENT][INDENT][INDENT]jump through some hoops
[/INDENT][/INDENT][/INDENT]

---

### Post by sudodus on 2015-11-09
There might be several reasons why your third computer is stubborn. But with our help I think you will make it run with Ubuntu or an Ubuntu family operating system.

0. Bashing-om's guess.

and my guess

1. Have you booted into Vista and reduced the size of the Vista partition? After doing that you should reboot into Vista to let it repair the file system. Do not create any file system in Vista.

2. After that you can boot from the Ubuntu DVD or USB drive and

- either let the installer create a root partition and a swap partition automatically,
- or start gparted and do it manually, and start the installer after that, select Something else at the partitioning window and use the partitions created with gparted.

-o-

Please specify your third computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

It will help us help you.

---

### Post by grahammechanical on 2015-11-09
> But it does not give me the option to install side-by-side with the  Vista partition.  It will only allow me to erase everything and install  Ubuntu.

While we are guessing, can I have a go? It is the 4 primary partition limit. Machines with a BIOS boot system will only allow us to create 4 primary partitions on the hard disk. If the manufacturer has installed Windows and used up the 4 primary partition allocation then the Ubuntu installer has no choice but to offer only the Erase disk and install Ubuntu option.

If this is the true situation then we need to delete one of the existing partitions and use the freed up 1 primary partition allocation to create a special primary partition called an Extended partition. Then we can tell the Ubuntu installer to install Ubuntu into the Extended partition and it will create 2 Logical partitions. One for Ubuntu and one for swap.

Or the installer will notice that there are only 3 primary partitions and that there is unallocated space and offer to Install Alongside. And it will create the Extended partiition with 2 Logical partitions inside.

We can have any number of logical partitions inside an Extended partition. And in this way we get around the 4 primary partition limit that effects Windows users as well as Linux users.

Regards.

---

### Post by mastablasta on 2015-11-10
> **sudodus said:**
> 

Please specify your third computer



and post a screen shot from Vista disk manager, so we can see how you have partitions arranged on the hard disk. The install options you are getting are there:
- if 4 primary partitions are already occupied (you should be able to change one to secondary then).
- if empty space is between partitions (we can guide you with manual install)


make sure you do backups before any partition work as that can always go wrong. well chances are small that it does but when it does you may lose everything on disk. easiest way is to image the disk (RedoBackup, Clonezilla...) before messing around with it.

---

### Post by rdb3 on 2015-11-10
I re-sized the Vista partition and that bad boy is now installing nicely alongside Vista.  Thank you.

BTW, the pc is an older Dell Inspiron  531 desktop with 2 GB ram.

I'll wrap things up on here later after the install finishes.

Many thanks!!

---

### Post by rdb3 on 2015-11-12
I'm back.  I only get short windows of time to work on this pc as it is used for school work (in Vista) until I can stabilize Ubuntu.  

So after I installed a few days ago (via DVD), there were problems... certain functions would freeze the system with a pretty pattern on the screen and, I would have to 
power down and power back up the pc.

I then decided to boot via USB drive and got that resolved.  I used the Universal USB Installer to install Ubuntu 15.10 on the stick.
After installing 15.10, it is good, but not without some issues...

The Dash - if I click on it, all kinds of flashing takes place.  I have been able to recover from it to the
 desktop so far.

Settings Shut Down - if I click on Shut Down, the Restart and Shutdown buttons and the entire image they are contained within are in various color patterns.  I can also recover from it though.

Hibernation - just noticed that when I walk away from the pc and return a short while later and click on the mouse to wake it up.... it doesn't wake up.  That makes me have to power pc down and then back up.

Firefox and other functions are working fine.

From Settings > Details
Ubuntu 15.10
mem 2 GB
Processor AMD Sempron
Graphics Gallium Q4 on NV4C
32-bit
Disk 77.5 GB

The software is up to date.  It is a Bios machine.

---

### Post by sudodus on 2015-11-12
I think you have problems between the graphics driver and the graphics chip/card.

I browsed the internet with the search string ***NV4C*** and found some links, that can be interesting for you.

Maybe you can find a proprietary driver, that works better than Gallium.

---

### Post by rdb3 on 2015-11-12
Thanks sudodus.  I will give it a go.  When installing a driver, does it matter if the pc is running under Vista or Ubuntu?

---

### Post by Geoffrey_Arndt on 2015-11-12
Yes . . . a driver is software.   It exists only on the partition or drive you've installed it to . . . . . Windows is not really even aware of Linux or it's files or programs.   Windows exe's don't work in Linux, and Linux programs don't work in Windows.

The Ubuntu drivers should be installed using the "additional drivers" application in Ubuntu (just type that into the dash search to bring up the app).

---

### Post by rdb3 on 2015-11-12
Thanks Geoffrey!!  Will try it.

---

### Post by rdb3 on 2015-11-12
Nvidia-304 installed and corrected problems.  Computer 3 is good to go now.

Here's what I followed to do this via command line since the Dash didn't work at the time.

 [http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt](http://askubuntu.com/questions/22118/can-i-install-extra-drivers-via-the-command-prompt)

Many thanks for the help.

---

### Post by sudodus on 2015-11-12
Congratulations :KS

and thanks for sharing the solution :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by rdb3 on 2015-11-12
Done,  Thanks... and until the next time....

---

