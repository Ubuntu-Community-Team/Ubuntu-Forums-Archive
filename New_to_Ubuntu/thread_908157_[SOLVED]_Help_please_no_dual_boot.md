---
title: "[SOLVED] Help please: no dual boot?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by BeccyBug on 2008-09-02
Long story short!

After completely messing up my computer last night, I have reinstalled my version of windows black xp - first I partitioned the SATA hdd with the xp installation disc, installed windows, and then booted from the ubuntu (8.04) disc and installed it on the free space.  (Followed instructions from [here)]("https://help.ubuntu.com/community/WindowsDualBoot#Master%20boot%20record%20and%20boot%20manager")

On restart I get no options - it just boots straight to windows.  Any ideas?  Asking now before I try to reinstall and mess up partitions, which is what I did early hours of this morning!

When I get to step 4 of reinstalling, and go to manually prepare disc space I can see:

/dev/sda1 ntfs  (7700/125024MB used)

/dev/sda5 ext3 (3200/119908MB used)
/dev/sda6 swap (0/5124MB used)

and my spare hdd is also showing.  Am completely lost here, but I presume from that it looks like ubuntu has installed successfully, but just won't boot for some reason?

Thanks for any help!

---

### Post by soloman498 on 2008-09-02
when i messed up my computer and had to reload windows it would only boot in windows as windows wouldn't recognise ubuntu,so i reloaded ubuntu and have had no problems.it now boots with a choice of ubuntu or windows

---

### Post by iamthestig on 2008-09-02
I had similar issues when I was playing around with RedHat. I had my computer set up for a RedHat/XP Pro dual boot. After a while only Windows would boot. I never got it to work right, so I reinstalled as an XP only system.

---

### Post by BeccyBug on 2008-09-02
Thanks for that - I think in a minute I will have no choice but to keep fingers crossed, reinstall and hope I do it in the right partition!!

I know nothing about all this, but I don't think it's windows not recognising ubuntu, since I installed it on a separate partition.  I can't see any ubuntu files from windows, but as far as I understand it (not a lot) I shouldn't be able to because of where I installed it?

The only other clue I have is a message that has always been there on bootup that says "If you want to install Linux Default Partition RAID driver, please do not use OPROM creation operation" - but I have no clue what that means!

---

### Post by Bucky Ball on 2008-09-02
You need to have grub bootloader installed to get Ubuntu up. It is probably there, but hard to know where if you can't get into a shell to find it.

Try this for now and we can try to work it from there. There are ways of doing this from the live cd, but you might find it easier for now to go to:

[www.supergrubdisk.org](www.supergrubdisk.org)

Download and burn a cd. Reboot and set in the bios to boot from cd (you may need to quickly hit a key like delete or f1 to get to bios). Once you have set to boot from cd, insert the cd then hit f10 to exit and save changes. This will restart and boot from the supergrubdisk. If there is a grub there, it will find it and should (should) get you going.

Have a read on the supergrub website, it is excellent and you can learn a heap (I sure have).

Give all this a try and let us know how you went. And welcome to the community! :)

---

### Post by Bucky Ball on 2008-09-02
[quote=beccybug]don't think it's windows not recognising ubuntu[/quote]

That is definitely not your problem. Windows wouldn't know Ubuntu from a toasted scallop (!) and forget the raid option ... you are not running it (you would know if you were), Hope you get this before you go through the whole palaver again. Fingers crossed. You are very close, my friend. 

If this all works, you might want to have a play around with Ubuntu and do a little research, break a few things, get to know it a little better, then reinstall and manually setup partitions you might need (currently you have one big partition for Ubuntu and one swap - you might want a data partition for music/vid, personal files, whatever). :)

---

### Post by MeURi on 2008-09-02
Hi BeccyBug, try looking at [thread=24113]this thread[/thread], it explains how to restore a GRUB installation.

Then check your menu.lst under /boot/grub/ and see if there are any inconsistencies

---

### Post by Bucky Ball on 2008-09-02
[quote=beccybug]On restart I get no options - it just boots straight to windows.[/quote]

MeURI - she can't get to a shell to do what you suggest and probably has no idea what you mean anyhow. I like where you are going but ...

[QUOTE=MeURI]check your menu.lst under /boot/grub/ and see if there are any inconsistencies[/QUOTE]

? She has 9 posts and hasn't gotten into Ubuntu yet.

---

### Post by LowSky on 2008-09-02
easiest and best way to fix dual boot set up


[QUOTE=vnbuddy2002]HOWTO: Restore GRUB (if your MBR is messed up) 

--------------------------------------------------------------------------------

Restore GRUB quite simple in Ubuntu, instead going through all the "gain root access" and play with shell commands, you can use the Ubuntu installation CD to restore it without going through all kinds of hassles.

Here are the steps:

1. Boot your computer up with Ubuntu CD
2. Go through all the process until you reech "[!!!] Disk Partition"
3. Select Manual Partition
4. Mount your appropriate linux partions (from Manual Partition)
"/" and  "swap"


5. DO NOT FORMAT THEM.
6. Finish the manual partition
7. Say "Yes" when it asks you to save the changes
8. It will give you errors saying that "the system couldn't install ....." after that
9. Ignore them, keep select "continue" until you get back to the Ubuntu installation menu
10. Jump to "Install Grub ...."
11. Once it is finished, just restart your computer

Good luck!.[/QUOTE]

---

### Post by MeURi on 2008-09-02
Bucky Ball, the thread I linked says to boot using Ubuntu live cd (and it's the same thread quoted by LowSky)

---

### Post by BeccyBug on 2008-09-02
> **Bucky Ball said:**
> 

? She has 9 posts and hasn't gotten into Ubuntu yet.

Nah - this is on my other computer - installed ubuntu 2 weeks ago on my spare, and think I'd like to swap completely (eventually) so trying to dual boot on my other puter before I give up windows completely.

Supergrub looks like a great (if complicated programme - it has told me it succeeded in fixing the boot of linux, and when I tried to reboot it gave me the options, but then said "error 22: no such partition" <grrr>

Tried again with the disc and it tells me the same thing:

Booting 'Ubuntu 8.04.1, kernel 2.6.24-19-generic'
root (hd0,4)
Error 22: no such partition
Press any key...

Hmmm... it also says it can't boot windows - filesystem type is unknown, and NTLDR is missing...

Guess I will have a go with the installation disc, although choosing the wrong partitions was what messed me up yesterday!

Thanks for all your help - I will probably be back in another 5 minutes! :lolflag:

Said I'd be back!  The instructions in the thread looked simple enough - got as far as selecting manual partition ... then it says to mount them - can't see this as an option here - can edit it: use as fat32 etc but most else is greyed out - I guess looking at the date of the thread (2005) this could be a different option for 8.04????  

Beginning to tear my hair out now!

---

### Post by BeccyBug on 2008-09-02
OK - this is getting ridiculous!!!  I tried to reinstall with the live cd - deleted the partitions the original install had created, formatted them and let the installer create new ones.  On reboot I have the options, but selecting any ubuntu options produces:

error 22: no such partition

Selecting windows brings up NTLDR is missing, press ctrl+Alt+Del to restart

(which obviously brings me right back to the boot menu that apparently doesn't work!:confused:Any ideas?

---

### Post by BeccyBug on 2008-09-02
Tried this 
 Re: HOWTO: Restore GRUB (if your MBR is messed up)
Isn't it easier to do this:

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,6)", or whatever your harddisk + boot partition numbers are (my /boot is at /dev/sda7, which translates to hd0,6 for grub).

from the same thread and it tells me the hd doesn't exist (I used the numbers generated by supergrub) 

Think I want to give up in a minute, but now it won't boot to either os so am left with the option of reformatting and just installing windoze, which I really don't want to do.  Been at this all day and night now!!!!!  Getting desparate!:mad: And now feel like I'm having a conversation with myself!

As an aside - when booted from the live disc it can see the 119GB 'media' with the usual folders that should be in my homefolder - I can also see another 'media' with windows type files in it, so it does look like both os are installed somewhere, but something is pointing in the wrong direction when I reboot.

---

### Post by kansasnoob on 2008-09-02
Slow down. You needn't have reinstalled the last time. Give me a couple minutes.

---

### Post by kansasnoob on 2008-09-02
Are you running the live CD right now?

---

### Post by BeccyBug on 2008-09-02
Yep

---

### Post by kansasnoob on 2008-09-02
Boot from the Live CD if you're not already.
In the terminal, run:

```
sudo grub
```

At the grub command prompt, run the following command:

```
find /boot/grub/stage1
```

And post the result here. It'll be something like hd(0,1).

---

### Post by BeccyBug on 2008-09-02
result is (hd0,4)

---

### Post by kansasnoob on 2008-09-02
> **BeccyBug said:**
> result is (hd0,4)

OK. You still need the grub prompt to finish this so if necessary type grub in terminal again and we'll repeat part of what you've already done:

```
root (hd0,4)
```

(That's zero,4)

```
setup (hd0)
```

```
quit
```

Restart and see if you can boot Ubuntu. If so then we'll try to tackle the Win problem.

---

### Post by kansasnoob on 2008-09-02
Oh that's also a zero in "setup (hd0)"

---

### Post by BeccyBug on 2008-09-02
at the boot options it is still giving me the error 22: no such partition!  Rebooting with the live cd again!

---

### Post by kansasnoob on 2008-09-02
> **BeccyBug said:**
> at the boot options it is still giving me the error 22: no such partition!  Rebooting with the live cd again!

Arrgh!

---

### Post by caljohnsmith on 2008-09-02
> **BeccyBug said:**
> at the boot options it is still giving me the error 22: no such partition!  Rebooting with the live cd again!
Please slow down here. :) I think what might be your problem is that some older BIOSes do not recognize partitions that lie beyond the first 137 GB of your HDD, and that could be why you are getting that Grub error. Please post the output of the following from the Live CD:
```
sudo fdisk -lu
```
And we can help you figure out what might be the best solution.

---

### Post by kansasnoob on 2008-09-02
> **caljohnsmith said:**
> Please slow down here. :) I think what might be your problem is that some older BIOSes do not recognize partitions that lie beyond the first 137 GB of your HDD, and that could be why you are getting that Grub error. Please post the output of the following from the Live CD:
```
sudo fdisk -lu
```
And we can help you figure out what might be the best solution.

Man, am I glad to see you:)

---

### Post by BeccyBug on 2008-09-02
lots of gobldeygook!!!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff54ff54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244187999   122093968+   7  HPFS/NTFS
/dev/sda2       244188000   488392064   122102032+   5  Extended
/dev/sda5       244188063   478383569   117097753+  83  Linux
/dev/sda6       478383633   488392064     5004216   82  Linux swap / Solaris

Disk /dev/sdb: 3500 MB, 3500007424 bytes
128 heads, 63 sectors/track, 847 cylinders, total 6835952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b5b3a41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     6830207     3415072+   7  HPFS/NTFS


Did my bios come with my motherboard?  I build this computer less than a year ago!

---

### Post by caljohnsmith on 2008-09-02
> **kansasnoob said:**
> Man, am I glad to see you:)
Thanks for the vote of confidence. :) Now if we can just get BeccyBug to slow down a little here, maybe we can help her. As fast as she moves, I bet her computer is smoking by now. :D

---

### Post by kansasnoob on 2008-09-02
> **BeccyBug said:**
> lots of gobldeygook!!!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff54ff54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244187999   122093968+   7  HPFS/NTFS
/dev/sda2       244188000   488392064   122102032+   5  Extended
/dev/sda5       244188063   478383569   117097753+  83  Linux
/dev/sda6       478383633   488392064     5004216   82  Linux swap / Solaris

Disk /dev/sdb: 3500 MB, 3500007424 bytes
128 heads, 63 sectors/track, 847 cylinders, total 6835952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b5b3a41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     6830207     3415072+   7  HPFS/NTFS


Did my bios come with my motherboard?  I build this computer less than a year ago!

You can have hope now. Caljohnsmith is as good as anyone I've ever seen at diagnosing & fixing boot problems!

---

### Post by caljohnsmith on 2008-09-02
> **BeccyBug said:**
> lots of gobldeygook!!!

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xff54ff54

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   244187999   122093968+   7  HPFS/NTFS
/dev/sda2       244188000   488392064   122102032+   5  Extended
/dev/sda5       244188063   478383569   117097753+  83  Linux
/dev/sda6       478383633   488392064     5004216   82  Linux swap / Solaris

Disk /dev/sdb: 3500 MB, 3500007424 bytes
128 heads, 63 sectors/track, 847 cylinders, total 6835952 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b5b3a41

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63     6830207     3415072+   7  HPFS/NTFS


Did my bios come with my motherboard?  I build this computer less than a year ago!
Please clarify, when you get that error 22, do you get that after you select an entry in the Grub menu, or do you get that error before you even see the Grub menu? And does it say anything about "hit ESC to see the menu"?

---

### Post by BeccyBug on 2008-09-02
I am a little impatient :) - and trying to do my next weeks work at the same time.  Slowing down now though - been shouted for tea - be right back!

And thanks a million :popcorn: - this went so smooth on my last puter - can't believe the probs now!!!

---

### Post by Luke771 on 2008-09-02
BeccyBug, Windows overwrote the MBR (master boot record) so now you go straignt into windows and donì't get the boot options: there's a very simple solution for this:

- Google Supergrub (or was it super grub?). You should get to a bootable iso image
- burn a Supergrub cd
- boot from it, choose restore linux boot (or something like that), when you get the message 'operation successful' reboot with ctrl-alt-del and your old Grub menu will pop up ;)

---

### Post by BeccyBug on 2008-09-02
> **caljohnsmith said:**
> Please clarify, when you get that error 22, do you get that after you select an entry in the Grub menu, or do you get that error before you even see the Grub menu? And does it say anything about "hit ESC to see the menu"?

The message comes after I select an entry in the menu - just checking to see if it says anythinga about escape

no esc - says use arrow. enter to boot, e to edit commands before booting or c for a command line

---

### Post by BeccyBug on 2008-09-02
> **Luke771 said:**
> BeccyBug, Windows overwrote the MBR (master boot record) so now you go straignt into windows and donì't get the boot options: there's a very simple solution for this:

- Google Supergrub (or was it super grub?). You should get to a bootable iso image
- burn a Supergrub cd
- boot from it, choose restore linux boot (or something like that), when you get the message 'operation successful' reboot with ctrl-alt-del and your old Grub menu will pop up ;)

Have the supergrub disc and did the "fix boot of linux" - it said it was successful - it was in that I now get the grub menu, but nothing will start from that menu - I get an 'error 22: no such partition" if I hit any ubuntu option, and "NTLDR is missing, press ctrl,alt,del to restart" if I hit the windows option... so no os at all, but I can see them both when I run the live CD  :confused:

---

### Post by caljohnsmith on 2008-09-02
> **BeccyBug said:**
> Have the supergrub disc and did the "fix boot of linux" - it said it was successful - it was in that I now get the grub menu, but nothing will start from that menu - I get an 'error 22: no such partition" if I hit any ubuntu option, and "NTLDR is missing, press ctrl,alt,del to restart" if I hit the windows option... so no os at all, but I can see them both when I run the live CD  :confused:
No problem, just boot your Live CD, open a terminal, and do the following: 
```
sudo mount /dev/sda5 /mnt
gksudo gedit /mnt/boot/grub/menu.lst &
```
That will pull up your Grub's menu.lst, so scroll down to the Ubuntu entries, and where it has a "root (hdX,Y)" line, use:
```
root (hd0,4)
```
Leave everything else with the Ubuntu entry alone though, just change the "root" line. And this is how your Windows entry should look:
```
title   Windows XP
root    (hd0,0)
makeactive
chainloader +1
```
Try that, and if that doesn't work, then please post the entire contents of your menu.lst; also let us know exactly what errors you get (if any) when you use the above entries.

---

### Post by kansasnoob on 2008-09-02
Re: the windows rewrote mbr. That only happens when Windows is installed after Ubuntu is installed.

You've now reinstalled Grub 3 times (4 if you include reinstalling Ubuntu altogether), so that's not the solution. Supergrubdisk is a great tool though, I have it on a thumb drive, on floppy and on CD .......... just in case!

You'll probably have to wait for caljohnsmith to get back here, but I did have a silly thought ........... feel free to laugh at me! Is it even remotely possible that at any point, even before installing windows, that a memory card or any external media of any sort was left in a card reader or drive:confused:

I know that's stupid, but hey, gotta ask.

I also wonder, since you did reinstall windows (I think), what if any previous problems the computer was having:confused:

Edit: Oops, I hadn't seen your last post.

---

### Post by BeccyBug on 2008-09-02
> **kansasnoob said:**
> Is it even remotely possible that at any point, even before installing windows, that a memory card or any external media of any sort was left in a card reader or drive:confused:

I know that's stupid, but hey, gotta ask.


Not stupid - when I did a complete install on my other (this) computer I did it with 2 usb drives attached and a spare ntfs drive I use for backups that I then couldn't mount...  :lolflag: ...mind you, everything else (including the external drives) are working!

> **kansasnoob said:**
> 
I also wonder, since you did reinstall windows (I think), what if any previous problems the computer was having:confused:

Edit: Oops, I hadn't seen your last post.

Its biggest problem (apart from Itunes) was me installing in the wrong partition at 12:45 lsat night...:lolflag:

Just tried editing the menu.lst, and it came up with the same (now very anoying) error 22.  Just rebooting to make sure I saved the changes! :confused:

---

### Post by BeccyBug on 2008-09-02
ok - menu.lst is as follows - although I just realised I edited the wrong bit - I did an example line that started with #  :oops:  but the 'real' entry was already right, if I'm understanding this right - anyway - here goes:

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
timeout		10

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
# root		(hd0,4)
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
# kopt=root=UUID=3efcec46-799f-4cdb-8719-69096321c8a6 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)

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

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3efcec46-799f-4cdb-8719-69096321c8a6 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=3efcec46-799f-4cdb-8719-69096321c8a6 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

---

### Post by caljohnsmith on 2008-09-02
A Grub error 22 is "no such partition". So are you still getting that error when choosing Ubuntu, even after you changed Ubuntu to use (hd0,4)? That could mean you installed Grub to your 3.5 GB drive at some point, and you are actually booting from that drive. Is that a USB flash drive or what is it? Can you disconnect it? That would help troubleshoot the true cause of your problem.

---

### Post by BeccyBug on 2008-09-02
Yep - still getting error 22.

Disconnecting now - the 3.5GB is ntfs - it is just storage for backups and downloaded progs.  Will try rebooting after disconnecting and let you know...  doh - that means that you think grub is on the 3.5GB drive, and it's looking for ubuntu on there instead of on the SATA drive?  (in simple speak?!)

---

### Post by BeccyBug on 2008-09-02
That's half the problem solved - with the ide(?) drive disconnected I can now boot into ubunu :popcorn:

But it now says error 22 when I try to boot into windows :(

Still - that is huge progress...

---

### Post by caljohnsmith on 2008-09-02
> **BeccyBug said:**
> That's half the problem solved - with the ide(?) drive disconnected I can now boot into ubunu :popcorn:

But it now says error 22 when I try to boot into windows :(

Still - that is huge progress...
Yes, that's definitely progress, because that clears up what was happening; you installed Grub to the master boot record of your 3.5 GB drive, and then pointed it to your Ubuntu drive for all its system files (menu.lst and others). So at this point, can you change your BIOS so your Ubuntu HDD is first in the boot sequence? If so, that will allow you to hook your 3.5 GB back up and not cause problems. 

Try changing your Windows entry as follows:
```
title   Windows XP
root    (hd0,0)
makeactive
chainloader +1
```
In case you're unsure how to access your menu.lst again, when you've booted into Ubuntu (on your HDD) just do:
```
gksudo gedit /boot/grub/menu.lst
```
That's all it should take to boot the Windows that's on the same drive as Ubuntu. Let me know how it goes and if you get any errors.

---

### Post by BeccyBug on 2008-09-02
YES!  That did it all.  And how silly - should probably have disconnected the other drive last night before I did anything at all.

Thank you so much for your time and patience!!

---

### Post by caljohnsmith on 2008-09-02
> **BeccyBug said:**
> YES!  That did it all.  And how silly - should probably have disconnected the other drive last night before I did anything at all.

Thank you so much for your time and patience!!
You're welcome, and I'm glad everything is finally working for you now. Have fun! :)

---

### Post by Bucky Ball on 2008-09-03
Cool. Hope all works out. :)

---

### Post by Bucky Ball on 2008-09-03
```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
**root**
```

In your menu.lst, what is the root I have in bold doing there?

---

### Post by caljohnsmith on 2008-09-03
> **Bucky Ball said:**
> ```
# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
**root**
```

In your menu.lst, what is the root I have in bold doing there?
That's a sort of crude Grub hack to get a "labeled divider" to help organize the OSs listed in Grub's menu on start up; you have to do it that way since Grub does not inherently have the feature to make a divider to separate the OSs. More specifically, that "root" line goes with the "Other operating systems:" title, and you need to have the root line so you can have the "Other operating systems" title listed in the menu. So a "labeled divider" is really just another operating system listing in your Grub's menu, but it is a bogus one that doesn't boot anything.

---

### Post by BeccyBug on 2008-09-03
> **Bucky Ball said:**
> Cool. Hope all works out. :)

Thanks - I'm sure it will.  Think you were right, too, about wanting to change partitions in the near future - I'm presuming that will mean I can store music or photos on different partitions without the danger of losing them if all goes wrong with whatever os I am running at the time?  The more I look into ubuntu the more I love it :)  was just an experiment for my summer holidays, but think I am hooked now :lolflag:

---

