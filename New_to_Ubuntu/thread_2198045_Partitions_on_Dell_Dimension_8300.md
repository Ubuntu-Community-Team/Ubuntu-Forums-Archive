---
title: "Partitions on Dell Dimension 8300"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by mick_ub_v11 on 2014-01-06
I have a Dell PC desktop with WinXP. I had 9 GB partitioned EXT4 (SDA7) with Ubuntu 13.04 running just fine.  I upgraded to 13.10 AND attempted to increase the Ubuntu partition from 9 to 20GB during the install.  Instead I ended up with a second partition of 10GB (SDA6) [also EXT4].

The 13.10 runs REALLY slow.  So I reverted back to installing 12.04 LTS.  Runs ok speedwise, but the display is something like 600x800 instead of 1380 x something, so I cannot access the entire page view to edit things.

Next I installed 13.04, but when I run it, I end up with only a gray screen with a cursor.

I realize I can dump the WinXP side of things and set up the PC as entirely Ubuntu, but I don't want to run away from this challenge.  Is there some "Partitioning 101" basics that I have probably violated?  Is this PC too limited in hardware to run 13.10 properly?

Thanks,

Mick



P.S.  Current Dell PC details:

Dell Dimension 8300
Intel Pentium 4,  3.0 GHz, 512 MB RAM
WinXP Pro SP 3

During Ubuntu install, the "Something Else" option shows this:

/dev/sda
/dev/sda1  NTFS; 60GB; 33GB Used; WinXP
/dev/sda6  EXT4; 10GB; 2.3GB used (for what?!)
/dev/sda7  EXT4; 9.4GB; 3.4GB; Ubuntu 13.04
/dev/sda5  SWAP; 534 MB; 0MB used.


Under my "Edit Partitions" window I get these choices:
sda6; Size 10041 -/+ MB
Use As:
 - do not use the partition;
 - EXT4 Journaling File System
 - EXT3 Journaling File System
 - EXT2 File System
 - BTRFS
 - JFS Journaling File System
 - XFS Journaling File System
 - FAT16 file system
 - FAT32 file system
 - swap area
 - physical volume for encryption


Device for boot loader installation:
/dev/sda  ATA ST3808110AS  (80.0GB)


Note:  I recognize the FAT16 and FAT32 file systems as Windows systems.  I'm fairly ignorant of the Linux/Ubuntu systems.

---

### Post by mörgæs on 2014-01-06
In a live boot you can delete sda 5, 6 and 7 (if you have a backup of all you need)
After that I suggest installing Lubuntu 13.10.

---

### Post by king.of.random on 2014-01-06
A good light distro that includes gparted is SystemRescue. [http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage) .

Before you repartition make sure you backup all your important files as partitioning will delete them. Then boot into the live distro and use Gparted to delete the linux partitions and then create one ext4 partition and a swap partition which should be twice the size of the amount of RAM you have ie 1024mb. Actually looking at the amount of RAM you have it might be an idea to source more perhaps another 512mb stick. If this prove too expensive or difficult then may I suggest you take a look at a really light distro called Crunchbang. It is really light on resources and uses apt-get etc. 
[http://crunchbang.org/](http://crunchbang.org/)

---

### Post by mick_ub_v11 on 2014-01-07
> **mörgæs said:**
> In a live boot you can delete sda 5, 6 and 7 (if you have a backup of all you need)
After that I suggest installing Lubuntu 13.10.


I burned a Lubuntu 13.10 DVD, deleted sda5, 6, 7.
Created EXT4 with 19GB and Swap with 1 GB.
Installed Lubuntu from DVD.  Everything goes well untill the end when the install CRASHES.

Tried twice.  Now what?

Thanks,

 - Mick

---

### Post by mörgæs on 2014-01-07
You don't need a DVD for Lubuntu. A CD will do.

Which graphics card do you use?

---

### Post by mastablasta on 2014-01-07
> **mick_ub_v11 said:**
> Everything goes well untill the end when the install CRASHES.


where exactly does it crash? does it leave a message? what is the last thing it does before it crashes?

i am asking since i recently couldn't do a dualboot. installer crashed 2 or 3 times on me. until i finllay saw i that it can't write GRUB to the disk (still haven't had time to figure out if it's HW or SW error). i changed the disk and instalelr went on fine. the point i am trying to make is look at the installer to see what it does when it crashes. it might give clues as to what went wrong.

then again i had Lubuntu installer crash on me as well but i didnt' have enough RAM for it. 

hmm... what GPU is there indeed? and how much ram does the GPU take? if it takes 256 MB or close it could be that is why installer is crashing.

other ubuntu distros that should work on your setup:
Xubuntu 
LXLE (lubuntu 12.04 with patches etc.)

another thing to try is mini.iso

---

### Post by mick_ub_v11 on 2014-01-07
Burned a CD-ROM for Lubuntu 13.10 (instead of another DVD).  Same result at end:  Just when the install is wrapping up at the end I get an "Installer Crash" message.  It says I will get a chance to submit a bug report, the installer collects data, then the screen goes black and the system hangs.

I'm not sure what other PC hardware info you need that is not listed at the top of the thread.

BTW:  I did at least repartition the disk to this:

/dev/sda
/dev/sda1  NTFS  60000 MB  WinXP
/dev/sda5  EXT4 / 18956 MB  Ubuntu 13.10  (it says Ubuntu even though it is Lubuntu that I installed)
/dev/sda6  Swap   1069 MB

I placed the Mount Point for EXT4 at "/".  Is that the best choice?  (That is the "root", correct?)
The Mount Point choices being:
/
/boot
/home
/tmp
/usr
/var
/srv
/opt
/usr/local


Bearing in mind that I originally had Ubuntu (either 13.04 or 12.04 ) installed on this machine with about 9GB for the EXT partition and 534 MB for the Swap running fine (well, fine enough, anyway).

So, after the CD-ROM Installer for Lubuntu 13.10 crashed, I went back and tried the Ubuntu 12.04 LTS install again.  Of course now with the 19GB EXT4 / 1GB Swap partitions set up.
As before, the 12.04 install results in a Display of 648x480 (4:3) where I cannot see the whole screen image.
The physical dimensions of the (standard) Dell screen display are:
17" Diagonal  (Approx:  13.25" W; 10.75" H)
 
So, again I install Ubuntu 13.10, deleting 12.04 in the process.
The install goes ok.  It says to restart the PC after install.  I click "Restart".  The CD-ROM kicks out of the drive, but the machine then hangs and I have to physically power off the PC and repower it again to boot.
The PC boots to Ubuntu 13.10.  The display is fine, but it does blink to black several times before settling down.
The display details are this:
1024x768 (4:3)  (The alternative not chosen is 800x600  (4:3)).

The Ubuntu 13.10 System Details are:
Memory:  495 Mib
Pentium 4; 3.0 GHz
OS:  32 bit
Disk:  18.5 GB
Graphics:  Gallium 0.4 on llvmpipe (LLVM 3.3, 128 bits)


So, I'm right back to square one.


Thanks all again,

Mick
 




Thanks,

 - Mick

---

### Post by mick_ub_v11 on 2014-01-07
I forgot the important part on the Ubuntu 13.10 install:
It works and in a good display setting, but in SLOW MOTION (i.e., not practical or useful).

Thanks,

 - Mick

---

### Post by mick_ub_v11 on 2014-01-07
I'm not sure if this is the graphics card or just the Display Driver:
NVIDIA GeForce FX5200  (Microsoft)
version 5.6.7.3
file version:  6.14.10.5673

Otherwise, how do I figure out what the graphics card is?

Thanks,

 - Mick

---

### Post by mörgæs on 2014-01-07
Nvidia screen cards often need either the nomodeset [boot option]("https://help.ubuntu.com/community/BootOptions") or closed-source drivers. 
Are you able to install using the [alternate ISO]("https://help.ubuntu.com/community/Lubuntu/Alternate_ISO")?

---

### Post by efflandt on 2014-01-07
I have an 8300 at work from 2003 that is about to be retired (about time), although, it has been upgraded to 2 GB. The video card is Nvidia FX5200. I don't know if any proprietary nvidia drivers support that 10 year old card any more, so you may be stuck with the default nouveau driver. It might work best with a 12.04 version (maybe Lubuntu which is lighter). I know that graphics seemed to slow down in 12.10 with the nouveau driver even with a faster graphics card, but I don't know how 13.10 compares because I only have that on a laptop with nvidia GTX 765M (along with Intel graphics).

My old PC at home from 2004 with Athlon64 3200+ (2 GHz) w/2 GB RAM originally included FX5200 and I had to upgrade the psu to handle a faster video card (currently a legacy ATI Radeon X1300). It still has Ubuntu 10.04 on it, but 12.04 iso on USB stick seems to work fine on it, so I should upgrade it one of these days and give it to my grand nephew twins (they currently have Ubuntu based "Qimo for Kids" on a Pentium 550 MHz).

---

### Post by mastablasta on 2014-01-08
> **mick_ub_v11 said:**
> I forgot the important part on the Ubuntu 13.10 install:
It works and in a good display setting, but in SLOW MOTION (i.e., not practical or useful).

Thanks,

- Mick


now go to software center and find and install Lubuntu desktop.

reboot and before you sign in select lubuntu desktop instead of ubuntu/unity/gome whatever it says nowadays.

alternatively you can install only lxde and then add programs found in lubuntu.

nomodeset might be a good boot option to use but we'll see if it works without it first.

---

### Post by mick_ub_v11 on 2014-01-08
I created a Lubuntu Alternate ISO install CD.
The install starts up with a DOS appearance, asks "English", "US", and all that, and then hangs.

If I run from the CD, the graphics are fine and the speed is fine.
When I had Ubuntu (12.04 or 13.04, I forget now which) running (before trying to upgrade to Ubuntu 13.10) the graphics and speed were fine (or at least adequate).


If I install and run Ubuntu 12.04 LTS, the speed is fine but the graphics are out of whack (648x480).
If I install and run Ubuntu 13.04, it just hangs with a gray screen.
If I install and run Ubuntu 13.10, the graphics are fine and the speed is really slow.

If I install Lubuntu 13.10, the final step of the install crashes.

Thanks,

Mick

---

### Post by mörgæs on 2014-01-08
> **mick_ub_v11 said:**
> 
If I install and run Ubuntu 12.04 LTS, the speed is fine but the graphics are out of whack (648x480).
If I install and run Ubuntu 13.04, it just hangs with a gray screen.
If I install and run Ubuntu 13.10, the graphics are fine and the speed is really slow.

If I install Lubuntu 13.10, the final step of the install crashes.



else
   [INDENT]goto [#12]("http://ubuntuforums.org/showthread.php?t=2198045&page=2&p=12894638&viewfull=1#post12894638")[/INDENT]

---

