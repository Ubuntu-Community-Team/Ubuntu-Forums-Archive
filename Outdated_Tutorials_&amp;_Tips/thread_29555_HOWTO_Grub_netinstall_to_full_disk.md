---
title: "HOWTO: Grub netinstall to full disk"
date: 2005-04-24
forum: Outdated Tutorials &amp; Tips
---

### Post by Curufir on 2005-04-24
This is based on the work in these two threads:
[http://ubuntuforums.org/showthread.php?t=29358](http://ubuntuforums.org/showthread.php?t=29358)
[http://ubuntuforums.org/showthread.php?t=28948](http://ubuntuforums.org/showthread.php?t=28948)

Problem I found with their solution is that you can't give Ubuntu the full disk (Both of those HOWTOs require certain files to already be on the disk).

So here's a set of floppy disk images that do exactly the same thing without needing files on the disk.

Instructions:

Grab 5 1.44mb floppy disks.

Due to forum restrictions I've had to split these files into chunks (Please ignore the .zip extension, they're plain binary files). Reassemble them using 'cat <file.1> <file.2> > <file.img>' on *nix, on Windows the copy command can do the same thing (Can't remember the exact syntax).

Dump the disk images onto the floppy disks. If you use Windows then get Rawrite. If you use *nix then just 'dd if=<image name> of=/dev/fd0' for each disk.

Reboot, set BIOS to boot from floppy and boot from the disk you wrote boot.img to. Insert the other disks as requested.

Notes:

The initrd doesn't contain all the modules that the ubuntu CD has. As far as network support goes YMMV. In particular there are none of the restricted modules.

The GRUB on boot.img is hacked to allow composition of an initrd from separate files. DO NOT report bugs to the GRUB devs.

I repeat that these **ARE NOT ZIP FILES**. The forum forces uploaded files to have an extension, that's just the one I decided to use.

Todo:

If someone desperately needs more drivers I'll look into throwing together a more complete initrd and kernel.

md5sums:

74cd9c932866574fa76e8ef0d1887f9a  boot.img
0dc8cfd1d2daafceeec2cfb90eb0f7b6  disk1.img
5c0bd5586d75edf4846276ac8dcd14ca  disk2.img
49d9dcb1991064bf9a9076dad1209b9c  disk3.img
f35695e66f62d2bd3c50a9326e28c1a9  disk4.img

---

### Post by Curufir on 2005-04-24
Disks 1 and 2

---

### Post by Curufir on 2005-04-24
Disks 3 and 4

---

### Post by ed_agamemnon on 2005-04-24
Sweet!

I was just working on a solution myself using the windows ramdrive program to set up a virtual drive and copying the parts of (split with a DOS program called 'bisector') initrd.gz and linux over and then fooling GRUB into thinking that the ramdrive is (hd0)... didn't have much joy though :(

So happy that the problem's been solved :D


...


To answer your point about the windows copy command, well, it doesn't seem to be able to handle the files:

> 
C:\>dir *.zip
 Volume in drive C has no label.
 Volume Serial Number is E0EF-4AE0

 Directory of C:\

25/04/2005  02:50           737,280 boot.img.1.zip
25/04/2005  02:50           737,280 boot.img.2.zip
               2 File(s)      1,474,560 bytes
               0 Dir(s)   8,343,076,864 bytes free

C:\>copy boot.img.1.zip+boot.img.2.zip boot.img
boot.img.1.zip
boot.img.2.zip
        1 file(s) copied.

C:\>dir boot.img
 Volume in drive C has no label.
 Volume Serial Number is E0EF-4AE0

 Directory of C:\

25/04/2005  02:51            46,913 boot.img
               1 File(s)         46,913 bytes
               0 Dir(s)   8,343,027,712 bytes free

C:\>


As you can see, boot.img is only 45-odd kb large... which is odd!
 

-ed

---

### Post by Curufir on 2005-04-24
My apologies, I should have looked into the Windows syntax instead of just saying it was possible.

On Windows you need a /b flag to force copy into using binary mode.

Eg

copy /b boot.img.1.zip+boot.img.2.zip boot.img

---

### Post by theonewhoismany on 2005-04-27
hi disk one doesn't work for me. it only creates a 42k image file for me.  ](*,)


derr....i forgot the /b switch

---

### Post by arcilite on 2005-04-29
I tryed using the disks like they are described and i get a kernel panic. Above the final line it is griping about a bad entry in directory #434 and 353 saying that it is small than minimal.

---

### Post by Curufir on 2005-04-30
Well there is nothing wrong with those images (Just downloaded them to check).

You've either got some bad floppies (Sounds likely with that error) or you've messed up putting the images back together.

***

On a different note I should have called this thread something different. "Ubuntu netinstall from floppies" is much more explanatory.

---

### Post by jr_G-man on 2005-08-14
Just followed your instructions last night and I have a brand new Ubuntu system installed on my system with no CD drive.  Thanks very much for your work.

---

### Post by Dreamglider on 2005-10-05
new to linux here, could someone make this install Ubuntu 5.10 by any chance ?
anyways, i have tried some ways to get Ubuntu on my laptop  but in vain, since i cannot boot from usb and my cd/dvd drive is totaly busted but this seems to be working fine :) it&#180;s now installing the base system,.. it just rebooted downloading packages now :) seems to be working nice thanks alot :)
Keep up the nice work, this one did indeed work with out a hazle and nice to see that the floppys now install 5.10 :) thanks mate.

---

### Post by Hex on 2006-01-04
I have a problem loading drivers for my PCMCIA card. The Debian [net-drivers.img]("http://ftp.egr.msu.edu/debian/dists/sarge/main/installer-i386/current//images/floppy/net-drivers.img") has the needed drivers, but I am not sure how to load it during install (Debian install has that option).

Also, I don't see the option to enter local IP, DNS and gateway, but that may be due to the fact that I can't load the drivers for my PCMCIA card.

Help here please!

p.s. Wonderful job on the installer!

---

### Post by n0manarmy on 2006-02-10
I've just started messing with this entire setup provided by this thread and I've got a couple questions.

First off, my laptop. I've got an external floppy and no CD-Rom so i have to use a floppy option, no other choice.

When i use the current floppy setup i can only get 5.04, i can't get breezy (5.10)

Is there a way to redirect the mirror selection to download the latest version of ubuntu instead of 5.04?

Follow up question, how would i redirect the mirror if i wanted to install Kubuntu instead of ubuntu, kde would be better than gnome (for my preference.)

---

### Post by martypants on 2006-06-07
Very nice solution...  Many thanks...

Could somebody please do the same for Dapper Drake???  This would be even sweeter...

I've used your solution and then upgraded to Dapper...  Which works fine...

---

### Post by trash on 2006-06-12
When i try to cat the img's all i get is garbled text and the process never ends. Am i missing something on a clean install of Xubuntu or is there another way to join the files?

EDIT:
never mind, it was the double >> that threw me off

---

### Post by moedje on 2006-07-14
Using a Portege R100 with no CD. Had TEAC USB CD but could not boot off it. Been trying different solutions all morning to get Ubuntu to install, your solution was the first one I was able to get to work, thanks for all the work. :KS

---

### Post by Technosites on 2006-07-31
Hi,
Thanks for all the hard work but I had one problem:
I burn all the floppys, and boot from the boot disk. It loads the grub, i star install. It propmts for the first disk, i put it in, it works away but then it comes up with Error 16: Inconsistant File type

What does that mean and how can i get it to work?
Many Thanks,
Technosites

---

### Post by DrThodt on 2006-08-06
I also got the error 16, started over and it vanished (same disks). The more odd error I get is that once the disks have fully extracted and installation begins, I'm prompted for language and country, then it downloads the required setup files, the asks me for language and country again, and again, and again and so forth. endless loop. Any ideas?

---

### Post by gonzalezmaur on 2006-09-18
This worked out great for me.  I got it installed and running.  I did have one little problem.

when I was trying to put the images together using windows i used the command

copy /b ..... and then I tried to put it to a:\ but it kept saying there was not enough space available.  This is because windows formats disks at 1.38mb not 1.44.#-o 

So after i put my images together I went and go a program called DiskWrite.  it's easy to find just google it.  After this I got my floppies and the install went flawless.=D>

---

### Post by socalboomer on 2006-09-29
the copy /b is only to combine the two files into a single image file so you can blow that onto the floppy.

So - copy /b file1+file2 destinationfile for each disk's imagefiles

THEN use rawrite to blow the destinationfile onto each floppy

HOpe that makes sense.

---

### Post by Airais on 2006-10-13
um okay make the disk NOW WHAT the first disk just brings up a promt (now what am I suposed to do)

---

### Post by grabula on 2006-12-12
Everything work fine, but how to change this in order to install Ubuntu 6.10 (Edgy Eft)?

---

### Post by Niels Engdahl Jensen on 2007-12-13
Dear Curufir
I have tryed to install Ubuntu the way you described here.
I made the disks in Windows and they work fine and it finds the router ok.
But it can't find the Release file on any of the mirrors.
I dont think I am behind a mirror, but I have a Linksys router between the PC and the Motorola kabel-modem and the router gives ip-addresses for the PC's.
Is this way obsolete now in december 2007? or what is wrong?
Can it be used for newer releases?

---

### Post by Niels Engdahl Jensen on 2007-12-13
ttt

---

### Post by supernova_hq on 2008-01-03
I got the boot disk made, but when I booted it, all i got was:

GRUB

with a blinking cursor, no keyboard input does anything (can't even get letters to show up) and it never asks for anything.

My computer does have a CD-Rom, but the BIOS will not boot off of it. I've tried the sbm thing, but i can't even get that to start (Bad SBMK!). 

Any help would be greatly appreciated. Thanks.

---

### Post by Tyrmatt on 2008-06-05
I hate to pull this bit of threadomancy here but this method has gotten me closer to installing a new OS on a trashed OS Portege with nothing but a USB floppy drive.
Is it possible to upgrade this to handle later releases as the current set are obsolete and no longer hosted on the archive. 
Even better, if it could be turned into a Xubuntu installer?
Much appreciated.

---

### Post by hca on 2008-12-01
I agree!!
I successfully made the 5 floppies. They worked on my old Dell laptop up until the installation process gave the following error message : (my translation from Danish to English)
"The indicated Ubuntu-archive mirror is either not accessible or does not contain a valid "Release" file. Please try an other archive mirror." - I tried a handful mirrors with other European messages than my own, but all with the same negative result.

Maybe someone could tell how to edit the flopies to point to an existing archive with a good release file.

> **Tyrmatt said:**
> I hate to pull this bit of threadomancy here but this method has gotten me closer to installing a new OS on a trashed OS Portege with nothing but a USB floppy drive.
Is it possible to upgrade this to handle later releases as the current set are obsolete and no longer hosted on the archive. 
Even better, if it could be turned into a Xubuntu installer?
Much appreciated.

---

### Post by hca on 2008-12-01
I agree!!
I successfully made the 5 floppies. They worked on my old Dell laptop up until the installation process gave the following error message : (my translation from Danish to English)
"The indicated Ubuntu-archive mirror is either not accessible or does not contain a valid "Release" file. Please try an other archive mirror." - I tried a handful mirrors with other European messages than my own, but all with the same negative result.

Maybe someone could tell how to edit the floppies to point to an existing archive with a good release file.

> **Tyrmatt said:**
> I hate to pull this bit of threadomancy here but this method has gotten me closer to installing a new OS on a trashed OS Portege with nothing but a USB floppy drive.
Is it possible to upgrade this to handle later releases as the current set are obsolete and no longer hosted on the archive. 
Even better, if it could be turned into a Xubuntu installer?
Much appreciated.

---

