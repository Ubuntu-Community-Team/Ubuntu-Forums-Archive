---
title: "cannot mount volume"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by moecoors on 2008-05-01
Hi folks
 I'm totally new to Linux. Trying to load my windows wireless driver (broadcom43xx). I tried via CD and also USB stick. I don't have a internet connection with Hardy only with Vista. I get the message box CANNOT MOUNT VOLUME for both devices.
Only trying to load inf and sys files.
Any ideas.
thanks
PS It shows the devices in computer but won't open the files.
PSS The usb stick is a U3.

---

### Post by Jason2gs on 2008-05-01
Does it show the prompt box when you try to mount it? If it does, there should be a small drop-down error in it. If you hit that, it'll give you a command to run to force-mount the volume.

---

### Post by moecoors on 2008-05-01
THanks I'll try again. Have to log off to do it be back later

---

### Post by rbc on 2008-05-01
Have you tried mounting it via CLI? I had several flash drives with that horrible U3 partition and none of them would automount because of it

---

### Post by moecoors on 2008-05-01
CLI???? don't laugh to hard. Please explain.
 I got error message- DBus error no reply-
when trying CD.
I would show you the whole messsage box but don't know how to do that either.:)

---

### Post by MangasColoradas on 2008-05-01
This is happening to me too. Dunno about USBs but for DVD/CD drives I got around it this way...

In the terminal type

```
more /etc/fstab
```

This is my result of that command...

```
stone@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7e5ec-a013-4747-acb3-703b3570f1d1 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=842d5f56-c9da-47c6-9477-1af12059e8cc /home           ext3    relatime      
  0       2
# /dev/sda2
UUID=05DE-C6ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8cbba75e-91c2-4735-ab08-36490b034932 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
stone@ubuntu:~$ sudo mount /dev/scd1
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: /dev/scd1 already mounted or /media/cdrom1 busy
mount: according to mtab, /dev/scd1 is already mounted on /media/cdrom1
```

From that I could see that the mount points for my DVD drives were '/dev/scd0' and '/dev/scd1'

So I then was able to use the terminal to mount them...

```
sudo mount /dev/scd1
```

---

### Post by rbc on 2008-05-01
CLI (Command Line Interface)=terminal. Applications-->Accessories-->Terminal. If MangasColoradas' method does not work, and it seems it will, here's what I did to access the flash drive. Plug it in, then go to terminal and type "sudo fdisk -l" (without the quotes) to see how your flash drive is recognized. For me, it was sdb1. Then, in terminal I typed "pmount /dev/sdb1 /media/sdb1" The pmount command will create the mount point "folder", so make sure it doesn't already exist. The unmount command is "pumount /dev/sdb1". Of course, you'll have to change "sdb1" to whatever fdisk -l shows your thumb drive to be

---

### Post by moecoors on 2008-05-01
> **MangasColoradas said:**
> This is happening to me too. Dunno about USBs but for DVD/CD drives I got around it this way...

In the terminal type

```
more /etc/fstab
```

This is my result of that command...

```
stone@ubuntu:~$ more /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=10b7e5ec-a013-4747-acb3-703b3570f1d1 /               ext3    relatime,error
s=remount-ro 0       1
# /dev/sda5
UUID=842d5f56-c9da-47c6-9477-1af12059e8cc /home           ext3    relatime      
  0       2
# /dev/sda2
UUID=05DE-C6ED  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=8cbba75e-91c2-4735-ab08-36490b034932 none            swap    sw            
  0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
stone@ubuntu:~$ sudo mount /dev/scd1
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: /dev/scd1 already mounted or /media/cdrom1 busy
mount: according to mtab, /dev/scd1 is already mounted on /media/cdrom1
```

From that I could see that the mount points for my DVD drives were '/dev/scd0' and '/dev/scd1'

So I then was able to use the terminal to mount them...

```
sudo mount /dev/scd1
```

Tried but get" File or directory not found"

---

### Post by rbc on 2008-05-01
Can you post your fstab for us?

---

### Post by moecoors on 2008-05-01
Whats the procedure to bring a screen shot from Hardy to Vista? Then I could help you help me.:)
The message was "file or directory not found"

---

### Post by MangasColoradas on 2008-05-01
Hi moe, just do  

```
more /etc/fstab
``` and post the results then someone can tell you what to do from there.

:)

---

### Post by rbc on 2008-05-01
Actually, scratch that for now. What I was after was making sure your CD/DVD drive was listed in fstab, how it's listed, and where the mount point is. Is it listed at all, and if so, is it the same as MangasColoradas'? In other words, /dev/scd0 or scd1?

---

### Post by moecoors on 2008-05-01
No it wasn't listed under either 0 or 1 or 2.
Sorry have to log off till tomorrow. 
thanks a bunch people. Hope I can get your help again when I get back.

---

### Post by moecoors on 2008-05-02
Ok tried again with the CD. When I load the disk I get "invalid mount option" message. The cd-dvd drive icon changes to UDF volume. fstab= file or directory not found. Can't post results because no internet connection with Hardy. I'm dual booting with Vista so every time I get help here I have to reboot to try. Very slow going. 
Thanks

PS invalid mount option is referring to UDF volume not the drive





'

---

### Post by rbc on 2008-05-02
How about this. Since your main objective right now is to get the wireless drivers, just boot up Vista, download the driver to My Documents or wherever. Then, boot into Ubuntu, access the Windows partition and transfer it over to whichever directory you want in Ubuntu

---

### Post by LinuxRocks713 on 2008-05-02
Try executing:

sudo mkdir /media/scd1
sudo mount /dev/scd1 /media/scd1

and to unmount:

sudo umount /dev/scd1

---

### Post by moecoors on 2008-05-02
Ok will try it thanks

---

### Post by moecoors on 2008-05-02
Right no luck with terminal, don't know what I'm doing wrong. However did the driver file fetch from Vista. The "windows wireless drivers" panel asked me for the inf file, installed it and says hardware detected. No wireless option under networks. The installer did not ask me for the sys. files which I understand are needed. ndiswrapper is installed but I guess I have to activate it or what?
Progessing slowly but surely.

---

### Post by rbc on 2008-05-02
Glad you, at least, have the drivers over in Ubuntu now. I haven't, LUCKILY, had to mess with ndiswrapper in a long time, so I can't help you there. Just a suggestion, though, you may want to start a separate thread, since you've obviously got two issues

---

### Post by moecoors on 2008-05-02
New thread it is.
Thanks people

---

