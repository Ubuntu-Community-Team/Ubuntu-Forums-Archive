---
title: "Grub Pen Drive Problems"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by guillem_bcn on 2011-11-01
hi all!
 
i have windows vista in my hard drive, and i value ubuntu in a pendrive usb as i can take it with me, plug it in any computer and have my docs, my cloud and everything with me, without carrying a computer.
 
 
i mean, i want my computer as is, with vista, but when i plug the usb pendrive, i want it to boot ubuntu. it can be done, as i've done it, via grub.
 
i've had several hard problems with grub, though:
1st: it installed in my hd, crashing my windows.
2nd and 3rd: it crashed my ubuntu pendrive when updating.
 
i've searched for a week, trying to find if i can install ubuntu in a pendrive as if it was a hard drive: NO GRUB AT ALL!!! it isnt needed if ubuntu is installed in a hd, so... why is it needed in a pendrive???
 
i'm about to quit ubuntu. i'm not comfortable with mbrs partitions sudos fat32 and such jargon. i just value having a full system in a pendrive bootable from any computer without touching its hd: carrying a pendrive is much easy than carrying a computer!!!
 
i've got a headache and stressed every time i update, fearing -and guessing!- it will crash.
 
my options are install ubuntu in a pendrive WITHOUT grub, supergrub, ultragrub, magicgrub, grub 2.0 or any other boot selector or quit ubuntu and wait for windows 8 in a pendrive or android in a pendrive. i simply cannot go on investing a week learning what went wrong in every update to find it was (again) grub.
 
grub is not installed in the hard disk if i use the whole disk for ubuntu, so... why is it needed in a pendrive, which can be used as a hard disk?
 
does anybody know any way to install ubuntu or any linux without grub or similar in a pendrive??? i've read someplaces that it's necessary, but, before quitting, i'd appreciate any suggestions to keep a portable ubuntu in my life.
 
thanks a lot
guillem

---

### Post by Rex Bouwense on 2011-11-01
Works for Lubuntu.  You can try this:
[http://ubuntuforums.org/showthread.php?t=1872303](http://ubuntuforums.org/showthread.php?t=1872303)
Enjoy.

---

### Post by grahammechanical on 2011-11-01
I am confused by terms like pen drive, thumb drive, USB memory stick, so we may not be talking about the same thing, but

last week I purchased an 8GB USB memory stick and I created an Edubuntu live USB with persistence. I was able to boot from the drive without making any changes to my machine's Grub menu. It is like a live CD but you can make changes to what is on the USB Memory stick.

I have been able to update the OS, add/remove programs, put music files and PDF documents on to the memory stick, add users and modify each user's desktop, install Compiz configuration Settings Manager and set wobbly windows as an effect, and of course connect to the internet. The size of the memory stick limits how much can be put it. The open source video driver is good enough to run Unity 3D on my machine.

All I did was to download an ISO image, type USB in the Dash and then run Startup Disk Creator. I assigned a suitable amount of the stick's memory for the persistent storage. And let Startup Disk Creator do its stuff.

After some experimentation with my machine's BIOS settings I was able to load a Live USB Ubuntu with the Try Before Installing Options. And that is how I do it.

Remember, with a Live USB you are running as a user called Ubuntu who has administrator privileges (but no password needed). If you set up another user when you select shutdown you will get to a login greeter screen. Select Other and type Ubuntu as the user, press enter as the password, then when you are back to the desktop select shutdown again and the thing will shutdown correctly.

It would be nice to not have t0 chose language screen and the Try Ubuntu menu options and for it to load like a hard disk Ubuntu but I do not know how to do that.

Regards.

---

### Post by Rex Bouwense on 2011-11-01
I believe that thumb drive, pen drive, memory stick, and flash drive are all names for the same thing.  What the OP wants to do is install Ubuntu on one of those drives unless I read the post wrong.

---

### Post by I2k4 on 2011-11-01
That "303" link looks very good - wish I'd had it before mistakenly installing GRUB on my netbook HDD while trying to create a pendrive only installation of Lubuntu 10.10.

Unfortunately:  from what I made out, once GRUB replaces the Windows "Master Boot Record" on the HDD, there is no easy way to remove it.  Windows 7 appeared as a choice on GRUB, but no way to get rid of GRUB short of full Windows recovery from a disk.  I ended up putting a dual boot for W7/Lubuntu on the netbook HDD - luckily I had experimented and like Lubuntu enough not to regret it.

For portability the original poster wants, the best way definitely seems to be to ensure GRUB goes on the pendrive, as instructed in the "303" link.  

I've been experimenting with "Live USB" for nearly a year, and found two major problems:  a) it starts out fully functional but seems to lose functionality over time - demanding non-existent passwords to do things, or losing recognition of the hard drive or other devices; and b) Live USB requires that any machine its plugged into have BIOS set to boot priority for the USB Drive, which most machines don't.

That said, the official Ubuntu "How To" instructions for Live USB here are simple and bulletproof in my experience:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

The one extra step is at Step 2, to set the "Persistence" option on the Pendrive installer to permit the drive to save changes and store application packages between reboots.  As I say, once the machine's BIOS is set for boot priority, this works quite well - but in my experience gets buggy eventually.

---

### Post by oldfred on 2011-11-01
Do not be afraid of grub. You have to have a boot loader and with Ubuntu the default is grub. If installed to a drive with only Ubuntu you still have grub but will not see it. That is like Windows when you have just one Windows system, you so not see the Windows boot loader but it is still there. 

If your Flash drive is 4GB or less you have to use the persistent install. If 8GB or more a full install will let your use more of the available space.


Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Step by Step Full install 8GB C.S.Cameron Post #7
[http://ubuntuforums.org/showthread.php?t=1719346](http://ubuntuforums.org/showthread.php?t=1719346)

HOW TO Avoid Wubi & Install Ubuntu on USB Drive -amjjawad
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)

---

### Post by Steve54 on 2011-11-01
> **guillem_bcn said:**
> hi all!
 
i have windows vista in my hard drive, and i value ubuntu in a pendrive usb as i can take it with me, plug it in any computer and have my docs, my cloud and everything with me, without carrying a computer.
 
 
i mean, i want my computer as is, with vista, but when i plug the usb pendrive, i want it to boot ubuntu. it can be done, as i've done it, via grub.
 
i've had several hard problems with grub, though:
1st: it installed in my hd, crashing my windows.
2nd and 3rd: it crashed my ubuntu pendrive when updating.
 
i've searched for a week, trying to find if i can install ubuntu in a pendrive as if it was a hard drive: NO GRUB AT ALL!!! it isnt needed if ubuntu is installed in a hd, so... why is it needed in a pendrive???
 
i'm about to quit ubuntu. i'm not comfortable with mbrs partitions sudos fat32 and such jargon. i just value having a full system in a pendrive bootable from any computer without touching its hd: carrying a pendrive is much easy than carrying a computer!!!
 
i've got a headache and stressed every time i update, fearing -and guessing!- it will crash.
 
my options are install ubuntu in a pendrive WITHOUT grub, supergrub, ultragrub, magicgrub, grub 2.0 or any other boot selector or quit ubuntu and wait for windows 8 in a pendrive or android in a pendrive. i simply cannot go on investing a week learning what went wrong in every update to find it was (again) grub.
 
grub is not installed in the hard disk if i use the whole disk for ubuntu, so... why is it needed in a pendrive, which can be used as a hard disk?
 
does anybody know any way to install ubuntu or any linux without grub or similar in a pendrive??? i've read someplaces that it's necessary, but, before quitting, i'd appreciate any suggestions to keep a portable ubuntu in my life.
 
thanks a lot
guillem
 
GRUB does still install even if you use all of the HDD, it just doesn't show you the boot menu when it thinks there is only one OS installed.
 
The simplest way to install it to the pendrive without GRUB throwing a spanner in the works is to temporarily disconnect the HDDs so that GRUB doesn't see them.
 
I'm not sure if you can move a fully installed Linux OS from PC to PC, you certainly can't with Vista as drivers will be wrong on the change of hardware. I think you need a 'Live CD' version with persistence as suggested by grahammechanical.

---

### Post by guillem_bcn on 2011-11-01
first of all, thank you all.
 
some comments: 
 
*i have tried persistence, but i recomend full install, as if the pendrive was a hard disk.
*i call it usb pendrive, but its also a flashdrive plugged in a standard usb. mine is 16gb.
*1st time i installed ubuntu in a pendrive, i missed the 'install boot in sdb', so my vista hd crashed and i went mad to rtestore it and get my data back! be careful.
*the two times i updated ubuntu (from 9 to 10 and from 10 to 11) it crashed (both times!) at the same point: grub. that's exactly why i dont want it installed.
 
it seems it *has* to be installed. :-( so i can see it will crash again when i update, as i've installed 10.04 again, because i have the livecd already burnt.
 
i'm really scared about grub, because it crashed 3 times causing me severe pain and anxiety. the mbr vista incident was really scary for me, and the 2 updates put me angry :-(((. each of these problems implied a whole stop-all-and-repair-it week. 
 
though i am an advanced windows vista user, i cant get the idea of all this mbr sudo mount grub_rescue fdisk gparted things. VERY confusing!!! seems dangerous, also, and, twice, i couldn't simply load ubuntu!
 
my bet is, as suggested, disconnect the hard disk (via bios, i guess), and install it again in the pendrive, though, as i can read, grub WILL be installed.
 
All my headaches have come from grub when installing (mbr vista thing) and twice from the ubuntu 'one-button' update-now!. i think install programmers should take a look at it, as i know several people who suggested me this ubuntu-in-a-pen thing and i suggested it to many others.
 
maybe (maybe) many users like this idea of taking a flash drive instead of a whole computer, and wish to keep their (our) windows in the hard drive as is, i mean... not a dual boot, just a pen that, when plugged, boots ubuntu in almost ANY computer (as i have happily checked!), but i right now come from a friend's home having this exact problem :-( to who i installed his first ubuntu in a pen...
 
ok, so recaping:  i'll disconnect the hd via bios, install 10.04 in a pen, with grub carefully installed in sbd1 (letting the install program to format it)  and then update to 11. 
 
hate to say i dont have too much hope on it, as i've tested in my very flesh that grub IS the problem.
 
very sincere thanks for your help, and please, *PLEASE* have fun!
 
also, have a nice day.
 
hugs for all
 
guillem

---

### Post by oldfred on 2011-11-01
Unless the installer sees the flash drive as sda, any of the auto installs will install grub to sda. You best use manual install.

Grub remembers where to reinstall on updates. So if you initially install it wrong, it still remembers that and reinstalls to the wrong location.

Best to reset to correct location or disable grub updates.

#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

---

### Post by ixtok on 2011-11-01
I have installed ubuntu 11.10 on a 8gb memory stick. My computer has no cd drive so I created a live 11.10 usb. My computer runs ubuntu 10.10. Running of this live usb, I chose install and was careful to install to the 8gb usb and carefull to choose to install grub to it also. This worked. My computer with 10.10 on its hard disk was not touched. I can boot this 11.10 memory stick on both of my computers although one of them required a change in bios as it thinks the memory stick is a hard drive. I have used update manager on this stick with no problems.

---

