---
title: "how to access to windows"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by jfchabot on 2008-09-07
Hello

I am very new with ubuntu and need to access to my windows files (my windows system have just crashed) and may be be able to use some windows compatible software.
I will really appreciate some help for some ccoperative person

Thank you

John

---

### Post by Tatty on 2008-09-07
Hi,

Could you just clarify,  do you have ubuntu installed already on your computer, or are you just asking how to recover your windows data?

If you are just looking for a way in to your broken system, boot with a ubuntu live CD, from there you can mount your windows partition and rescue your data.

If you already have ubuntu installed then boot into it, and go to places->computer.  From there you should be able to see your windows partition and mount it.

If you cannot see your windows partition, please paste the output of the following commands into this thread:
```
sudo fdisk -l
```
```
cat /etc/fstab
``` (only need if you already have ubuntu installed)

---

### Post by jfchabot on 2008-09-07
thanks Tatty

I have windows (XP cracked) and ubuntu installed. Windows crashec yesterday. I do not not know recover windows and decide to use linux everyday. i need to get access to my windows files and may be use some windows software yet installed

---

### Post by jfchabot on 2008-09-07
> **jfchabot said:**
> thanks Tatty

I have windows (XP cracked) and ubuntu installed. Windows crashec yesterday. I do not not know recover windows and decide to use linux everyday. i need to get access to my windows files and may be use some windows software yet installed

whhat do you mean by "mount"

---

### Post by jfchabot on 2008-09-07
> **Tatty said:**
> Hi,

Could you just clarify,  do you have ubuntu installed already on your computer, or are you just asking how to recover your windows data?

If you are just looking for a way in to your broken system, boot with a ubuntu live CD, from there you can mount your windows partition and rescue your data.

If you already have ubuntu installed then boot into it, and go to places->computer.  From there you should be able to see your windows partition and mount it.

If you cannot see your windows partition, please paste the output of the following commands into this thread:
```
sudo fdisk -l
```
```
cat /etc/fstab
``` (only need if you already have ubuntu installed)

what do you mean by "mount" ?:confused:

---

### Post by DOS4dinner on 2008-09-07
> **jfchabot said:**
> whhat do you mean by "mount"

Mount means "To make a hard drive available to the operating system" roughly. I don't know the commands needed, but someone here should, or google might help.

About your windows programs: You will have to install them from their setup/install.exe in ubuntu with wine. You will not be able to just copy over programs, as they (probably) will not run right, if at all. 

Did you do a wubi install, per chance? If so, you might already have access to the files through the search for files button under places.

---

### Post by jfchabot on 2008-09-07
> **DOS4dinner said:**
> Mount means "To make a hard drive available to the operating system" roughly. I don't know the commands needed, but someone here should, or google might help.

About your windows programs: You will have to install them from their setup/install.exe in ubuntu with wine. You will not be able to just copy over programs, as they (probably) will not run right, if at all. 

Did you do a wubi install, per chance? If so, you might already have access to the files through the search for files button under places.
Thank you for your kelp DOS4dinner.

---

### Post by Tatty on 2008-09-07
If you go to Places->Computer, you should be able to see your windows partition on the left hand side.  You should then be able to click on it to access your windows files.

If not, we should be able to set this up to work, but we will need you to open a terminal and post the output of the following two commands:

```
sudo fdisk -l
```

```
cat /etc/fstab
```

---

### Post by Xiong Chiamiov on 2008-09-07
It sounds like you probably don't actually want to install and use Linux, even though you think you do.

You cannot expect Windows programs to run on Linux.  Some of them will, through Wine, but most do not, or only work *somewhat*.

If you are willing to change the way you think about computing, and spend some time learning how things work, then we'll help you switch.  If not, though, then our time would be better spent helping you backup your windows files and reinstall that.

---

### Post by jfchabot on 2008-09-07
> **Tatty said:**
> If you go to Places->Computer, you should be able to see your windows partition on the left hand side.  You should then be able to click on it to access your windows files.

If not, we should be able to set this up to work, but we will need you to open a terminal and post the output of the following two commands:

```
sudo fdisk -l
```

```
cat /etc/fstab
```
thanks again Tatty
on the left hand side of Places->Computer i just have Home folder and File system
i am sorry

---

### Post by jfchabot on 2008-09-07
> **Xiong Chiamiov said:**
> It sounds like you probably don't actually want to install and use Linux, even though you think you do.

You cannot expect Windows programs to run on Linux.  Some of them will, through Wine, but most do not, or only work *somewhat*.

If you are willing to change the way you think about computing, and spend some time learning how things work, then we'll help you switch.  If not, though, then our time would be better spent helping you backup your windows files and reinstall that.
Thank you for your comments
I would love both.
1 - restore my windows system and ues ubuntu everyday but i need to use some windows programs like homestead site editor, smart draw, gsite crawler, Internet business promoter,... that do not work with Linux
And, now, my windows system has crashed and would like to resotre it.
I have tryed to restore with C:\windows\system"É\RESTORE\RSTRUI.EXE but it do not work. I get the restore windows but it stay blank. I cannot enter as safe mode because pressing F8 do not work

---

### Post by Tatty on 2008-09-07
Can you please post the output from

```
sudo fdisk -l
```

```
cat /etc/fstab
```

If you arent sure how to do this, first you need to open a terminal by clicking Applications->Accessories->Terminal

Then in the terminal type (or preferably copy and paste) the first command.  If you have typed it correctly it will list the partitions in your computer, please copy and paste that into this thread.

Then do the same with the second command which will let us know how ubuntu is currently dealing with your patitions.

note: to copy and paste in a terminal you must use ctrl+shift+c and ctrl+shift+v respectively.

---

### Post by jfchabot on 2008-09-07
> **Tatty said:**
> Can you please post the output from

```
sudo fdisk -l
```

```
cat /etc/fstab
```

If you arent sure how to do this, first you need to open a terminal by clicking Applications->Accessories->Terminal

Then in the terminal type (or preferably copy and paste) the first command.  If you have typed it correctly it will list the partitions in your computer, please copy and paste that into this thread.

Then do the same with the second command which will let us know how ubuntu is currently dealing with your patitions.

note: to copy and paste in a terminal you must use ctrl+shift+c and ctrl+shift+v respectively.
WITH sudo fdisk -l I GET:
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140       14283    57384180   83  Linux
/dev/sda3           14284       14593     2490075    5  Extended
/dev/sda5           14284       14593     2490043+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21f16422

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS


WITH cat /etc/fstab I GET:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b5a4f4dc-3360-4942-a66f-949b869a3b01 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8416e18-7cf7-47ec-96ca-ce051f169aa9 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

What do i do with that please.

Thanks again !

---

### Post by Tatty on 2008-09-07
If you want the windows partition to mount permanently each time you boot your computer, firstly create a folder to mount it into:
```
sudo mkdir /mnt/windrive
```

then you need to add a line to your fstab file, first we will back it up in case it all goes wrong:

```
sudo cp /etc/fstab /etc/fstab.backup
```

Now open it for editing as superuser with:

```
gksu gedit /etc/fstab
```

This will prompt you for your password - this is the same password you log into your account with.

next add the following line to the bottom of your file

```
/dev/sda1 /mnt/windrive ntfs-3g defaults 0 0
```

Then save and close gedit.  When you reboot your computer, your windows drive should be available in /mnt/windrive.

---

### Post by jfchabot on 2008-09-07
> **Tatty said:**
> Can you please post the output from

```
sudo fdisk -l
```

```
cat /etc/fstab
```

If you arent sure how to do this, first you need to open a terminal by clicking Applications->Accessories->Terminal

Then in the terminal type (or preferably copy and paste) the first command.  If you have typed it correctly it will list the partitions in your computer, please copy and paste that into this thread.

Then do the same with the second command which will let us know how ubuntu is currently dealing with your patitions.

note: to copy and paste in a terminal you must use ctrl+shift+c and ctrl+shift+v respectively.
WITH sudo fdisk -l I GET:
/dev/sda1   *           1        7139    57343986    7  HPFS/NTFS
/dev/sda2            7140       14283    57384180   83  Linux
/dev/sda3           14284       14593     2490075    5  Extended
/dev/sda5           14284       14593     2490043+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21f16422

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS


WITH cat /etc/fstab I GET:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=b5a4f4dc-3360-4942-a66f-949b869a3b01 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d8416e18-7cf7-47ec-96ca-ce051f169aa9 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

What do i do with that please.

Thanks again !

---

### Post by Tatty on 2008-09-07
See my above post :)

---

