---
title: "I screwed up my dual-boot install"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by Grendel336 on 2008-09-03
So not too long ago I was shutting down my Dell laptop. I have an Inspiron E1505 and was using Ubuntu almost exclusively for a few months with great delight. 

I clicked the shutdown option and waited for the laptop to power off. It didn't turn itself off. I waited for a few minutes but it appeared stuck. I had to go and did not want to leave the laptop open and on, so I pushed and held the laptop's power button to "force" it to shut off. Apparently that was a mistake.

The next time I tried to boot up Ubuntu I got the "Error 15" message. I was very annoyed at myself. I rebooted a few times but kept getting the same message. I booted up Windows Vista and that worked fine. Shut down and went back to Ubuntu and got the error 15 message.

So I did the total newb thing and thought, why don't I just uninstall Ubuntu and then install it again? So I did that. 

Yay!!! I can now log into Ubuntu again. 

BUT, now I have to go through the whole thing with getting my wireless going again. I have the Dell 1390 WLAN thing which I had worked out with wonderful results before. 

As I start working through the steps to fix my wireless I get error messages right from the get-go.


Did I really make a major mistake forcing the power off when I first encountered what appeared to be a frozen shut-down mode?

Why wouldn't uninstalling Ubuntu then re-installing it take me back to ground zero? It appears things were not removed completely and are still hampering my ability to hook up to the internet through my wireless.

I'd appreciate some advice on what to do in order to get back to where I was a few months ago. 

Thanks in advance.

---

### Post by bobnutfield on 2008-09-03
While not a good thing to do when your system hangs, forcing a hard shutdown with the power button is called an unclean shutdown and usually will not cause the errors you are not describing (although continuous hard shutdowns this way can create bad sectors on your disk.)

Error 15 means that Grub could not find the partition you were trying to boot, as though it was not there.  A hard shutdown will not delete your system.  More likely, it corrupted the entry in your menu.lst file.

If you reinstalled, that would wipe the partition clean and should not be affecting your new installation.  You might try reformating the partition first and then reinstalling.  That will definitely insure that no previous installation is affecting a reinstalled system.

---

### Post by Grendel336 on 2008-09-03
Do I reformat from Window's Vista????

Sorry for asking, but I've never done something like that before. 

Thanks for the quick response too.

---

### Post by bobnutfield on 2008-09-03
NO!!  Do NOT REFORMAT YOUR VISTA PARTITION!  I meant that you could try to reformat the partition that you Ubuntu installation was on.  You would do that with the Gparted program on the Live cd

EDIT:  Are you using a WUBI installation within Windows?

---

### Post by Grendel336 on 2008-09-03
WUBI installation?

I burnt the Ubuntu installation CD and then installed it on my hardrive as a bootable OS. 

When I first turn on the computer I get a boot screen where I can chose between Vista or Ubuntu as my OS. 

I do not need a CD in the computer to do this.

Does that mean I'm using a WUBI installation?

---

### Post by luckydeveloper on 2008-09-03
no it does not mean wubi installation. its ok .. never confuse yourself now. continue what bobnutfield told you

---

### Post by luckydeveloper on 2008-09-03
i too get a similar error. i always used to install windows first and then kubuntu in other partition from the boot(not wubi) and it worked for about 1.5 years(from the days of 7.04) but suddently some 2 months back...(i know i should have done a similar thing like force shut down) the windows is booting well from the menu but when i go to kubuntu...it does not boot....instead it gives me an error. i even formatter my whole hard disk and tried installing windows and kubuntu( first windows then kubuntu) and it gave the same error when i choose kubuntu in my grub menu

i tried several times but it never worked. i didn't want to strain my hard drive by formatting and installing it again and again. so i installed it through wubi... and tada.... it is working properly. though i am not fully satisfied by installing it through wubi... i always want to give a raw hard drive partition to kubuntu and work in that. 
what could have went wrong ?

---

### Post by t0p on 2008-09-03
> **luckydeveloper said:**
> i didn't want to strain my hard drive by formatting and installing it again and again

What do you mean, "strain the hard drive"?  Formatting and installing won't harm your computer!

---

### Post by Grendel336 on 2008-09-04
> **bobnutfield said:**
> NO!!  Do NOT REFORMAT YOUR VISTA PARTITION!  I meant that you could try to reformat the partition that you Ubuntu installation was on.  You would do that with the Gparted program on the Live cd

OK, thanks. I thought doing something through Windows did not make sense. 

So I would do this partition cleaning through the Terminal then right?

I would put my CD of Ubuntu back into the CD drive and open Terminal correct?

I assume there's a command I need to type to start/find Gparted?

Can somebody step me through this?

I appreciate the help.

---

### Post by Sef on 2008-09-04
> So I would do this partition cleaning through the Terminal then right?

I would put my CD of Ubuntu back into the CD drive and open Terminal correct?

I assume there's a command I need to type to start/find Gparted?

Can somebody step me through this?

GParted is on the Live CD.  System > Administration > Partition Editor

However, do this first from the terminal (Applications > Accessories > Terminal)

paste or type in this command:

```
sudo fdisk -l
``` Small L  That will show you your partitions.

Then paste or copy it here.  Once here, we can tell you which partition to reformat.

---

### Post by bobnutfield on 2008-09-04
OK, firstly, be very careful when working with partitions.  If you are dual booting with Windows, you do not want to do anything with the Windows partition.

My question about WUBI was simply to see if you were using Ubuntu as a file within Windows (obviously you are not, so disregard the question.)

Before you do anything with repartioning,  clarify what you mean by errors when trying to re-set up your wireless.  Just want to make sure reinstalling Ubuntu is necessary or recommended.

---

### Post by Grendel336 on 2008-09-04
I had to work through this "fix" when I first loaded Ubuntu to get my wireless working.

[This Fix]("http://ubuntuforums.org/showthread.php?t=760568&highlight=wireless+1390") <-- worked great

After my problems, when I try to do the first set of commands in the instructions regarding the ndiswrapper I am getting a message that I can't remember right now and won't be able to post until later today. (I'm at work now....)

The reason I was trying to work through the tutorial again was because I could not connect with my wireless router again. I assumed that when I uninstalled Ubuntu that I lost the ndiswrapper stuff i'd added/fixed previously along with the appropriate driver for my wireless card. 

I'm sorry if this is confusing, but I'm such a novice at this kind of thing I can't think of a better way to communicate what I'm getting.

---

### Post by bobnutfield on 2008-09-04
OK, if you now have Ubuntu and Windows both booting properly for you, don't reinstall until you can post the errors you are getting when trying to reset-up your wireless.
We may be able to get it resolved for you without reinstalling.

---

### Post by Grendel336 on 2008-09-04
Thanks for your help. I will try to post what I'm getting later this evening. It's a pain since I can only connect to internet through Windows so I have to keep changing OS's to work through these bugs.

Is there any specific command I should run from the terminal, or should I just post the results I find when I start trying to run through the tutorial?

---

### Post by bobnutfield on 2008-09-04
If the tutorial worked for you previously, simply post the errors you get when attempting it.  That should be enough to determine what is happening.

If you have been using ndiswrapper, there are a number of ways to get it going.  Just make sure ndiswrapper is installed.  You can get it from the repos.

---

### Post by Grendel336 on 2008-09-04
I need to get the driver that the tutorial tells me to get. 

It's a download from Dell (R151519.exe)

I have to do this from Windows Vista. I burnt it to a CD, but when I view the CD when using Ubuntu the CD shows that there is nothing on it. The CD shows as being blank.

Is my CD format in a Windows format that Ubuntu can't recognize? 

What am I doing wrong?

---

### Post by bobnutfield on 2008-09-05
A CD burnt in Windows should show up in Ubuntu as both use ISO9660 files for CD's.  I cannot tell you I the CD is showing up as blank in Ubuntu.  Does Ubuntu read other CD's OK?  In the meantime, you might try loading the file onto a USB stick if you have one as Ubuntu has no trouble reading a VFAT file system.

---

### Post by Grendel336 on 2008-09-05
It's supposed to be pretty crappy weather here tomorrow as Hanna blows through...I'll try to type out the messages I get when working through the commands. 

I'll try to burn another CD with the driver exe file on it. I did this once before but I just can't remember what I did. It's very frustrating to not have a great computer mind at times like this. 

Thank you for your patience. You've been a great help.

---

### Post by Grendel336 on 2008-09-05
Here's what I got from the sudo fdisk command:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x40000000



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1           7       56196   de  Dell Utility

/dev/sda2               8        1313    10485760    7  HPFS/NTFS

/dev/sda3   *        1313       14333   104580096    7  HPFS/NTFS

/dev/sda4           14333       14594     2097152    f  W95 Ext'd (LBA)

/dev/sda5           14333       14594     2096128   dd  Unknown

link@link-laptop:~$ 

---

### Post by Grendel336 on 2008-09-05
And here's what I got when I performed the "Troubleshooting" commands in the tutorial:

> link@link-laptop:~$ lspci -nn | grep 14e4
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
0b:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 01)
link@link-laptop:~$ gksudo gedit /etc/rc.local
link@link-laptop:~$ ndiswrapper -1
install/manage Windows drivers for ndiswrapper

usage: ndiswrapper OPTION
-i inffile       install driver described by 'inffile'
-a devid driver  use installed 'driver' for 'devid' (dangerous)
-r driver        remove 'driver'
-l               list installed drivers
-m               write configuration for modprobe
-ma              write module alias configuration for all devices
-mi              write module install configuration for all devices
-v               report version information

where 'devid' is either PCIID or USBID of the form XXXX:XXXX,
as reported by 'lspci -n' or 'lsusb' for the card
link@link-laptop:~$ 1smod | grep b43
bash: 1smod: command not found
link@link-laptop:~$ lsmod | grep b43
b43                   115104  0 
rfkill                  8592  4 rfkill_input,b43
mac80211              165652  1 b43
led_class               6020  1 b43
input_polldev           5896  1 b43
ssb                    32260  1 b43
link@link-laptop:~$ lsmod | grep ndiswrapper
link@link-laptop:~$ ls -1 /etc/rc.local
/etc/rc.local
link@link-laptop:~$ 

---

### Post by Grendel336 on 2008-09-06
So I'm having an issue around the same thing.

I need a specific driver to be able to connect to the internet. 

The tutorial says to get a driver from Dell. The driver downloads as a .exe file. 

So do I need this wine, or can I run the exe. in windows then copy something specific over to Ubuntu? 

Or do I have to go with this "wine" thing. The post that states it's not very stable worries me since my current issues are due to a system shut-down problem I had a few months back.

---

### Post by SuperSonic4 on 2008-09-06
Drivers don't work in wine anyway.

Have you looked in System -> Admin -> Restricted Hardware (or somewhere similar) and seeing if the wireless card is there?

---

### Post by Grendel336 on 2008-09-06
But the instructions in the tutorial I'm following state this:

> cd ~/wireless-install/
unzip -a R151519.EXE -d R151519/
cd R151519/DRIVER/
sudo ndiswrapper -i bcmwl5.inf

Note the R151519.exe part?????

Sorry, but I am confused. Is this different than perhaps a different type of .exe file?

---

### Post by zipperback on 2008-09-06
> **Grendel336 said:**
> So I'm having an issue around the same thing.
I need a specific driver to be able to connect to the internet. 



Start a new thread and we can help you get your wireless working.

- zipperback
:popcorn:

---

### Post by SuperSonic4 on 2008-09-06
Seems like an ordinary exe file to me. Just with a filename of R151519 although I could be wrong.

---

### Post by Grendel336 on 2008-09-06
> **zipperback said:**
> Start a new thread and we can help you get your wireless working.

- zipperback
:popcorn:

I did:

[http://ubuntuforums.org/showthread.php?t=909597]("http://ubuntuforums.org/showthread.php?t=909597") <-- clicky

I'm not being impatient. I appreciate everything most people here have done for me. I saw this thread on .exe files and just had to ask a question.

---

### Post by Grendel336 on 2008-09-07
It appears I have fixed my own problem. I am currently up and running on the internet using Ubuntu. 

I am happy once again. 

Thank you to those who helped, or tried to help.

I fully appreciate it.

---

