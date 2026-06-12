---
title: "crashed"
date: 2011-10-08
forum: New to Ubuntu
---

### Post by wildfootprints on 2011-10-08
I have ubuntu operating system as my default I can also boot up Windows. I have a serious issue my ubuntu has crashed and I cant boot it up. Widows I can still get into. But all my files are in Linyx. What can I do

---

### Post by matt_symes on 2011-10-08
Hi

You can get you files off your drive using a LiveCD/USB and mounting your Ubuntu partition.

As to your issue, we need much more information to try to help you fix the crash and the reason why you can't use Ubuntu.

Where is it failing ?

Kind regards

---

### Post by wildfootprints on 2011-10-08
So Im completely not tech savy so could you explain - LiveCD/USB and mounting your Ubuntu partition, please.

My computer comes up with UUbuntu 2.6.32-34
mount ;mounting/dev on/root/dev failed
no such file or directory
mount:mounting/sys on/sys failed
no such file or directory
mount:mounting/proc on/root/proc failed
no such file or directory

Target file system doesnt haw/sbin/init
No init found. Try passing init=bootarg

Busy Box v1.1.13 (ubuntu 1.1.13.3-1 ubuntu) build in shell 1 ash.
Enter 'help' for list of comands


Does this help with helping solve my problem??
I have command list too, Ill type it out

---

### Post by wildfootprints on 2011-10-08
The commands my computer is ordering

.:[alias break cd chdir command continue echo eval exec exit export false getopts hash help let local printf pvd read readonly return set shift source test times trap true type ulimit umask clear cmp cp cut dealloct df du dumpkmap echco egrep env expr false fbset fdflash fgrep find gunzip gzip host name if config ip kill In loadfont loadkmap Is mkdir mkfifo mknod mkswap nktemp more mount mv openvt pidof printf ps pwd readlink reset run rmdin sed setkeycodes sh sleep sort stat static-sh stty sync tail tee test touch tr true tty unmount uname uniq wc wget yes 3cat

What this means I have no idea but it may help someone understand what my comuter needs?
Help/

---

### Post by madjr on 2011-10-08
live cd how to:

[http://www.youtube.com/watch?v=p6TBuab-EPw](http://www.youtube.com/watch?v=p6TBuab-EPw)

[http://www.youtube.com/watch?v=gG6BvS0ve3g&feature=related](http://www.youtube.com/watch?v=gG6BvS0ve3g&feature=related)

should be similar for newer versions

---

### Post by drofart on 2011-10-08
> **wildfootprints said:**
> I have ubuntu operating system as my default I can also boot up Windows. I have a serious issue my ubuntu has crashed and I cant boot it up. Widows I can still get into. But all my files are in Linyx. What can I do


[http://ubuntuforums.org/showthread.php?p=11181195#post11181195](http://ubuntuforums.org/showthread.php?p=11181195#post11181195)   //////

LIVE_CD/USB



[LIST=1]
[*]Enter  your computers BIOS to check computer can boot from CD ROM. If you can  boot from CD, insert CD ROM into drive. Exit the BIOS (if needed save  your settings to make sure the computer boots from the CD ROM).
[*]When the Ubuntu splash screen comes up with the **boot:** prompt, type in **rescue** and press enter.
[*]Choose your language, location (country) and then keyboard layout as if you were doing a fresh install.
[*]Enter a host name, or leave it with the default (Ubuntu).
[*]At  this stage you are presented with a screen where you can select which  partition is your root partition (there is a list of the partitions on  your hard drive, so you are required to know which partition number  Ubuntu is on). This will be  dev/discs/disc0/partX, where the **X** is a partition number.
[*]You are then presented with a command prompt (a hash), type:
[/LIST]

$ grub-install /dev/XXX
where XXX is the device of your Ubuntu install. (eg: *grub-install /dev/sdb*). 



Hope it will fix you.

---

### Post by matt_symes on 2011-10-08
Hi

> **wildfootprints said:**
> So Im completely not tech savy so could you explain - LiveCD/USB and mounting your Ubuntu partition, please.

My computer comes up with UUbuntu 2.6.32-34
mount ;mounting/dev on/root/dev failed
no such file or directory
mount:mounting/sys on/sys failed
no such file or directory
mount:mounting/proc on/root/proc failed
no such file or directory

Target file system doesnt haw/sbin/init
No init found. Try passing init=bootarg

Busy Box v1.1.13 (ubuntu 1.1.13.3-1 ubuntu) build in shell 1 ash.
Enter 'help' for list of comands


Does this help with helping solve my problem??
I have command list too, Ill type it out

As others have described, backup your files off Ubuntu using a liveCD.

Is this a WUBI or partition install ?

You are being dropped to the Busy box prompt. Being dropped to the busy box prompt can happen for a number of reasons. 

We can tackle this after you have backed up your files if you want or you can reinstall Ubuntu. The choice is yours.

Kind regards

---

### Post by ajgreeny on 2011-10-08
If this is a partitioned install, not a wubi version, where ubuntu is installed in windows, you can try running a system check from a live CD.

1.  Boot to live Ubuntu CD.
2.  Open a terminal; how you get that depends on version of ubuntu.  In 11.04 it is in the launcher bar on the left of the screen, in 10.04 it is in Applications ->Accessories menu.
3.  In terminal type ```
sudo fdisk -l
``` look for the partition with an linux file system and note the /dev/sda#.
4.  Run command ```
sudo e2fsck /dev/sda#
```and note any error messages that appear, then try rebooting to your ubuntu installation.  If still no luck tell us the error messages that you saw.

---

### Post by wildfootprints on 2011-10-13
Thanks for all that great input.
I got it up and running again.

I went out and got an external hard drive to much to loose it scared me!

---

