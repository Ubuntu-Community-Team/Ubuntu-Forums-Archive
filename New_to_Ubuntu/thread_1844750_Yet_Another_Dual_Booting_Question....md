---
title: "Yet Another Dual Booting Question..."
date: 2011-09-15
forum: New to Ubuntu
---

### Post by john wagner on 2011-09-15
Thanks in advance!  My question is thus, I have looked at all the similar questions/threads also, I recently bought a Toshiba Qosimio laptop, 6 gig ram, dual 500 gig HDD, i7, running win 7 on a 64 bit platform.  How can I load Ubuntu 10.04 on one drive and keep windows 7 on the other?  
Before I attempt this (since I've read of buttloads of problems), I would like step by moronic step for me, the moron.  It's been 10 years since my last new computer, so I don't want to break the shiny doing this!

It appears that windows is loaded on the first HDD, at least it shows 465 gig available.  So do I just boot from my ubuntu cd, manually install it to the second drive and all will be good?  Go to BIOS and set that drive as primary?  Or will all my marbles fall out of the bag?

I actually would prefer to keep only 100 gig for windows and the balance all go to ubuntu, but that might confuse windblows as I would have to re partition the HDD with the windows OS on it.  I know how picky it can be.

Any wiki's/threads/instructions I can go off to study?  Any advice?  I really don't want to break the shiny and have to reload windows 7, bad enough it's gonna be there!

john

---

### Post by snip3r8 on 2011-09-15
Once you install ubuntu you should have the grub bootloader which will give you an option to boot either windblows or linux,i dont forsee any problems ,even with partitioning.

---

### Post by candtalan on 2011-09-15
As long as you can determine (with certainty) which is the first (windows) drive and which is the second (unused) drive then during the ubuntu install you will see (I think) an option to choose the second drive and allow it to be erased and taken over by Ubuntu. 
This approach is useful because it does not affect any partitions on the first (windows) drive, which further reduces the risk of install problems.

Once installed, you will have boot options for Windows or Ubuntu. You do not need to allocate the second drive as master or anything. The MBR master boot record is on the first drive and will be changed during Ubuntu install to suit the new situation.

---

### Post by wildmanne39 on 2011-09-15
Hi, one method that a lot of people prefer so they do not accidently write over there windows partition is to disconnect the windows drive then install ubuntu on the second drive, then run this command in ubuntu after the install is complete to update the boot menu.

Also it is recommended to make backup of your data, and many windows systems you have to create recovery disk yourself, I suggest you do that before you try to install ubuntu.
```
sudo update-grub
```
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Thank you

---

### Post by john wagner on 2011-09-15
> **wildmanne39 said:**
> Hi, one method that a lot of people prefer so they do not accidently write over there windows partition is to disconnect the windows drive then install ubuntu on the second drive, then run this command in ubuntu after the install is complete to update the boot menu.

Also it is recommended to make backup of your data, and many windows systems you have to create recovery disk yourself, I suggest you do that before you try to install ubuntu.
```
sudo update-grub
```
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Thank you

Yeah. I haven't installed anything yet on the Toshiba.  Gonna back it all up first then tackle the ubuntu loading.

Thanks, I'll let you all know how it goes!

---

### Post by wildmanne39 on 2011-09-15
Hi, great let us know how it goes.
Thank you

---

### Post by oldfred on 2011-09-15
Please go back and edit your post and change to Windows. We have to show respect even if it is not our favorite operating system.

Herman has several versions all with good info. If you are installing on a second drive this may be appropriate. You have to use manual install to get the combo box on where to install the grub2 boot loader.

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by anewguy on 2011-09-15
See my signature for a illustrated guide to installing to a 2nd or external disk.

Dave ;)

---

