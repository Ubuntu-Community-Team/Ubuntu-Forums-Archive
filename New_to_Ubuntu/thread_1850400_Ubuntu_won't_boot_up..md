---
title: "Ubuntu won't boot up."
date: 2011-09-26
forum: New to Ubuntu
---

### Post by suomalainen on 2011-09-26
Ubunteros,

I tried to boot up my machine but as you can see from the attached picture I cannot.

My O/S is on an external drive and version 10.04LTS.

I have another version of 10.04 on a usb Stick just for such emergencies. So that's how I got online right now.

Can someone tell me how I can get my system back up and running.

Thank you very much.

---

### Post by westie457 on 2011-09-26
> **suomalainen said:**
> Ubunteros,

I tried to boot up my machine but as you can see from the attached picture I cannot.

My O/S is on an external drive and version 10.04LTS.

I have another version of 10.04 on a usb Stick just for such emergencies. So that's how I got online right now.

Can someone tell me how I can get my system back up and running.

Thank you very much.

Hello.

First step here is to start Gparted while running from the USB stick and run a file system check over the USD drive partitions.
If that does not fix it then check for badblocks using the terminal to attempt repairs.

After that if you still cannot use the drive I strongly suggest that you use the drive manufacturers software to give it a full diagnostic check.

Hopefully the first suggestion works.

---

### Post by Lisiano on 2011-09-26
Seems like you had a hard-shutdown recently. Try running this [/code]sudo fsck /dev/sdb#[/code]
Replace # with the partition number. You can find it using ```
sudo blkid
```Or ```
mount
```Or ```
sudo fdisk -l
```
Also make sure it is not listed in "mount" when you run fsck.

EDIT: Ninja-d by westie457. Though right, try using GParted if you don't want to use the Terminal.

---

### Post by suomalainen on 2011-09-26
Thanks everyone for the suggestions!

@ Lisiano

I ran "sudo blkid" but how do I know what sdb or sdd to use? I think it is ssd1 but unsure. You can help me?

Thanks for your support!!

paavo@paavo-laptop:~$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D5-0B16" TYPE="vfat" 
/dev/sda2: UUID="0EA8C6E9A8C6CF01" TYPE="ntfs" 
/dev/sda3: LABEL="DellRestore" TYPE="vfat" 
/dev/sdb1: UUID="22b752f7-525e-4ee6-b3ef-fc8978607ae5" TYPE="ext4" 
/dev/sdb5: UUID="f4590d33-c961-49f4-aeab-405f5358703f" TYPE="swap" 
/dev/sdd1: LABEL="Jasper" UUID="64F0E18EF0E166B0" TYPE="ntfs" 
/dev/sdd2: LABEL="Ununtu 10.04 LTS" UUID="51a8859b-9c27-4e9d-b7cf-f17178aefc95" TYPE="ext3" 
/dev/sdd3: UUID="1fb0bff6-e5fa-405c-ba42-f5a8003c90d5" TYPE="swap"

---

### Post by westie457 on 2011-09-26
```
sudo fdisk-l
``` should give a clearer indication of which drive is which.

---

### Post by suomalainen on 2011-09-26
I got this msg:

paavo@paavo-laptop:~$ sudo fdisk-l
[sudo] password for paavo: 
sudo: fdisk-l: command not found
paavo@paavo-laptop:~$ sudo fdisk-l

Also how do I unmount a drive if it is mounted already?

Thank again for the help!

---

### Post by westie457 on 2011-09-26
> **suomalainen said:**
> I got this msg:

paavo@paavo-laptop:~$ sudo fdisk-l
[sudo] password for paavo: 
sudo: fdisk-l: command not found
paavo@paavo-laptop:~$ sudo fdisk-l

Also how do I unmount a drive if it is mounted already?

Thank again for the help!

I am not very good with the command line even though I do use it, I cannot remember all the commands so I usually suggest GUI apps.

Start Gparted it should find all your drives, by default it will display /dev/sda in the top-right corner. Clicking here should also display the other drives, slect each in turn until you find the right one. To unmount any partition, right-click on it and then select unmount.

---

### Post by suomalainen on 2011-09-26
I installed Gparted but it will not let me unmount the drive in question.

I'd like to use a line command in terminal but don't know how to...

---

### Post by razorxpress on 2011-09-26
You unmount a drive using umount command like
$ sudo umount /dev/sdb1

If you don't have fdisk running then init process is not running. So this problem has arrived before linux has started. Linux starts only after init gets called. In your fdisk -l did you type fdisk-l instead. There should be space between fdisk and -l. If fdisk command still does not get executed then ubuntu has not started even to give you command. I have had such situations. Those were in my old computer with corrupted hard disks. If you don't shutdown properly then also such problems can come. Solution is to run  fsck.

If you are not sure which drive the problem has come, you can try mount command.

$ mount

It is only a hope that mount runs if you are not mounted to drives already.

So your solution would be to rely on fdisk like
$ sudo fdisk -l

or if sudo even does not run you can try fdisk -l

and try to run fsck to every drive. Other drives that are not related to Linux don't generate such problems, so you can check all the drives listed as Linux under System on the result of fdisk. If you did not create drives like /boot then even /home won't have you such fatal error. The culprit is most of the time / (root) drive.

sudo fsck /dev/sda6

Here I assue 6 as the drive number

If fsck starts to generate suggestions, you can use -y with fsck to say yes to all the settings it wants to suggest.

You said you installed gparted. If you are booting from pen drive(drive) it already has gparted. May be you were trying to unmount (umount) filesystem drive that is the root of pendrive. Your previous drive should be something else.

If you boot in recovery mode there is an option at the bottom of scrollbar called root that takes you to a terminal. There you can umount all drive using

# umount -a

However it will not unount /, you can check you root(/) even without unmounting in such situations. You said your drive is ext3 so run
# mount
# fsck.ext3 /dev/sda1

If sda1 is your root. Here # is not any command it is only root prompt and mount will show only drives mounted, it will not mount anything unless drive specified.

---

### Post by Lisiano on 2011-09-26
It seems your Ubuntu partition is either /dev/sdd2 due to it's Label.
```
/dev/sdd2: LABEL="Ununtu 10.04 LTS" UUID="51a8859b-9c27-4e9d-b7cf-f17178aefc95" TYPE="ext3" 
```
Or /dev/sdb1 due to it being ext4
```
/dev/sdb1: UUID="22b752f7-525e-4ee6-b3ef-fc8978607ae5" TYPE="ext4" 
```
To unmount them, type
```
sudo umount -f /dev/sdd2
sudo umount -f /dev/sdb1
```
Now just fsck them both
```
sudo fsck /dev/sdd2
sudo fsck /dev/sdb1
```

Also, if you type ```
mount
``` before trying to unmount either partition and you see that either sdd2 or sdb1 is / like so
```
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
```
Then don't try to unmount it, as it's not possible and there is no need to since we are not checking your USB Pendrive.

---

### Post by suomalainen on 2011-09-26
@ Everyone !!!!

Thanks for all your support toward helping me. Much appreciated!

I was able to FSCK sdd2 and then I rebooted but nothing happened. Problem remained.

However, I went to Gparted again and this time it let me check the drive in question. I guess because FSCK checked and unmounted it?

In any case it's being checked at the moment and I'll report back as soon as practical. and gparted has finished what it is that it does.

Thanks again for your support.

---

### Post by suomalainen on 2011-09-26
Gparted didn't work so I'm not sure if there is anything else I can try?

What are your thoughts?

---

### Post by westie457 on 2011-09-27
Do you have an earlier kernel in your Grub menu to boot from?

If so choose it and then update to the newer one to (hopefully) correct the errors you are getting at the moment.

If that fails then reinstall from the USB Stick. It is a Live one I hope. Without formatting any partitions, this should keep your data safe and reset the OS. Be prepared by making a backup of your data if you do not already have one.

The last resort if the above fails is a clean install including formatting of the / partition.


                +++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

Edit:    I would still check the drive for bad sectors at some point, if only for peace of mind that there is no damage to the hard drive itself. It won't hurt.

---

### Post by suomalainen on 2011-09-27
@westie457

I had to do a new install. I have 10.04LTS running on my external drive. Would you happen to know how I can check if GRUB had been installed correctly and to the right place?

Thanks!

---

### Post by westie457 on 2011-09-27
The only thing I know of that will do that is one of the most widely used diagnotic programs for investigating general start up problems - bootinfoscript.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It can be run from a LiveCD or a normal Desktop. Download and usage instructions including ones for posting to a Forum are provided.

---

### Post by suomalainen on 2011-09-27
I know there is a terminal command that shouws where GRUB is placed with everythnig else.

---

### Post by westie457 on 2011-09-27
I am sure you are right about the command, however I do not know what it is. The only thing I have found that might help is _[here]("https://help.ubuntu.com/community/Grub2")_.
It is a long way down the page.

---

### Post by suomalainen on 2011-09-28
All,

The only fix to this situation was a re-install of 10.04LTS!

I have to say that I was left amazed that when I copied over my .mozilla and .evolution files everything remained intact. The simplicity was so easy that I believe, at least for me, that this is a better way to back up settings. Especially for email.

The crash I experienced occurred after following the instructions here:

[http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/](http://franklinchua.wordpress.com/2010/05/03/huawei-e1550-on-ubuntu-10-04-lucid-lynx/)

Does anyone see anything bad within the code listed? As for me, this is what killed my o/s......

Thanks to everyone that offered support!

Suomalainen

---

