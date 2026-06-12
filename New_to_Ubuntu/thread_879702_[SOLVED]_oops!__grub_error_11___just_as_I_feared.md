---
title: "[SOLVED] oops!  grub error 11   just as I feared"
date: 2008-08-04
forum: New to Ubuntu
---

### Post by adamogardner on 2008-08-04
So after some recent thread I felt finally emboldened enough to go mess with partitioning.  I went into vista.  Got rid of everything (it's skeletal) and defragged the Disk.  Since I already copied my HP Recovery partition I deleted it (I was about to delete Windows altogether so I don't care if that move seemed stupid, I just want as little Vista as possible.  Then I tried to use Vist'a partition manager to shrink the windows partition but it could not because it claimed to still be defragging.  So I thought A restart was in order.  That is when I got GRUB ERROR (i think #11.)  So not knowing the GRUB commands I booted and installed Debian which comes with a fresh grub and reordered the existing and lost operating systems (vista and Ubuntu) under it.  So now I can boot into any of three but I don't want Debian.  I want Gentoo (which I burned to CD last night), but it doesn't come with GRUB.  My question is how do I replace Debian with Gentoo and not have boot failure?  Is there another question In should ask?

---

### Post by caljohnsmith on 2008-08-04
One way of solving your problem would be to give your ubuntu partition back control over the MBR. First of all, if everything boots fine when Debian's in control of the MBR, then I would replace your Ubuntu's /boot/grub/menu.lst with the Debian menu.lst (where ever they put that file, maybe /boot/menu.lst if not /boot/grub/menu.lst). Then from the terminal do the following:
```
sudo grub
grub> find /grub/boot/menu.lst
[COLOR="Blue"][this should only find the Ubuntu partition, and not the Debian if you deleted the menu.lst in Debian, otherwise you get to figure out which partition is Ubuntu yourself][/COLOR]
grub> root (hd0,X)  [COLOR="Blue"]<--use results from previous command[/COLOR]
grub> setup (hd0)

```
The above reinstalls Grub to the MBR and then points it to the Ubuntu partition for all its configuration files. After that, go ahead and install Gentoo over Debian. You'll have to figure out how to add Gentoo to the menu.lst though. What boot loader does Gentoo come with anyway? If it comes with any kind of boot loader, then I would have it install its boot loader into its own partition instead of the MBR, and then you can "chainload" it really easy to get it to boot. If you need more details let me know.

---

### Post by adamogardner on 2008-08-04
this is as far as I got:

grub> find /grub/boot/menu.lst

Error 15: File not found

grub>

---

### Post by caljohnsmith on 2008-08-04
Do you have Grub installed in Ubuntu, i.e. does your /boot/grub/ directory have stuff in it? So you did move your Debian menu.lst to your Ubuntu /boot/grub directory? If so that "find /boot/grub/menu.lst" in the Grub CLI should find it. In the Grub CLI, if you do "find /boot/grub/stage1" does it return a partition (hd0,X)?

---

### Post by adamogardner on 2008-08-04
What do I do from here?

grub> find /boot/grub/menu.lst
 (hd0,1)
 (hd0,3)

grub>

---

### Post by bumanie on 2008-08-04
Grub error 15 is something to with the correct kernel image not being located and thus the computer won't boot. Suggest you go to [here]("http://users.bigpond.net.au/hermanzone/p15.htm"). About 2/3 down the page there is a list of grub errors, the likely cause and possible fixes. Reinstalling grub at this point will not help - you need to track down which kernel image is being sought by grub and make it available again.

---

### Post by adamogardner on 2008-08-04
> **bumanie said:**
> . Reinstalling grub at this point will not help - you need to track down which kernel image is being sought by grub and make it available again.

What about the GRUB Debian is using?  The kernal image it is looking for probably is that deleted partition HP Recovery.  Whats wrong with what caljohnsmith is saying?

---

### Post by bumanie on 2008-08-04
I am fairly sure reinstalling grub will not fix a grub error 15. Look at the link given - it can explain things much better than I can. Reinstalling grub works well for grub error 17 and 22 (may be others), but I am fairly certain it won't help a grub error 15.

---

### Post by caljohnsmith on 2008-08-04
Bumanie, I think you might be misunderstanding. Adamogardner got the "error 15" in response to "find /boot/grub/menu.lst" because grub could not find /boot/grub/menu.lst in any partition at that point. He didn't get that error at boot time when trying to boot a distro, which in that case you would be correct about it looking for a kernel. Adamogardner seems to have fixed that particular problem, because in his next post he says the "find /boot/grub/menu.lst" returned (hd0,1) (hd0,3), which is what he would hope it would return. My guess is that (hd0,1) is Ubuntu and (hd0,3) is Debian, and they both have a /boot/grub/menu.lst according to his last post. 

Adamogardner, if you know which of those Grub partition's is Ubuntu, then you can do what I said before to replace your MBR with Grub and have it use Ubuntu for all its configuration files (vs. using Debian):
```
sudo grub
grub> root (hd0,X)        [should be (hd0,1) or (hd0,3)]
grub> setup (hd0)
```

---

### Post by adamogardner on 2008-08-04
> **caljohnsmith said:**
>  Adamogardner, if you know which of those Grub partition's is Ubuntu, then you can do what I said before to replace your MBR with Grub and have it use Ubuntu for all its configuration files (vs. using Debian):
```
sudo grub
grub> root (hd0,X)        [should be (hd0,1) or (hd0,3)]
grub> setup (hd0)
```

Well I did get the error at boot time.  Installing Debian installed a new grub.  Now at startup I hav e debian at the top of the list and Ubuntu and Vista listed as other operating systems.  I don't know what is what by looking at the output I got.

---

### Post by bumanie on 2008-08-04
> **caljohnsmith said:**
> Bumanie, I think you might be misunderstanding. Adamogardner got the "error 15" in response to "find /boot/grub/menu.lst" because grub could not find /boot/grub/menu.lst in any partition at that point. He didn't get that error at boot time when trying to boot a distro, which in that case you would be correct about it looking for a kernel. Adamogardner seems to have fixed that particular problem, because in his next post he says the "find /boot/grub/menu.lst" returned (hd0,1) (hd0,3), which is what he would hope it would return. My guess is that (hd0,1) is Ubuntu and (hd0,3) is Debian, and they both have a /boot/grub/menu.lst according to his last post. 

Adamogardner, if you know which of those Grub partition's is Ubuntu, then you can do what I said before to replace your MBR with Grub and have it use Ubuntu for all its configuration files (vs. using Debian):
```
sudo grub
grub> root (hd0,X)        [should be (hd0,1) or (hd0,3)]
grub> setup (hd0)
```

Can see what you mean now, but when I began writing the reply, the reference to /boot/grub menu.lst had not been posted - the recorded time re when they were posted, indicate they were posted at the same time - obviously, adamogardner posted just before I did.

---

### Post by caljohnsmith on 2008-08-04
> **adamogardner said:**
> So not knowing the GRUB commands I booted and installed Debian which comes with a fresh grub and reordered the existing and lost operating systems (vista and Ubuntu) under it.  [COLOR="Blue"]So now I can boot into any of three[/COLOR] but I don't want Debian.
OK, you originally said you had no problem booting any of your operating systems when Debian was in control of the MBR. 
> **adamogardner said:**
> Well I did get the error at boot time.  Installing Debian installed a new grub.  Now at startup I hav e debian at the top of the list and Ubuntu and Vista listed as other operating systems.  I don't know what is what by looking at the output I got.
So can you boot all three operating systems, or is one of them giving you a Grub error 15 when you try to boot it, and if so, which one? The original error 15 you reported was when I had you look for the /boot/grub/menu.lst in the grub CLI. It would be good to make sure your menu.lst in Debian can correctly boot Ubuntu and Windows before moving that menu.lst into Ubuntu. 

(hd0,1) corresponds to sda2/hda2 and (hd0,3) corresponds to sda4/hda4. Do you know which partition is Ubuntu? If not, you could do something like:
```
mount | grep ' / ' | awk '{print $1}'

```
And it will show you which partition you are in when you run that command. In other words, if you are in Debian when you run that command, and the command outputs /dev/sda4, then that is your Debian partition. The other one sda2 then would obviously be Ubuntu.

---

### Post by caljohnsmith on 2008-08-04
> **bumanie said:**
> Can see what you mean now, but when I began writing the reply, the reference to /boot/grub menu.lst had not been posted - the recorded time re when they were posted, indicate they were posted at the same time - obviously, adamogardner posted just before I did.
Gotcha, I didn't notice you posted at the same time. :)

---

### Post by adamogardner on 2008-08-04
yes I can start all three operating systems presently.  The GrUB error occurred before installing Debian which I did to fix everything, but I don't want Debian I just wanted it's grub.  I really prefer something else though I'm still deciding what.

I distinctly remember everything is on something called ".../sda3"  which you seemingly omitted just now.

---

### Post by unutbu on 2008-08-04
After following caljohnsmith's advice, would you also please post
```

sudo fdisk -l
```
I searched your previous posts, and surprisingly, was unable to locate that info.

---

### Post by adamogardner on 2008-08-04
> **unutbu said:**
> After following caljohnsmith's advice, would you also please post
```

sudo fdisk -l
```
I searched your previous posts, and surprisingly, was unable to locate that info.

you mean about /sda3 ?  No, I didn't say I remember "sayin,"  Just "I remember" from the grub menu.   if that's what you mean.  here's that list:

sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x33f133f0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19012   152705915+   7  HPFS/NTFS
/dev/sda2           19127       28432    74750445   83  Linux
/dev/sda3           28433       28905     3799372+   5  Extended
/dev/sda4           28906       30401    12016620   83  Linux
/dev/sda5           28433       28833     3221001   82  Linux swap / Solaris
/dev/sda6           28834       28905      578308+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 255 MB, 255066112 bytes
16 heads, 32 sectors/track, 973 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         973      249037+   6  FAT16

---

### Post by unutbu on 2008-08-04
> you mean about /sda3 ? No, I didn't say I remember "sayin," Just "I remember" from the grub menu. if that's what you mean.

Huh? :) When I said for you to follow caljohnsmith's advice I meant boot up into Debian and run:

```
mount | grep ' / ' | awk '{print $1}'
```

This would quite definitively settle which Linux partition is Debian.

Thanks for the fdisk output. It shows Ubuntu and Debian are on /dev/sda2 and /dev/sda4.

/dev/sda3 is an extended partition. It is a wrapper around /dev/sda5 and /dev/sda6 -- your swap partitions. There is no permanent data on /dev/sda3.

/dev/sda2 looks to be about 74GB, and /dev/sda4 is about 12GB. 

Once you can tell us which partition is Debian, we can tell you how to move its GRUB menu.lst to Ubuntu so you can trash Debian.

---

### Post by adamogardner on 2008-08-04
> **unutbu said:**
>  Once you can tell us which partition is Debian, we can tell you how to move its GRUB menu.lst to Ubuntu so you can trash Debian.

How do I figure this out? by running that command in Debian?

---

### Post by unutbu on 2008-08-04
Yes. Boot up Debian, and type
```
% mount | grep ' / ' | awk '{print $1}'
```
You will see something like this
```
/dev/sda4
```
as output. If you see /dev/sda4, it means Debian is on /dev/sda4.

Edit: I recall you being interest in learning CLI commands, so here's an explanation of the above:

The output of mount is something like
```
/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
```

"grep ' / '" means look for the pattern ' / '.
You'll see that pattern on the first line. 
(Try the command
```
mount | grep ' / ' 
```

-- You'll see the effect of grep.)

The line 
```
/dev/sda4 on / type ext3 
```
means that the filesystem on /dev/sda4 is mounted at /. When you boot Debian, (or Ubuntu) it mounts a particular partition's filesystem at / -- and that's the information we are after.

The "awk '{print $1}'" prints just the first space-separated word in the line: /dev/sda4. 

The pipes (|) pass the output of one program to the next.

(I used /dev/sda4 as an example in the above; your output might be different.)

---

### Post by adamogardner on 2008-08-04
everything is clear now.  I'll be back to edit in the results.  If you don't hear from me in an hour, send help.

---

### Post by caljohnsmith on 2008-08-04
[CENTER]**[SIZE="5"]Unutbu:[/SIZE]**

[SIZE="4"]
On behalf of the Ubuntu Forums, I hereby present you with the:[/SIZE]


:KS :KS :KS [SIZE="5"]**"Patience of the Year Award"**[/SIZE] :KS :KS :KS


...not that I have any authority to do so, but I still think you deserve it anyway. :biggrin:[/CENTER]

---

### Post by adamogardner on 2008-08-04
i'm back,  dev/sda4 is debian

oh come on cal, I'm not that bad.

---

### Post by unutbu on 2008-08-04
Thank you caljohn, you made my day :) On behalf of chipmunks around the world, I accept!

PS: adamogardner, nah, you're not bad at all... :)

Okay now. Boot up Ubuntu. Type
```

sudo mkdir /D
sudo mount /dev/sda4 /D
cd /boot/grub
sudo cp menu.lst menu.lst-20080804
sudo cp /D/boot/grub/menu.lst menu.lst

sudo grub
root (hd0,1)
setup (hd0)
quit

```
Reboot. You should now be booting off of Ubuntu's menu.lst.

If everything works, after you reboot you can remove the temporary directory /D with

```
sudo rmdir /D
```
(This will not erase Debian).

---

### Post by adamogardner on 2008-08-04
so now that I know deb is on sda4, and Ubuntu is on sda2, where is Vista?

so now that I have a map, how do I move grub to Ubuntu and replace debian with a sick alternative? Or how does that go?

ok working on 23

---

### Post by unutbu on 2008-08-04
Vista uses an NTFS filesystem. Your fdisk output shows

```
/dev/sda1 * 1 19012 152705915+ 7 HPFS/NTFS
```

Therefore, your Vista OS is on /dev/sda1.

Adamogardner, would you post your new Ubuntu /boot/grub/menu.lst? I think it might be a good idea to check that it sufficiently similar to Ubuntu's usual menu.lst.

---

### Post by adamogardner on 2008-08-04
the GRUB menu on reboot was still seated in debian and listed Ububtu as another operating system.  how do I print that grub/menu.lst?

---

### Post by unutbu on 2008-08-04
```
cat /boot/grub/menu.lst
cat /boot/grub/menu.lst-20080804
```

On second thought, we better look at both.

(Alternatively, you could just post both as attachments. But to get the files past the ubuntuforums attachment filter, you'd have to rename the files to end in something like .txt, so it's probably more work than 'cat'-ing the files...)

---

### Post by adamogardner on 2008-08-04
adamogardner@CRONUS:~$ cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode) (on /dev/sda2)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single 
initrd		/boot/initrd.img-2.6.24-19-generic
savedefault
boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
  


and secondly,

adamogardner@CRONUS:~$ cat /boot/grub/menu.lst-20080804
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		120

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd		/boot/initrd.img-2.6.24-19-generic




### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1

---

### Post by unutbu on 2008-08-04
Boot into Ubuntu. Type

```
cd /boot/grub
sudo mv menu.lst menu.lst-debian
gksu gedit menu.lst
```
Paste this into menu.lst
```

cat /boot/grub/menu.lst
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/sda4 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,3)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(single-user) single
# altoptions=(single-user mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
Save and quit gedit.
This includes Debian boot stanzas after the Ubuntu boot stanzas. 
If you can boot Ubuntu and Vista as you desire, then you can boot Ubuntu and type
```

gksu gedit /boot/grub/menu.lst
```

and take out the Debian boot stanzas:
```

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/sda4 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

```

---

### Post by adamogardner on 2008-08-04
here's what happened.  looks like an error but I did paste that script in that list like you said.  before I proceed with deleting Debian Am I good?  Or are things not right.  What did I just do?  ANd that second part removes the debian operating system from my computer?

adamogardner@CRONUS:~$ cd /boot/grub
adamogardner@CRONUS:/boot/grub$ sudo mv menu.lst menu.lst-debian
sudo: unable to resolve host CRONUS
[sudo] password for adamogardner: 
adamogardner@CRONUS:/boot/grub$ sudo mv menu.lst menu.lst-debian
sudo: unable to resolve host CRONUS
mv: cannot stat `menu.lst': No such file or directory
adamogardner@CRONUS:/boot/grub$ gksu gedit menu.lst
adamogardner@CRONUS:/boot/grub$

---

### Post by adamogardner on 2008-08-04
this sucks,  So after doing that last post I restarted to see If GRUB was where I wanted and I have 2 debians a Vista ANd my Ubuntu is missing.  What next?  I'd like to do this in Ubuntu so if we can backtrack that 'd be great.  I'm in windows now because I have no graphix in Debian.

---

### Post by unutbu on 2008-08-04
Sorry, Adamogardner, my mistake. There is an error in the menu.lst I posted. Hold on, I'm fixing it now...

---

### Post by adamogardner on 2008-08-04
ok  thanks(anxiously)  WHoa whatt the hell am I doing with a mug of cappucino?

---

### Post by unutbu on 2008-08-04
Do you have a USB flash drive?

---

### Post by adamogardner on 2008-08-04
i thing you stick in to store info?  No. I have  dvd+RW

---

### Post by unutbu on 2008-08-04
Do you have a floppy drive?
Or can you access the internet from a LiveCD?

Basically, we need to edit /boot/grub/menu.lst on /dev/sda2 to
```

## ## End Default Options ##

title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

(The stuff currently between
```
## ## End Default Options ##
...
### END DEBIAN AUTOMAGIC KERNELS LIST
```
needs to be deleted and replaced by the above)

---

### Post by adamogardner on 2008-08-04
no  maybe with mandriva cd

---

### Post by unutbu on 2008-08-04
Oh! I know, we can use the backup menu.lst-debian.
Hold on while I write instructions.

---

### Post by unutbu on 2008-08-04
Boot from the Ubuntu LiveCD.
Open a terminal and type:

```
sudo mkdir /U
sudo mount /dev/sda2 /U
gksu gedit /U/boot/grub/menu.lst

```
Find the lines  
```

## ## End Default Options ##
... stuff to delete ...
### END DEBIAN AUTOMAGIC KERNELS LIST
```

and remove the boot stanzas in between.

Now click File>Open in the gedit window and open /boot/grub/menu.lst-debian as well.

Go down to near the bottom of menu.lst-debian and you'll see

```
title Ubuntu 8.04, kernel 2.6.24-19-generic
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro quiet splash
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

title Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root (hd0,1)
kernel /boot/vmlinuz-2.6.24-19-generic root=UUID=b268eb6a-59da-462c-a80d-897b34edbf38 ro single
initrd /boot/initrd.img-2.6.24-19-generic
savedefault
boot

```
Copy these lines and paste them into /boot/grub/menu.lst:
```

## ## End Default Options ##
... paste here ...
### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by adamogardner on 2008-08-04
looks like I have a busy day tomorrow.  Hope it works. Goodnight, Unutbu

---

### Post by unutbu on 2008-08-04
Okay, good luck.

---

### Post by adamogardner on 2008-08-05
I got a second wind, took care of it everything is perfect.  ubuntu started so quickly though, I didn't notice a grub menu. Thanks, I'm glad I have you in my corner.

---

### Post by unutbu on 2008-08-05
To increase the time the GRUB menu stays up,
increase the timeout in /boot/grub/menu.lst. Debian used 120:

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 120
```


> **adamogardner said:**
> WHoa whatt the hell am I doing with a mug of cappucino?

Cheers :lolflag:

---

