---
title: "Dead PC....ubuntu able to save it ?"
date: 2012-09-26
forum: New to Ubuntu
---

### Post by lucas1973 on 2012-09-26
I have an Acer Aspire M3910 desktop with a Windows 7 install on it and its "died"....

No recovery disc made....it won't boot into Acer recovery mode (alt f10 brings up an error message)....trying to boot normally tells me bootmgr is missing....and it won't even allow me to install XP from a Dvd (boot attempts result in a head drive configuration issue error.

In short I just want to rescue as much data as possible before deciding what to do with the PC. The Windows 7 I had was preinstalled and lurks as part of a recovery process in a partition I don't seem able to access.

So I saw that ubuntu can be installed to a usb stick. If I do this (try to do it ?) Would I get to a state where I can boot from it and move the data I want to save ? Will it allow me to see if I can "save" my Windows 7 recovery files ? I don't mind buying a proper windows operating system down the line but for now its about resurrecting the pc that won't even boot.

Am I barking up the wrong tree or am I heading in the right direction ?

Thanks in advance :-)

---

### Post by Deuce1912 on 2012-09-26
> **lucas1973 said:**
> Am I barking up the wrong tree or am I heading in the right direction ?

I would say you are heading in the right direction. You can make a bootable usb drive with Ubuntu on it which will bring you to a live environment (Desktop) of Ubuntu. 

You can then save any files from the windows drive to a secondry drive and then install ubuntu from the usb drive after you've saved all the data you need if you wish.

I hope this helps.

- Deuce1912

---

### Post by acrazyplayer on 2012-09-26
> **lucas1973 said:**
>  Will it allow me to see if I can "save" my Windows 7 recovery files ?

You probably will not be able to do this part. Even if you did manage to move the files you probably wouldn't be able to use them. 

I suppose it could be possible however if you have certain folders available and certain programs that can turn those folders into a windows installation disk on another PC that works, but its a unlikely.

Here is the program which might help you if you can get the folders it requires (if it even does - I've never used it). 

[http://www.rt7lite.com/rt-se7en-lite.html](http://www.rt7lite.com/rt-se7en-lite.html)

---

### Post by ld114 on 2012-09-26
There is a chance (as mentioned above) that your data will be windows specific or not usable. However, before things get too complicated, boot up with a live Ubuntu CD, or a live Ubuntu USB stick, and use the file manager to see what data you can see on the hard disk. (There is always a chance that your disk has died.) If you can see data then you should be able to copy it onto another medium, to work on later.

---

### Post by OrangeCrate on 2012-09-26
> **ld114 said:**
> There is a chance (as mentioned above) that your data will be windows specific or not usable. However, before things get too complicated, **boot up with a live Ubuntu CD, or a live Ubuntu USB stick, and use the file manager to see what data you can see on the hard disk.** (There is always a chance that your disk has died.)** If you can see data then you should be able to copy it onto another medium, to work on later.**

Best answer.

---

### Post by kurt18947 on 2012-09-26
A couple things come to mind.  Do you have another functioning PC?  To create a bootable USB you'll need to use something like Unetbootin which is available for Windows & Linux.  The second thing is you may need to change the boot sequence on your problem machine.  In order to my desktop to boot from a Live USB, I have to make my first boot device a USB hard disk drive (even though it's a flash drive).  Your machine's terminology may be different but if your failed hard disk installation is the first choice,  your machine will probably never boot from the live USB. It has to 'see' the USB drive before the internal hard drive.

---

### Post by lucas1973 on 2012-09-26
Well I've managed to get the usb boot working fine and dandy and can access the hard drive so the PC isn't dead *hoorah*.
 
I am able to see the files I want and move them to somewhere "safe" which is fab too :)
 
However seeing as you guys are a fountain of knowledge I may as well ask the following....
 
If there is a problem with the bootmgr file (which I asume controls how the PC boots up) is there anything I can do about that now I have access to the PC is a fashion ?
 
I've tried the notion of removing it (I backed it up first) and just got a "bootmgr is missing message" so thats a no go.
 
I know before everything went pear shaped something had happened to the partition structure as I got a message along the lines of "cannot install operating systems after this change" from windows AFTER I had created a new partition (which I just thought was weird).
 
I'm assuming the best idea (now I can get the stuff I want) is to start from scratch with a retail version of windows but its not the most cost effective if I can somehow save the operating system thats already on there.
 
Any advice will be gratefully received and thanks so much thus far !

---

### Post by ld114 on 2012-09-26
I'm afraid I don't know much about windows so will have to leave this to others. The first thing I did with a new laptop was to use clonezilla to create a backup image of the windows disk installation (just in case), and then remove windows from the pc altogether before installing Ubuntu (or other version of linux).

If you have rescued your data, and want to experiment, maybe this is your time to try out Ubuntu.

---

### Post by mips on 2012-09-26
> **lucas1973 said:**
> 
I'm assuming the best idea (now I can get the stuff I want) is to start from scratch with a retail version of windows but its not the most cost effective if I can somehow save the operating system thats already on there.
 
Any advice will be gratefully received and thanks so much thus far !

No. You should be able to recover somehow. The recovery partition is still there.

[http://support.acer.com/acerpanam/desktop/0000/Acer/AspireE360/AspireE360faq40.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireE360/AspireE360faq40.shtml)
[ftp://ftp.support.acer-euro.com/notebook/empowering_technology/NB%20ET2%20user's%20guide/Acer%20eRecovery%20Management%20English.pdf](ftp://ftp.support.acer-euro.com/notebook/empowering_technology/NB%20ET2%20user's%20guide/Acer%20eRecovery%20Management%20English.pdf)


If this still does not work PM me and I will try and provide you with a 100% legit OEM download iso image for that PC but I require some info.

---

### Post by daslinkard on 2012-09-26
After you get the data off the computer that you need from the Ubuntu environment you can restart your PC and at the 1st screen start tapping F8 repeatedly....from here you will select Repair Your Computer.

The PC may ask for your password....you will then be prompted to what options you would like to perform.  There should be a recovery manager in which you would be able to select this and take the PC back to the factory settings.  This will restore the system to the out of state condition of when you first bought the PC.

---

### Post by cmcanulty on 2012-09-26
I have a similar acer and Ubuntu works great no issues at all

---

### Post by KosakiHook on 2012-09-26
Puppy Linux is another possibility.  Download the latest .iso, burn to a CD, and boot the puppy linux CD.  You can mount the Windows partition, also mount a USB drive, and copy your windows files to the USB drive.

I bought a used desktop that had a corrupted Win Vista drive.  I was able to recover many of the files and give to the original owner.

---

### Post by kurt18947 on 2012-09-27
I would think there's a way to restore to 'factory' condition but have no experience.  When I've bought notebooks with various partitions I do an initial setup then create an image of that partition using something similar to clonezilla.  Then I remove all partitions except the Windows one and generally shrink that.

If you are not able to use the restore, you can download legit Windows 7 ISOs.  You *must* download the correct image.  For instance, if your notebook came with Win7 professional 32 bit,  you must download exactly that in order for the Windows key that came on your machine to work.  Here is one source:

[http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/](http://www.mydigitallife.info/download-windows-7-iso-official-32-bit-and-64-bit-direct-download-links/)

Of course the above are generic Windows installs.  They won't include drivers, manufacturers' utilities and such.  I hope you're able to get things working.

---

### Post by daslinkard on 2012-09-27
> **daslinkard said:**
> After you get the data off the computer that you need from the Ubuntu environment you can restart your PC and at the 1st screen start tapping F8 repeatedly....from here you will select Repair Your Computer.

The PC may ask for your password....you will then be prompted to what options you would like to perform.  There should be a recovery manager in which you would be able to select this and take the PC back to the factory settings.  This will restore the system to the out of state condition of when you first bought the PC.

Not for sure if this got looked over but here is how you can do the system restore without the recovery media disc.

---

### Post by cmcanulty on 2012-09-27
You can put the image on a USB key.Unetbootin is very east to use.I have done my acer netbook with a usb image.Just hit the right key at boot to set bios to boot from flash drive, Usually f2, f10 or f12 it will flash up as it tries to boot unless you are totally black screen. If so just try all the f keys until you hit the right one.Email me if more help is needed. Good luck

[http://nixliving.blogspot.com/2010/01/ubuntu-rescue-remix-helped-factory.html]("http://nixliving.blogspot.com/2010/01/ubuntu-rescue-remix-helped-factory.html")

---

### Post by daslinkard on 2012-09-27
Really truly once you get into the Live Environment for any Linux distro it should be rather easy for you to move to your HD and find your old documents.  I believe that you said you were running Windows 7 so you would need to look for the folder labeled "User" and then draw out the files from there as this would have your old information.

From that point in time I'd have to rev the engines up for Linux and get me some Ubuntu!

---

### Post by cmcanulty on 2012-09-27
yeh the ubuntu will wiz along compared to windozzze. Especially if you try Xubuntu or Lubuntu though mine does Ubuntu 12.04 fine.

---

### Post by daslinkard on 2012-09-27
> **cmcanulty said:**
> yeh the ubuntu will wiz along compared to windozzze. Especially if you try Xubuntu or Lubuntu though mine does Ubuntu 12.04 fine.
Yes indeed Linux will absolutely destroy Windozzze.

---

