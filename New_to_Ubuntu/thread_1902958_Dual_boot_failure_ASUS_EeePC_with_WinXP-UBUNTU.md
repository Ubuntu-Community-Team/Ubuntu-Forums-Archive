---
title: "Dual boot failure ASUS EeePC with WinXP-UBUNTU"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by el10 on 2012-01-01
My son in law has recently (Oct.-2011) bought an Asus EeePC 1201NL, preloaded with Win XP.  No Recovery or Utilities CD/DVD, (although the manual says the CD/DVD that comes with the machine), were supplied with the netbook. 

He has been using Ubuntu, and wanted Ubuntu 10.04 on the new machine. He was told by the vendor that it would accept Ubuntu. 
He he came to me for assistance. 
Although I have successfully installed at least 4 dual booting systems (Win-XP & Ubuntu) on variuos discarded machines. 
On this occasion I tried to install side by side to the existing Windows XP, but when the process was finished we could NOT access the machine either with Win XP nor with Ubuntu.

I have tried all sorts of things but I always end up by getting the following on the screen:
	&#8220; error: no such device: e3d001dd-b57e-4b27-ac3a-6e6cbf02a17c.
    	grub rescue>&#8221;

After a lot of fiddling I managed to access the machine as follows:
 	Inserting a USB with Ubuntu 11-04 Live.  On Boot up and pressing the ESCape key (sometimes after pressing the f2  Key),  it will give me the Dual Boot choice, and I could access the netbook HDD and consequently I could access either Win XP or Ubuntu. 

If I do not follow the above procedure I get the above error message.

My guess is that the problem could solved by using grub and removing the necessity of having to boot the machine with the USB 11.04 inserted, but I do not know HOW and a Step by Step solution would be very much appreciated ! 

Can anyone help ?  
Thank you

---

### Post by dixonstalbert on 2012-01-01
hello

I have the same netbook dual booting with XP

I am not a grub guru but it sounds like a problem with the UUID's assigned to the different partitions.

If you can start your 10.04 on disk using the USB, run command in terminal

sudo fdisk -l

to list your partitions.

then run 

blkid


to list your UUIDs assigned to them.

then open /boot/grub/grub.cfg and see if grub line for 10.04 has the right UUIDs

If not, you have found your problem. 

Probably easiest to fix is search ubuntuforums for 'grub2 tutorial'. There is a a guru who has written how to fix UUID problems and in his signature is a link to utility called 'Boot Repair' which automatically fixs grub2 problems. 

hope this gets you started good luck.

---

### Post by el10 on 2012-01-01
Thank you,dixonstalbert. 
I have to get the machine from my son in law and it will take a few days, but I will try what you suggested and keep you posted.

I am determined to sort this out for him. The shop does not want to know about it and Asus wants another £35 to reset the machine 
Thank you.

---

### Post by dixonstalbert on 2012-01-01
your welcome

Here is link to forum post I mentioned


[http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub2+tutorial](http://ubuntuforums.org/showthread.php?t=1769482&highlight=grub2+tutorial)

---

### Post by el10 on 2012-01-03
Thank you  dixonstalbert 
 After downloading Secure Netbook Remix and installing it on an USB, I used Boot Repair to restored the boot to Windows but I hve lost access to the not successfull Ubuntu installation. So I am now (defeated)  accepting the situation " as is", but would like to restore the disk space used by Ubuntu (see image), and hand back the machine. 
Would it be OK using **gparted** to delete the space used by Ubuntu?
I may possibly have another attempt at Dual Booting  (it has been fine on my other 4 machines- but not on this one) at a  later time, after practicing the use of fdisk. 
Has all hese problems have anything to do with the EF shown on the image? 
Thank you 
Attachments of "Partition Magic", "Gparted" and "Fdisk-blkid".

---

