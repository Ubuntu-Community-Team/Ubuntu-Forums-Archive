---
title: "Installing Ubuntu 11.10 from a LiveUSB to a different USB"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by davidc60 on 2011-10-20
Hi,
I have been trying to &#8216;install&#8217; Ubuntu 11.10 from a LiveUSB to a different (brand new) 8gb USB (rather than installing to my HDD). It seemed to be going fine with most files installed but suddenly there was a &#8220;fatal error&#8221; &#8211; a message appeared saying &#8220;executing &#8216;grub-install/dev/sdd1&#8217; failed &#8211; this is a fatal error&#8221;. Then another message appeared saying that it was not possible to install the &#8220;bootloader&#8221; at the specified location&#8221; although it did not say why. The USB in question was partitioned as follows:
[LIST]
[*]Active partition &#8211; 5000mb (using the Ext2 File system as suggested by Ubuntu (it wouldn&#8217;t accept my attempt to use a FAT32 file system))
[*]Free space &#8211; 956mb
[*]Swap area &#8211; 2048mb
[/LIST]Incidentally, when I first selected the USB (dev/sdd1) as the location for the &#8216;install&#8217; I specified the &#8216;mount point&#8217; simply as /, rather than the 2 potential options of /dos, or, /windows.
[LIST]
[*]Maybe I needed to add something after the / to ensure a successful install?
[*]If it's not that that's the problem then I wonder whether anyone can enlighten me **in very simple terms** as to why the &#8216;install&#8217; might have failed.
[*]Is there anything I can do now to retrieve the situation with the existing 8gb USB (dev/sdd1) without going through the process again just to end up with the same failed outcome ie. Can I somehow insert the bootloader &#8216;manually&#8217; and if so, again **in very simple terms**, how can I actually do that?  **NB.** I cannot access the new USB (dev/sdd1) at the moment as the bootloader is not yet installed!).
[/LIST]Thanks,
DavidC (very new to Ubuntu)

---

### Post by ixtok on 2011-10-20
I installed 11.10 on a 8gb usb stick but I didn't try any partitioning. I just made sure the stick was blank and formatted normally then I let the live session install automatically. It installed grub on the stick with no problems and everything is working fine.

---

### Post by kemtnbkr on 2011-10-20
Here is a tutorial for installing on a USB drive; it's for 10.10 or 10.04 I think, but the basic idea should be the same- not too much should have changed:
[http://ubuntuforums.org/showthread.php?t=1650699](http://ubuntuforums.org/showthread.php?t=1650699)

Also, just out of curiosity, why do you have your primary partition as ext2 (and wanted in FAT32)?  And why do you have free space sitting around?  Just curious:)  

I've never tried to install to a USB as described, and I've never encountered your errors.  It may be worth it to google the exact error message you got; with lots of these things, there's people who have had the problem before, the trick is just finding where they figured it out.

---

### Post by oldfred on 2011-10-20
Not sure why you wanted to install grub2's boot loader to sdd1 (a partition), it has to be installed to sdd (the drive's MBR), to make it bootable. The only reason to install to a partition is if you have another boot loader and it is not as reliable with grub2 as there just is not enough space and it uses hard coded addresses to make it work.

amjjawad's link posted above it good, this is another with screen shots but is for Maverick. Process is the same with some minor difference in screens.
It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

---

### Post by davidc60 on 2011-10-21
Hi guys, thanks for all of your replies.  
  I will try to digest everything that has been suggested, including reading the linked threads, and will post again if I eventually succeed in doing what I've been trying to do.
  Note for 'Kemtnbkr' and 'oldfred': the primary partition was set as Ext2 simply because that was suggested to me when a message appeared on the screen during the attempted installation process and I left some space as 'free' simply to allow a bit of flexibility in case I wanted to re-arrange things later on. I had no 'knowledge' whatsoever about Ubuntu until just a few days ago and my knowledge of computers isn't much better. Consequently, my selections made during the installation process (eg. Re: the partitions etc) have not been based on any knowledge of what I am doing but rather more experimental in the hope that it would work. Needless to say, it hasn't so far but I 'll keep at it!!;);)

---

### Post by davidc60 on 2011-10-22
Hi, 
just posting this as an update - the message and link posted by Kemntbkr (ie. amjjawad' thread) was very relevant and has proved successful in installing from a Live USB to a second USB. 
The only issue I can see so far is that there is no swap area on the second (installation) USB . ie I did not create one during the installation process when I had the chance because I thought that it might be done automatically during installation and I didn't want to end up with 2 swap areas. 
Can I now easily create one within the installation USB without going through the installation process again?
Alternatively, will it really make much difference if I go without a swap area for the next few months until I move onto to the next version of Ubuntu ie. how crucial is the swap area? (Incidentally, I am not a heavy computer user - I have really only installed Ubuntu at this stage to see what it is about). 
Thanks, davidc

---

### Post by oldfred on 2011-10-23
For my installs to a Flash drive I do not not install a swap partition. I normally suggest either 2GB or the size of RAM for swap but on a flash drive you can get by without if you have a fair amount of RAM  - 3GB or more. Or if you do not load a lot of larger applications at once. 

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
HOWTO: Use swapfile instead of partition and hibernate 
[http://ubuntuforums.org/showthread.php?t=1042946](http://ubuntuforums.org/showthread.php?t=1042946)

You can check memory use. Linux uses RAM as cache so if it shows a higher use it may not be full.
Memory use including swap
free -m

---

### Post by davidc60 on 2011-10-24
Thanks to oldfred and everyone else who has replied to this thread - it has been a great help.
davidc

---

