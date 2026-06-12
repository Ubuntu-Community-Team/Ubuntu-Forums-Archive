---
title: "GRUB 1.5 error 17 HALP!!!!"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by mike941 on 2008-09-03
Recently i've been trying out diffrent distros and i ended up deciding to install zenwalk 1.5 over the partition that has my dominant grub on it. I thought this wouold replace that grub with the zenwalk grub. It didn't. I tried running lilofix(the zenwalk bootloader installer i think) but it had an error and couldn't install it's bootloader. So now i get error 17 whenever i try and start my laptop. How can i fix this? Is there a way to make the ubuntu grub the dominant grub again? Can i just install grub again from some linux distros liveCD?

---

### Post by bobnutfield on 2008-09-03
Here are instructions from a previous post on the forum for just this problem:

>  How to restore Grub from a live Ubuntu cd.
This will restore grub if you already had grub installed but lost it to a windows install or some other occurence that erased/changed your MBR so that grub no longer appears at start up or it returns an error.

(This how to is written for Ubuntu but should work on other systems. The only thing to take note of, when you see "sudo" that will mean to you that the following command should be entered at a root terminal.)

Boot into the live Ubuntu cd. This can be the live installer cd or the older live session Ubuntu cds.

When you get to the desktop open a terminal and enter. (I am going to give you the commands and then I will explain them later)

Code:

sudo grub

This will get you a "grub>" prompt (i.e. the grub shell). At grub>. enter these commands

Code:

find /boot/grub/stage1

This will return a location. If you have more than one, select the installation that you want to provide the grub files.
Next, THIS IS IMPORTANT, whatever was returned for the find command use it in the next line (you are still at grub>. when you enter the next 3 commands)

Code:

root (hd?,?)

Again use the value from the find command i.e. if find returned (hd0,1) then you would enter root (hd0,1)

Next enter the command to install grub to the mbr

Code:

setup (hd0)

Finally exit the grub shell
Code:

quit

That is it. Grub will be installed to the mbr.
When you reboot, you will have the grub menu at startup.

Now the explanation.
Sudo grub gets you the grub shell.
Find /boot/grub/stage1 has grub locate the file stage1. What this does is tell us where grub's files are. Only a small part of grub is located on the mbr, the rest of grub is in your boot folder. Grub needs those files to run the setup. So you find the files and then you tell grub where to locate the files it will need for setup.
So root (hd?,?) tells grub it's files are on that partition.
Finally setup (hd0) tells grub to setup on hd0. When you give grub the parameter hd0 with no following value for a partition, grub will use the mbr. hd0 is the grub label for the first drive's mbr.
Quit will exit you from the grub shell.



THIS IS AN EDIT. 5-HT MADE A GOOD POINT AND I AM JUST GOING TO COPY/PASTE IT HERE

Quote:
Just have recommendation to add that may be irrelevant: it might be of benefit to give an explicit warning (though it is mentioned) that this guide will write GRUB to the MBR (just in case someone is using a different boot loader on their MBR and would like to reinstall GRUB to a partition).

If someone wants GRUB on a partition, the 'setup (hd0)' step can be modified to 'setup (hdX,Y)'. Where X is the hard disk, and Y the partition using GRUB's nomenclature of starting from 0 (first partition=0, second=1,...).
THIS IS ANOTHER EDIT. TOSK POSTED A WAY TO MOUNT PROC AND UDEV. THIS WAS NEEDED BECAUSE GRUB WASN'T RECOGNISING THE DRIVE. I THOUGHT IT WAS A VALUABLE COMMENT AND DECIDED TO PUT IT IN THE ORIGINAL POST SO PEOPLE WILL SEE IT AT THE TOP. IT MAY BE MISSED AS JUST A REPLY POST DOWN THE PAGE.
ALL KNOWLEDGE IS WELCOME!

Quote:
Mine was a slightly different story. I couldn't get grub to find the stage1 file or even recognize my drive. So I borrowed some knowledge I picked up while using Gentoo:

You have to mount your root partition using the livecd:
Code:

$
Code:

sudo mkdir /mnt/root

$
Code:

sudo mount -t ext3 /dev/sda6 /mnt/root

Then you have to mount the proc subsystem and udev inside /mnt/root also:
Code:

$
Code:

sudo mount -t proc none /mnt/root/proc

$
Code:

sudo mount -o bind /dev /mnt/root/dev

Doing this allows grub to discover your drives. Next you have to chroot:
Code:

$
Code:

sudo chroot /mnt/root /bin/bash

Now that you're chrooted into your drive as root everything should work.
Code:

#
Code:

sudo grub

I edited in the sudo, just to be safe. When I enter grub and not sudo grub, grub cannot find the file. I do not know if the chroot changes this because I did not try it that way. In the end I figured it was better to err on the side of caution. Tosk I hope you don't mind my editing of your reply.
grub>
Code:

find /boot/grub/stage1

It found mine on (hd0,5)
Code:

grub>
Code:

root (hd0,5)

It successfully scanned the partition and recognized the filesystem-type
Code:

grub>
Code:

setup (hd0)

That was it. It installed and on reboot I was thrown back into Ubuntu.

This might help some people who are having issues so I thought I would post it.

---

### Post by crazyclown on 2008-09-05
I am having a similar issue.  The computer was working great until I rebooted today.  Then I received error 17.
I tried this:
sudo grub

find /boot/grub/stage1
Error 15: File not found.  

Is what I get back.  Any suggestions.

---

### Post by caljohnsmith on 2008-09-05
Crazyclown, post the output of:
```
sudo fdisk -lu
```
Also, do the following and see if it returns anything:
```
sudo grub
grub> find /grub/stage1
```

---

### Post by crazyclown on 2008-09-05
Here is my output for Caljohnsmith
```
sudo fdisk -lu

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x90909090

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   153468944    76734441   83  Linux
/dev/sda2       153468945   160071659     3301357+   5  Extended
/dev/sda5       153469008   160071659     3301326   82  Linux swap / Solaris
ubuntu@ubuntu:~$sudo grub 

grub> find /boot/grub/stage1

Error 15: File not found

```

---

### Post by caljohnsmith on 2008-09-05
OK, from the Live CD, try the following:
```
sudo mount /dev/sda1 /mnt
ls -lR /boot
```
And post the output.

---

### Post by crazyclown on 2008-09-05
For the first command which file system should I specify ext3 for something else
```
sudo mount /dev/sda1 /mnt
mount: you must specify the filesystem type

```

---

### Post by crazyclown on 2008-09-05
Here is the other command.
```

ubuntu@ubuntu:~$ ls -lR /boot
/boot:
total 10916
-rw-r--r-- 1 root root  422607 2008-04-10 16:51 abi-2.6.24-16-generic
-rw-r--r-- 1 root root   79964 2008-04-10 16:51 config-2.6.24-16-generic
-rw-r--r-- 1 root root 7765601 2008-04-22 18:44 initrd.img-2.6.24-16-generic.bak
-rw-r--r-- 1 root root  103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root  899892 2008-04-10 16:51 System.map-2.6.24-16-generic
-rw-r--r-- 1 root root 1904248 2008-04-10 16:51 vmlinuz-2.6.24-16-generic
ubuntu@ubuntu:~$ 
```

---

### Post by caljohnsmith on 2008-09-05
"mount" shouldn't need to ask for the file system type of sda1 since it is a known type it can figure out, so I suspect there may be something wrong with sda1. Before you try and mount it again, do the following:
```
sudo fsck /dev/sda1
```
If you get any errors and it asks to fix them, say yes.

---

### Post by crazyclown on 2008-09-05
Thanks I am doing that right now. It has found several errors and is fixing them now.

---

### Post by crazyclown on 2008-09-05
That fixed my grub error.  Now I am researching a new error
```
Could not start kstartupconfig. Check your installations.

```
Thanks Caljohnsmith and sorry for hijacking your thread Mike941.

---

### Post by bodhi.zazen on 2008-09-05
Just as a work of generic support, here is the best source of information I now of re: grub:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

There are some specialized things, such as encryption and LVM that I do not think are on there ...

but it is a great guide.


Otherwise you are in competent hands with caljohnsmith ;)

---

