---
title: "Terminal command: Permission denied?"
date: 2008-08-26
forum: New to Ubuntu
---

### Post by kansasnoob on 2008-08-26
I just did some repartitioning and everything seemed to be working OK, but I wanted to check the UUID on all partitions because it's bound to be hosed somewhere and I get permission denied when I try to access fstab or initramfs.

I'd bet I'm just forgetting something simple. Maybe I need to use gedit or something? I've done it before, but I must have written darn poor notes because now I can't figure it out:confused:

This is what I get:

> lance@lance-desktop:~$ sudo blkid 
/dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs" 
/dev/sda5: UUID="3f6a93da-cbc0-4203-92ce-42ff70394f0a" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5b397135-2a82-4933-aefd-00d7ff23b413" 
/dev/sda7: UUID="cb8d8925-8059-46bc-8312-9ce5f42afa91" SEC_TYPE="ext2" TYPE="ext3" 
lance@lance-desktop:~$ sudo blkid -c /dev/null
/dev/sda1: UUID="5A3CAE183CADEEE7" TYPE="ntfs" 
/dev/sda5: UUID="3f6a93da-cbc0-4203-92ce-42ff70394f0a" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="5b397135-2a82-4933-aefd-00d7ff23b413" 
/dev/sda7: UUID="cb8d8925-8059-46bc-8312-9ce5f42afa91" SEC_TYPE="ext2" TYPE="ext3" 
lance@lance-desktop:~$ /etc/fstab
bash: /etc/fstab: Permission denied
lance@lance-desktop:~$ /etc/initramfs-tools/conf.d/resume
bash: /etc/initramfs-tools/conf.d/resume: Permission denied


---

### Post by arpanaut on 2008-08-26
ehm...

sudo cat /etc/fstab
or:
gksudo gedit /etc/fstab

maybe?

---

### Post by halitech on 2008-08-26
try this
```
gksu gedit /etc/fstab
```

---

### Post by Separ on 2008-08-26
> **arpanaut said:**
> ehm...

sudo cat /etc/fstab
or:
gksudo /etc/fstab

maybe?

"cat" does not require root privileges as it only outputs the content of a file.

It would also be "gksudo **gedit** /etc/fstab"

---

### Post by kansasnoob on 2008-08-26
Yep, I just hadn't included the gksudo gedit prefix in my notes!

Thanks all.

---

### Post by amitkr on 2009-07-10
> **arpanaut said:**
> ehm...

sudo cat /etc/fstab
or:
gksudo gedit /etc/fstab

maybe?


> **vanadium said:**
> Sorry, sorry, I did not notice you are a xubuntu user. gedit is standard with Ubuntu.

Anyway, you can use the text based "nano" editor. The command becomes

```

sudo nano /etc/fstab

```


I am using ubuntu 7.04, but now i am not able to login. It starts with black screen saying- /etc/init.d/rc: 2: sed: Permission denied

after i enter the root & password, it asks me to run apt-get install sed.

I don't have any clue, why it is happening?

I am able to see my files with ls command.

Command prompt is - root@(none):/#

when i run command  **sudo fdisk -l**

            Device      boot  Start     End      Blocks        Id      System
           /dev/sda1    *       1        1913    1536641      7      HPFS/NTFS
           /dev/sda2            **1914 **  9729    62782020     f      W95 Ext'd (LBA)
           /dev/sda5            **1914**   3122    9711261      83     Linux
           /dev/sda6            4464   7013    20482843+  b       W95 FAT32
           /dev/sda7            7014   9729    21816238+  b       W95 FAT32
           /dev/sda8            3189   4463    10241406    7        HPFS/NTFS
           /dev/sda9            3123   3188    530113+      82     Linux swap / solaris  

But now when i am trying to mount the linux partition /dev/sda5 with the following command, it is showing [B]sudo: mount: command not found
[/B]
**sudo mount /dev/sda5 /etc/amit**

Eveen when i am running **mount** command, it's showing -

**-bash: /bin/mount: Permission denied**

when i run **sudo cat /etc/fstab, **1st few lines are: [B]

#<file system>   <mount point>  <type>  <options>   <dump>    <pass>
proc                         /proc               proc      defaults           0             0
#/dev/sda5
UUID=e7a84097-a404-4bd4-bff6-f90b2eb2bb7c2 /         ext3         defaults, erors=remount-ro    0          1
   
[/B] It seems i don't have the permission to mount it. plz help me out. thanx in advance

---

