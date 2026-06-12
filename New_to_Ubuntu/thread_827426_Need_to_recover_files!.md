---
title: "Need to recover files!"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by vanjagator on 2008-06-12
Hello,

Im completely desperate tonight. I just finished some work on my craptop tonight. I turned on the computer again and my Windows XP would not start (some registry failure). I did not want to format C: right away and install a fresh copy of Windows XP, because I have important documents on my Desktop that I need tomorrow.

Then I remembered I have an Ubuntu 5.10 Live CD, so I thought I will access my files with that. I think I know how to mount the C: drive, but Im not able to access it. It says I do not have permission. Im totally desperate, and I need step by step help ASAP. If it is even possible.

Thank you guys and girls!

I promise I will use Linux more often in the future :)

PS any other non-ubuntu ideas are welcome as well :)

---

### Post by gr4nf on 2008-06-12
Try using sudo before the mount command. That will give you admin power. If that fails, which it will, use SAMBA. I have never used it before, but have heard it is rather self-explanitory.

---

### Post by vanjagator on 2008-06-12
I did use sudo, but it still wont let me access the files. I do not know if it is possible with such old version of Ubuntu.

Can I run SAMBA even thou Im using Live CD. It wont mess up anything?

---

### Post by gr4nf on 2008-06-12
Yes.

---

### Post by sam_delta on 2008-06-12
i duno if ubuntu 5.10 has ntfs default support? 

yes, you can get your data back, id recomend to download ubuntu 8.04 or 7.10 and the window$ c: drive should appear under places>computer

ive done this before, when my brothers window$ crashed and would not boot

again, im not sure if 5.10 has ntfs support, i might be wrong

sam

---

### Post by vanjagator on 2008-06-12
Is there a Live version for every Ubuntu version?

---

### Post by gr4nf on 2008-06-12
all of the ones i know of. Definitely for 7.10 and 8.4

---

### Post by sam_delta on 2008-06-12
yeah, you can download them from ubuntu website
[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

sam

---

### Post by vanjagator on 2008-06-12
Thanks a lot guys!

Will I need to mount again in the newest version or will it just appear?

---

### Post by Sef on 2008-06-12
For pulling data off a hard disk, [Knoppix]("http://knoppix.com") works great.  If the data has been deleted, I would use [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by vanjagator on 2008-06-12
is this the only file I need: [ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso](ftp://ftp.kernel.org/pub/dist/knoppix/KNOPPIX_V5.1.1CD-2007-01-04-EN.iso)

---

### Post by sam_delta on 2008-06-12
> **vanjagator said:**
> Thanks a lot guys!

Will I need to mount again in the newest version or will it just appear?

you will have to mount it, but its an automatic process. you will just click in the top-panel 'places>computer' and a window will appear, under that window, you will see all the drives on your computer, you just double click your windows drive, and it will be automatically mounted, and a window with all the files will pop-up.

sam

---

### Post by sam_delta on 2008-06-12
the new knowpix is a DVD, so if you decide knopix over ubuntu , itll take longer to download, and youll need a dvd burner

sam

---

### Post by vanjagator on 2008-06-12
You saved my day (and night).

Thanks a lot!

Cant wait to finish downloading :)

---

### Post by sam_delta on 2008-06-12
> **vanjagator said:**
> You saved my day (and night).

Thanks a lot!

Cant wait to finish downloading :)
alright, just wondering you decided on knopix or ubuntu :P?

anyways when you finish the download, if you need help, we'll be around

sam

---

### Post by jdrodrig on 2008-06-12
> **vanjagator said:**
> You saved my day (and night).

Thanks a lot!

Cant wait to finish downloading :)

It might be very stupid comment but, why you dont use the winXp installation disk. It should boot and give you access to your disk.

You mention you were about to do a fresh install, so I assume you have the CD.

Just something you can try, while you wait to download the other option.

---

### Post by vanjagator on 2008-06-13
Im pretty good with windows so I know Ive done everything I could. :)

Download failed and I saw that when I woke up few mins ago so I started downloading Ubuntu 8.04 again. Even 5.10 is easy to use, so I didnt want to experiment with Knoppix for now.

---

### Post by sam_delta on 2008-06-13
alright, good luck and keep us up to date :p

make sure you burn the disk at a low speed and check it for defects on the live cd menu

sam

---

### Post by vanjagator on 2008-06-13
It says it is unable to mount location :confused:

*DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.*

Any tips? Can I mount it from the terminal anyhow?

I can see more details now:

$LogFile indicates unclean shutdown (0, 0) Failed to mount... ... Operation is denied because NTFS is marked to be in use...

---

### Post by _sphinx_ on 2008-06-13
I think you will not be able to mount the ntfs partition because either you have done a cold shutdown or hibernated your windows as the error says.

---

### Post by vanjagator on 2008-06-13
Thats because I cant start windows regularly :(

Is there any way to bypass that? Is the "force" function dangerous?

---

### Post by aquavitae on 2008-06-13
Don't you have a friend with windows? You could just remove your drive and plug it into his computer. As for mounting the ntfs: it is because winxp didn't shut down properly. I keep having the same problem so I'll google it. I'll post back if I find anything.

---

### Post by vanjagator on 2008-06-13
Its a laptop so I cant just connect hard drive to a different computer :(

---

### Post by aquavitae on 2008-06-13
Googled and found ntfsfix. Try this:
```
ntfsfix /dev/sda1
```
assuming the device is /dev/sda1. I assume you know the device name if you're using mount.

---

### Post by vanjagator on 2008-06-13
I am sorry, but I am completely new to Linux and Ubuntu.

What exactly do I need to type in the terminal?

How to be sure that it is sda1?

---

### Post by aquavitae on 2008-06-13
What command did you use for mount? Should be something like ```
sudo mount /dev/sda1
```
To make it slightly easier, post the output of ```
sudo fdisk -l
```.

---

### Post by vanjagator on 2008-06-13
It is sda1.

But when I try to mount it from the terminal it says: 

mount: cant find /dev/sda1 in /etc/fstab or /etc/mtab

---

### Post by aquavitae on 2008-06-13
Yes, you'd need to specify a mount point. The full command would be something more like ```
sudo mount /dev/sda1 /media/windows
```But don't worry about that, continue trying to mount it the way you were before, just type this command first:
```
sudo ntfsfix /dev/sda1
```

---

### Post by vanjagator on 2008-06-13
SUCCESS!!!

:guitar:

---

### Post by aquavitae on 2008-06-13
Good! Now I also know how to do it :)

---

### Post by Voland on 2008-06-13
> **vanjagator said:**
> SUCCESS!!!

:guitar:

You could use option --force in mount command without any big risk. Unclean turn-off in M$ Windows might leave some opened descriptors of files. This option cleans them.

---

### Post by sam_delta on 2008-06-13
gladdd you got your info back bro :p

sam

---

