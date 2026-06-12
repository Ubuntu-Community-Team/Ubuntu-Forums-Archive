---
title: "First time: 8.04 LTS: Grub issues"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by DThurman on 2008-10-16
I have downloaded Ubunto 8.04 LTS (desktop) (standard)
ISO file, created the boot CD, booted the CD, and began
installing Ubunto.

I have specified the installation partitions as follows:
/dev/sda10 - /boot
/dev/sda11 - /root
/dev/sda6  - swap

Also, since my system has other OS's and distros
already installed, I do not want Ubunto to install
the bootloader as one already exist and I want to
keep my current bootloader as it is. So I have selected
the 'Advanced' button and unchecked "Install Bootloader"
and assumed that grub would still be installed, just not
the bootloader? (Previously, I did left the "Install
Bootloader" checked but specified that the bootloader be
installed into /dev/sda10, but grub was not installed either,
so it appears that either way, grub (stage1) was never installed)

So, after the installation was "completed", the installer
proceeded to startup the desktop with the "Examples" folder
and the "Install" Icon on the Desktop. So I am still in
the install stage (I have tried rebooting, but of course
it failed to boot Ubunto, so I am at the second CD reboot)
and remaining here until I get advice/help in this forum
as I type this message.

Next, I fired up the Terminal application, and
ran `sudo passwd root', set the password, and
proceeded to review the contents of /target and
/target/boot

In the two cases where I allowed/disallowed bootloader
to be installed, I found that Ubunto did install the
basic packages, and did create files in /target/boot
as follows:

abi-2.6.24-19-generic     memtest86+.bin
config-2.6.24-19-generic  System.map-2.6.24-19-generic
vmlinuz-2.6.24-19-generic lost+found

It seems that the grub directory (with it's stage one
contents) are missing and a missing initrd, although the
vmlinuz is there.

I also discovered that there is a /boot directory and
the contents are:

abi-2.6.24-19-generic        grub
System.map-2.6.24-19-generic config-2.6.24-19-generic
memtest86+.bin               vmlinuz-2.6.24-19-generic

grub:
device.map

So, the grub directory was installed in /boot, but there
is no initrd, there is device.map but no stage1 and
other related files (grub.conf)

So, I tried:

# grub-install /dev/sda10
Could not find device for /boot: Not found or not a block device.

# mkinitrd initrd-2.6.24-19-generic 2.6.24-19
bash: mkinitrd: command not found

Strangely, mkinitrd is missing, so I cannot create initrd.

So - my question is - what can I do at this point, i.e.
how can I get grub installed in my /dev/sda10 partition
and how can I get initrd built?

Thanks!
Dan

---

### Post by philinux on 2008-10-16
Using the terminal enter grub.

**Installing Grub to PBR (Partition Boot Record): **

 grub> setup (hd0,1) **change this to suit your system.**
This installs Grub into the second partition of the first disk 
If you install GRUB into a partition or a drive other than the first one, you must chain-load GRUB from another boot loader.
If you do that you're supposed to know how to chainload 
grub> quit  
quit makes you leave the grub "terminal" On occasion this has generated an "error 27". If so use the reset button or if in a gnome/KDE terminal just close it. Reboot and you will find your grub menu again. 
If the method above does not work, maybe Super Grub helps you: 

You can either use the chainloader command in your main grub menu.lst or use config file like I do to boot intrepid on my second hard drive.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Me.
# linux installation on /dev/sdb1.

title Intrepid GRUB configuration file
configfile (hd1,0)/boot/grub/menu.lst
philcb@philcb-desktop:~$ 

```

---

### Post by DThurman on 2008-10-16
Fast response!  Thanks!

Ok, I now have grub installed in the boot
partition (/dev/sda10)!  But alas, I do not
have initrd in order to proceed.

Side question:  I downloaded the ISO from the Ubunto
site ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)) and
used this to install Ubunto but nothing was said that
this was a "Live CD" ISO boot disc.  This particular
ISO gives you a menu of choices, one of which you can
install the product - but having done this already,
how to I skip that and go directly to "Live" mode
without the install menu item?

When I searched for "Live CD" I was directed to a
different page ([http://releases.ubuntu.com/hardy/](http://releases.ubuntu.com/hardy/))
and there it shows the 8.04.1 and I am wondering if
this ISO is the same thing? Can you clarify this?

What I want to do is to build the initrd (which is
missing) and need the correct boot/live cd in order
to carry out this last step and one that supports
mkinitrd which was missing from the first ISO I used
to install the product?

Thanks!
Dan

---

### Post by philinux on 2008-10-16
Not sure on this.

but if you installed from the livecd but just missed out the grub. Then as long as you've edited your main /boot/grub/menu.lst as shown above to use the config file then reboot and select your config file boot stanza.

---

### Post by lswb on 2008-10-16
The ubuntu installer normally will put your kernel and initrd in /boot (A subdirectory of / , not a /boot partition unless you have manually configured it this way) and provide symlinks in / to the installed kernel. So if you do ls /boot it should show something like: 

abi-2.6.24-21-generic         initrd.img-2.6.24-21-generic.bak
config-2.6.24-21-generic      System.map-2.6.24-21-generic
initrd.img-2.6.24-21-generic  vmlinuz-2.6.24-21-generic

In your ubuntu / partition the symlinks to the most recent kernel and initrd.img will be simply named vmlinuz and initrd.img

I would not make a separate /boot partition for ubuntu, just use a subdirectory of /
I am guessing that where you wrote /root above you really meant just / . Is that correct?

You shouldn't have to make an initrd.img from scratch. Perhaps try the installer again, maybe it was interrupted before the initrd was copied to the hd the 1st time.
Try to install grub to your ubuntu / partition and you can boot it by using a chainloader statement in your main bootloader grub. Or, you could just put direct kernel and initrd lines in the main boot grub, but then every time there is a kernel upgrade you'll have to edit them.

---

### Post by DThurman on 2008-10-16
Thanks for responding.

Yes, by stating /root, I meant /

The reason I created a separate /boot partition is/was
because from experience - I had noted with other distros,
that somehow changing the / partition (via directory
creation at the root level), mucks up the grub /boot
"reference" and when it does, rebooting/booting, grub
fails to find /boot and falls back into the grub prompt.

So it is/was standard practice (for me) that one does not
put the boot contents directly into /boot, but insteads
mounts the boot partition onto /boot so that the grub
reference was retained. Maybe this has changed "recently",
but I have never had problems with grub boot again.

One should not have to worry about adding symlinks in /
to point to vmlinuz and initrd in the boot partition or
to /boot, because the /etc/fstab entries mounts the boot
device partition onto /boot.  Maybe Ubunto does things
differently than Fedora - of which I am a heavy user.

As for the creation of initrd - I have twice tried to fresh-install
from the boot CD and it fails to install initrd and there was no
interruption from what I can tell.  It is possible that the problem
was caused due to the fact I used the "import" users feature to
import users from the fedora root partition (which it failed to
create the users anyway, but there was no reported errors), so I
dunno what is going on there.  I have not (yet) tried to fresh-install
without this import feature to see if this is the case.

Since I am downloading the 2nd "Live CD" at the moment as I write,
unless I can get a Live-CD running (without the installer), and
if I fail to get mkinitrd to work - I may be forced to do a third
fresh-install and try this time without that "import" feature and
maybe the initrd will work this time, but if not, then I am back
to "square one".

Hmm..  I hope "the third time works like a charm", but certainly
I will let you know and in this thread. :D

Dan

---

### Post by philinux on 2008-10-16
If you use the alternate text based install cd, the advance option has one to install grub to wherever you like if I remember.

---

### Post by DThurman on 2008-10-16
I found out that there is no difference between the
two ISO Install CDs.  For both, I completely missed
the first menu item - Live CD is there.

I tried many ways to install Ubunto, I ignored the
user import feature, I have unchecked install bootloader,
I have checked bootloader to hd0,0 and to hd0,11 and none
of these attempts created the needed initrd.img file.

mkinitrd does not exist on either boot ISO CDs so I
cannot manually create it.

I have been able to get grub installed but without
the initrd file, I am dead in the water.

Can someone please let me know where I can go from here?

Thanks!
Dan

---

### Post by lswb on 2008-10-16
> **DThurman said:**
> Thanks for responding.

Yes, by stating /root, I meant /

The reason I created a separate /boot partition is/was
because from experience - I had noted with other distros,
that somehow changing the / partition (via directory
creation at the root level), mucks up the grub /boot
"reference" and when it does, rebooting/booting, grub
fails to find /boot and falls back into the grub prompt.

So it is/was standard practice (for me) that one does not
put the boot contents directly into /boot, but insteads
mounts the boot partition onto /boot so that the grub
reference was retained. Maybe this has changed "recently",
but I have never had problems with grub boot again.

This sounds like perhaps your menu.lst is set up something like

root      (hd0,9)
kernel    /vmlinuz-2.x.x.x root=(hd0,10) ....

Where (hd0,9) is the /boot partition and (hd0, 10) is the / partition where /boot is mounted.

With a boot directory, it would be 

root    (hd0,10)
kernel  /boot/vmlinuz-2.x.x.x root=(hd0,10) .....

If you've set it up to use /boot partitions, do you use a separate /boot partition for each distro? Just curious about that.

> **DThurman said:**
> 
One should not have to worry about adding symlinks in /
to point to vmlinuz and initrd in the boot partition or
to /boot, because the /etc/fstab entries mounts the boot
device partition onto /boot.  Maybe Ubunto does things
differently than Fedora - of which I am a heavy user.


The symlinks are more a convenience than anything else. The default grub does point to the actual kernel & initrd, but if things get messed up and you need to manually boot from the grub command line, it is easier to find and type the simple symlink names than the full path and kernel name.

> **DThurman said:**
> 
As for the creation of initrd - I have twice tried to fresh-install
from the boot CD and it fails to install initrd and there was no
interruption from what I can tell.  It is possible that the problem
was caused due to the fact I used the "import" users feature to
import users from the fedora root partition (which it failed to
create the users anyway, but there was no reported errors), so I
dunno what is going on there.  I have not (yet) tried to fresh-install
without this import feature to see if this is the case.

Dan

I'm not sure what's going on with that initrd. Are you saying that the kernel was installed but the initrd.img was not? That seems really strange. Something to check: is there anything in the /boot directory of the ubuntu / that is used as the mountpoint for the boot partition? That is, is that directory empty? Maybe the initrd was installed there. Or, if you do in fact have different partitions that are mounted as /boot by different directories, maybe the initrd.img and kernels were somehow copied to the wrong partition?

Also, not sure if it has anything to do with the "import users" problem, but IIRC fedora starts numbering regular users at 500 while ubuntu starts at 1000.

I'll be interested to see the resolution of your problems. Good luck!

---

### Post by DThurman on 2008-10-17
> **lswb said:**
> This sounds like perhaps your menu.lst is set up something like

root      (hd0,9)
kernel    /vmlinuz-2.x.x.x root=(hd0,10) ....

Where (hd0,9) is the /boot partition and (hd0, 10) is the / partition where /boot is mounted.

With a boot directory, it would be 

root    (hd0,10)
kernel  /boot/vmlinuz-2.x.x.x root=(hd0,10) .....

If you've set it up to use /boot partitions, do you use a separate /boot partition for each distro? Just curious about that.


One more thing:

root      (hd0,9)
kernel    /vmlinuz-2.x.x.x root=(hd0,10)
initrd    /initrd.img-2.x.x.x  <<<=== What about this?

Since I do not find initrd.img\* *anywhere* after install
I am beginning to think Ubunto does not require it?  I
looked for initrd under, over, and in-between and it is
nowhere to be found.

> **lswb said:**
> 
The symlinks are more a convenience than anything else. The default grub does point to the actual kernel & initrd, but if things get messed up and you need to manually boot from the grub command line, it is easier to find and type the simple symlink names than the full path and kernel name.


Agreed.

> **lswb said:**
> 
I'm not sure what's going on with that initrd. Are you saying that the kernel was installed but the initrd.img was not? That seems really strange. Something to check: is there anything in the /boot directory of the ubuntu / that is used as the mountpoint for the boot partition? That is, is that directory empty? Maybe the initrd was installed there. Or, if you do in fact have different partitions that are mounted as /boot by different directories, maybe the initrd.img and kernels were somehow copied to the wrong partition?


The kernel is there, no problem, but as I said, over and over
- initrd is NOT CREATED!  I tried installing the most basic way
possible. the most convoluted as I could - nothing I tried produced
initrd!  I looked in the install areas (when LiveCD is loaded), in
the target areas, in /boot, in the mounted FS areas, everywhere I
could look and did not find the "Easter Egg".

The ONLY thing that LiveCD created in / FS is a symlink:

vmlinuz -> boot/vmlinuz-2.6.24-19-generic [OK]
initrd.img -> boot/initrd.img-2.6.24-19-generic [Broken Link]

I did a `find' through the ENTIRE disk under Fedora where all
partitions are mounted under /media and initrd.img\* is nowhere
to be found!

> **lswb said:**
> 
Also, not sure if it has anything to do with the "import users" problem, but IIRC fedora starts numbering regular us which is terrible IMOers at 500 while ubuntu starts at 1000.


Yes, I noted that.  But still - if it is a IMPORT - those
"differences" should have been resolved as it *seemed* to
imply and they did not work in importing my fedora user profiles.


> **lswb said:**
> 
I'll be interested to see the resolution of your problems. Good luck!

No resolution at this time.  I have tried everything I can throw
at Ubunto 8.04-1.  The fact is (at least for me), is that grub
actually failed to install and work properly (I had to MANUALLY
add grub to boot (grub's 'setup' did not actually work, nor
did grub-install), and initrd failed to be created (and there is
no mkinitrd available during the Live/Install CD in case things
screw up).

I am tempted to try the new Beta CD and toss 8.04-1 out the window.

Grr.
Dan

---

### Post by Keen101 on 2008-10-17
You could always try the super grub disk. Not sure if it will help in your weird situation, but you should know all options.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by lswb on 2008-10-17
I checked on my system and found that ubuntu (and I suppose any debian based distro) uses the name mkinitramfs (and update-initramfs) instead of mkinitrd. I didn't boot a live CD to see if it is included, but I would think it must have some way to generate the initrd.img for an installation. OTOH with the failed grub installation there may be other problems that the live CD installer is having with your system. Maybe you could try the alternate install CD.

From what the manpages for mkinitramfs says, you might be able to boot with one generated on another system using the same kernel & architecture. If you can't build one I can send you a copy of mine if you like. I have
 
initrd.img-2.6.24-19-generic
and
initrd.img-2.6.24-21-generic

on a Pentium M 1.4Ghz system.

I did add the fbcon and vesafb modules to mine for framebuffer, but they are otherwise stock, and I also have copies of the unmodified initrd.img for the same kernels.

---

### Post by DThurman on 2008-10-22
For some strange reason, I was able to get the initrd
file.  Instead of trying to install using two partitions
of /boot and /, I decide to try to install in a single
partition and sure enough, /boot has all the required
files I needed.

So this problem is now solved.

Dan

---

