---
title: "Script to comine DSL, Puppy, GParted into one CD"
date: 2008-03-07
forum: Other OS Talk
---

### Post by maybeway36 on 2008-03-07
This is a shell script designed to build a multiboot CD image containing many different Linux distributions and/or utilities.

The script used to be on this post, but it has since moved to [http://multicd.tuxfamily.org]("http://multicd.tuxfamily.org"). Check it out!

---

### Post by Bungo Pony on 2008-03-07
Would I easily be able to replace Puppy with TinyMe? If so, that would be incredibly useful.

---

### Post by maybeway36 on 2008-03-07
I will check that out. It shouldn't be too hard to implement.

---

### Post by maybeway36 on 2008-03-08
Version 1.1 is now released, with TinyMe support. Check out the original post for the updated script.

---

### Post by maybeway36 on 2008-03-23
Version 1.3 is out now, which lets you add more things onto the ISO image with includes. If you want to add more to the bottom of the isolinux,cfg in the finished image, put your additions in includes/boot/isolinux/footer.cfg.

---

### Post by ruibernardo on 2008-03-23
Thanks maybeway,

it worked with just very well. Just tried it with dsl, gparted. I'm going to try with puppy and slax later too. It's useful to carry a cd like this and rebuilding it on-the-fly. Great!

Id like to add the network "mini.iso" of Ubuntu and the Debian in it too, but I would like to know if this would work on USB? 

I'm creating a USB installer with the mini.iso to boot mini.iso and to be able to change the preseed files just changing preseed files, and I'm using USB with a ext2 partition and extlinux to boot. So USB would fit me just fine :) To have DSL and gparted with a mini.iso or an alternate.iso, all in the same ISO/USB would be very good to install Ubuntu or Debian on other computers.

Anyway, thanks for the script :)

---

### Post by maybeway36 on 2008-03-25
That's a great idea! I've put the mini.isos on multiboot CDs before, but I haven't worked them into this script yet. I'll start working on it soon.
I'm not quite sure how to do USB, seeing as none of my computers will boot from it. :/

---

### Post by maybeway36 on 2008-03-25
I just put up version 1.4, which lets you use the mini.isos from Ubuntu and Debian.
Gutsy, Hardy, Etch, Lenny and sid should all work, but you can only put one version of Ubuntu and one version of Debian on the CD (this may change later.)
The Ubuntu mini.iso is available at:
[http://archive.ubuntu.com/ubuntu/dists/](http://archive.ubuntu.com/ubuntu/dists/)*codename*/main/installer-i386/current/images/netboot/mini.iso
while the Debian one is at:
[http://ftp.us.debian.org/debian/dists/](http://ftp.us.debian.org/debian/dists/)*codename*/main/installer-i386/current/images/netboot/mini.iso

---

### Post by maybeway36 on 2008-03-30
Version 1.5 has been released, with support for adding Fedora 9. Grab this image and save it as fedora-boot.iso:
[ftp://mirrors.kernel.org/fedora/releases/test/9-Beta/Fedora/i386/iso/Fedora-9-Beta-i386-netinst.iso]("ftp://mirrors.kernel.org/fedora/releases/test/9-Beta/Fedora/i386/iso/Fedora-9-Beta-i386-netinst.iso") (114 MB)

---

### Post by smartboyathome on 2008-03-30
Would it be possible to use this to combine Ubuntu, Xubuntu, and Kubuntu ISOs into one like what looks like is being done with DSL, Puppy, and GParted?

---

### Post by maybeway36 on 2008-03-30
Those ISOs use squashfs files in the same places, so they conflict with each other. It might be possible with the alternate CDs, but I'm not quite sure how to pull it off.

ADMINS: Could you change the thread title to "Script to comine DSL, Puppy, Slax, and more into one CD" ? I've improved the script since my first post.

---

### Post by az on 2008-03-31
> **maybeway36 said:**
> Those ISOs use squashfs files in the same places, so they conflict with each other. It might be possible with the alternate CDs, but I'm not quite sure how to pull it off.

ADMINS: Could you change the thread title to "Script to comine DSL, Puppy, Slax, and more into one CD" ? I've improved the script since my first post.

In Casper, the filesystem.sqashfs is the only file that the Ubuntu live component (Casper) will look at.  It does have an offset value.  That means that you can cat together any number of the actual filesystem in squashfs form into one big filesystem.squashfs file.  You tell your bootloader (isolinux, syslinux of extlinux) what offset of the file is the actual squashfs filesystem for the OS you want to boot.  They all use the same kernel.

The problem is that some filesystems cannot handle really big files.  I think isofs has a max value of 4 GB.  

If you are booting from usb, you don't need an iso filesystem.  You can actually use ext2 (extlinux instead of isolinux) and benefit from large files and relative symlinks to make your bootable media.  

[https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

---

### Post by maybeway36 on 2008-03-31
How would tyou tell the bootloader what offset to use? Is it somewhere in APPEND?
I suppose Ubuntu+Kubuntu+Xubuntu would only be 2100 MB, which would be good for a DVD. This would probably be a seperate project if I attempt it, though.

---

### Post by az on 2008-04-01
> **maybeway36 said:**
> How would tyou tell the bootloader what offset to use? Is it somewhere in APPEND?
I suppose Ubuntu+Kubuntu+Xubuntu would only be 2100 MB, which would be good for a DVD. This would probably be a seperate project if I attempt it, though.

I made a mistake.  What I described does not apply to the sqashfs filsesystem file, but to the iso image.  From the casper manpage:

live-media-offset=BYTES
              This  way you could tell casper that your image starts at offset
              BYTES in the above  specified  or  autodiscovered  device,  this
              could  be  useful  to  hide  the debian-live iso or image inside
              another iso or image, to create "clean" images.

I suppose it would work the same way.  Yes, it is a boot option you append to the kernel line in isolinux/syslinux/extlinux.

---

### Post by maybeway36 on 2008-04-01
Support for the very small [SliTaz]("http://www.slitaz.org/en/") has been added with version 1.6. Thanks to Distrowatch for helping me find out about this neat distribution.

---

### Post by DJiNN on 2008-04-06
Many thanks for a great script maybeway36. :)  But i'm having trouble getting it to complete for some reason. It always seems to stop when it gets to "Downloading Syslinux". ??  Any ideas as to why that is?

I've also been looking around on the Net for something to put several distro ISO's onto a "Bootable" DVD...... nothing so far. Anything like that on your "todo list"? :)

---

### Post by maybeway36 on 2008-04-06
In the next version of the script,  I'll have it prefer the installed syslinux package, if present. This way, if the SYSLINUX download doesn't work, you can just install "syslinux" thorugh Synaptic, aptitude or apt-get and try again.

---

### Post by maybeway36 on 2008-04-06
The new version 1.6.1 lets you get around downloading SYSLINUX by installing the package on your computer:
```
sudo apt-get install syslinux
```
I probably won't be adding support for big ISOs like the Ubuntu live CD anytime soon, since I don't have a DVD burner. I think you can still burn the ISO image from this script onto a DVD, but I'm not sure.

---

### Post by DJiNN on 2008-04-06
> **maybeway36 said:**
> The new version 1.6.1 lets you get around downloading SYSLINUX by installing the package on your computer:
```
sudo apt-get install syslinux
```I probably won't be adding support for big ISOs like the Ubuntu live CD anytime soon, since I don't have a DVD burner. I think you can still burn the ISO image from this script onto a DVD, but I'm not sure.

Thanks for adding that. I'll give it a try later on tonight if possible.  Have you ever thought of adding "SysRescueCD" to the list? It's just as good as GParted (if not better), works superbly, and would be a great addition to the excellent apps that you have already chosen. :)

Personally i'm not too fussed about the larger ISO's as i tend to use the smaller ones more foten anyway, and just to be able to get them all on one disk is great. :)

Well done anyway, on a great script, and i'll let you know how it goes.

---

### Post by smartboyathome on 2008-04-06
Would you consider supporting Feather Linux? Also, if you have the RAM, a good way to test ISOs is with Virtualbox or QEMU, eliminating the need to burn a CD.

---

### Post by maybeway36 on 2008-04-06
I usually test my CDs with Qemu (or VirtualBox if Qemu is too slow.) I'm not including large ISO images in the combo script mostly because I don't use them all that often.
I might add SystemRescueCD and/or Feather soon, when I have some spare time. (The reason I included the plain GParted live CD for partitioning is its small size - 50MB.)

---

### Post by DJiNN on 2008-04-07
> **maybeway36 said:**
> I usually test my CDs with Qemu (or VirtualBox if Qemu is too slow.) I'm not including large ISO images in the combo script mostly because I don't use them all that often.
I might add SystemRescueCD and/or Feather soon, when I have some spare time. (The reason I included the plain GParted live CD for partitioning is its small size - 50MB.)

Hi maybeway36, just wanted to let you know that i ran the new version of the script and it works great. Love what you've created there, and i know it probably takes a lot of time to work on it, but i do hope that you continue to do so.

SystemRescueCD is a very useful tool, and could possibly  replace Gparted because it has Gparted incorporated into it, and a lot more besides. When nothing else would sort out my partitions, SysRescue did the job just fine.  :)

BTW, the link in your sig for the "Linux Vault".... is that something that you have put together yourself? It's a great idea and i hope that it takes off...... having a lot of Linux info in one place makes it a lot easier & quicker to find what you're after.

---

### Post by smartboyathome on 2008-04-07
I have got the MultiBuntu DVD mostly made, but I I can't seem to get past a bug. For some reason, I can't get syslinux to stay up, it comes up for a second, then disapears again and boots up to the default selection (Ubuntu Live). It works similar to how you made this script (thanks for it! it helped me a lot in learning how to combine it), but it has some differences. I may release a pre-alpha image tarball.

---

### Post by maybeway36 on 2008-04-07
The Linux Vault is something I found on Digg. I put the x11vnc tutorial there so it's easy to update and add on to.

---

### Post by maybeway36 on 2008-04-07
smartboyathome: I just noticed your post about the MultiBuntu DVD you're making. Check to make sure your isolinux.cfg includes the line "PROMPT 1". I made a CD once where I forgot that, and it did the same thing (booting to the default.)

---

### Post by smartboyathome on 2008-04-07
Thanks, that worked, but now I don't know how to redirect the kernel to the renamed squashfs files.

---

### Post by maybeway36 on 2008-04-08
I just released version 1.7, with SystemRescueCd support. Thanks DJiNN for recommending it; I'll use it instead of GParted from now on.

---

### Post by smartboyathome on 2008-04-08
How about incorperating the Arch Linux CD? :) Good job on the script.

---

### Post by DJiNN on 2008-04-08
> **maybeway36 said:**
> I just released version 1.7, with SystemRescueCd support. Thanks DJiNN for recommending it; I'll use it instead of GParted from now on.

That's great, and thanks once again for such a great script. It's a hard choice between Gparted & SysRescueCD, because they're both great, but SysRescueCD has GParted on it already, plus some other really great tools for partitioning and disk tools etc..... a really useful tool.

---

### Post by maybeway36 on 2008-04-21
A new version is out now. Version 1.8 has some general bugfixes and adds DBAN support. Noting too exciting, I suppose.

---

### Post by maybeway36 on 2008-05-06
I posted a new version. Nothing too exciting, just cleaned up the code a bit (and Balder is no longer included by default.)

---

### Post by DJiNN on 2008-05-07
Nice going maybeway36 - Good to see that you're still working on this great script. I'm just about to give it another go with some newer versions of the current included distros etc. Out of interest, why did you remove Balder? I've never even heard of Balder, but think that the ability to boot into some kind of DOS would be pretty cool. 

Thanks once again anyway, for a great script, and for continuing to update & improve. I'm sure that many people are using it even if they're not always vocal about it.  :)

---

### Post by maybeway36 on 2008-05-07
You now include Balder like you include the ohter systems - download balder10.img from finnix.org/Balder, and save it as balder.img in the multicd folder. I mostly did this to make it more coherent, but maybe since it's so small it should be downloaded during the building process, like it was before.

---

### Post by maybeway36 on 2008-05-09
Version 2.0 is out. This version goes back to downloading Balder during the building process. However, if you want to not include either Balder or Memtest, you can use command line options! :D See the first post for details.
There are also two new boot options for Puppy: root prompt and don't load to ram. These were always available in Puppy, but I forgot to put them in the menu until now.

---

### Post by maybeway36 on 2008-05-23
New version 2.1 is out! Support for Debian Live / live-helper was added, as well as Feather Linux support.

---

### Post by K.Mandla on 2008-05-23
Moved to Other OS Talk.

---

### Post by K.Mandla on 2008-05-23
Moved to Other OS Talk.

---

### Post by Fred_E _krugar on 2008-05-24
I think you missed one of the best tools that has saved me A couple of times



SuperGRUB.


Could you add that??

---

### Post by DJiNN on 2008-05-25
+1 for SuperGrub. Wonderful, extremely helpful and very very small. :)

---

### Post by Caraibes on 2008-05-25
That sounds like a lot of fun !!!

-Where can I download this iso ?

---

### Post by maybeway36 on 2008-05-25
I can't distribute an ISO for three reasons:
1. Of all the distros you can combine, you can only choose some of them to keep it on a single CD,
2. I would have to find all the source code (big hassle!) and
3. I don't have any hosting space big enough.
If you follow the instructions in the first post, it will make an ISO for you (install "genisoimage" first.)

P.S. I will probably add Super Grub Disk next time I update.

---

### Post by maybeway36 on 2008-05-30
I just posted version 2.2, a small update with Super Grub Disk support (thanks Fred_E _krugar!)

---

### Post by Fred_E _krugar on 2008-05-30
Hey I am just a noob and I cant count how many time that SuperGrub has saved me from a total meltdown lol

---

### Post by ciencio on 2008-05-31
Hello, it sounds to be a great job the one you are doing here.
I wondered if it was possible to add support for AntiX, a minidistro addressed to old computers based on Mepis.
In the mean time I will give your piece of work a try... it seems to be exactly what I was looking for.

Bye

Ciencio

---

### Post by maybeway36 on 2008-06-07
Version 2.3 is out. Support for antiX has been added. I also added support for GRUB4DOS, a GRUB-like bootloader with more features, although it just goes to the command line (since there's no menu.lst on my CD) and doesn't have the automatic options like Super Grub Disk does.

---

### Post by anticapitalista on 2008-06-08
Thanks for this script. A wonderful idea.

A request for Wolvix-cub to be added.

---

### Post by maybeway36 on 2008-06-17
Version 2.4 is out. Wolvix-cub support has been added, and the command-line options were changed a bit (including a new "verbose" option.)

---

### Post by maybeway36 on 2008-06-20
I just posted version 2.5, which adds the option of including ANY floppy disk image that you want. Just give it the extension ".mcd.img" and put it in the same folder as the script.

---

### Post by maybeway36 on 2008-06-30
v2.6, out now, lets you add additional Slax modules. [(Here are mine.)]("http://www.slax.org/modules.php?author=7297")

---

### Post by smartboyathome on 2008-07-01
> **maybeway36 said:**
> v2.6, out now, lets you add additional Slax modules. [(Here are mine.)]("http://www.slax.org/modules.php?author=7297")

What about delete/replace modules? I know I would love this if I could replace KDE with something like XFCE or LXDE (the latter I would create modules for).

---

### Post by dvader on 2008-07-02
Tried the script  and it worked OK .. Had a few little glitches , but was able to try them out using qemu  as mentioned in a previous 

Thanks maybeway36


Is it possible to add a distro  ... a blank template so one can insert what ever iso file they want


Dvader

Spelling corrected

---

### Post by VCSkier on 2008-07-09
This is awesome!  I've spent the last two days trying to figure out how to do this on my own.  Why didn't I find this earlier?  To take this another direction, would it be possible to do something like this, but include utilities for non-windows systems?  I was thinking something with [Trinity Rescue Kit]("http://distrowatch.com/table.php?distribution=trinity") and the [Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").  I ask because dual-booting with Vista seems to sometimes be problematic, and so having the recovery disc available would be helpful when installing Ubuntu on new users' systems if things go bad.  Not to mention, Trinity is simply a great tool for showing off the power of linux to your Windows friends.  Thanks for the great script; I'll be building my Puppy/SystemRescueCD/SuperGrubDisk/DBAN/Ubuntu-mini.iso momentarily.  :)

---

### Post by maybeway36 on 2008-07-09
> **smartboyathome said:**
> What about delete/replace modules? I know I would love this if I could replace KDE with something like XFCE or LXDE (the latter I would create modules for).
You could do this by editing the script before running it. Find the block of code:
```
if [ $SISO = 1 ];then
 echo "Copying Slax..."
 if [ -d slax ];then
  true
 else
  mkdir slax
 fi
 if grep -q `pwd`/slax /etc/mtab ; then
  umount slax
 fi
 mount -o loop slax.iso slax/
 cp -R slax/slax multicd/slax
 mkdir -p multicd/boot/slax
 cp slax/boot/vmlinuz multicd/boot/slax/vmlinuz
 cp slax/boot/initrd.gz multicd/boot/slax/initrd.gz
 umount slax
 rmdir slax
fi
```
Add a line after "rmdir slax" but before "fi" that reads something like:
```
rm multicd/slax/base/003-desktop.lzm multicd/slax/base/004-kdeapps.lzm multicd/slax/base/005-koffice.lzm
```
The modules that come with the default slax are: 001-core.lzm, 002-xorg.lzm, 003-desktop.lzm, 004-kdeapps.lzm, 005-koffice.lzm, and 006-devel.lzm. (You can get rid of all of those except core if you want it to be really small.)
I was thinking about adding a feature to tell the script to remove the modules via a command-line argument, but I'm not sure how this would work quite yet.

> **dvader said:**
> Is it possible to add a distro  ... a blank template so one can insert what ever iso file they want


Dvader

Spelling corrected
The hard part with ISOs is that the Linux kernel and initrd, the main files needed for booting, are in different places, so the script wouldn't know where to find them.

> **VCSkier said:**
> This is awesome!  I've spent the last two days trying to figure out how to do this on my own.  Why didn't I find this earlier?  To take this another direction, would it be possible to do something like this, but include utilities for non-windows systems?  I was thinking something with [Trinity Rescue Kit]("http://distrowatch.com/table.php?distribution=trinity") and the [Vista Recovery Disc]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").  I ask because dual-booting with Vista seems to sometimes be problematic, and so having the recovery disc available would be helpful when installing Ubuntu on new users' systems if things go bad.  Not to mention, Trinity is simply a great tool for showing off the power of linux to your Windows friends.  Thanks for the great script; I'll be building my Puppy/SystemRescueCD/SuperGrubDisk/DBAN/Ubuntu-mini.iso momentarily.  :)
I will look into adding one of those. It certainly can't be too hard to add support for one of them.

Thanks for all the comments. If it weren't for all the users making suggestions, I would probably only have 5 or 6 distros supported. :)

---

### Post by maybeway36 on 2008-07-11
I finished it quicker than I had expected, and version 2.7 is now out. The changes are:
[LIST]
[*]bug fixes relating to including Slax modules and floppy images ([thanks to the help I got on the Programming Talk forum]("http://ubuntuforums.org/showthread.php?t=855678"))
[*]added Trinity Rescue Kit support!
[*]TRK, as well as antiX and GParted, now have submenus
[*]because of some code simplifications, Super Grub Disk is now treated like an ordinary floppy image. Rename it from "sgd.img" to "SuperGrubDisk.img" if you use it.
[/LIST]
Known bug: you can't use spaces in disk image names - the script will think it's multiple files and try and fail to copy files that don't exist.

---

### Post by MethodOne on 2008-07-13
Could you add support for the openSUSE "NET", Mandriva boot.iso, and Arch FTP images?

---

### Post by ryaxnb on 2008-07-15
Question: Could I add a smart boot mgr floppy img, and then have smart look for a ISO image or set of folders and boot another, non-supported OS? This would be really handy.

---

### Post by maybeway36 on 2008-07-16
I don't think Smart BootManager can support booting ISO images. I tried to use GRUB4DOS to boot an ISO image, but it didn't work (at least in QEMU.)

---

### Post by maybeway36 on 2008-07-16
Version 2.8 is out. openSUSE and Mandriva installers are supported, and you can put your own files on the CD by putting them in a directory called "includes."

---

### Post by maybeway36 on 2008-07-25
I just posted version 2.9, which adds Arch Linux support (the FTP and CORE CDs both work) and fixes another LZM bug.
A neat tip: you can add the FreeBSD installer too. Just download [http://downloads.sourceforge.net/sourceforge/lubi/freebsd-7.0.img.gz](http://downloads.sourceforge.net/sourceforge/lubi/freebsd-7.0.img.gz) and rename it to something like "FreeBSD.img". The script will treat it like a regular disk image and include it in the menu.

---

### Post by smartboyathome on 2008-07-25
Nice work Maybeway! I wouldn't have thought this project could advance so much. Maybe you should set up an actual project for this on Launchpad. :D

---

### Post by maybeway36 on 2008-07-25
I'll look into it. Sort of reminds me of what happened with origami when you mention it :)
I'm putting out a quick update now, 2.9.1. (I forgot a dollar sign and introduced a bug.)

---

### Post by Tamil on 2008-07-28
Thanks. Why don't you add links ([SystemRescueCd](http://www.sysresccd.org/))?

---

### Post by maybeway36 on 2008-07-28
That's a good idea, thanks. :)

---

### Post by Tamil on 2008-07-29
Can you add [Offline NT Password & Registry Editor](http://home.eunet.no/pnordahl/ntpasswd/)?

---

### Post by maybeway36 on 2008-07-30
Version 3.0: The Offline NT Password & Registry Editor has been added, as well as the newest version of Parted Magic. In even bigger news, the multicd script will fron now on be hosted at [http://multicd.tuxfamily.org/]("http://multicd.tuxfamily.org/")! (I figured the forums weren't made for script hosting :p)

---

### Post by MethodOne on 2008-07-31
When version 3.0 of the script tries to extract the SYSLINUX 3.70 archive, I get the following error message:

```
Downloading SYSLINUX 3.63...
Unpacking and copying files...
cp: cannot stat `/tmp/syslinux-3.70/isolinux.bin': No such file or directory
```

isolinux.bin is found in the "core" directory of that archive.

---

### Post by maybeway36 on 2008-07-31
The problem was related to a change in SYSLINUX packaging and should be fixed with version 3.0.1 which is on the site now.

---

### Post by Tamil on 2008-07-31
Could you add [Ultimate Boot CD](http://www.ultimatebootcd.com/) & [BartPE](http://www.nu2.nu/pebuilder/)?

Got following error message when I try to run script.> ./multicd.sh: 234: Syntax error: word unexpected (expectiong "do")

---

### Post by maybeway36 on 2008-07-31
I can't reproduce the error. It might be because I'm using Debian lenny, but both /bin/bash and /bin/dash run v3.0.1 fine.
Ultimate Boot CD might be added in the future. BartPE probably won't be added soon, as I don't have a reference image to work off of (considering I don't use Windows.)

---

### Post by smartboyathome on 2008-08-01
One more: It says you may replace the Gentoo-based GParted Livecd, would you replace it with the [official one](http://gparted.sourceforge.net/download.php) instead? Thanks. :D

---

### Post by maybeway36 on 2008-08-02
Version 3.1 f the script is out, which adds support for Ultimate boot CD and everything in it. Now you can brag about your CD: "Haha, your Ultimate Boot CD only has 121 boot options? Mine has 130!" :p
> **smartboyathome said:**
> One more: It says you may replace the Gentoo-based GParted Livecd, would you replace it with the [official one](http://gparted.sourceforge.net/download.php) instead? Thanks. :D
I found the new CD about a week ago, which was why I labeled the Gentoo one as being depreciated. The new GParted Live is 91MB, so I personally prefer Parted Magic, but I will likely add the new GParted CD soon. (I can copy most of the code I used for Debian Live, so it shouldn't take long and should be in 3.2.)

---

### Post by MethodOne on 2008-08-04
When I try to use Trinity Rescue Kit, I get the following output:

```
**Trying to find TRK on your 1 CD-drive(s)**
**TRK not found on CD, checking harddisks and USB sticks (sleep 5 secs let them settle in)**
cat: /etc/trkhd: No suck file or directory
**Seems we didn't find anything yet.  Trying CD-drives once more**
/etc/mountcd.sh: line 108: SeachCd: command not found 
**Something's wrong in startup, dropping to a shell, stop booting**
**'use dmesg | more' to rerun your startup sequence and report the error on the forum**
**Also perform 'cat /proc/partitions' and 'cat /proc/sys/dev/cdrom/info'**
bash: dircolors: command not found
bash: locale: command not found
bash: tty: command not found
bash: head: command not found
```

Then it ends at a basic root shell.

---

### Post by maybeway36 on 2008-08-04
Try checking the md5sum of both the ISO and the CD you burned.
If they're both correct, it might be a problem with the script.
Normally, however, Trinity prompts you for a device name when it can't find itself, instead of dropping to a shell.

---

### Post by MethodOne on 2008-08-05
I tried running Trinity Rescue Kit by itself (not on a CD made with the script) and it worked.

---

### Post by maybeway36 on 2008-08-05
TRK runs just fine for me on my script-generated ISO. Are the MD5sums correct? That's the only thing I can think of.

---

### Post by maybeway36 on 2008-08-08
Version 3.2 is out now, which adds DeLi Linux support thanks to PsynoKhi0. Get it at: [ftp://downloads.tuxfamily.org/multicd/]("ftp://downloads.tuxfamily.org/multicd/")

---

### Post by tzepu on 2008-08-18
hi
first of all congrats for your work
i need your help with something
you added a lot of distros in you script, but i need more (actually i want the top 5 distro's livecd's combined with the 32 and 64 bit versions in one disk
can you do that?
actually i need a pendrive to put all this on (i found the program that does it, but the multiboot disk created with several creators(i will try your script too) just fails
thanks

---

### Post by tzepu on 2008-08-18
well i have some issues about it
i placed in the folder with multicd.sh several iso and  one .exe from grub ( all about 2.8Gb)
it builds the iso but it has just 1.8 Mb 
do i do something wrong ?
al the iso's are on your list, i did as it is explained on the script page, i just do not figure what is wrong in here

L.E.well i figured out about what is going on, it includes just this
"List of boot options that will be included:
Ultimate Boot CD
Damn Small Linux
Balder (FreeDOS)
Memtest86+and this even if i have about 10 iso files in there (all of them supported)

---

### Post by maybeway36 on 2008-08-18
Can you post the output of "ls" for your directory? I want to see what ISO names you are using.
As for adding new distros, I don't think I will be adding anything over 400MB for the most part. Other people are welcome to use the framework in my script to do so (in that case, please send the code to me so I can include it.)

P.S. I don't think you can combine Ubuntu and Linux Mint live CDs onto one DVD, because they use the same files in the same locations. I might be wrong, though.

---

### Post by smartboyathome on 2008-08-18
> **maybeway36 said:**
> Can you post the output of "ls" for your directory? I want to see what ISO names you are using.
As for adding new distros, I don't think I will be adding anything over 400MB for the most part. Other people are welcome to use the framework in my script to do so (in that case, please send the code to me so I can include it.)

P.S. I don't think you can combine Ubuntu and Linux Mint live CDs onto one DVD, because they use the same files in the same locations. I might be wrong, though.

You can't, it uses the exact same structure. Its like trying to combine Ubuntu, Kubuntu, and Xubuntu onto one DVD, very hard work. :(

---

### Post by maybeway36 on 2008-08-19
I just uploaded version 3.3, which removes support for the old GParted Live CD and adds support for the new one. Note that you can't use it with Debian Live, since they use the same framework.
Also, the Trinity Rescue Kit submenu now has the original splash screen. :)

---

### Post by tzepu on 2008-08-19
what do you mean by 'ls' ?
a am a newbie in this, so...

---

### Post by maybeway36 on 2008-08-19
Just go t the terminal, go to the script directory, type
```
ls
```
and copy/paste that here.

---

### Post by RedPandaFox on 2008-08-19
Wow, this sounds like a brilliant project! This could save me stacks of time, going through all my ISO Cd's trying to find what is after if I can put a few into one DVD.

Also, I was wondering, because I reformat all my HDDs every 6 months (including my XP HDD which I re-activate with same key by calling Microsoft) is it possible to build in a Windows OS with the script? If I use my key? I'm pritty much a newb but I know I can use the same key as long as its the same machine and only use the key one at a time (as I have been allowed to do this for a long time) 

Also is there a how-to for newbs on this? Or a Wiki? I think this is a wonderful idea and I want to try it out (but I'm at work right now anyway) and I want to read a bit more into it before I try it and, no doubt end up wasting a few DVDs before I get it working.

---

### Post by Tamil on 2008-08-20
Could you add [EASEUS Disk Copy 2.0](http://www.easeus.com/disk-copy/)?

---

### Post by maybeway36 on 2008-08-20
> **RedPandaFox said:**
> Wow, this sounds like a brilliant project! This could save me stacks of time, going through all my ISO Cd's trying to find what is after if I can put a few into one DVD.

Also, I was wondering, because I reformat all my HDDs every 6 months (including my XP HDD which I re-activate with same key by calling Microsoft) is it possible to build in a Windows OS with the script? If I use my key? I'm pritty much a newb but I know I can use the same key as long as its the same machine and only use the key one at a time (as I have been allowed to do this for a long time) 

Also is there a how-to for newbs on this? Or a Wiki? I think this is a wonderful idea and I want to try it out (but I'm at work right now anyway) and I want to read a bit more into it before I try it and, no doubt end up wasting a few DVDs before I get it working.

I really don't think it's possible to put Windows on the CD, because of how picky the installer is about the filesystem combined with the fact that I've never been able to boot the Windows installer with ISOLINUX.

There's sort of a howto at [http://multicd.tuxfamily.org/]("http://multicd.tuxfamily.org/"). It's pretty straightforward.

---

### Post by maybeway36 on 2008-08-22
Out now is version 3.4: with these changes:
*EASEUS Disk Copy 2.0 is now supported. (It was very easy to add - just copy two files!)
*A typo in the Mandriva code was fixed, so that works now.
*The DBAN menu option now boots directly to DBAN, without going through the boot: prompt. (If you want to use commands like *autonuke*, press ESC on the CD menu to pull up its boot: prompt and type the DBAN option to launch. Warning - many of them will erase your hard drive without asking!)
*Finally, with the new -c option, you can add an md5sum.txt file to the CD image (for checking integrity.)

---

### Post by Bungo Pony on 2008-08-23
Absolutely fantastic tool! (Yeah, I finally got to try it out.) I have a CD Wallet I take with me whenever I'm doing work on someone's computer. It's full with lots of Linux distros, CDs full of Windows utilities and OSes, etc. The wallet is full. This will make room for a couple more discs I need.

Thanks so much for creating and maintaining this script!

---

### Post by RedPandaFox on 2008-08-25
Is it possible to put the ISO's onto some other removable media, such as SD Card or USB flash drive using this script?

---

### Post by maybeway36 on 2008-08-26
> **RedPandaFox said:**
> Is it possible to put the ISO's onto some other removable media, such as SD Card or USB flash drive using this script?
It's not a feature right now, and I don't plan on implementing it because I usually boot from CD-RWs (most of my computer's won't boot from USB.)
Theoretically, it should be possible. You would need to use syslinux instead of isolinux and change the Slax options to allow resume, among other things.

---

### Post by anticapitalista on 2008-08-26
maybeway36

Could you change the antiX to point to newer versions (antiX-M7.5 and antiX-M7.5-base if it makes any difference)

Thanks for a great script.

---

### Post by maybeway36 on 2008-08-27
The new version 3.5 has these changes:
*When including a Debian Live ISO, almost all of the files will be copied. If you only want to copy over the essentials (*install* and *live*), run multicd.sh with the "condeb" option.
*If you have dialog installed, you can use a new portion of the script that lets you leave out certain modules from the official Slax release to save space. Run multicd.sh with the "modules" option.
*The options for antiX were updated for 7.5 (thanks anticapitalista!)

---

### Post by medic2000 on 2008-09-23
Can you add support for RIPLinux?

Great script by the way. I was getting sad when i burn a small .iso in an entire cd. Thanks so much!

---

### Post by wolfen69 on 2008-09-24
> **medic2000 said:**
> Can you add support for RIPLinux?

Great script by the way. I was getting sad when i burn a small .iso in an entire cd. Thanks so much!

cd's are .10 now. well worth it to me to pay 1 dollar to try out 10 distros even if i don't like them.

to me, it's not worth :wink:he effort to combine any 2 or more distros as i can only use 1 at a time anyway. it's not hard to just pop in the next cd. to each his/her own i guess. :wink:

---

### Post by kaiju on 2008-09-25
> **wolfen69 said:**
> cd's are .10 now [...]

for all we know, **medic2000** could be writing his/her posts sitting on an ice shelf on the antarctic. and i for one certainly wouldnt think cds costing .10 dollars (weather those are australian, canadian, hong kong, new zealand, singapore or even us dollars) to be a universal fact ;)

this is a great project, even if just for the fact that it might contribute to reducing the amount of cds bought, that will end up as junk plastic sooner or later anyway. not to mention that the idea is cool and useful at the same time. thanks, **maybeway36** :)

---

### Post by VCSkier on 2008-09-25
I find this project incredibly useful.  I like to be able to do recovery on-the-go for a number of reasons, and this keeps me from having to have 6 or 8 different cd's with me.  Sure, PartedMagic is my choice most of the time, what if it won't boot on whatever computer I'm using for some reason, or if someone needs the Windows MBR rewritten.  Particularly if I'm introducing someone to linux, or installing it on their computer, I need to be prepared for every possible situation, and this makes that easy.  Thanks maybeway36.

---

### Post by maybeway36 on 2008-10-03
The new version 3.6 supports RIPLinuX, grab it at [ftp://download.tuxfamily.org/multicd/multicd-3.6.sh]("ftp://download.tuxfamily.org/multicd/multicd-3.6.sh").

---

### Post by Bungo Pony on 2008-10-11
I found a problem...

With DSL on this multi-boot disk, you CANNOT do a frugal install.

---

### Post by maybeway36 on 2008-10-13
This problem arises from the DSL files being in a different location. Come to thing of it, I should put them in the same place as on the original disk; I forgot about DSL's install feature. (This is what I do with Puppy now so its install works.)

---

### Post by mrnaughty on 2008-11-23
I tried to run: sudo multicd-3.6.1.sh and I'm getting error:
sudo: multicd-3.6.1.sh: command not found

---

### Post by smartboyathome on 2008-11-23
> **mrnaughty said:**
> I tried to run: sudo **./**multicd-3.6.1.sh and I'm getting error:
sudo: multicd-3.6.1.sh: command not found

The bolded portion should fix it. :)

---

### Post by maybeway36 on 2008-11-24
If it doesn't, make sure the script is executable:
```
chmod +x multicd-3.6.1.sh
```

---

### Post by mrnaughty on 2008-11-24
Thank you for prompt help but:
-----------------------------------------------
mrnaughty@mrnaughty-desktop:~$ cd multicd
mrnaughty@mrnaughty-desktop:~/multicd$ ls
antiX-M7.5.iso                  multicd.sh.bak~
antiX-M7.5.iso.md5sum           multicd.sh.URL
archlinux-2008.06-ftp-i686.iso  openSUSE-11.0-NET-i386.iso
clonezilla-live-1.2.1-17.iso    pmagic-3.1.iso
dsl-4.4.10.iso                  puppy.iso
feather-0.7.5.iso               SimplyMEPIS-CD_7.0-rel_32.iso
flexxxpup v1.2 Nibiru.iso       SimplyMEPIS-CD_7.0-rel_32.md5sum
LinpusLite.iso                  slax-6.0.7.iso
mini_deb.iso                    slitaz-1.0.iso
mini.iso                        systemrescuecd-x86-1.1.2.iso
multicd-3.6.1.sh                TinyMe-2008.0.i586.iso
multicd-3.6.1.sh~               ubcd.iso
multicd-3.6.1.sh.gz             wolvix-cub-1.1.0.iso
multicd.iso                     wolvix-cub-1.1.0.iso.md5
multicd.sh
mrnaughty@mrnaughty-desktop:~/multicd$ chmod +x multicd.sh
mrnaughty@mrnaughty-desktop:~/multicd$ sudo ./multicd.sh
[sudo] password for mrnaughty: 
sudo: unable to execute ./multicd.sh: No such file or directory

---

### Post by mrnaughty on 2008-11-25
finally:
Continuing in 3 seconds - press Ctrl+C to cancel
Copying Ultimate Boot CD...
Copying DSL...
Copying Puppy...
Copying Feather Linux...
Copying SliTaz...
Copying Slax...
Copying Wolvix...
Copying Parted Magic...
Copying files from the SYSLINUX package installed on your computer...
Downloading memtest86+ 2.0.1 from memtest.org...
Downloading Balder from finnix.org...
Writing isolinux.cfg...
Building CD image...
mrnaughty@mrnaughty-desktop:~/multicd$ sudo ./multicd-3.6.1.sh
List of boot options that will be included:
Ultimate Boot CD
Damn Small Linux
Puppy Linux
Feather
SliTaz
Slax
Wolvix
Parted Magic
Debian netboot installer
Ubuntu netboot installer
Arch Linux
Balder (FreeDOS)
Memtest86+

I had to rename ISO file to names as in "sh" script. Right guys?

---

### Post by medic2000 on 2008-11-25
> **wolfen69 said:**
> cd's are .10 now. well worth it to me to pay 1 dollar to try out 10 distros even if i don't like them.

to me, it's not worth :wink:he effort to combine any 2 or more distros as i can only use 1 at a time anyway. it's not hard to just pop in the next cd. to each his/her own i guess. :wink:

The thing that make me sad is not the price though the price of cds'. It is about carrying so much cd or making cd pollution when they could fit into only one cd. I use different kind of small distors for different purposes. And i work on old to new many computers. For example PartedMagic has useful disk utilities and gparted also.But requires min 300mb of ram to run while the sole GpartedLive requires less ram.

And also some distros doesn't run on some machines.Sometimes DSL runs but Puppy not. And sometimes Puppy runs and DSl not.

For the last thing i need to say is the cds are here in Türkiye are not .10 :) They rather about .25 :)

---

### Post by maybeway36 on 2008-11-25
> **mrnaughty said:**
> finally:
Continuing in 3 seconds - press Ctrl+C to cancel
Copying Ultimate Boot CD...
Copying DSL...
Copying Puppy...
Copying Feather Linux...
Copying SliTaz...
Copying Slax...
Copying Wolvix...
Copying Parted Magic...
Copying files from the SYSLINUX package installed on your computer...
Downloading memtest86+ 2.0.1 from memtest.org...
Downloading Balder from finnix.org...
Writing isolinux.cfg...
Building CD image...
mrnaughty@mrnaughty-desktop:~/multicd$ sudo ./multicd-3.6.1.sh
List of boot options that will be included:
Ultimate Boot CD
Damn Small Linux
Puppy Linux
Feather
SliTaz
Slax
Wolvix
Parted Magic
Debian netboot installer
Ubuntu netboot installer
Arch Linux
Balder (FreeDOS)
Memtest86+

I had to rename ISO file to names as in "sh" script. Right guys?
Yep. That's the only way the script can find them :)

---

### Post by mrnaughty on 2008-11-25
Thanks to all!

---

### Post by maybeway36 on 2008-11-26
I just added support for [FreeDOS 1.0]("http://www.freedos.org") to the script. Either fdbasecd.iso or fdfullcd.iso should work. fdfullcd has lots of extra programs and comes with a live CD portion, while fdbasecd just has the essentials to install FreeDOS.

---

### Post by mrnaughty on 2008-12-02
Is t possible to add all or one of this:

1. G4L (Ghost 4 Linux)
2. PING (Partimage Is Not Ghost)
3. Clonezilla
 
Thank you.

---

### Post by greatscott on 2008-12-13
> **mrnaughty said:**
> Is t possible to add all or one of this:

1. G4L (Ghost 4 Linux)
2. PING (Partimage Is Not Ghost)
3. Clonezilla
 
Thank you.

I would like to know this also. It would be great to have Gparted and Clonezilla on the same CD.

---

### Post by maybeway36 on 2008-12-14
Version 3.8 is out. This adds PING support and fixes a few bugs. I'll look into Clonezilla for the next version.

---

### Post by greatscott on 2008-12-14
Take a look at post #3 of [this]("http://gparted-forum.surf4.info/viewtopic.php?id=4054") thread if you would like to know how to have both Gparted and Clonezilla on one CD. The problem is that Clonezilla gives weird warning messages in yellow when the live directory is different (I'm not sure if it is anything serious). But Gparted doesn't so you can change it and leave Clonezilla alone.

So here is an example of the isolinux.cfg with Clonezilla and Gparted.
```

***
label GParted Live
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL ^GParted Live (Default settings)
  # MENU PASSWD
  kernel /gparted/live/vmlinuz1
  append initrd=/gparted/live/initrd1.img live-media-path=gparted/live boot=live union=aufs    noswap vga=788 ip=frommedia
***
label Clonezilla live
  # MENU DEFAULT
  # MENU HIDE
  MENU LABEL ^Clonezilla live (Default settings, VGA 1024x768)
  # MENU PASSWD
  kernel /live/vmlinuz1
  append initrd=/live/initrd1.img boot=live union=aufs    ocs_live_run="ocs-live-general" ocs_live_extra_param="" ocs_live_keymap="" ocs_live_batch="no" ocs_lang="" vga=791 ip=frommedia nolocales

```


**Edit:**
Maybe [this]("http://ubuntuforums.org/showpost.php?p=5175091&postcount=27") can fix the yellow warning message if you decide to change live directory for Clonezilla.

---

### Post by maybeway36 on 2008-12-24
I just uploaded version 3.9, with Clonezilla support. It works with both GParted and Clonezilla on the same disc, by renaming the folders and passing a kernel option.

---

### Post by smartboyathome on 2008-12-25
**BUG REPORT:** cp: cannot stat `/tmp/syslinux-3.71/com32/meodules/chain.c32': No such file or directory

---

### Post by maybeway36 on 2008-12-26
Version 3.9.1 with the bug fixed:
[ftp://downloads.tuxfamily.org/multicd/multicd-3.9.1.sh](ftp://downloads.tuxfamily.org/multicd/multicd-3.9.1.sh)

---

### Post by maybeway36 on 2009-01-18
Version 4.0 is out! This adds a new feature: if you put floppy images in the "games" subfolder within the multicd directory, they will be included in a submenu instead of the regular menu. This way I can put all my favorite freeware DOS games onto the CD :)
Also, .imz files (gzip-compressed disk images) are now accepted as well as .img files.
[ftp://downloads.tuxfamily.org/multicd/multicd-4.0.sh](ftp://downloads.tuxfamily.org/multicd/multicd-4.0.sh)

---

### Post by kagashe on 2009-01-24
> **maybeway36 said:**
> It's not a feature right now, and I don't plan on implementing it because I usually boot from CD-RWs (most of my computer's won't boot from USB.)
Theoretically, it should be possible. You would need to use syslinux instead of isolinux and change the Slax options to allow resume, among other things.Could you please elaborate it further?

Assuming that syslinux and isolinux are basically same I tried the following:
I copied the contents of multicd.iso to FAT16 partition and renamed isolinux directory as syslinux and isolinux.cfg as syslinux.cfg.
I installed syslinux through 'sudo syslinux /dev/hdaX' and there was a file 
'ldlinux.sys' on /.

I made a grub entry to chainload the bootloader on hdaX and tried to boot but I am getting Boot error.

What should I do?

kagashe

---

### Post by maybeway36 on 2009-01-25
kagashe: I sorry I can't really help you further. I think many of the images would work just copying to USB, but yours sound like a SYSLINUX problem. There are guides online to help.

Also:
**[Version 4.1](http://multicd.tuxfamily.org/)** is out with support for NetbootCD (another project of mine.)

---

### Post by Phylum on 2009-02-05
This is a very cool script to accomplish something I've been trying to get working for ages.  I thank you for that.

However, I'm trying to load other OS' not listed in your script.  I have a series of [bootable] ISO's taken from CD's DVD's & websites.
[INDENT]Gentoo (Live CD)
Linux Mint (Full)
Ubuntu (Full)
BackTrack 3
GParted (which is supported)
RIPLinuX
Offline NT Password & Registry Editor (linux variant)
Maxtor MaxBlast 5 - Hard Drive utility (not a must but useful)[/INDENT]

Instead of carrying 8 CD's, I'd like to create a multi-boot DVD that gives me the option of choosing which tool/OS I wish to boot into.  I've scoured the net and found lots of outdated information some of which doesn't even work [anymore(?)].  I even purchased MagicISO with the expectation it would accomplish this, but its not born any fruit.

I'm not desperate but I just need to know if its possible, and if not, why.  I would **_GREATLY_** appreciate any useful/constructive comments and/or suggestions on this topic.  If you can refer me to another link/thread that discusses this, thats even better.
I'm not looking to be spoonfed, I just need some guidance.  I don't mind getting my hands dirty, but I'm not quite ready to edit 134 files in each distro to make sure it boots!

J

---

### Post by smartboyathome on 2009-02-05
Linux Mint and Ubuntu cannot exist on the same CD as far as I know, since both use the same hardlinked underlying arcitecture. No Ubuntu derivatives can exist alongside another Ubuntu derivative because of this.

---

### Post by Phylum on 2009-02-05
Does this mean everyone else, aside from Ubuntu & Linux Mint, will play nicely?

---

### Post by smartboyathome on 2009-02-05
> **Phylum said:**
> Does this mean everyone else, aside from Ubuntu & Linux Mint, will play nicely?

Should, but no guarantees since they could be using files which overlap. I suggest taking a look at the script to see how it works before you try this. ;)

---

### Post by maybeway36 on 2009-02-05
If you want Ubuntu and Linux Mint on the same disc, you need to edit the initrd for one of them. [jabagawee's post](http://ubuntuforums.org/showthread.php?t=703905&page=3) can probably help you with this. I'm planning to support the Ubuntu and Linux Mint live CDs in the script soon, but not both on the same disc.

---

### Post by maybeway36 on 2009-02-07
I posted version 4.2 which can support Ubuntu or Linux Mint. (You need a DVD if you want anything else, of course.) Next I plan to add another favorite of mine, Knoppix. :)

---

### Post by scottuss on 2009-02-16
Ubuntu and Puppy seem to have issues being together, when selecting the Puppy option on my boot menu it starts to load some Ubuntu stuff then drops to BusyBox. It's def running an Ubuntu kernel.. any ideas?

Thanks in advance

---

