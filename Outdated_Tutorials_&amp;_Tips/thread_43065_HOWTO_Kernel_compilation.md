---
title: "HOWTO: Kernel compilation"
date: 2005-06-20
forum: Outdated Tutorials &amp; Tips
---

### Post by luca_linux on 2005-06-20
I thought to write this HowTo, since the kernel compile process on Ubuntu is made easier because this distro is debian-based.
First of all, download the kernel package you like from [kernel.org](http://www.kernel.org) or from the Ubuntu repositories.
If you want the official kernel patched by the Ubuntu Team, just type:
```
sudo apt-get install linux-tree
```
In this case we'll use the latest stable vanilla kernel version available.
For the compile process you'll need the following packages on Ubuntu:
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

```
Now untar the package:
```

cd /usr/src
sudo tar --bzip2 -xvf linux-2.6.12.tar.bz2

```
Create the following symlink:
```

sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux
cd /usr/src/linux

```
Now you can start customizing your kernel configuration; there two way, the first one is graphical, the second one pseudo-graphical:
```
sudo make xconfig
```
Or:
```
sudo make menuconfig
```
Then, after having finished the customization, we have to start the compile process:
```

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-custom kernel_image modules_image

```
The revision flag is optional and is just useful to edit the kernel name showed through uname -r. You can write whatever you want instead of "-custom".

There's also another interesting and useful flag, that is --initrd. The vanilla kernel is not enable yet to make use of initrd properly, and in fact there's a patch for this. The Ubuntu official kernel is a vanilla kernel patched with some patches among which there's the one for initrd. So, if you are compiling a vanilla kernel, you should take --initrd out; otherwise, if you are compiling a Ubuntu kernel, you can make use of initrd and you probably would that.

Note that now you'll have a .deb package in /usr/src ready to be installed as any other package through a simple double-click.
Grub will be updated automatically.
So, just type:
```
sudo dpkg -i kernel-image-2.6.12-custom_10.00.Custom_i386.deb
``` 

Enjoy.

---

### Post by ArBaDaCarBa on 2005-06-20
Very nice HOWTO, clear and precise. Thanks !

---

### Post by TheRealEdwin on 2005-06-20
```
:/usr/src$ sudo make xconfig
make: *** No rule to make target `xconfig'.  Stop.
:/usr/src$ sudo make menuconfig
make: *** No rule to make target `menuconfig'.  Stop.
:/usr/src$
```

I don't know what to do. =\

---

### Post by luca_linux on 2005-06-20
Yes, you're right. You need to:
```
cd /usr/src/linux
```
HowTo fixed.

---

### Post by skoal on 2005-06-20
Great howto.  If you're going to include the '--initrd' switch in there, it probably wouldn't hurt to point out what kernel options are needed in order to do so.  Otherwise, a lot of people will get 'kernel panic' if they build some essential options as modules (and *not* statically linked).

CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_INITRD=y

You'll probably need 'CONFIG_CRAMFS=y' as well since by default '/etc/mkinitrd/mkinitrd.conf' uses it (although you can change that).  I don't remember the exact steps or options since I didn't write them down during my own compile, but I believe you'll need those for the initial ramdisk.

\\//_

---

### Post by TheRealEdwin on 2005-06-20
You should also add that they need the QT development packages in order to use the graphical configuration. 

```
sudo apt-get install libqt3-dev
```

There is also a multi threaded version.

---

### Post by luca_linux on 2005-06-20
Ok, I've made some changes: first of all I've added the package "libqt3-mt-dev" (that I prefer to "libqt3-dev") as needed, then I've decided to keep out the "--initrd" flag at all because I realized it also needs a kernel patch included in the Ubuntu Official kernel patches, but not in the vanilla kernel, so it could have been a bit confusing for newbee.

---

### Post by TheRealEdwin on 2005-06-20
Question for xconfig. When customizing I am assuming a checkmark is yes, and a empty box is no. What then is a filled square box mean?

---

### Post by luca_linux on 2005-06-20
It means to compile that option as a module.

---

### Post by TheRealEdwin on 2005-06-20
[quote=Original Poster]```

sudo make-kpkg clean
sudo make-kpkg --revision=-custom kernel_image modules_image

```
The revision flag is optional and is just useful to edit the kernel name showed through uname -r. You can write whatever you want instead of "-custom".
[/quote]
 I'm not sure what this means or wants me to do.

```
 I note you are using a hyphen in the revision number.
 Please ensure that the upstream and debian revision
 numbers are policy compliant enough that dpkg and
 shall not choke on them at the end of the compile
 The revision -custom fails policy compliance, aborting
```

My only guess is that we have a bad hyphen somewhere in the filename.

edit: Changing custom to the kernel number (2.6.12) worked. :P

---

### Post by skoal on 2005-06-20
[QUOTE=TheRealEdwin]My only guess is that we have a bad hyphen somewhere in the filename.

edit: Changing custom to the kernel number (2.6.12) worked. :P[/QUOTE]
Yeah, I guess you figured it out already, but straight from the 'make-kpgk' man pages: '*Secondly, the version may contain only alphanumerics and the  characters  + . (full stop and plus) and must contain a digit.*' -> no hyphens.

The general format for the kernal package naming scheme is this:
kernel-image-(kernel-version)(--append-to-version)_(--revision)_(arch).deb

for example, when I built my 2.6.12 kernel, I used the following command:
make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers

which gives me:
skoal@morpheus:///usr/src $ ls *.deb
kernel-headers-2.6.12-custom_190605_i386.deb
kernel-image-2.6.12-custom_190605_i386.deb

\\//_

---

### Post by Kyral on 2005-06-20
Could you also do a make oldconfig to duplicate your current kernel?

---

### Post by vaskark on 2005-06-20
[QUOTE=Kyral]Could you also do a make oldconfig to duplicate your current kernel?[/QUOTE]

Would that keep all the config options the same? I compiled 2.6.12 successfully but it didn't boot. No error messages ... just a blank screen. All I really want is to get inotify working for Beagle. 

I didn't know what to select at the xconfig stage :???:

---

### Post by skoal on 2005-06-20
make oldconfig? Absolutely.  That's what I did when moving from 2.6.10 to the vanilla 2.6.12 I downloaded off kernel.org.  After you run that command, you will be presented with a few prompts (and their default y/n/m questions) for any differences between the 2 revisions.  I just selected all the defaults and went back under 'make menuconfig' and started from the top anyway, slicing and dicing what I didn't need.

\\//_

---

### Post by TheRealEdwin on 2005-06-20
Is there a list of items that you MUST have? Looks like I goofed up and i get kernel panics.

---

### Post by TheRealEdwin on 2005-06-21
So after a bunch of different compiles, and all of them failing, is there a way to remove them from grub and the installed stuff? I know you install it with dpkg -i but how do I uninstall it?

edit: Nevermind, found it after looking around for a few hours. 

If the filename is "kernel-image-2.6.12-custom_210605_i386.deb" the command would be ```
sudo dpkg -r kernel-image-2.6.12-custom
```

edit 2: Bah! Still getting "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)".

---

### Post by luca_linux on 2005-06-21
[QUOTE=TheRealEdwin]So after a bunch of different compiles, and all of them failing, is there a way to remove them from grub and the installed stuff? I know you install it with dpkg -i but how do I uninstall it?

edit: Nevermind, found it after looking around for a few hours. 

If the filename is "kernel-image-2.6.12-custom_210605_i386.deb" the command would be ```
sudo dpkg -r kernel-image-2.6.12-custom
```

edit 2: Bah! Still getting "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)".[/QUOTE]
 You have to compile the support for the file system you use (for example ext3) not as a module but built-in.
Plus, don't add the support for /dev, it's deprecated. Instead, enable tmpfs.

---

### Post by luca_linux on 2005-06-21
[QUOTE=skoal]Yeah, I guess you figured it out already, but straight from the 'make-kpgk' man pages: '*Secondly, the version may contain only alphanumerics and the  characters  + . (full stop and plus) and must contain a digit.*' -> no hyphens.

The general format for the kernal package naming scheme is this:
kernel-image-(kernel-version)(--append-to-version)_(--revision)_(arch).deb

for example, when I built my 2.6.12 kernel, I used the following command:
make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers

which gives me:
skoal@morpheus:///usr/src $ ls *.deb
kernel-headers-2.6.12-custom_190605_i386.deb
kernel-image-2.6.12-custom_190605_i386.deb

\\//_[/QUOTE]
 Yeah, you're right. I confused --append-to-version with --revision for awhile.
HowTo fixed.

---

### Post by Kyral on 2005-06-21
Is anyone else having problems downloading the 2.6.12 source tarball from Kernel.org, 'cause it never completes for me, and I can't wget it

---

### Post by skoal on 2005-06-21
I hesitate to post my kernel .config, but I will anyway.  *So before you post back with this .config don't work, please read my specs below (and make the appropriate changes with 'menuconfig' for any differences)*.  - see attached -

My rig with relevant kernel config parameters:
[list]
[*]Pentium 4
[*]Intel motherboard chipsets
[*]All IDE host hardware
[*]Nvidia Ti-4600 
[*]ALSA (only emu10k1 driver installed)
[*]only e100 for NIC driver
[*]only ACPI, no APM.
[*]USB and Filesystems all modules and should work for any rig.
[*]probably sumtin' sumtin' else impotant I'm missing here.
[/list]
NOTES:
[list]
[*]I stripped this kernel like a true playa would.  All my kernels are phat, *not* fat.  You feelin' me??  Any driver I don't use, ain't using me?? You feelin' this??
[*]I do not use local APIC or any framebuffer devices -> not good with Nvidia cards and performance stability (in general).  Those 2 cause more Nvidia related problems (outside of RenderAccel) than spilling crunk juice on some green fab marked with Nvidia TM.
[*]All (and everything) SCSI is stripped.  I'm all IDE bay-bee - living large and in charge.
[*]All irrelevant networking (experimental) doohickeys only IT netadmins would remotely care about, have been pimp slapped to /dev/null.  Don't even look for it in my configs.
[/list]

howto Build:
[list=1]
[*]copy attached config to /usr/src/linux/.config
[*]* run 'make menuconfig' and change any subtle differences between my rig and yours. (note the asterisk).
[*]make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers
[*]dpkg -i kernel-image-2.6.12-custom_190605_i386.deb
[*]dpkg -i kernel-headers-2.6.12-custom_190605_i386.deb (for installing nvidia drivers after reboot)
[*]reboot.
[*]You'll see some 'warning' when your ramdisk starts, like missing dis or dat.  Just ignore it like a true playa rollin' through stop signs while flippin' the switches on his '64.  That's how we roll...
[*]drop to custom init level for console, or /etc/init.d/gdm stop, or wait for gdm to puke on it's own.  Compile nvidia drivers, startx,  and off you go! weeeeeeeeee!!!!
[/list]

If you want to fix the 'modules missing' stuff at startup when your ramdisk mounts, you can play with adding those particular ones to /etc/mkinitrd/modules.  If you want to see what's missing from your ramdisk module startup:
 
skoal@morpheus://~ $ sudo mount -t cramfs -o loop /boot/initrd.img-2.6.12-custom /mnt && cd /mnt

check what filesystem/modules are missing...

skoal@morpheus:///mnt $ cat loadmodules 
modprobe -k  fan 2> /dev/null
[...]
modprobe -k  ide-generic
modprobe -k  ide-disk

add 'em to /etc/mkinitrd/modules (in the proper order), remake ramdisk, and drop it like it's hot.  That's how we roll...

\\//_

---

### Post by TheRealEdwin on 2005-06-21
I tried your command since I also like to get the headers but I recieve this error when I try to.
```
edwin@Doomhammer:/usr/src/linux$ make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers
I note that you are using the --revision flag with the value
   210605.
However, the ./debian/changelog file exists, and has a different value
   10.00.Custom.
I am confused by this discrepancy, and am halting.

```

---

### Post by skoal on 2005-06-21
"*However, the ./debian/changelog file exists, and has a different value 10.00.Custom.*"

That's from you using the $(date +'%d%m%y') in --revision.  Just use '--revision 10.00.Custom' instead.

That date part I use is part of a compile script I have, so you don't need to use it and I probably should have left it out altogether in my instructions.

\\//_

---

### Post by Heliode on 2005-06-22
I've got a question... I would like to try this, but does this procedure overwrite the current kernel, or does it **add** the new kernel to GRUB, so you keep the option to boot the old one?

I use my Ubuntu machines quite a lot and I don't want to have them in an unusable state.

---

### Post by oddabe19 on 2005-06-22
[QUOTE=TheRealEdwin]
edit 2: Bah! Still getting "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)".[/QUOTE]
 I get the exact same thing, and I compiled Ext3 and Ext2 into the kernel NOT as a module.

---

### Post by dresnu on 2005-06-22
[QUOTE=oddabe19]I get the exact same thing, and I compiled Ext3 and Ext2 into the kernel NOT as a module.[/QUOTE]

Check this thread: [http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd](http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd)
Scroll down to the last post and do what is suggested there.

---

### Post by dresnu on 2005-06-22
oh, and after that do update-grub obviously  :grin:

---

### Post by luca_linux on 2005-06-22
[QUOTE=Heliode]I've got a question... I would like to try this, but does this procedure overwrite the current kernel, or does it **add** the new kernel to GRUB, so you keep the option to boot the old one?

I use my Ubuntu machines quite a lot and I don't want to have them in an unusable state.[/QUOTE]
 The new kernel will be added, so you'll be able to continue using the old one.

---

### Post by luca_linux on 2005-06-22
[QUOTE=skoal]I hesitate to post my kernel .config, but I will anyway.  *So before you post back with this .config don't work, please read my specs below (and make the appropriate changes with 'menuconfig' for any differences)*.  - see attached -

My rig with relevant kernel config parameters:
[list]
[*]Pentium 4
[*]Intel motherboard chipsets
[*]All IDE host hardware
[*]Nvidia Ti-4600 
[*]ALSA (only emu10k1 driver installed)
[*]only e100 for NIC driver
[*]only ACPI, no APM.
[*]USB and Filesystems all modules and should work for any rig.
[*]probably sumtin' sumtin' else impotant I'm missing here.
[/list]
NOTES:
[list]
[*]I stripped this kernel like a true playa would.  All my kernels are phat, *not* fat.  You feelin' me??  Any driver I don't use, ain't using me?? You feelin' this??
[*]I do not use local APIC or any framebuffer devices -> not good with Nvidia cards and performance stability (in general).  Those 2 cause more Nvidia related problems (outside of RenderAccel) than spilling crunk juice on some green fab marked with Nvidia TM.
[*]All (and everything) SCSI is stripped.  I'm all IDE bay-bee - living large and in charge.
[*]All irrelevant networking (experimental) doohickeys only IT netadmins would remotely care about, have been pimp slapped to /dev/null.  Don't even look for it in my configs.
[/list]

howto Build:
[list=1]
[*]copy attached config to /usr/src/linux/.config
[*]* run 'make menuconfig' and change any subtle differences between my rig and yours. (note the asterisk).
[*]make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom --revision $(date +'%d%m%y') kernel_image kernel_headers
[*]dpkg -i kernel-image-2.6.12-custom_190605_i386.deb
[*]dpkg -i kernel-headers-2.6.12-custom_190605_i386.deb (for installing nvidia drivers after reboot)
[*]reboot.
[*]You'll see some 'warning' when your ramdisk starts, like missing dis or dat.  Just ignore it like a true playa rollin' through stop signs while flippin' the switches on his '64.  That's how we roll...
[*]drop to custom init level for console, or /etc/init.d/gdm stop, or wait for gdm to puke on it's own.  Compile nvidia drivers, startx,  and off you go! weeeeeeeeee!!!!
[/list]

If you want to fix the 'modules missing' stuff at startup when your ramdisk mounts, you can play with adding those particular ones to /etc/mkinitrd/modules.  If you want to see what's missing from your ramdisk module startup:
 
skoal@morpheus://~ $ sudo mount -t cramfs -o loop /boot/initrd.img-2.6.12-custom /mnt && cd /mnt

check what filesystem/modules are missing...

skoal@morpheus:///mnt $ cat loadmodules 
modprobe -k  fan 2> /dev/null
[...]
modprobe -k  ide-generic
modprobe -k  ide-disk

add 'em to /etc/mkinitrd/modules (in the proper order), remake ramdisk, and drop it like it's hot.  That's how we roll...

\\//_[/QUOTE]
 Ok, I'll give you the kernel config back tomorrow.

---

### Post by TheRealEdwin on 2005-06-22
How would I go about uninstalling multiple kernels? Here is what I want to do.

```
title		Ubuntu, kernel 2.6.12 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12 root=/dev/hda3 ro quiet splash
savedefault
boot

title		Ubuntu, kernel 2.6.12 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12 root=/dev/hda3 ro single
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,2)
kernel		/boot/memtest86+.bin  
savedefault
boot

```

I want to get rid of the 2.6.10-5-386 (why use 386 when I have a 686 kernel that works), the .12 kernel (doesn't work). Is there a way to remove them cleanly? Only thing I can think of is if dpkg has a command to list all packages. Any suggestions?

edit: After much searching I found it. Still don't know how to uninstall the 386 version of the kernel.
```
sudo dpkg --get-selections | less
sudo dpkg -r kernel-image-2.6.12
```

---

### Post by Seer on 2005-06-22
You forgot to mention that you also need 

> sudo apt-get install kernel-package

in order to use 

> sudo make-kpkg clean

if you don't already have it... (...which I didnt and I have no clue what they are but I googled it :) )

---

### Post by luca_linux on 2005-06-22
Added to the HowTo.
Thanks.

---

### Post by FLeiXiuS on 2005-06-22
Also might want to include that $ make menuconfig requires ncurses.  Ubuntu doesn't include them by default but lovely apt has them :-).

$ sudo apt-get instal libncurses5-dev

---

### Post by luca_linux on 2005-06-22
I had already included that package...

---

### Post by cutOff on 2005-06-22
One question: why not to compile linux-source-2.6.12 from breezy instead of kernel from kernel.org??

---

### Post by TheRealEdwin on 2005-06-22
I'm having a difficult time understanding the linked threads mentioning how to fix the issue I am having. According to the other thread, Ubuntu requires initrd but it is not included in this howto and I am unsure of how to go about it. I've read the other thread but only really have a vagure idea. I'm trying it out but I lack the experience to do this on my own.

[http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd](http://www.ubuntuforums.org/showthread.php?t=9807&highlight=mkinitrd)

---

### Post by luca_linux on 2005-06-23
I'm successfully running a fresh kernel (2.6.12 + -ck patchset) just following my HowTo.
Initrd is useful but not indispensable.
I've kept initrd out for a reason: the kernel needs a patch against cramfs to make initrd work properly. So I prefered going on without it. But everything is working well anyway.

---

### Post by skoal on 2005-06-23
[QUOTE=luca_linux][..]the kernel needs a patch against cramfs to make initrd work properly.[/QUOTE]
Actually, that's not entirely true. I'm using "romfs" instead with no problems, and actually didn't have any problems using cramfs.  Just make the appropriate changes in /etc/mkinitrd directory. Now, getting your initrd to work properly with a udev only system is another story.  The quick and dirty way is to build "devfs" into the kernel.  I'm still working on my custom initrd using busybox and adding a splash to it.  I think you're wise just to leave the initrd part out of your howto.

\\//_

---

### Post by dulljeff on 2005-06-24
Experiencing the same trouble - Kernel panic.

I don't wanna use initrd, so I didn't compile romfs but ext2 and ext3 into the kernel.

But still, I'm not able to boot into it. What can be the problem?

---

### Post by skoal on 2005-06-24
[QUOTE=dulljeff]But still, I'm not able to boot into it. What can be the problem?[/QUOTE]
1. Maybe an obvious question, but, did you make sure that you are not using 'initrd          /initrd.img-2.6.12' (or the like) in your '/boot/grub/menu.lst' entry?
2. If you compile in the file system you use (at least for your root partition), you should not get that kernel panic, although maybe another unrelated one.
3. At the very worst, at least enable these 2 options (under Device Drivers > Block Devices):
BLK_DEV_RAM
BLK_DEV_INITRD

* Whether you use the 'initrd' at boot or not, at least build these in and see if you still get VFS kernel panic.

\\//_

---

### Post by dulljeff on 2005-06-24
Hi again,

still no luck, though I tried something very promising.
For the former tests I used the linux-tree 2.6.11, so now I installed linux-tree 2.6.10, made oldconfig (with no manual confirmations, since I'm running on the standard 2.6.10-kernel) and assembled the deb-package as described.

Running on ext3, I built the file system into the kernel and left everything else unchanged. Reboot - and again kernel panic with vfs not able to mount on unknown file system (0, 0).

Do you, skoal, or anybody else have another suggestion what I can try? I'm willing to do whatsoever ;) I only want to use one self-compiled kernel; only one (on Gentoo, this one thing wasn't a big deal).

Help very much appreciated!

---

### Post by skoal on 2005-06-24
Well, I had this config posted on another reply of mine (earlier in the thread), but I was goofing around with "User CP" stuff and blew away *all*...that's right...all my prior attachments since I became a member of these forums.  I was trying to be a "good citizen" by sparing server space and thought I was nearing some limit.  How come this forum gives me root priveleges to wipe away 1/2 my existence here.  I need a forum 'sudo' toggle button...

Anyways, try out my config file I attached here!  Check my prior post for my specs.  This .config is mean and lean and only has what I need for my rig.  At the very least, you can use my config and add back what you want.  It'll save time anyway instead of using a 'make oldconfig'.  This config works great with initrd.

Just 'gunzip' it and move it to '/usr/src/linux/.config'

\\//_

---

### Post by picpak on 2005-06-24
This has taken hours and hours and hours...is it supposed to take that long?

---

### Post by skoal on 2005-06-24
picpak, is this your first kernel compile?  The time it takes depends on your system specs, but even on a P3 it shouldn't take more than 45 minutes.  On my P4~1.7 it takes about 10, or somewhere there about (depending on how many modules I've got compiled in).  That may be your issue.  I turn off all options (modules) in the kernel I don't need...and there are a *lot*.

\\//_

---

### Post by picpak on 2005-06-24
[QUOTE=skoal]picpak, is this your first kernel compile?[/QUOTE]

Yes.

> even on a P3 it shouldn't take more than 45 minutes.

Oh...that's exactly what I have.

> I turn off all options (modules) in the kernel I don't need...and there are a *lot*.

You turn them off? I just left them. I was afraid to touch them  :|

---

### Post by luca_linux on 2005-06-25
[QUOTE=picpak]I just left them. I was afraid to touch them  :|[/QUOTE]
That's why it took so long.

---

### Post by dulljeff on 2005-06-25
[QUOTE=skoal]Just 'gunzip' it and move it to '/usr/src/linux/.config'[/QUOTE] Tried that, unfortunately to no avail. Everytime the same error, not a single time a self-compiled kernel has worked.  :mad: Even though I used an initial rd this time. Obviously that is not the point after all, it doesn't depend on the ramdisk in my opinion 

Can I provide any more information maybe? Are the error or the cause of the kernel panics logged somewhere?

---

### Post by skoal on 2005-06-25
"*Everytime the same error, not a single time a self-compiled kernel worked.*"

dulljeff, could you repeat the error again.  The exact one.  I don't which one exactly that is.

here's some options you can try:
[list=1]
[*]using my .config, just compile all the *filesystems* into the kernel -> NO modules.
[*]or also using my .config, keep all the modules as they are but use my (/etc/mkinitrd/) settings. - see attached -
[list=i]
[*]backup your /etc/mkinitrd dir first. sudo cp -a /etc/mkinitrd ~ (or something similar).
[*]copy/untar my mkinitrd dir in /etc (cd /etc && sudo tar xvzf mkinitrd.tar.gz).
[*]change the RESUME var in 'mkinitrd.conf' to *your* own root device.
[*]add what modules (filesystem ones) you need to 'modules'.
[/list]
[/list]
I don't know why you would be getting VFS panics if all filesystem modules are statically linked into kernel (like the author of this howto suggested).

"*Are the error or the cause of the kernel panics logged somewhere?*"

Now that's a good question.  I believe the only way to resolve those logs is to do it remotely on boot with another linux box.  I have never done that, so I don't know what to suggest there.  Of course, if your filesystem never mounts, you really can't see what the kernel logs unfortunately.  It's a good question you ask.  I wish I knew an answer to provide for you.

\\//_

---

### Post by dissident on 2005-06-26
I could not get this howto to work even while compiling the file system into the kernel. I would always reboot and get this kernel panic error: 

*Kernel panic - not syncing: VSF: Unable to mount root fs on unknown-block(0,0)*

The only way I got it working was to add intitrd to the compile command like so:

*sudo make-kpkg --initrd --append-to-version=-custom kernel_image modules_image*

and ignore the warning message that came up. Is that bad? Is something not going to work doing it this way? I would like to know.

PS: You might warn people in the beginning that if they have nvidia drivers installed they may need to change "nvidia" back to "nv" in /etc/X11/xorg.conf in order to get X to start. Luckily, I knew enough to do that on my own.

---

### Post by skoal on 2005-06-26
[QUOTE=dissident][...]and ignore the warning message that came up. Is that bad? Is something not going to work doing it this way? I would like to know.[/QUOTE]
Nah, that's not bad.  That just means you need to adjust some kernel compile time options and/or fix your initrd settings in /etc/mkinitrd.  I had those same "issues" and simply added my filesystem module to the /etc/mkinitrd/modules file, compiled in "devfs", and made some other adjustments to my initrd.  I truly don't understand the Ubuntu way of handling udev/devfs and the initrd.  It should be possible to just have udev only compiled into the kernle (with no devfs), and all your filesystems as modules.  I'm currently working at "fixing" my initrd to take care of those "issues", and most of it is an exercise in understanding the boot process (and how Ubuntu mounts the udev filesystem as compared to other approaches).  Either way, if it boots, just pull out the 'ole hammer and bang away at a few of the "nails"...

\\//_

---

### Post by dulljeff on 2005-06-26
It finally worked! :)

I also needed the *--initrd* argument to make the kernel work.
So at least I have SMT enabled now.

[QUOTE=skoal]dulljeff, could you repeat the error again. The exact one. I don't which one exactly that is.[/QUOTE] Without initrd, I get the exact same error as *dissident* does.

As usual for linux users, there's always something you're not happy with. ;) 
So is there a solution to our problem? Can we get rid of the initrd?

---

### Post by dissident on 2005-06-26
Thanks skoal. I hope you figure it out.

FYI, if anyone wants to set up their nvidia drivers and compile a new kernel at the same time, check out this thread. I just used xconfig instead of gconfig along with the newest kernel and it worked great for me.  :grin: 

[http://www.ubuntuforums.org/showthread.php?t=21111](http://www.ubuntuforums.org/showthread.php?t=21111)

---

### Post by DonVla on 2005-06-27
hello,

the comiling works for me so far, but
i've got some questions: 
how do i compile patches, eg the debian/ubuntu-patches? are they automatically compiled with the kernel or do i have to add "add-patches" to the make-kpkg command? for me "add-patches" does nor work proper. i get errors.
how can i add patches from linux.org? or is this not recommended? 
i use the linux-tree-2.6.12 from breezy on an all-hoary-system.

thank you in advance,
vlad

---

### Post by luca_linux on 2005-06-27
Just patch the sources before compiling the kernel. You don't have to add any other parameter to make-kpkg.
```
sudo patch -p1 < file.patch
```

---

### Post by DonVla on 2005-06-27
thank you,

but can i use linux.org patches on the ubuntu-kernel? or is it not allowed because of the ubuntu patches?
i don't really understand the ubuntu patches policy...

thanx alot again,

vlad

---

### Post by luca_linux on 2005-06-27
If you want the latest kernel sources, you need to download it from linux.org. You can choose whatever patchset you want (-ck, -ac, -mm, etc.).
If you install the ubuntu official sources prepatched from apt, then patching with other patch may be a pain.
My suggest: download the latest kernel from linux.org and patch it with -ck patchset.
It's really useful and is worth trying.

---

### Post by DonVla on 2005-06-27
thank you.

i'll try ...

greetz vlad

---

### Post by zue on 2005-06-27
[QUOTE=skoal]1. Maybe an obvious question, but, did you make sure that you are not using 'initrd          /initrd.img-2.6.12' (or the like) in your '/boot/grub/menu.lst' entry?
2. If you compile in the file system you use (at least for your root partition), you should not get that kernel panic, although maybe another unrelated one.
3. At the very worst, at least enable these 2 options (under Device Drivers > Block Devices):
BLK_DEV_RAM
BLK_DEV_INITRD

* Whether you use the 'initrd' at boot or not, at least build these in and see if you still get VFS kernel panic.

\\//_[/QUOTE]

Hey.  I've been struggling with this same problem the last few days.  I followed the original howto and did everything on the above list and I'm still getting that VFS kernel panic.  I guess the only thing left is to try using initrd at boot.

---

### Post by skoal on 2005-06-27
Check out this thread here: [http://www.ubuntuforums.org/showthread.php?t=27709&highlight=vfs+kernel+panic](http://www.ubuntuforums.org/showthread.php?t=27709&highlight=vfs+kernel+panic)

I think that might give you a sol'n.  I really don't know what else to suggest.  I posted my kernel config and entire mkinitrd folder a while back in this thread, and it gives me no problems at all.  Shoot, I even got rid of that "Not able to find EXT3 filesystem warning the stock Ubuntu package shows..."

\\//_

---

### Post by zue on 2005-06-27
[QUOTE=skoal]Check out this thread here: [http://www.ubuntuforums.org/showthread.php?t=27709&highlight=vfs+kernel+panic](http://www.ubuntuforums.org/showthread.php?t=27709&highlight=vfs+kernel+panic)

I think that might give you a sol'n.  I really don't know what else to suggest.  I posted my kernel config and entire mkinitrd folder a while back in this thread, and it gives me no problems at all.  Shoot, I even got rid of that "Not able to find EXT3 filesystem warning the stock Ubuntu package shows..."

\\//_[/QUOTE]

I read that thread a while ago, but being a newbie, I didn't understand what I actually had to do from what was posted there.  I tried my kernel config with initrd and still got the same kernel panic.  But then again I didn't apply that patch you guys were talking about earlier to my kernel either, because I didn't know how and I was hoping it would  work without it, or at least be bootable.  So now I'm going to try your config file, and see what happens.  Is there anything I should do to make the initrd work before I compile and install my new kernel?

Thanks,
Zue

---

### Post by dulljeff on 2005-06-28
I know it's a little bit offtopic, but I'm very curious: Why does the Debian/Ubuntu way work with initrd if it is causing so much trouble and people are obviously unused to that?

---

### Post by DonVla on 2005-06-28
[QUOTE=zue]Hey.  I've been struggling with this same problem the last few days.  I followed the original howto and did everything on the above list and I'm still getting that VFS kernel panic.  I guess the only thing left is to try using initrd at boot.[/QUOTE]



hello,

i've got for a long time the same problem with initrd at boot. be sure you've enabled (not as a module) cramfs in the " miscellaneous fs" options of the kernel (as skoal said) . and also 
#XFS support
  CONFIG_MINIX_FS=y  # i do not know why
  CONFIG_INOTIFY=y
  CONFIG_DNOTIFY=y

then try this: 

" sudo fakeroot make-kpkg --append-to-version -"name" --revision "num.ber" kernel_image _--initrd binary_ "

that worked for me. no errors, but booted very very slow...
the new kernel i compiled without initrd and it worked great. do only:

" sudo make-kpkg --rootcmd fakeroot --append-to-version -"name" --revision "num.ber" kernel_image "

try that,

vlad

---

### Post by luca_linux on 2005-06-28
I'm not getting any problem and I'm not using initrd. So I think I'll post my kernel.config.
Now I'm not on my laptop, so I'll post it later.

---

### Post by DarkT on 2005-06-28
Nice howto :) I just wanted to add that people who are in gnome and don't want the qt libs can make gconfig (although I've found it to be somewhat buggy). 
Also if you 
```

sudo adduser *their_username* src 

```
they will be able to do things in the src directory without sudoing everything which is handy.

---

### Post by zue on 2005-06-29
So I tried this again using skoal's .config file with initrd (haven't tried without), and what do you know, it booted.  It's funny though, I couldn't find any difference at all in the filesystem part of the config, except that skoal's had Reiser compiling as a module and I wasn't compiling it at all, I'd be curious to know what was making the difference.  I still have to do this at least once more because I messed up with the sound drivers and now linux doesn't even find my sound card, but at least I now have a kernel I can boot with. 

I'm also getting another couple of errors at startup.  In my /var/log/dmesg file they look like this:

> PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
PCI: Cannot allocate resource region 3 of device 0000:00:00.0
PCI-DMA: Disabling IOMMU.

> 
..MP-BIOS bug: 8254 timer not connected to IO-APIC
 failed.
timer doesn't work through the IO-APIC - disabling NMI Watchdog!
Uhhuh. NMI received for unknown reason 2d.
Dazed and confused, but trying to continue
Do you have a strange power saving mode enabled?
 works.
Using local APIC timer interrupts.
Detected 12.436 MHz APIC timer.
testing NMI watchdog ... CPU#0: NMI appears to be stuck (1->1)!
checking if image is initramfs...it isn't (bad gzip magic numbers); looks like an initrd

(I'm not sure if the last line is relevant or not.)  I was hoping someone could give me a hand with this before I compile another kernel; I'm sure the error is in my custom config since I wasn't getting this message when I was using the precompiled kernel.

Thanks for your help,
Zue

---

### Post by dulljeff on 2005-06-29
```
http://www.hereyoucangeteverythingyoulikeatanygiventimeandofcourseyoucanalwaysgetitforfreethatsforsureandnodoubtswhatsoever.com
```

---

### Post by skoal on 2005-06-29
Ooops! One thing I forgot about using my 'mkinitrd' directory is that you'll need to get the 'genrom' .deb package (which has genromfs in it), which is used to make the initrd.

Hey zue, It's good to see you got most of it working.  If you were using my .config, I turn off the local APIC support.  It sounds like that's what your problem is here and maybe didn't catch it?

* Try enabling these under "Processor Type and Features" > "Local APIC support on uniprocessors" (CONFIG_X86_UP_APIC) and that should get rid of that NMI watchdog error.

As for the sound error, once again, I only turned on the module for my sound blaster, which is 'emu10k1'.  You'll need to find yours and enable that.  It looks like you might have an nForce chipset?  If that's the case, you'll need to just enable these:

* "Device Drivers" > "Sound" > "Advanced Linux Sound Architecture" > "PCI devices" > "Intel/SiS/nVidia/AMD/ALi AC97 Controller" (CONFIG_SND_INTEL8X0).

\\//_

---

### Post by zue on 2005-06-29
> As for the sound error, once again, I only turned on the module for my sound blaster, which is 'emu10k1'. You'll need to find yours and enable that. It looks like you might have an nForce chipset? If that's the case, you'll need to just enable these:

* "Device Drivers" > "Sound" > "Advanced Linux Sound Architecture" > "PCI devices" > "Intel/SiS/nVidia/AMD/ALi AC97 Controller" (CONFIG_SND_INTEL8X0).
Cool thanks, I must've missed that.  That's one more problem down.  But:
> 
* Try enabling these under "Processor Type and Features" > "Local APIC support on uniprocessors" (CONFIG_X86_UP_APIC) and that should get rid of that NMI watchdog error.

...if there's nothing even remotely resembling "Local APIC support on uniprocessors" under "Processor Type and Features", is something really weird going on?  ...I tried show all options and it's still not there.

Edit:  OK... I'm not on drugs:

> zue@miranda:/usr/src/linux$ cat .config |grep APIC
CONFIG_X86_GOOD_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_LOCAL_APIC=y

That's all I get, no CONFIG_X86_UP_APIC.  It really isn't there.  I'm confused.  Any thoughts?

Zue

---

### Post by dorris on 2005-06-29
hey, anyone got any ideas as to whats going on here
```
root@moo:/boot# mkinitrd -o /boot/initrd.img-2.6.12-mm2-dorris 2.6.12-mm2-dorris
find: /lib/modules/2.6.12-mm2-dorris/kernel/drivers/acpi: No such file or directory

```

the reason I'm compiling this kernel in the first place is coz I desparately need acpi fixes for my laptop, hence using mm patch set.
what is the exact meaning of the error, is this y I still can't boot to my kernel without the acpi=off switch??
It still creates the ramdisk, and allows me to boot into the kernle, but ALAS, still no acpi.
Any ideas on how to fix this?

---

### Post by Superdooperhero on 2005-06-30
Can you add something for how to do a make oldconfig? Also when you get the kernel from kernel.org does that still give you an Ubuntu system at the end of the day, or are you putting yourself in a position where you're not as compatible with the rest of ubuntu. I can't do an apt-get because I need to recompile the kernel in order to get my internet working.

---

### Post by skoal on 2005-06-30
[QUOTE=zue]That's all I get, no CONFIG_X86_UP_APIC.  It really isn't there.  I'm confused.  Any thoughts?[/QUOTE]
Zue, do you have "Symmetric multi-processing support" (CONFIG_SMP) enabled?  That's probably why you're not seeing the xUPx (uni-processor) stuff.

\\//_

---

### Post by skoal on 2005-06-30
[QUOTE=dorris][...]the reason I'm compiling this kernel in the first place is coz I desparately need acpi fixes for my laptop, hence using mm patch set.
what is the exact meaning of the error[...][/QUOTE]
/edit you're apparently missing that directory.  Oops! Maybe because you have all teh options compiled in?
From my directory:
```
skoal@morpheus:///lib/modules/2.6.12-3/kernel/drivers $ ls
[COLOR=DarkRed]acpi[/COLOR]  base  block  cdrom  char  ide  input  net  parport  usb  video
skoal@morpheus:///lib/modules/2.6.12-3/kernel/drivers $ [COLOR=DarkRed]ls acpi/[/COLOR]
ac.ko         battery.ko  fan.ko       processor.ko  toshiba_acpi.ko
asus_acpi.ko  button.ko   ibm_acpi.ko  thermal.ko    video.ko
```
and relevant kernel configs:
```
skoal@morpheus:///usr/src/linux-2.6.12 $ grep -i acpi .config
# Power management options (ACPI, APM)
# ACPI (Advanced Configuration and Power Interface) Support
CONFIG_ACPI=y
CONFIG_ACPI_BOOT=y
CONFIG_ACPI_INTERPRETER=y
# CONFIG_ACPI_SLEEP is not set
CONFIG_ACPI_AC=m
CONFIG_ACPI_BATTERY=m
CONFIG_ACPI_BUTTON=m
CONFIG_ACPI_VIDEO=m
CONFIG_ACPI_FAN=m
CONFIG_ACPI_PROCESSOR=m
CONFIG_ACPI_THERMAL=m
CONFIG_ACPI_ASUS=m
CONFIG_ACPI_IBM=m
CONFIG_ACPI_TOSHIBA=m
CONFIG_ACPI_BLACKLIST_YEAR=0
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_BUS=y
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_PCI=y
CONFIG_ACPI_SYSTEM=y
# CONFIG_ACPI_CONTAINER is not set
CONFIG_PNPACPI=y
# CONFIG_SERIAL_8250_ACPI is not set
```
which I believe is all stock Ubuntu stuff.  I pulled that over from make oldconfig and never touched that part.

* I assume you *do* want acpi? right? If so, it looks like you need these values set above.  For your initrd problem, I *would* compile them as modules (if you statically linked them before).

\\//_

---

### Post by luca_linux on 2005-07-01
Here's attached my kernel.config file!
I don't make use of initrd. It just works.
Enjoy.

---

### Post by iluciv on 2005-07-02
First off, thanks for the HOWTO and everyone who has asked and answered the various questions in this thread. They have been so helpful in trying to workout how to do this (which I almost have...almost :) 

I was having same VFS compile error as everone else so I read through the thread and followed the tips and now I have a working 2.6.12.1 kernel (YAY)   BUT 

I've got a sempron 2800+ chip and I couldn't find any info on if it could compile as an athlon/duron chip.. so I selected this anyway  :razz: 

It boots but at boot time I get these errors 

the ext3 module one (np) 
ERROR: Removing amd74xx Device or resource   busy 
ERROR: Removing Generic   Device  or resource busy 
ERROR: Removing Opti6r1   Device  resource busy 
swsusp: Suspend partition has wrong signature 

I don't fully remember the "Device busy" part of the error it does say something else but I'll edit this post after I reboot  
ok I edited that part 

There is also another error concering hda I'll post that too after reboot but it has somthing to do with not reponding resetting device/drive fixed (for now) 

as for nvidia drivers is it alright to use 
apt-get install nvidia-glx ?? Like stock ubuntu kernel 2.6. or do you have to use nvidia ones?
Sorry for so many questions 

Oh yeah one last one   :grin:  
Now when I'm running Xwindow system I right click to run terminal and get the following error 
'There was an error creating the child process for this terminal'
I do get a terminal window and a cursor but no prompt and I'm unable to type into the window 
*this is now my main problem but I thinkI may have found the problem do you I discovered that I have installed  /dev  so am going to recompile without it and big kernel block yada and see what happens (I think it was earlier on in this post that I think skoal said not to compile this in )  I've also gone back to i386 just to see if that helps instead of i686 and athlon (which I have previously tried 2.6.12.1 and now 2.6.12.2) 
TV-Card is now detected and works fantastic (reason for recompile in the fiest place  \\:D/   With tv-time )    
It prolly somthing I didn't compile into the kernel right
Heres hoping

---

### Post by zue on 2005-07-02
[QUOTE=skoal]Zue, do you have "Symmetric multi-processing support" (CONFIG_SMP) enabled?  That's probably why you're not seeing the xUPx (uni-processor) stuff.

\\//_[/QUOTE]

Nope.  CONFIG_SMP is not set.  But maybe something else I enabled made it disappear.  I guess I'll have to play around with it.  Thanks though.  If you have any other ideas let me know...

Zue

---

### Post by Heliode on 2005-07-02
Well, you are not going to believe this, but I got a kernel to actually boot! I used 'make oldconfig' and then the command 
```

sudo make-kpkg --append-to-version=-custom kernel_image modules_image --initrd binary

```
to bake the kernel.

However, when I boot it, I get all kind of strange error messages about devices being busy, and when Ubuntu desktop is started I noticed 'klogd' maxes my my 2,4 ghz cpu to 100% activity. Any ideas what might be causing this?

After I get this one working i'm going to use menuconfig to strip it down for as far as I can without breaking it, so i'll have an optimized kernel ;)

---

### Post by hardwarder on 2005-07-02
I tried using luca's config file and it worked great. Had to edit it a bit to suit my needs.
I think the package udev is needed to remove some /dev issues.

---

### Post by luca_linux on 2005-07-02
[QUOTE=iluciv]First off, thanks for the HOWTO and everyone who has asked and answered the various questions in this thread. They have been so helpful in trying to workout how to do this (which I almost have...almost :) 

I was having same VFS compile error as everone else so I read through the thread and followed the tips and now I have a working 2.6.12.1 kernel (YAY)   BUT 

I've got a sempron 2800+ chip and I couldn't find any info on if it could compile as an athlon/duron chip.. so I selected this anyway  :razz: 

It boots but at boot time I get these errors 

the ext3 module one (np) 
ERROR: Removing amd74xx Device or resource   busy 
ERROR: Removing Generic   Device  or resource busy 
ERROR: Removing Opti6r1   Device  resource busy 
swsusp: Suspend partition has wrong signature 

I don't fully remember the "Device busy" part of the error it does say something else but I'll edit this post after I reboot  
ok I edited that part 

There is also another error concering hda I'll post that too after reboot but it has somthing to do with not reponding resetting device/drive fixed (for now) 

as for nvidia drivers is it alright to use 
apt-get install nvidia-glx ?? Like stock ubuntu kernel 2.6. or do you have to use nvidia ones?
Sorry for so many questions 

Oh yeah one last one   :grin:  
Now when I'm running Xwindow system I right click to run terminal and get the following error 
'There was an error creating the child process for this terminal'
I do get a terminal window and a cursor but no prompt and I'm unable to type into the window 
*this is now my main problem but I thinkI may have found the problem do you I discovered that I have installed  /dev  so am going to recompile without it and big kernel block yada and see what happens (I think it was earlier on in this post that I think skoal said not to compile this in )  I've also gone back to i386 just to see if that helps instead of i686 and athlon (which I have previously tried 2.6.12.1 and now 2.6.12.2) 
TV-Card is now detected and works fantastic (reason for recompile in the fiest place  \\:D/   With tv-time )    
It prolly somthing I didn't compile into the kernel right
Heres hoping[/QUOTE]
 1) You have to choose athlon.
2) Try to compile ext3 built-in and not as a module
3) The swsusp error is a known issue. Maybe it's been solved with the latest kernel from kernel.org.
4) You'd better use the nvidia driver from nvidia.com.

---

### Post by iluciv on 2005-07-02
Cheers agian 

I've now patched the 2.6.12.2 with 2.6.13-rc1 patch (Why not hey) 

But I still have the major problem at the bottom of my post where I can't get a gui terminal. I also can't get into user groups through the gui either. I think it has something to do with permissions being mixed up; but I'm only taking a wild guess 

Well I'm going to compile agian so I'll edit this post with my latest results


wOOt! got it working with terminal and everyfing  \\:D/  

Bit bloated though but I'm not as yet willing to tamper with it anymore; I think I compiled about 7 times and it takes a long time to compile. 

I'm now getting errors at boot time same as before (with a few extras) which I think has to do with compiling ext3 into the kernel instead of module (as they dissappear when ext3 is compiled as a module.) 

But I don't mind as I know have a working kernel with all of my hardware supported 

Thanks agian luca_linux for this howto and everyone else thats posted in this thread. I wouldn't have all my hardware working if not for this thread and its contributers. 

for those interested I did (please before you start I am a newbie at computers) 

download kernel from kernel.org (this time 2.6.12.2)
move .bz2 file to sudo mv /home/iluciv/Desktop/linux-2.6.12.2.tar.bz2 /usr/src/
sudo tar xjvf linux-2.6.12.2.tar.bz2 (unpack file)
cd /usr/src/linux-2.6.12.2 (cause I haven't learnt how to get rid of symlinks yet)
sudo make mrproper (just for everytime I had to start agian) 
sudo make-kpkg clean (agian same as above) 
sudo make xconfig (cause I'm a girlie gui user  ;-)  )
selected what I know I needed and a few I thought I did and a few I didn't know 

sudo make-kpkg --initrd kernel_image kernel_headers modules_image

(the --append_to_version=-custom never worked for me would always abort spewing out some nonesense I couldn't understand so I just axed it cause I'm a trail blazer LOL  :grin: ) 
and it compiled fine with everything then installed everything 
the cd .. out of /usr/src/linux-2.6.12.2 to /usr/src

then sudo dpkg -i ker*.deb (to install everything) 

I used drivers from nvidia.com and just 

sudo killall gdm  (to kill gnome and get pure command line ) 
sudo sh NVIDIA*.run (in whatever directory  
follow the prompts 
sudo vi /etc/X11/xorg.conf
scroll down to find 
Section "Device"
	Identifier	"NVIDIA Corporation [GeForce 7800GTX LOL I Wish  :grin: ]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
INSERT KEY 
change "nv" to "nvidia" 
ESC KEY To stop insertion of text into file 
:w (to write file)
:q (to quit vi text editor) 

then at command line type 
startx 

Pop collar an PAT ONES SELF ON THE BACK you can even do a little dance if you like 

If you no longer want the Nvidia logo at boot time  
Section "Device"
	Identifier	"NVIDIA Corporation NV11 [Geforce2 MX/MX 400]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
        Option         "NoLogo"
Same as before put the Option line in your /etc/X11/xorg.conf file 

I know there would be alot faster ways of doing the same thing as above but I thought I would expose my complete newbieness for others who might find things like getting into command line and stopping gnome a little confusing 

Hope helps and I don't get flammed for going a little off topic 
 :grin:
(gota love brackets)

DAMMM MY Nvidia Drivers just bOrked  ](*,)  on  a second reboot 
Oh well It did work I'll just have to read more and get it working agian I'll post when do

---

### Post by zue on 2005-07-04
[QUOTE=skoal]
* Try enabling these under "Processor Type and Features" > "Local APIC support on uniprocessors" (CONFIG_X86_UP_APIC) and that should get rid of that NMI watchdog error.
\\//_[/QUOTE]

Hi skoal.  So I started from scratch (with your .config file again) and this time I noticed that the first time I start make xconfig I get this:
```

.config:104: trying to assign nonexistent symbol X86_POPAD_OK
.config:106: trying to assign nonexistent symbol X86_INTEL_USERCOPY
.config:107: trying to assign nonexistent symbol X86_USE_PPRO_CHECKSUM
.config:112: trying to assign nonexistent symbol X86_UP_APIC
.config:113: trying to assign nonexistent symbol X86_UP_IOAPIC
.config:118: trying to assign nonexistent symbol X86_MCE_NONFATAL
```
(There's actually quite a few more of these).  
This explains why I don't see a CONFIG_X86_UP_APIC option.  Anyone have any ideas why this is happening?

Thanks,
Zue

---

### Post by adamb10 on 2005-07-07
[QUOTE=zue]Hi skoal.  So I started from scratch (with your .config file again) and this time I noticed that the first time I start make xconfig I get this:
```

.config:104: trying to assign nonexistent symbol X86_POPAD_OK
.config:106: trying to assign nonexistent symbol X86_INTEL_USERCOPY
.config:107: trying to assign nonexistent symbol X86_USE_PPRO_CHECKSUM
.config:112: trying to assign nonexistent symbol X86_UP_APIC
.config:113: trying to assign nonexistent symbol X86_UP_IOAPIC
.config:118: trying to assign nonexistent symbol X86_MCE_NONFATAL
```
(There's actually quite a few more of these).  
This explains why I don't see a CONFIG_X86_UP_APIC option.  Anyone have any ideas why this is happening?

Thanks,
Zue[/QUOTE]
 I recieve a kernel panic upon bootup of the new kernel:

kernel panic:  not syncing: VFS: Unable to mount root fs on unknown-block (0,0)

---

### Post by luca_linux on 2005-07-08
[QUOTE=adamb10]I recieve a kernel panic upon bootup of the new kernel:

kernel panic:  not syncing: VFS: Unable to mount root fs on unknown-block (0,0)[/QUOTE]
 As said some post above, you have to disable initrd, compile your file system support built-in and not as a module nad you need support for udev, so some changes in Block Device section.
You can follow my kernel.config for reference attached some post above.

---

### Post by dorris on 2005-07-08
[QUOTE=luca_linux]As said some post above, you have to disable initrd, compile your file system support built-in and not as a module nad you need support for udev, so some changes in Block Device section.
You can follow my kernel.config for reference attached some post above.[/QUOTE]
 Or alternatively make a Ramdisk to boot into. This is preferable for me currently, and might be for others, as I can add things such as dsdt tables into the initrd, instead of recompiling the kernel everytime I want to try a new table.
to add an initrd for kernel 2.6.12-<revision> , type :
```

cd /boot
mkinitrd -o /boot/initrd.img-2.6.12-<revision>     2.6.12-<revision>

```
edit /boot/grub/menu.lst, and under your kernel entry, enter the following line, after the kernel line:
```

initrd                           /boot/initrd.img-2.6.12-<revision>
```

---

### Post by geearf on 2005-07-10
Hello,

just to add a little something to the how to.

Sometimes, when you build a new kernel it might wanna use another version of gcc, not the one you usually use (probably a newer one).

But then if you try to build nvidia drivers (or something else), it will fail.

The solution is simple, look at /proc/version to know which gcc was used to compile the kernel, and use the same to compile the nvidia drivers (or others) : 
sudo ln -s /usr/bin/gcc-theversion /usr/bin/gcc
(you may have to remove the old gcc link first).

---

### Post by dorris on 2005-07-13
Can I make a suggestion, to make the howto a bit more portable.
currently the .deb created is only good for the machine the kernel was compiled on, to put it on another machine is OK, but there will be no headers, etc.
by replacing the lines
```

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-custom kernel_image modules_image

```

with

```

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-custom binary modules_image

```

this will create 4 debs, the kernel image, kernel source, kernel headers, and docs.

much better for compiling kernels for another machine.

---

### Post by geearf on 2005-07-13
Also i do not know why, but most of the time, witout initrd, i cannot boot.

so --initrd might be usefull.

---

### Post by iluciv on 2005-07-14
Any suggestions as to why one would get 'segmentation faults' after kernel compile. 

This happens after installling anything i.e apps, games etc, the NVIDIA drivers will usually fail. I can just run the nv drivers and most things work (except XMMS, 3D games) 

I've looked up the gcc version and it is using the same one (as there is only one gcc installed) from post above 

Can I install a later version? Would that help?  

I haven't found much pertaining to this problem on the web but prehaps I'm not searching right

---

### Post by geearf on 2005-07-14
One option would be (well it happened to me), the problem come from the nvidia driver not completely installed.

Try uninstalling and see what happens (that did the trick for me before).

Then if it was that, try installing them for good this time.

---

### Post by epb613 on 2005-07-17
Nice howto. A major problem though: after following all the steps and booting into my new kernel, nothing happens. Ie: I click the new kernel in grub and then the screen just goes blank. Any ideas?

---

### Post by jodar on 2005-07-21
Okay, I did everything just as on the front page and I get the whole problem with kernel panic (0,0) or whatever...I see that you guys are suggesting solutions, but the thing I loved about this guide was that it was step by step...I can follow that and learn. 

When it is said that I need to put initrd in my kernel not as a module, I have no idea how to do that.  If someone could walk me step by step on how to get from where the first post ends (great guide by the way...I learned alot already), to the point where I shouldn't get that error, then that would be great.

---

### Post by geearf on 2005-07-22
Try with this : 
sudo make clean
sudo make mr proper
sudo make-kpkg clean
sudo make menuconfig
sudo make-kpkg --initrd --append-to-version=-customise kernel_image modules_image

---

### Post by dorris on 2005-07-22
apparently the --initrd is not so good with some kernel versions, I just make the initrd myself
```

cd /boot
sudo mkinitrd -o /boot/initrd.img-2.6.12-386 2.6.12-386

```

---

### Post by geearf on 2005-07-22
i never had any trouble with it so i don't know about this.

---

### Post by jodar on 2005-07-24
Okay, the kernel doesn't get "kernel panic" anymore, but now it hangs at the PCMCIA step in the boot process.  Any ideas?

---

### Post by luca_linux on 2005-07-24
Maybe you're missing something in your kernel.config...Look at mine (that is here attached to a post) to figure it out.

---

### Post by Ezzet on 2005-07-24
So what is the final Kernel Compilation howto? I've readed all the posts and I'm little bit confused now! Is there compilation differences depending of which kernel (vanilla etc) you use? And do you really need --initrd or not?
Please can anyone explain these things a little bit "deeper"? :-?

---

### Post by luca_linux on 2005-07-24
The vanilla kernel is not enable yet to make use of initrd properly, and in fact there's a patch for this. The Ubuntu official kernel is a vanilla kernel patched with some patches among which there's the one for initrd. So, if you are compiling a vanilla kernel, you should take --initrd out; otherwise, if you are compiling a Ubuntu kernel, you can make use of initrd and you probably would that.

---

### Post by tseliot on 2005-07-26
Hi, I've finally found a kernel that suits (part of) my needs. It's "2.6.12-4-amd64-k8" from Breezy repos (but I have Hoary). It works well but I need to fix 2 things: 

1)enable DMA on all my cdreaders natively (without hdparm); 2) Make its nvidia modules;

I know how to do both (thanks to the HOWTOs I've found in this forum).

I'd like to make an exact copy of my current kernel and modify these 2 things. I've tried using a vanilla kernel (the latest is 2.6.12.3) with "make oldconfig". However when I boot the system with the new kernel it has some problems (during the bootstrap) that is some undetected devices. I didn't want to damage my hardware so I destroyed the new kernel (actually I did it 2 times).

Let's get to the point: if I download the source of "2.6.12-4-amd64-k8" from Breezy:

1) If I used "make oldconfig" would I have an exact copy of my current kernel?

2) Should I use the patch (for this kernel) that is available from Breezy repos? Or would it be included in the sources?

---

### Post by luca_linux on 2005-07-26
1) Yes, you would.
2) If you download the linux-tree package, it will be included (the sources will be already patched).

---

### Post by tseliot on 2005-07-26
Grazie x la risposta. Ti farò sapere i risultati

---

### Post by tseliot on 2005-07-26
Just another question. I've installed the source-tree and now I've got these folders.

alberto@ubuntu:/usr/src$ ls
linux-patches        linux-source-2.6.12.tar.bz2  nvidia-kernel-source.tar.gz
linux-source-2.6.12  modules                      rpm

Should I add something to the usual command to compile the patches in the kernel?

make-kpkg --rootcmd fakeroot --initrd --append_to_version -custom –revision=1 kernel_image modules_image kernel_headers

---

### Post by luca_linux on 2005-07-26
No, just create the symlink as suggested in the HowTo.

---

### Post by tseliot on 2005-07-26
The kernel compiled flawlessly though I can't make the nvidia driver to work (even with the right module).

I solved the problem with the DMA: now I don't have to prompt sudo hdparm -d1 /dev/hdd every single time I restart my computer.

Thanks

---

### Post by Malakin on 2005-07-26
These instructions seemed to work at first but they totally messed up my menu.list file. I assumed it at least kept my original ubuntu kernel entry intact but when trying to boot it wouldn't boot off either the new kernel even though I used the exact same .config file with the same kernel before and the original ubuntu kernel wouldn't boot either so it's pretty much totally messed up my menu.lst file and possibly more since I can't seem to figure out why it's not booting now. In the future I I'll just add kernels the old fashioned way.

A note to backup your menu.lst file if you've customized it should at least be added to the instructions.

---

### Post by luca_linux on 2005-07-26
What you said has never happened to me.

---

### Post by tseliot on 2005-07-28
Could you help me with this problem, please?

[http://ubuntuforums.org/showthread.php?t=52641](http://ubuntuforums.org/showthread.php?t=52641)

Update: Problem solved

---

### Post by KupernikuZ on 2005-08-04
[QUOTE=luca_linux]
...If you want the official kernel patched by the Ubuntu Team, just type:
```
sudo apt-get install linux-tree
```
...
[/QUOTE]

I just tried to write sudo apt-get install linux-tree because I want the version from the Ubuntu team. I just got the message, that the package dosn't exist.
How do I upgrade to the newest Kernel version?
-Do I have to do it 'manualy'?

:?

---

### Post by tseliot on 2005-08-04
You can find it in Synaptic.

---

### Post by KupernikuZ on 2005-08-05
[QUOTE=tseliot]You can find it in Synaptic.[/QUOTE]
 Can't run Synaptic, cause my server is locatet somewhere else fysically. I'm loggin on the server through a terminal. 

Instead I tried:
> apt-get install linux-686
That updatet the system to an:  2.6.8.1-5-686 #1 Tue Jun 14 22:55:54 UTC 2005 i686 GNU/Linux

---

### Post by geearf on 2005-08-05
if you use ssh, you can also export X, and have anything work, even if you are not in front of the computer.

---

### Post by npaladin2000 on 2005-08-06
Did someone forget "make gconfig"

I dunno WHY you're having us install all that QT garbage, when there's a perfectly good GTK GUI for the kernel config. ;)

---

### Post by Nego on 2005-08-06
Thanks for the howto, kernel works great. Now I have to compile the Fglrx modules  ](*,)

---

### Post by tymek666 on 2005-08-07
I have some problem with xconfig. Of course i can still configure kernel using menuconfig, but i'd like to fix xconfig too. I've got this message:

sed < scripts/kconfig/lkc_proto.h > scripts/kconfig/lkc_defs.h 's/P(\([^,]*\),.*/#define \1 (\*\1_p)/'
  HOSTCC  scripts/kconfig/kconfig_load.o
/usr/share/qt3/bin/moc -i scripts/kconfig/qconf.h -o scripts/kconfig/qconf.moc
  HOSTCXX scripts/kconfig/qconf.o
  HOSTLD  scripts/kconfig/qconf
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status
make[1]: *** [scripts/kconfig/qconf] Error 1
make: *** [xconfig] Error 2

I have no idea what is 'lqt' :(
 Do you have any idea how to fix it?

---

### Post by geearf on 2005-08-07
Have you install the qt libs ?

---

### Post by tymek666 on 2005-08-07
[QUOTE=geearf]Have you install the qt libs ?[/QUOTE]
Do you mean this:
libqt3-mt-dev ?

Yes, i have.

---

### Post by theinvictus on 2005-08-08
since I don't have internet access in linux (part of the reason I need the kernel) is there any site I can download the the official kernel patched by the Ubuntu Team, to avoid the apt-get part.

thnx,
-theinvictus

---

### Post by luca_linux on 2005-08-08
Here you are: [http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

Enjoy.

---

### Post by theinvictus on 2005-08-08
any idea exactly which package it is?

---

### Post by geearf on 2005-08-08
this should be easier I guess : 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by luca_linux on 2005-08-08
[QUOTE=geearf]this should be easier I guess : 

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)[/QUOTE]
 Yeah. That's what I meant to post.
Then I posted the wrong link...

---

### Post by theinvictus on 2005-08-09
how do I install the contents of the .deb file?

EDIT: never mind....I'm getting lazy, amazing what a little googling will do...thnx anyways

---

### Post by luca_linux on 2005-08-09
> 
Note that now you'll have a .deb package in /usr/src ready to be installed as any other package through a simple double-click.
Grub will be updated automatically.
So, just type:
```
sudo dpkg -i kernel-image-2.6.12-custom_10.00.Custom_i386.deb
``` 


That's what there's written in the HowTo...

---

### Post by xodeus on 2005-08-09
Okay, I will ny try to build a new kernel, but I'm stading right here for asking u something.
I'm running AMD64 CPU with an normal Ubuntu Hoary 386 version.
So what arch shoul I compile? The AMD K7 (i686) or AMD K8 (x86_64).

---

### Post by luca_linux on 2005-08-09
I think you can choose AMD K8 arch.

---

### Post by xodeus on 2005-08-09
[QUOTE=luca_linux]I think you can choose AMD K8 arch.[/QUOTE]
U think that?
But the system will not use any amd64 libs or so?
I don't really know?
Maybe I should make 2 sets of kernels. One K7 and one K8?

---

### Post by luca_linux on 2005-08-09
I haven't got an AMD64 processor yet, so I've never tried.
Anyway, just compile a new for K8. If it doesn't work, just choose the the kernel you're currently running from GRUB menu and then compile another kernel for K7.
Then let me know.

---

### Post by xodeus on 2005-08-09
[QUOTE=luca_linux]I haven't got an AMD64 processor yet, so I've never tried.
Anyway, just compile a new for K8. If it doesn't work, just choose the the kernel you're currently running from GRUB menu and then compile another kernel for K7.
Then let me know.[/QUOTE]
I'll be back then.
So If I would try to run the kernel with default ubuntu options I don't ahve to change anything else than my arch?

---

### Post by luca_linux on 2005-08-09
Type:
```
sudo make oldconfig
```
before typing "sudo make menuconfig" or "sudo make xconfig".
This command will make a .config file with the options of your running kernel; it will just ask you for new options not included in the running kernel configuration (this usually happens when the sources are newer that the running kernel).

That's it.

---

### Post by xodeus on 2005-08-09
[QUOTE=luca_linux]Type:
```
sudo make oldconfig
```
before typing "sudo make menuconfig" or "sudo make xconfig".
This command will make a .config file with the options of your running kernel; it will just ask you for new options not included in the running kernel configuration (this usually happens when the sources are newer that the running kernel).

That's it.[/QUOTE]
 Very strange.
When I make this.
```
sudo make oldconfig
sudo make menuconfig
```
Change the Processor type to K8
and follow with
```
sudo make-kpkg clean 
sudo make-kpkg --append-to-version=-custom kernel_image modules_image
```
I see several messages saying arch i386 when the kernel compiles. Okay, I'll wait now and see when it finnishes. :D How long does it take? 10 mins?

---

### Post by geearf on 2005-08-09
are you doing a 32 or 64bits kernel ?

---

### Post by xodeus on 2005-08-09
[QUOTE=geearf]are you doing a 32 or 64bits kernel ?[/QUOTE]
I don't really know. 
I just followed this guide.
Inserted make oldconfig
and changed the arch to Opteron, Atlon64, K8 as I wrote just above.

---

### Post by xodeus on 2005-08-09
[QUOTE=geearf]are you doing a 32 or 64bits kernel ?[/QUOTE]
 My filename is
kernel-image-2.6.10-custom_10.00.Custom_i386.deb
So i suppouse that the kernel is 32bit.
So, now I'm going to install and see what changed.

---

### Post by xodeus on 2005-08-09
[QUOTE=luca_linux]I haven't got an AMD64 processor yet, so I've never tried.
Anyway, just compile a new for K8. If it doesn't work, just choose the the kernel you're currently running from GRUB menu and then compile another kernel for K7.
Then let me know.[/QUOTE]
 Okay. 
I followed your guide as mentioned.
Added the make oldconfig before make menuconfig.
Then ran the build commands, installed the kernel.
When trying to boot it I get this Message:
```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block(0,0)
```

---

### Post by luca_linux on 2005-08-09
Have you used a vanilla kernel (from kernel.org) or the linux-tree available in the official Ubuntu repository.

---

### Post by xodeus on 2005-08-09
[QUOTE=luca_linux]Have you used a vanilla kernel (from kernel.org) or the linux-tree available in the official Ubuntu repository.[/QUOTE]
 I've used the linux-tree

---

### Post by luca_linux on 2005-08-09
Have you used the --initrd flag for make-kpkg?

---

### Post by xodeus on 2005-08-10
[QUOTE=luca_linux]Have you used the --initrd flag for make-kpkg?[/QUOTE]
 I don't think so. I just followed this guide by typing what it said in the code boxes.

```
sudo make-kpkg --append-to-version=-custom kernel_image modules_image
```

---

### Post by luca_linux on 2005-08-10
Here's the problem...after that code, there's written that if you use the Ubuntu linux-tree, you'll need the --initrd flag. So retype that command adding "--initrd".

---

### Post by cutOff on 2005-08-10
People who have Athlon XP, I've attached my .config file which worked fine for me. It doesn't include initrd image.

- DMA support for all drives
- Framebuffer console support (small fonts)
- SB Live emu10k1 support (ALSA)

---

### Post by c-m on 2005-08-10
I recently downloaded the latest k7 kernel  in apt, think it was 2.6.11-1 but that didn't work so i guess i'll have to compile my own. no big problem as i've done it before. There are however 2 things i'm curious about:

**1)** I was taught to use "make menuconfig" configure my kernel then run "make && make_modules install"  Why does no-one here seem to use that method?

**2)** I have an nvidia graphics card. How do i make this work with a newly compiled kernel? with the one i downloaded in apt i recieved the error "unable to load nvidia module" or something or other.

edit: just tried to compile and i got the following:

> 
root@ubuntu:/usr/src/linux-headers-2.6.10-5 # make menuconfig
scripts/kconfig/mconf arch/i386/Kconfig
#
# using defaults found in .config
#


*** End of Linux kernel configuration.
*** Execute 'make' to build the kernel or try 'make help'.

root@ubuntu:/usr/src/linux-headers-2.6.10-5 # make && make modules_install
  CHK     include/linux/version.h
  UPD     include/linux/version.h
  SPLIT   include/linux/autoconf.h -> include/config/*
make[1]: *** No rule to make target `init/main.o', needed by `init/built-in.o'.  Stop.
make: *** [init] Error 2




---

### Post by luca_linux on 2005-08-10
The Debian make-kpkg method is handier.

---

### Post by student on 2005-08-11
damn, I never get my mouse right
```
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc104"
(**) Generic Keyboard: XkbModel: "pc104"
(**) Option "XkbLayout" "be"
(**) Generic Keyboard: XkbLayout: "be"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(EE) xf86OpenSerial: Cannot open device /dev/input/mice
	No such file or directory.
(EE) Configured Mouse: cannot open input device
(EE) PreInit failed for input device "Configured Mouse"
(II) UnloadModule: "mouse"
(WW) No core pointer registered
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
No core pointer

Fatal server error:
failed to initialize core devices
```

what option is that in xconfig ?

---

### Post by luca_linux on 2005-08-11
Are you sure your mouse is /dev/input/mice?

---

### Post by student on 2005-08-11
[QUOTE=luca_linux]Are you sure your mouse is /dev/input/mice?[/QUOTE]
yes, I use exactly the same Xorg, the same everything in fact.
only I threw everything I didnt need out of my custom kernel, and made some things native that I always use.
I made ps2 mouse and keyboardcontroller native, and the drivers also.
I did dpkg-reconfigure -a also offcourse...

---

### Post by student on 2005-08-11
[QUOTE=student]yes, I use exactly the same Xorg, the same everything in fact.
only I threw everything I didnt need out of my custom kernel, and made some things native that I always use.
I made ps2 mouse and keyboardcontroller native, and the drivers also.
I did dpkg-reconfigure -a also offcourse...[/QUOTE]

**edit**
woeps, sorry. You were right, my mouse seems to be /dev/psaux
Looks like my custom kernel is a bit stricter then the standard one.
But thanks for letting me think  :smile:


damn, wrong button, and I cant remove this post, oh well...

---

### Post by tsaphah on 2005-08-12
The GRUB menu.lst file will be over wrote.  If you were set up to dual boot with Windows you will loose that option in your menu.  Be sure to add back in!!

---

### Post by luca_linux on 2005-08-13
Never happened to me.

---

### Post by radeon on 2005-08-17
I'am  interesting in two things :

1. How get the current config of the kernel, I mean where is the file with this 

2. How to make a working kernel that have IMQ, I heard that there is a lot of problems with debian kernels working with IMQ, and IMQ working with iptables

Thanks

---

### Post by luca_linux on 2005-08-17
1) It's in /boot: something like config-yourKernelVersion...
2) Maybe you're looking for this patch?: [http://www.linuximq.net/](http://www.linuximq.net/)
Note: to apply a patch just:
```

cd /usr/src/linux
sudo patch -p1 < /path/where/the patch/is/

```
(/usr/src/linux is the folder where the kernel sources are).

---

### Post by SpEcIeS on 2005-08-25
Well I tried to compile my own kernel, but came to failure. It would seem that everything builds and installs nice, but upon booting the grub loads then the screen goes blank. ? The system does seem to be loading, so I am sure that is it just a video related issue.

I have a nvidia card, and I have used the vesa option in the /etc/X11/xorg.conf, also tried nv. but all have failed. Same results. 

This has been a starting position prior to installing the latest 2.6.12 kernel. I cannot get to this stage unless the previous kernel, ubuntu's 2.6.10-5 builds and installs. 

Also, these compiles have been done using the default .config from the /boot directory.

What is causing this misshap?  :neutral:

---

### Post by luca_linux on 2005-08-25
When there's no longer hd activity, try to login, even if you can't see anything. Then let me know if X starts well or has the same issue of the console.

---

### Post by xodeus on 2005-08-25
[QUOTE=luca_linux]Here's the problem...after that code, there's written that if you use the Ubuntu linux-tree, you'll need the --initrd flag. So retype that command adding "--initrd".[/QUOTE]
 I've tried now with the --initrd flag but it didn't help.
So I can say I can only build k7 kernels when running i386 system on my amd64.

---

### Post by SpEcIeS on 2005-08-26
[QUOTE=luca_linux]When there's no longer hd activity, try to login, even if you can't see anything. Then let me know if X starts well or has the same issue of the console.[/QUOTE]
I was thinking about this and figured the video is out somehow, so I removed the vga=792, or 788 as the kernel deb install would have it, and it worked fine. 

I guess I would have to compile the nvidia drivers to solve this issue. I set my xorg.conf to "nv" prior to reboot.

Upon somewhat succeeding on this matter, I tried the 2.6.12.5 kernel, but found a lot of errors. However, I copied the .config-2.6.10(whatever) to the /usr/src/linux. Perhaps I should just use the one the comes with the 2.6.12 kernel and modify from there.

Modules such as dazuko and nvidia, can they be added to the /usr/src/linux directory, or do they need to be compiled on there own?

---

### Post by tseliot on 2005-08-26
[QUOTE=SpEcIeS]I was thinking about this and figured the video is out somehow, so I removed the vga=792, or 788 as the kernel deb install would have it, and it worked fine. 

I guess I would have to compile the nvidia drivers to solve this issue. I set my xorg.conf to "nv" prior to reboot.

Upon somewhat succeeding on this matter, I tried the 2.6.12.5 kernel, but found a lot of errors. However, I copied the .config-2.6.10(whatever) to the /usr/src/linux. Perhaps I should just use the one the comes with the 2.6.12 kernel and modify from there.

Modules such as dazuko and nvidia, can they be added to the /usr/src/linux directory, or do they need to be compiled on there own?[/QUOTE]
As far as nvidia modules are concerned, yes they have to be recompiled. You can do it in this way:

1) go to nvidia website and download the driver you need. The nvidia modules that can be found in Ubuntu repositories in 7174, so if it worked for you, download the installer for this driver.

This is the archive of 32bit drivers

[http://www.nvidia.com/object/linux_display_archive.html](http://www.nvidia.com/object/linux_display_archive.html) 

2) use my HOWTO to install the driver

[http://ubuntuforums.org/showthread.php?t=57368](http://ubuntuforums.org/showthread.php?t=57368)

---

### Post by SpEcIeS on 2005-08-27
Thanks for the tip. I will try it out soon. :)

---

### Post by chaumurky on 2005-08-31
I've just recently built the new vanilla 2.6.13 (It appears to need the --initrd option) However when booting I get this error (a few times in a row):

```
device-mapper: dm-linear: Device lookup failed
device-mapper: error adding target to table
```

Once booted my other two hard disks are not mounted (hdc & hdd).

Can anyone recognise what is missing for this to occur? Is a patch required or something enabled in the config?

Oh, yeah, this is on Breezy, if that makes any difference...

---

### Post by chaumurky on 2005-08-31
Hmm, perhaps [THIS](http://evms.sourceforge.net/install/kernel.html#bdclaim) may be the problem.

---

### Post by chaumurky on 2005-08-31
Yup, just added the drives to the exclusion list in /etc/evms.conf. All's well.....

---

### Post by zarathustra on 2005-09-01
Do you have to apply any sort of patch for SATA drives? My compilations never seem to work on my hard drives...

---

### Post by zarathustra on 2005-09-01
Nevermind, I got it to work. However, it never recognises my wireless card.

---

### Post by osxus3r on 2005-09-03
just a quick question, so I followed the how to and 'updated' my kernel but forgot to include the --initrd flag and now initrd.img is missing, is there a quick way to fix it without reinstalling the whole system??? Yes I know its possible to recompile the kernel again including the damn flag but then how can you install the .deb package if you're not actually booted into Ubuntu (cause its not working)?

---

### Post by luca_linux on 2005-09-04
Can't you boot in the previous working kernel? Have you already deleted it? You shouldn't delete the last working kernel from Grub without testing the new one.
So, if you still can, just boot in the old kernel and recompile the kernel.

---

### Post by osxus3r on 2005-09-04
[QUOTE=luca_linux]Can't you boot in the previous working kernel? Have you already deleted it? You shouldn't delete the last working kernel from Grub without testing the new one.
So, if you still can, just boot in the old kernel and recompile the kernel.[/QUOTE]

thanks for reply luca_linux , yes I still can and that's what I did, recompiled the kernel with the --initrd flag but it didn't help much , the system loads up to the stage where it says 'welcome to linux 2.6.13-custom' and nothing esle happens for like 5 minutes, the hard drive doesn't seem to be doing anything else after that, so I don't know.

I have also tried downloading the other guy's kernel (2.6.11) which was particulary compiled for mac mini and should give me sound but it throws A LOT of errors during the booting and doesn't even boot :)

---

### Post by odin on 2005-09-05
Very good howto I should say and thank's, it really helped me at the begining but I have another problem nowreally anoying.I need to select an option in the library routines menu so I have to compile the kernel from www.kernel.org.That's not a problem because I have done it succesfully several times.

The problem is that I need to build a module outside the kernel and for that I need to select crc functions when I do the "make menuconfig".The thing is that I cannot select one of them(the one in the middle which says "CRC32 options" in kernel 2.6..

I'm sure that one is the one I need since I have built the module I need with no errors but a warning saying that the module doesnt have a CRC.I just cant select it neither as a built-in option or as a module.I guess that option depends on others so I'm able to select it but I've tried many conbinations and nothing.

Could anyone help me or guide to find the solution?

What I'm trying to build is seppl-0.4 that you can find in [http://0pointer.de/lennart/projects/seppl](http://0pointer.de/lennart/projects/seppl)

Thank's in advance

---

### Post by slyk on 2005-09-08
[QUOTE=chaumurky]I've just recently built the new vanilla 2.6.13 (It appears to need the --initrd option) However when booting I get this error (a few times in a row):

```
device-mapper: dm-linear: Device lookup failed
device-mapper: error adding target to table
```

Once booted my other two hard disks are not mounted (hdc & hdd).

Can anyone recognise what is missing for this to occur? Is a patch required or something enabled in the config?

Oh, yeah, this is on Breezy, if that makes any difference...[/QUOTE]

You don't really need initrd to boot a vanilla 2.6.13 kernel build on Ubuntu 5.04.

If you are getting this error:
Kernel panic: VFS: Unable to mount root fs on unknown-block(0,0) 

You need to:

A) build your root filesystem support statically into the kernel:
CONFIG_EXT2_FS=y
CONFIG_EXT3_FS=y
CONFIG_REISERFS_FS=y
[or whatever root filesystem you have]

B) build your root device support statically into the kernel:
CONFIG_IDE=y
CONFIG_BLK_DEV_IDE=y
CONFIG_BLK_DEV_IDEDISK=y
[or whatever root device you have]

My advice is to include support for as many devices as possible - that won't bloat  the kernel if they are modules. This way, you won't have to rebuild the kernel every time you plug in a new device or upgrade your computer ;)

---

### Post by luca_linux on 2005-09-12
[QUOTE=odin]Very good howto I should say and thank's, it really helped me at the begining but I have another problem nowreally anoying.I need to select an option in the library routines menu so I have to compile the kernel from www.kernel.org.That's not a problem because I have done it succesfully several times.

The problem is that I need to build a module outside the kernel and for that I need to select crc functions when I do the "make menuconfig".The thing is that I cannot select one of them(the one in the middle which says "CRC32 options" in kernel 2.6..

I'm sure that one is the one I need since I have built the module I need with no errors but a warning saying that the module doesnt have a CRC.I just cant select it neither as a built-in option or as a module.I guess that option depends on others so I'm able to select it but I've tried many conbinations and nothing.

Could anyone help me or guide to find the solution?

What I'm trying to build is seppl-0.4 that you can find in [http://0pointer.de/lennart/projects/seppl](http://0pointer.de/lennart/projects/seppl)

Thank's in advance[/QUOTE]
 There should be a kernel.config of mine somewhere here...Maybe you can give it a look as reference.

---

### Post by odin on 2005-09-13
[QUOTE=luca_linux]There should be a kernel.config of mine somewhere here...Maybe you can give it a look as reference.[/QUOTE]

Thank you very much luca but now the problem is solved.I found in the net a config file I could use and I've got what I needed.

Thank's anyway

---

### Post by prelude on 2005-09-14
hi all

Ive been trying to build a custom kernel for my laptop running Ubuntu 5.10, as the default one got loads and loads of stuff I dont have and never use and this laptop isnt exactly great.. ;)

Ive used the guide in this thread, and downloaded linux-source-2.6.12 with apt-get, then extracted and made the symlink in /usr/src/. made xconfig and waded through the options there customizing for my laptop and then finally, I started the build with
```

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-prelude kernel_image modules_image

```

but Ive encountered a problem. my kernel doesnt complete the build giving me this output.

```

...
  CC      init/version.o
  LD      init/built-in.o
  LD      .tmp_vmlinux1
drivers/built-in.o:(.bss+0x64f4): multiple definition of `debug'
arch/i386/kernel/built-in.o:: first defined here
drivers/built-in.o: In function `dump_stack':
: multiple definition of `dump_stack'
arch/i386/kernel/built-in.o:: first defined here
ld: Warning: size of symbol `dump_stack' changed from 32 in arch/i386/kernel/built-in.o to 51 in drivers/built-in.o
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2

```

it might be something I broke in the config, actually, my best guess it is something I broke in the config as I turned off lots of stuff in there. Im providing my kernel config so someone more experienced can take a look at it and point out obvius mistakes. generally speaking I turned off the devices I know I dont have, and on the things I wasnt shure of I followed the reccomendations in the descriptions of the functions in question.


Edit:

I couldnt figgure out what was wrong, so I binned ubuntu on the laptop and installed it on my desktop instead. so far so good, starting to get a hang of this :)

---

### Post by sktrdie on 2005-09-19
I get this error when running make kpkg after like 20 mins  of compiling:

```
net/ipv4/ip_options.c: In function `ip_options_build':
net/ipv4/ip_options.c:74: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions,
see <URL:file:///usr/share/doc/gcc-3.4/README.Bugs>.
make[3]: *** [net/ipv4/ip_options.o] Error 1
make[2]: *** [net/ipv4] Error 2
make[1]: *** [net] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.12'
make: *** [stamp-build] Error 2
```

---

### Post by Xian on 2005-09-19
```
net/ipv4/ip_options.c: In function `ip_options_build':
net/ipv4/ip_options.c:74: internal compiler error: Segmentation fault
```

Is this an option that you need in the kernel?
If not, unselect it and try the compile again.

---

### Post by sktrdie on 2005-09-19
I cannot find that option in my .config
where should I unselect it, I don't think I need it.

---

### Post by Xian on 2005-09-19
Yeah, looks like you are correct so forget that line of thought.
Here is a mailing list post with a similar compile error.

Perhaps you can find some useful info: [Segmentation Fault](http://www.twuug.org/lists/twuug/2004-07/msg00076.html).

---

### Post by c-m on 2005-09-21
[QUOTE=Xian]Yeah, looks like you are correct so forget that line of thought.
Here is a mailing list post with a similar compile error.

Perhaps you can find some useful info: [Segmentation Fault](http://www.twuug.org/lists/twuug/2004-07/msg00076.html).[/QUOTE]
 i've made two successfull kernels in ubuntu following the instructions here, but since then every time i've tried i have failed. my latest error is here:

> 
fs/fat/inode.c: In function `fat_writepage':
fs/fat/inode.c:91: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[3]: *** [fs/fat/inode.o] Error 1
make[2]: *** [fs/fat] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.13.2'
make: *** [stamp-build] Error 2


I'm not sure what is going wrong. I'm well into double figures on the number of successfull kernel compiles in yopper and gentoo, but for some reason (most likely my own) i tend to get problems with ubuntu.

---

### Post by c-m on 2005-09-21
[QUOTE=Xian]Yeah, looks like you are correct so forget that line of thought.
Here is a mailing list post with a similar compile error.

Perhaps you can find some useful info: [Segmentation Fault](http://www.twuug.org/lists/twuug/2004-07/msg00076.html).[/QUOTE]
 i've made two successfull kernels in ubuntu following the instructions here, but since then every time i've tried i have failed. my latest error is here:

> 
fs/fat/inode.c: In function `fat_writepage':
fs/fat/inode.c:91: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[3]: *** [fs/fat/inode.o] Error 1
make[2]: *** [fs/fat] Error 2
make[1]: *** [fs] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.13.2'
make: *** [stamp-build] Error 2


just tried again istead using "make && make modules_install and this is the error i get:

> 
fs/ext3/balloc.c: In function `ext3_test_allocatable':
fs/ext3/balloc.c:542: internal compiler error: Segmentation fault
Please submit a full bug report,
with preprocessed source if appropriate.
See <URL:http://gcc.gnu.org/bugs.html> for instructions.
For Debian GNU/Linux specific bug reporting instructions, see
<URL:file:///usr/share/doc/gcc-3.3/README.Bugs>.
make[2]: *** [fs/ext3/balloc.o] Error 1
make[1]: *** [fs/ext3] Error 2
make: *** [fs] Error 2



I'm not sure what is going wrong. I'm well into double figures on the number of successfull kernel compiles in yopper and gentoo, but for some reason (most likely my own) i tend to get problems with ubuntu.

---

### Post by sktrdie on 2005-09-24
sorry to bring this thread up again, but I would really like a resolution for this.

---

### Post by zarathustra on 2005-09-26
Sorry if this is a bit off topic, I've downloaded the 2.6.13 kernel, patched it up to the 2.6.14rc2 with mm patch, which has drivers for my wireless card. However, I'm a bit stuck as to how to get my card working once the new kernel is installed, does anyone have any idea? It's the acx drivers for a US Robotics wireless card.

---

### Post by bluemist on 2005-09-26
Hi.

I am about to do this kernel compilation. What I want to know though is... can I UNDO this? Supposed I didn't like my compiled kernel, how can I delete it and use the previous/default kernel that I had?

EDIT: Okay, so I see the GRUB boot loader shows my existing kernels, but suppose I want to delete the custom kernel that doesn't work (didn't work because I didn't compile with --initrd), how do I? Is it as simple as deleting it in Synaptic? Isn't it that I need to configure GRUB?

---

### Post by luca_linux on 2005-09-27
[QUOTE=zarathustra]Sorry if this is a bit off topic, I've downloaded the 2.6.13 kernel, patched it up to the 2.6.14rc2 with mm patch, which has drivers for my wireless card. However, I'm a bit stuck as to how to get my card working once the new kernel is installed, does anyone have any idea? It's the acx drivers for a US Robotics wireless card.[/QUOTE]
Don't know about your card in particular: try to search for its module and load it with modprobe.

---

### Post by luca_linux on 2005-09-27
[QUOTE=bluemist]Hi.

I am about to do this kernel compilation. What I want to know though is... can I UNDO this? Supposed I didn't like my compiled kernel, how can I delete it and use the previous/default kernel that I had?

EDIT: Okay, so I see the GRUB boot loader shows my existing kernels, but suppose I want to delete the custom kernel that doesn't work (didn't work because I didn't compile with --initrd), how do I? Is it as simple as deleting it in Synaptic? Isn't it that I need to configure GRUB?[/QUOTE]
Yeah, just remove it through Synaptic: it will update the GRUB list automatically.

---

### Post by leverknight1 on 2005-09-27
i get to the part about customizing the kernel and i get this 
```
root@ubuntu-micron:/usr/src/linux # sudo make xconfig
rm -f include/asm
( cd include ; ln -sf asm-i386 asm)
make -C scripts kconfig.tk
make[1]: Entering directory `/usr/src/linux-2.4.21/scripts'
gcc -Wall -Wstrict-prototypes -O2 -fomit-frame-pointer -c -o tkparse.o tkparse.c
make[1]: gcc: Command not found
make[1]: *** [tkparse.o] Error 127
make[1]: Leaving directory `/usr/src/linux-2.4.21/scripts'
make: *** [xconfig] Error 2

```

and i cant get passed it i have tryed multiple times what should i do?

---

### Post by luca_linux on 2005-09-28
You have to install the packages build-essential and gcc.

---

### Post by mpvano on 2005-10-18
Hi:

This thread seems to have gotten a bit out of control and seems to be quite confusing to read because it's full of examples that special case the build process in such a way that it only works for non-standard config files.

Once a basic reference build is working, modifying the standard config file is easy and could be left to the reader. All these Interesting customizations might better be discussed in a separate thread.

Could someone post a TESTED update to it that shows a starting point for the ACTUAL breezy?

That is to say, one that clearly describes:

- the exact packages to add to a basic breezy install to duplicate standard kernels 
- the exact commands for duplicating the build of the simplest stadard kernel
- the exact commands for installing that kernel into the standard breezy

None of the existing complete examples seem to work with the standard breezy as a starting point.  Ideally, it would be nice to have this info as part of the breezy documentation or frozen as an FAQ of some sort that supercedes and clarifies all of the confusing information in this thread.

I've been building variant kernels for most of the major linux distributions for many years now, but I can't seem to find the information in this thread (or elsewhere) to create and install a working, reference breezy kernel based on the distributed ones.

thanks,

Mario Vano

---

### Post by jonathanzeuston on 2006-03-30
I installed my new compiled kernel 2.6.16.1 successfully.
but have trouble with my sd and USB disk mount

# mount /dev/mmcblk0p1 mmc/
mount: /dev/mmcblk0p1 already mounted or mmc/ busy

# fdisk -l

Disk /dev/mmcblk0: 1023 MB, 1023410176 bytes
4 heads, 16 sectors/track, 31232 cylinders
Units = cylinders of 64 * 512 = 32768 bytes

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1       31232      999416   83  Linux

---

### Post by garba on 2006-03-30
[QUOTE=luca_linux]I thought to write this HowTo, since the kernel compile process on Ubuntu is made easier because this distro is debian-based.
First of all, download the kernel package you like from [kernel.org](http://www.kernel.org) or from the Ubuntu repositories.
If you want the official kernel patched by the Ubuntu Team, just type:
```
sudo apt-get install linux-tree
```
In this case we'll use the latest stable vanilla kernel version available.
For the compile process you'll need the following packages on Ubuntu:
```

sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc
sudo apt-get install libncurses5
sudo apt-get install libncurses5-dev
sudo apt-get install libqt3-mt-dev

```
Now untar the package:
```

cd /usr/src
sudo tar --bzip2 -xvf linux-2.6.12.tar.bz2

```
Create the following symlink:
```

sudo ln -s /usr/src/linux-2.6.12 /usr/src/linux
cd /usr/src/linux

```
Now you can start customizing your kernel configuration; there two way, the first one is graphical, the second one pseudo-graphical:
```
sudo make xconfig
```
Or:
```
sudo make menuconfig
```
Then, after having finished the customization, we have to start the compile process:
```

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-custom kernel_image modules_image

```
The revision flag is optional and is just useful to edit the kernel name showed through uname -r. You can write whatever you want instead of "-custom".

There's also another interesting and useful flag, that is --initrd. The vanilla kernel is not enable yet to make use of initrd properly, and in fact there's a patch for this. The Ubuntu official kernel is a vanilla kernel patched with some patches among which there's the one for initrd. So, if you are compiling a vanilla kernel, you should take --initrd out; otherwise, if you are compiling a Ubuntu kernel, you can make use of initrd and you probably would that.

Note that now you'll have a .deb package in /usr/src ready to be installed as any other package through a simple double-click.
Grub will be updated automatically.
So, just type:
```
sudo dpkg -i kernel-image-2.6.12-custom_10.00.Custom_i386.deb
``` 

Enjoy.[/QUOTE]


luca_linux

I don't want to sound like mr-knows-it-all, please forgive me but your guide is slightly misleading, because:

1) There's no reason on earth why you should login as root to compile a new kernel, you can fetch the source, copy it over to your home dir, and then use fakeroot to do the mkpg-thing. You only need to be root to actually INSTALL the new kernel.
2) The /usr/src/linux symlink is a dread thing rising from the past, it's no longer needed, besides, the reason for being there in the first place was a non-sense. Torvalds himself took a strong stance against this perverted practice. ;) 

It's true that it's good practice to store the expanded kernel source in /usr/src for reference, but in my opinion you should first build the deb as an unprivileged user, and then, as root, dpkg -i the package, move the source tree from your home dir to /usr/src and then amend the symlinks in /lib/modules/<kernel-version> to make them point to the kernel source, which should be now in /usr/src/<kernel-version>.

Regards, andre

---

### Post by bunty on 2006-06-13
Long old thread but the length shows how useful it's been to so many, thanks a lot Luca.

I am pretty familiar with building custom kernel using Gentoo but have never managed to get one to boot on a Deb bases system!

I tried the usual *make && make modules modules_install *but it failed to boot so I have spent a lot of time searching and reading on debian ways of doing it but am getting no further.

I am sure it is some preconception I have from other systems or some trivial detail I am missing but I need someone to point it out to me.

```

cd /usr/src/linux
make menuconfig

sudo make-kpkg clean
sudo make-kpkg --append-to-version=-opt kernel_image modules_image
dpkg -i ../*deb

```

I am compiling from 2.6.15 kernel source.

I have /boot on hda3 , it starts to boot but fails with 

*root device not found hda22 or missing block (0,0)  *


the root fs is on /dev/hda22 and boots fine with the std kernel but that was with an initrd.

I get the impression that /dev is not getting populated but dont know where to look , this is supposed to be a udev system.

TIA for any bright suggestions. :D

---

### Post by bunty on 2006-06-13
OK , it will boot if I use --initrd and boot with that.

I now have added reiser4 support which was my basic reason for all this and it went very sweetly.

My remaining Deb question is why do I need and initrd and how do I remove this need?

TIA :D

---

### Post by tseliot on 2006-06-13
[QUOTE=bunty]My remaining Deb question is why do I need and initrd and how do I remove this need?

TIA :D[/QUOTE]
I'll tell you the truth: I have no idea. It's always been like that (since Ubuntu 5.04).

---

### Post by neuropsychguy on 2006-06-20
Thanks for the comiling guide. After a little tweaking I was able to compile the new 2.6.17 kernel. No problems so far (well, I have to get my wireless working again, but that's no problem). =D>

---

### Post by sailingboarder on 2006-11-16
wonderful quide, looks quite helpful

i am beginning the process of rebuilding my kernel for the first time
all i am trying to do is add support for my built in infrared port, and everywhere i look seems to be pointing me towards the kernel

i could not find the linux tree under ```
sudo apt-get instal linux-tree
```
but i did download linux-686 from apt-get and also the linux package from synaptic

however, when i try to unarchive the tar file, i can't find it
it is not under /usr/src as the guide says, nor could a search of my file system find any *.tar file
where are the sources located?

all i want to do is update my ubuntu kernel to include infrared support, i don't want to mess anything up by making a whole new kernel, at least not yet

tia, and hopefully everything will work fine

---

### Post by abobo on 2006-11-16
When I follow these instructions I end up with:
```
  LD      .tmp_vmlinux1
arch/x86_64/kernel/built-in.o: In function `get_smp_config':
(.init.text+0x7c3f): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `clustered_apic_check':
(.init.text+0x7d94): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `setup_early_printk':
(.init.text+0x813f): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `iommu_hole_init':
(.init.text+0x8e33): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o: In function `printk_address':
(.text.printk_address+0xb9): undefined reference to `__stack_chk_fail'
arch/x86_64/kernel/built-in.o:(.text.arch_ptrace+0x7e4): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.14'
make: *** [debian/stamp-build-kernel] Error 2


```

I am running:
```
Linux 2.6.17-10-generic #2 SMP Fri Oct 13 15:34:39 UTC 2006 x86_64 GNU/Linux

```

Any suggestions on what I might be missing?  Google has found a number of hits on my compile  error, but all posts are unanswered.

---

### Post by GQed76 on 2006-11-23
nm

---

### Post by hansworst on 2006-12-16
While compiling I get this error:

  LD      .tmp_vmlinux1
init/built-in.o: In function `try_name':
do_mounts.c:(.text+0x5e3): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `name_to_dev_t':
(.text+0x8cb): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `change_floppy':
(.init.text+0xa11): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `mount_block_root':
(.init.text+0xca7): undefined reference to `__stack_chk_fail'
init/built-in.o: In function `do_header':
initramfs.c:(.init.text+0x4343): undefined reference to `__stack_chk_fail'
arch/i386/kernel/built-in.o:(.text+0x54c6): more undefined references to `__stack_chk_fail' follow
make[1]: *** [.tmp_vmlinux1] Error 1
make[1]: Leaving directory `/usr/src/linux-2.6.17.10'
make: *** [debian/stamp-build-kernel] Error 2

What should I do? Thanks in advance!

---

### Post by noobaholic on 2007-01-08
Add -fno-stack-protector to CFLAGS

---

### Post by NattyFido on 2007-02-06
Thank you Luca, my first Kernel compile!!

It too nearly all day to finish compiling on my ancient Pentium 2 266MHz, but I got there in the end!!!
:lolflag:

---

### Post by melkor12 on 2007-02-06
> **noobaholic said:**
> Add -fno-stack-protector to CFLAGS

How do I do that?
Has anyone tried that?

thanks

---

### Post by garba on 2007-02-06
> **melkor12 said:**
> How do I do that?
Has anyone tried that?

thanks

that's an "environment variable", see "export" in the man pages

---

### Post by Megatog615 on 2007-02-15
Can somebody update the main tutorial on the first page? This seems like the only kernel compilation tutorial here and it is horribly outdated.

---

### Post by thor918 on 2007-03-10
and what if your new kernel boot's up just fine, but the screen is black?

---

### Post by king_arthur on 2007-06-22
Hi there everybody,

looks like linux-tree is gone a long time ago.

What is the replacement for it?


/P

---

### Post by phoenixjim on 2007-07-01
I believe that the replacement for linux-tree is linux-source. That's what I used.

Jim

---

### Post by cborga1985 on 2007-07-01
more up to date kernel howto [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)

---

### Post by sudhakar.sah on 2007-07-09
Hi
  

   I am trying to work on linux device drivers so i first tried to compile my kernel 
these are the steps i followed 
1. downloaded latest kernel
2. copied to /usr/src
3. un tar to the same dir
4. inside the directory typed make menuconfig 
but at this stage i am getting lot of errors 
i dont know how to counter this one becoz lat time i did the same thing with Cent OS and it got compiled 
Please tell me where i am wrong 


Sudhakar

---

### Post by Icarosaurus on 2007-07-09
In Ubuntu Feisty, for getting the latest Ubuntu patched kernel, you should write:
```

sudo apt-get install linux-source

```
linux-tree doesn't work for me too.
I think the howto should be fixed.

---

### Post by i.nihilist on 2007-07-11
I have downloaded the kernel versiosn 2.6.6 on my ubuntu 7.04 desktop edition
And unzipped the file into /usr/src/

also made the link as suggested in the HowTo

And then when i do cd linux
and then do make menuconfig

i'm getting the following errors..!!!

root@vikram-laptop:/usr/src/linux# make menuconfig
  HOSTCC  scripts/basic/fixdep
scripts/basic/fixdep.c:97:23: error: sys/types.h: No such file or directory
scripts/basic/fixdep.c:98:22: error: sys/stat.h: No such file or directory
scripts/basic/fixdep.c:99:22: error: sys/mman.h: No such file or directory
scripts/basic/fixdep.c:100:20: error: unistd.h: No such file or directory
scripts/basic/fixdep.c:101:19: error: fcntl.h: No such file or directory
scripts/basic/fixdep.c:102:20: error: string.h: No such file or directory
scripts/basic/fixdep.c:103:20: error: stdlib.h: No such file or directory
scripts/basic/fixdep.c:104:19: error: stdio.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from scripts/basic/fixdep.c:105:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
scripts/basic/fixdep.c:106:19: error: ctype.h: No such file or directory
scripts/basic/fixdep.c:107:24: error: netinet/in.h: No such file or directory
scripts/basic/fixdep.c: In function 'usage':
scripts/basic/fixdep.c:121: warning: implicit declaration of function 'fprintf'
scripts/basic/fixdep.c:121: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:121: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:121: error: (Each undeclared identifier is reported only once
scripts/basic/fixdep.c:121: error: for each function it appears in.)
scripts/basic/fixdep.c:122: warning: implicit declaration of function 'exit'
scripts/basic/fixdep.c:122: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'print_cmdline':
scripts/basic/fixdep.c:127: warning: implicit declaration of function 'printf'
scripts/basic/fixdep.c:127: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:130: error: 'NULL' undeclared here (not in a function)
scripts/basic/fixdep.c: In function 'grow_config':
scripts/basic/fixdep.c:143: warning: implicit declaration of function 'realloc'
scripts/basic/fixdep.c:143: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:145: warning: implicit declaration of function 'perror'
scripts/basic/fixdep.c:145: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c: In function 'is_defined_config':
scripts/basic/fixdep.c:161: warning: implicit declaration of function 'memcmp'
scripts/basic/fixdep.c: In function 'define_config':
scripts/basic/fixdep.c:174: warning: implicit declaration of function 'memcpy'
scripts/basic/fixdep.c:174: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c: In function 'use_config':
scripts/basic/fixdep.c:193: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:201: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:207: warning: implicit declaration of function 'tolower'
scripts/basic/fixdep.c:209: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:193: warning: unused variable 's'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:212: error: expected declaration specifiers or '...' before 'size_t'
scripts/basic/fixdep.c: In function 'parse_config_file':
scripts/basic/fixdep.c:214: error: 'len' undeclared (first use in this function)
scripts/basic/fixdep.c:220: warning: implicit declaration of function 'ntohl'
scripts/basic/fixdep.c:231: warning: implicit declaration of function 'isalnum'
scripts/basic/fixdep.c: In function 'strrcmp':
scripts/basic/fixdep.c:244: warning: implicit declaration of function 'strlen'
scripts/basic/fixdep.c:244: warning: incompatible implicit declaration of built-in function 'strlen'
scripts/basic/fixdep.c: In function 'do_config_file':
scripts/basic/fixdep.c:255: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:259: warning: implicit declaration of function 'open'
scripts/basic/fixdep.c:259: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:261: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:261: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:263: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:265: warning: implicit declaration of function 'fstat'
scripts/basic/fixdep.c:267: warning: implicit declaration of function 'close'
scripts/basic/fixdep.c:270: warning: implicit declaration of function 'mmap'
scripts/basic/fixdep.c:270: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:270: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:270: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:277: error: too many arguments to function 'parse_config_file'
scripts/basic/fixdep.c:279: warning: implicit declaration of function 'munmap'
scripts/basic/fixdep.c:255: warning: unused variable 'st'
scripts/basic/fixdep.c: At top level:
scripts/basic/fixdep.c:284: error: expected declaration specifiers or '...' before 'size_t'
scripts/basic/fixdep.c: In function 'parse_dep_file':
scripts/basic/fixdep.c:287: error: 'len' undeclared (first use in this function)
scripts/basic/fixdep.c:289: error: 'PATH_MAX' undeclared (first use in this function)
scripts/basic/fixdep.c:291: warning: implicit declaration of function 'strchr'
scripts/basic/fixdep.c:291: warning: incompatible implicit declaration of built-in function 'strchr'
scripts/basic/fixdep.c:293: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:293: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:294: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:296: warning: incompatible implicit declaration of built-in function 'memcpy'
scripts/basic/fixdep.c:297: warning: incompatible implicit declaration of built-in function 'printf'
scripts/basic/fixdep.c:289: warning: unused variable 's'
scripts/basic/fixdep.c: In function 'print_deps':
scripts/basic/fixdep.c:325: error: storage size of 'st' isn't known
scripts/basic/fixdep.c:329: error: 'O_RDONLY' undeclared (first use in this function)
scripts/basic/fixdep.c:331: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:331: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:333: warning: incompatible implicit declaration of built-in function 'exit'
scripts/basic/fixdep.c:337: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:341: error: 'PROT_READ' undeclared (first use in this function)
scripts/basic/fixdep.c:341: error: 'MAP_PRIVATE' undeclared (first use in this function)
scripts/basic/fixdep.c:341: warning: assignment makes pointer from integer without a cast
scripts/basic/fixdep.c:348: error: too many arguments to function 'parse_dep_file'
scripts/basic/fixdep.c:325: warning: unused variable 'st'
scripts/basic/fixdep.c: In function 'traps':
scripts/basic/fixdep.c:360: warning: incompatible implicit declaration of built-in function 'fprintf'
scripts/basic/fixdep.c:360: error: 'stderr' undeclared (first use in this function)
scripts/basic/fixdep.c:362: warning: incompatible implicit declaration of built-in function 'exit'
make[1]: *** [scripts/basic/fixdep] Error 1
make: *** [scripts_basic] Error 2


Can ayone tell me what is wrong?

---

### Post by garba on 2007-09-08
i swear one of these days im putting a bounty on people building a custom kernel as root in /usr/src :lolflag:

---

### Post by weijiantao on 2007-09-11
I followed the procedure carefully. However, after building is complete, I can not find *.deb file at all in top level kernel tree. In the end of the build, there is following output, 

Thanks in advance,

Brian Wei
AGCO Corporation


====== making stamp-kernel-image because of  ======
This is kernel package version 10.065ubuntu5.
echo done > stamp-kernel-image
====== making target kernel_image [new prereqs: stamp-configure stamp-build-kernel stamp-kernel-image]======
This is kernel package version 10.065ubuntu5.
for module in  ; do                       \
          if test -d  $module; then                                \
            (cd $module;                                          \
              if ./debian/rules KVERS="2.6.20.3-ubuntu1-custom" KSRC="/usr/src/linux" \
                             KMAINT="Unknown Kernel Package Maintainer" KEMAIL="unknown@unconfigured.in.etc.kernel-pkg.conf"      \
                             KPKG_DEST_DIR="/usr/src/linux/.."       \
                             KPKG_MAINTAINER="Unknown Kernel Package Maintainer"        \
                             KPKG_EXTRAV_ARG="EXTRAVERSION=.3-ubuntu1-custom"        \
                             ARCH="i386"                  \
                             KDREV="2.6.20.3-ubuntu1-custom-10.00.Custom" kdist_image; then    \
                  echo "Module $module processed fine";            \
              else                                                  \
                   echo "Module $module failed.";                  \
                   if [ "X" != "X" ]; then      \
                      echo "Perhaps $module does not understand --rootcmd?";  \
                      echo "If you see messages that indicate that it is not"; \
                      echo "in fact being built as root, please file a bug ";  \
                      echo "against $module.";                     \
                   fi;                                              \
                   echo "Hit return to Continue";                   \
                 read ans;                                        \
              fi;                                                   \
             );                                                    \
          else                                                      \
               echo "Module $module does not exist";               \
               echo "Hit return to Continue?";                      \
          fi;                                                       \
        done

---

### Post by wanadobee on 2007-12-19
Hi,

I was at step #2:

> sudo apt-get install kernel-package

and I got the following error:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package kernel-package

I googled but there wasn't much about it, so I figured Ubuntu couldn't download the files. I don't know how to fix it from console but I went to the menu **System > Administration > Software Sources**. 
In the Ubuntu Software tab, I have enabled **Source Code, Canonical-supported and Canonical-maintened.** I tried again and it worked.

I don't knowhow to fix it from console, maybe someone else can post it. 

I guess the problem came from the fact that during Ubuntu installation there was no internet connection, so Ubuntu disabled all the updates through the internet.

Hope it helps, other then this a very helpful tutorial.

---

### Post by wanadobee on 2007-12-19
I forgot also that:

> sudo apt-get install linux-tree

gave me the error:

> danilo@danilo-desktop:/usr/src$ sudo apt-get install linux-tree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-tree


but the command:

> sudo apt-get install linux-source

ùworked well and downloaded the source code.

---

### Post by JonNicc on 2008-02-26
Thank you, Luca_Linux. With your help, and that of tseliot, I successfully compiled and installed my first kernel, 2.6.24.2 . As I told tseliot, have a double shot cappuccino, and I'll donate the cost to Ubuntu. 

Thanks again.:)

JonNicc

---

### Post by maniacneron on 2008-03-03
hi i'am a newb about ubuntu.I need to add a system call to current kernel of to ubuntu 7.10 it may be a very simple task. i made some researchs that tell how to add a system call i need to make some changes at file "entry.s" but i can not find  such a file at the adress "arch/i386/kernel/entry.S" can anybody help me i don't know if the file is in another place or the name of the file changed.

I will be very happy if you can help me thanks a lot.

---

### Post by Godslove on 2008-05-22
How to update kernel on Ubuntu Feisty Fawn without internet connection. I have installed ubuntu desktop version 7.04 and they are unable to detect my network IC and i can't seem to find a way to install the driver besides updating the kernel...anyone can help?

---

### Post by Sam Lars on 2008-06-04
> **Godslove said:**
> How to update kernel on Ubuntu Feisty Fawn without internet connection. I have installed ubuntu desktop version 7.04 and they are unable to detect my network IC and i can't seem to find a way to install the driver besides updating the kernel...anyone can help?

You should be able to grab a newer Ubuntu kernel from the repositories or a vanilla from the kernel site and follow this guide.

---

### Post by unpredictablelinux on 2010-03-01
Hi Just a quick question, I'm following your howto i need to know something.

sudo make-kpkg --append-to-version=-custom kernel_image modules_image

Do i have to type --append-to-version=-custom. Does the append have to be done if i am upgrading the kernel itself to a new one? or will i just type make -kpkg -custom 

You said we can rename -custom to whatever we want but can u tell me what, is kernel_image modules_image a command. Can u help me to understand that command

Thanks indvance..

---

