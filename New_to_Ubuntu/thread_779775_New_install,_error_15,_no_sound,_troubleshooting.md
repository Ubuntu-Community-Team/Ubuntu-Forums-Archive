---
title: "New install, error 15, no sound, troubleshooting"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by jpcstl on 2008-05-03
Have just done an install of 8.04 using the wubi installer.  Overall the program seems to be running well except for a couple of things.

1) When I boot to Ubuntu I get a second boot screen that says:
find ubuntu/disks/boot/grub/menu.lst
find ubuntu/install/boot/grub/menu.lst
find menu.lst
find boot/grub/menu.lst
then something about command line, halt, reboot

When I select the first 'find' option, it takes me to a screen that then boots ubuntu.

If I select either of the second, third or fourth 'find' options, it gives me an Error 15, can't find file.

I did some reading on the forums and saw mention of hitting edit at the countdown screen, which I discovered is where I end up when selecting the first 'find' option (or when I simply hit b to continue booting).  When I did that, it appears to be saying my grub root (is that the correct terminology?) is at (hd0,4).  If I'm understanding this correctly, it's saying the root is on the first hard drive (I've only got one internal drive, and one usb external drive) and at the fifth partition (I've only got 2 partitions on the internal hard drive, one for the C drive which is about 20G and one for the E drive which is about 170G).  I tried to change this using 'e'dit, but when I typed in (hd0.1) it said it could not mount to the partition (or some such phrasing).

2) I don't have any sound.  I wonder if this is at all related to 1).

Any help is appreciated, thanks.

---

### Post by nowshining on 2008-05-03
if you can get in a working (gui) environment, can you post the contents of your /boot/grub/menu.lst file.

---

### Post by jpcstl on 2008-05-03
I think this is what you're looking for?

[INDENT]# menu.lst - See: grub(8), info grub, update-grub(8)
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
# kopt=root=UUID=E0FCAA0CFCA9DCD2 loop=/ubuntu/disks/root.disk ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,4)/ubuntu/disks

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

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,4)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=E0FCAA0CFCA9DCD2 loop=/ubuntu/disks/root.disk ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,4)/ubuntu/disks
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=E0FCAA0CFCA9DCD2 loop=/ubuntu/disks/root.disk ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd0,4)/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
chainloader	+1
[/INDENT]

---

### Post by jpcstl on 2008-05-03
I thought I'd just add this to my thread rather than starting a new one, but seems I can't add a repository either.  Unless I'm totally missing how to do it, when I put in the link for the APT line in the third party software dialog box, it never gives me the option to add source.  Add source simply remains grayed out.

---

### Post by jpcstl on 2008-05-03
Another update as I've been doing some exploring on my own.  Booted to XP and went looking for the missing files
[INDENT]find ubuntu/disks/boot/grub/menu.lst
find ubuntu/install/boot/grub/menu.lst
find menu.lst
find boot/grub/menu.lst[/INDENT]
Well, the first one seems to be there, in that directory, and the contents are pasted above.  I think it's also why ubuntu boots when I hit enter on the first option.  The other three aren't anywhere, or I'm not looking in the right place.

As for the partition issue, my internal hard drive partition is coming up as the E: drive.  A: is floppy, C: is my main 20GB partition where XP is installed, there is no D:, E: is my 175GB partition where I've installed Wubi/Ubuntu, and F: is my external WD hard drive.  So while I only have two partitions, maybe the reason it's showing up as E: in XP has some correlation with the partition number it's registering?  

And Re: sound, I have full sound in XP.

I'll keep messing about, if anyone has any ideas for me I'd be happy to hear them.  Thanks.

---

### Post by nowshining on 2008-05-03
there is to be only 1 menu.lst and that's it. :) it should contain all the info. too boot up the system.

hmmm, you'll have to wait for someone else to come along. :) I'm stumped as I seem to see nothing wrong with your menu.lst file. :? Hopefully if it does contain any errors someone with at least a dualboot system with xp will be able to help you out.

---

### Post by jpcstl on 2008-05-03
Thanks for the effort, I appreciate the reply.  As I'm just getting started in this whole thing, and hadn't gotten too far along, I'm going to try another install.  I just uninstalled wubi/ubuntu, and re-downloaded the wubi-8.04.exe so will start fresh and see if that fixes anything.  Here's hoping I won't be back! :)

---

### Post by jpcstl on 2008-05-03
> **nowshining said:**
> there is to be only 1 menu.lst and that's it. :) it should contain all the info. too boot up the system.

hmmm, you'll have to wait for someone else to come along. :) I'm stumped as I seem to see nothing wrong with your menu.lst file. :? Hopefully if it does contain any errors someone with at least a dualboot system with xp will be able to help you out.

I do have one question if you (or anyone else in the know) are still around.  Why is it asking to find (4) separate files if it's really just referring to the one?  And if it is looking for (4) files, I wonder why the first one, which does exist as evidenced by me quoting it's contents above, is showing up as unfound; and why the other three are nowhere to be found?  I guess that's the $64m question?

---

### Post by jpcstl on 2008-05-03
Ok, so I uninstalled and reinstalled wubi/ubuntu and I'm still getting the same error 15 upon boot up, but I've now got sound back :)

I've also done some more reading (but had to stop when the install was finished so I could reboot) and would appear that my installing to the E: drive (hd0,4) is what is causing the problem.  I didn't get to finish reading to see if there was a solution in the thread or not (I think there was 2 or 3 more pages to the thread I was devouring).

Not sure why my partition is called partition 4 when I've only got one internal HD with two partitions (C (primary) and E).

Also, not sure why it can't find the first menu.lst file mentioned above because I found it and it's right there (even on the latest reinstall), and I even found it using the command line cat (hd0,4)/ubuntu/.... (as I read about in another thread).

So, while I try and search for that thread again, if anyone has any thoughts, I'd appreciate them.

---

### Post by jpcstl on 2008-05-03
Ok, I know I'm doing a lot of talking to myself, but maybe something I say will jog some assistance.  I keep reading forum threads and getting bits and pieces of info, but I'm unable to pull it all together.  

Anyway, my new question is this.  If I uninstall and reinstall wubi/ubuntu yet again, but this time do it to my C drive, I suspect that will solve the error 15 problem BUT I only have about 7GB free on that primary partition, and I need a fair bit (if not all) of that for running XP (don't I?).  So, won't installing wubi/ubuntu to my C: only cause me other problems, and/or is there a suggestion on how I can SAFELY and EASILY make the partition bigger before I install it there?

---

### Post by al4844 on 2008-05-03
Not sure if I can help you or not, but I will share what I saw on mine.  I have two different hard drives, and had the second unplugged from the system.  Installed 8.04 64-bit, and during the first reboot, I powered my PC down and plugged in the second hard drive.  I got the same error 15.  I went through the whole process two more times, and got the same error 15 each time.  I was just about to think that I would not get past it, when I, for some reason made the decision to remove the second hard drive.  Once I did that, Ubuntu came up running great.  For some reason, it just did not like seeing two hard drives.  That this is just the way that I saw it.
Hope it helps.

---

### Post by jpcstl on 2008-05-03
I appreciate that, al4844.  Difference here is that I have only 1 physical (internal) drive with 2 partitions (C and E).  My other drive is an external USB HD (G).  I could see if turning off my usb drive does anything, but I suspect it's tied to me wanting to install wubi/ubuntu to my E drive rather than my C (primary) drive.  

I'm still trying to figure out what's possible if I don't have enough space on my C drive to install wubi/ubuntu there.  AND I'm wondering what I'm losing by booting past the 'find' files at boot-up, since right now, for as much as I've played (that includes running pidgin, firefox and rhythmbox) I don't seem to be having actual run issues, just the snafu at boot.  I suspect I'll have problems as I go on, but nothing yet (now that sound is back).

---

### Post by jpcstl on 2008-05-04
This might be my last post for this thread.  Here's my final question (for now) if anyone has a thought on it.

If I'm currently running wubi/ubuntu, and it appears to be running just fine except for the extra step at boot up, do I need to be worried about it saying it can't find those files (and that the first file exists, even if it says it can't find it)?  So far I've been on all evening, running firefox, pidgin, and rythmbox, have installed a new repository, have found my network printer and made it the default..... I'm just wondering if I should bother trying to fix this or not?  Or if there's really a problem?  And if there is, and I should work out a solution, what should that solution be?  Now that I've got sound, this is the best install I've had out of the three previous installations.

---

### Post by autocrosser on 2008-05-04
Well, I'll chime in here---

1. Linux counts all partitions it sees--I'll bet you have a couple of hidden partitions (Several computer companies hide restore partitions from users) & that will give you "interesting" counts:)

2. Wubi is a very new idea--not many are in the know about how it is setup--I'd just use the first option that gets you into boot-up.....

3. When I install for people, I have them do a liveCD for a while, then set a dual-boot system with Ubuntu on the second drive in the bios--I try to not mix OS types.

4. As you now have sound, I'd run with it for a while--I'm very sure that there will be several other questions you have not even formulated yet---It's a wild & wonderful world that is named Linux:). 

You'll have a good time with it--People that like Linux go thru 3 stages---check it out--dual-boot it--remove XP/Vista & use the space for better things.......


Welcome to freedom..........

---

### Post by jpcstl on 2008-05-04
Thanks for chiming in, autocrosser!  My buddy actually recommended the three-step system you proposed, and I did play around with the LiveCD ... for about an hour! :)  I was having issues with performance, I think because my (6-year old+) CDRom was cannibalized from my old PC.

(As an aside, I built my first computer last September, so unless XP itself or perhaps some other software I installed created the 'phantom partitions', I really don't know where the count is coming from, but who knows :) I do know it was/is the cleanest HDD I'd ever seen, no bloat except what the XP gave me!)

So, he had me try the LiveCD, had performance issues, and because I knew I wanted to move to Ubuntu anyway, I thought I'd try the wubi way.  Other than the issues here, it's working wonderfully (and I suspect I may not *really* be having issues?).  I don't know how much I want to play with the wubi install, as I don't know how much of the programs and settings I can keep when I go a dual-boot route and I don't necessarily want to do a whole new set up *yet again!*  

For now, though, I'm very content to keep playing and I'll see if I really do have any issues.  As you say, it'll give me a chance to have a boatload of other questions I'm sure I haven't even thought of yet.

Thanks again for chiming in, I do appreciate the encouraging feedback.  Just running with it seems like a great plan for now.

---

### Post by autocrosser on 2008-05-04
As for the Wubi install--If you set a second drive just for Linux you can "move" everything over to the new drive at your time space...I don't know how Wubi sets up, but there are several tutorials on moving into a new drive.

You will most likely have a few "dicey" moments---you'll need to edit your grub menu.lst when you move--think very carefully when you get to that stage. You will also want to create a separate partition for your /home...that makes it very easy for upgrades/problems/reinstalls should you need..there is a wealth of info here & most everyone is quite helpful....

---

