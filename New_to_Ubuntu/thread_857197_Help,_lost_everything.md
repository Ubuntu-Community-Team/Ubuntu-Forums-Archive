---
title: "Help, lost everything?"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by Canuck90 on 2008-07-12
Okay, so I think I may have lost everything I had on my hard drive. I installed Ubuntu on the same drive that I have/had XP on, but I guess it didn't partition it like it thought it would, it just deleted everything? I have been reading about testdisk, and looked at a few tutorials, but, knowing nothing about linux, I can't follow them. Is there any hope of recovery? If so, can someone explain in a dumbed down way how to do so.

---

### Post by philinux on 2008-07-12
Open a  terminal

Accessories Terminal

Copy and paste this

sudo fdisk -l

It will ask for your password, just type it and hit enter.

Post back with the output.

---

### Post by Canuck90 on 2008-07-12
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11601    93185001   83  Linux
/dev/sda2           11602       11978     3028252+   5  Extended
/dev/sda5           11602       11978     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS
ubuntu@ubuntu:~$

---

### Post by philinux on 2008-07-12
> **Canuck90 said:**
> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 98.5 GB, 98522403840 bytes
255 heads, 63 sectors/track, 11978 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11601    93185001   83  Linux
/dev/sda2           11602       11978     3028252+   5  Extended
/dev/sda5           11602       11978     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5c74ae42
[B]
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS[/B]
ubuntu@ubuntu:~$

This looks like your windows is still intact.

Reboot but when you see Grub stage 1.5 hit esc key

The menu should have an entry for your windows. Use the up down keys to hightlight that entry. Press the enter key and windows should boot.

---

### Post by Canuck90 on 2008-07-12
I've tried that, but it only lists 3 all related to Ubuntu

---

### Post by llama320 on 2008-07-12
can you post the output of 
```
tail -70 /boot/grub/menu.lst
```

This will tell us what grub is being told to display

---

### Post by Canuck90 on 2008-07-12
ubuntu@ubuntu:~$ tail -70 /boot/grub/menu.lst
tail: cannot open `/boot/grub/menu.lst' for reading: No such file or directory
ubuntu@ubuntu:~$ 

I take it there is something wrong with that line?

---

### Post by boblemur on 2008-07-12
how did you have your windows setup?? because thats a sepperate drive...


i would say that would be your data drive?? would i be correct?

run 

sudo mkdir /media/tmp
sudo mount /dev/sdb1 /media/tmp -t ntfs-3g -o force

and then goto places > filesystem

then navigate to /media/tmp and look in their... if its your c:\ drive (ie has windows, Documents and settings etc..) thats your windows drive :) and ur lucky its still their...

then its a prob of accessing it... 


first check to see if /boot/grub/menu.lst exists ( sudo gedit /boot/grub/menu.lst ) if thats no a blank document goto the end..,. check if windows isnt their.. add this if it isnt:

title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
chainloader	+1

hope this helps...

---

### Post by Canuck90 on 2008-07-12
Well the only thing that showed up in the media/tmp was the stuff on my external drive, which has neither XP or Ubuntu on it. They are both on the internal, C:\, drive. At the bottom of sudo gedit /boot/grub/menu.lst it lists the 3 Ubuntu options, no Windows. Another reason I think I may have lost everything is that Filesystem, which I guess is my C:\, has over 80GB of free space, it was around 24GB yesterday.:(

---

### Post by nothingspecial on 2008-07-12
If you`ve got your windows disk, you`ll be fine. Shame about your data.
However next time [SIZE="5"]BACKUP![/SIZE]

Since your here now may I suggest this as a good place to start -

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

Have fun and welcome:)

---

### Post by boblemur on 2008-07-12
yeh i guessed as much, didnt think that the 500gb hdd would be your windows parition

so id say yes you have over writen your windows parition

how did you setup your ubuntu install? did you sepperate home and root?

did you have a backup of your important data on the external??

now what i can suggest from here... if you are comfortable moving to ubuntu... thats awesome, the forums can help u sort out any prob you have with linux... but if you still need windows, it can be a bit of a pain to put on, over linux ( cause of the boot manager ) 

but it is possible, you will becomes rarther cramped on that 100gb drive however...

if you need to split the partition to make room, you will need to boot of the ubuntu live cd and use system > admin > partition editor to do it...

because u  can do it when its in use.,..

and then look at.. [http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

for instructions on installing windows back...

---

### Post by Canuck90 on 2008-07-12
Thanks, I don't have the Windows CD, Dell didn't give me one with my laptop :mad: and I was more concerned with getting my data back, it's easy enough to replace software, personal data is impossible.

---

### Post by Sealbhach on 2008-07-12
Here's a good tutorial on dual-booting with nice screenshots.


[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)


Sorry it didn't go well for you first time out.


.

---

### Post by boblemur on 2008-07-12
yeh well dell should have printed the cd key on your laptop... so see if you can borrow a friends cd and use your key...

yes i know its incredibly annoying to lose your data, but in future id suggest you always take an image of your drive before doing any major disk editing work...

esp when you have a large external ( slow but its worth the wait in situations like this)

i would also suggest that you separate your / partition from your /home

this helps when upgrading to a new version of ubuntu or something like that...

windows isnt very good at separation of data and programs, but Ubuntu makes it so easy and i defiantly recommend that you do it, if you ever are going to reinstall ubuntu.

so im sorry to say but your data is gone.

if you need anymore help, dont hesitate to ask :)

---

### Post by 52vincent on 2008-07-17
HiJack!!, hope you don't mind

Anyway hi all, new here. i have the same problem as canuck90. Installed Ubuntu and I did not partition prior, I think I chose the use all disk space option when I should not have. I have searched these forums for hours and it looks like Iam hosed. I thought of trying testdisk and have downloaded it but when i try to install from terminal cant be found yet Iam staring at it on the desktop. Following is my fdisk readout.


Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3ddf88b8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13995   112414806   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

here is my readout of sudo gedit

brian@molerat:~$ sudo gedit/boot/grub/menu.lst
sudo: gedit/boot/grub/menu.lst: command not found

not sure what happened there.

Any help would be great in attempting to recover Vista. should I try testdisk if so how do i install
I know this topic has been covered Ad Nauseum but none of the previous posts have helped.

If there is any other info I can provide i will.



Thanks again.

---

