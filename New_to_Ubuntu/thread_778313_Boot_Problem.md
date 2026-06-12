---
title: "Boot Problem"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by faisal892 on 2008-05-02
Hi all,

I had Windows XP, Mnadriva and openSUSE Linux installed on my system. Now I have installed Ubuntu as well. The problem is that I cannot login to Windows XP, Grub says :Error 17, cannot mount the drive, please any key to continue" When I press any key Grub menu appears again.

FYI, I can log in to Ubuntu, Mandriva and OpenSUSE linux without any problem but cannot to Windows XP.

Please if any body could help.


Regards

Faisal.

---

### Post by PmDematagoda on 2008-05-02
Can you post the outputs of:-
```
cat /etc/mtab
```
and
```
cat /boot/grub/menu.lst
```

---

### Post by faisal892 on 2008-05-02
Thanks alot for you message.

I am a newbie and don't know where I have to issue write the commands that you mentioned. 

Please help.

Regards

Faisal

---

### Post by faisal892 on 2008-05-02
> **PmDematagoda said:**
> Can you post the outputs of:-

```
cat /etc/mtab
```

faisal@faisal-laptop:~$ cat /etc/mtab
/dev/sda13 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-16-generic/volatile tmpfs rw 0 0
/dev/sda1 /media/sda1 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda10 /media/sda10 ext3 rw 0 0
/dev/sda12 /media/sda12 ext3 rw 0 0
/dev/sda5 /media/sda5 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda6 /media/sda6 fuseblk rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096 0 0
/dev/sda8 /media/sda8 ext3 rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
faisal@faisal-laptop:~$




and
```
cat /boot/grub/menu.lst
```

cat: /boot/grub/menu.lst[/CODE][/QUOTE]: No such file or directory

---

### Post by PmDematagoda on 2008-05-02
> **faisal892 said:**
> Thanks alot for you message.

I am a newbie and don't know where I have to issue write the commands that you mentioned. 

Please help.

Regards

Faisal

Sorry, you were supposed to enter it in a terminal, but I see you have done that already:).

About the error, post the output of:-
```
ls /boot/grub
```

---

### Post by rodh on 2008-05-02
> **faisal892 said:**
> cat: /boot/grub/menu.lst[/CODE]: No such file or directory[/QUOTE]

You have to open a terminal,  K ; Applications; Utilitys; Terminal.  Then some of the commands you might have to sudo  -(cmd)

Hope this helps,  Sorry I am using Kubuntu and the K is like start button. and you might try this link for a great tutorial on grub

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by Xiong Chiamiov on 2008-05-02
A very nifty tool to have when dealing with boot issues is [Super GRUB disk]("http://supergrubdisk.org").

---

### Post by faisal892 on 2008-05-02
> **PmDematagoda said:**
> Sorry, you were supposed to enter it in a terminal, but I see you have done that already:).

About the error, post the output of:-
```
ls /boot/grub
```

Here it is

faisal@faisal-laptop:~$ ls /boot/grub
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
faisal@faisal-laptop:~$

---

### Post by muteXe on 2008-05-02
> **Xiong Chiamiov said:**
> A very nifty tool to have when dealing with boot issues is [Super GRUB disk]("http://supergrubdisk.org").

I agree.  It is very very useful.

---

### Post by PmDematagoda on 2008-05-02
> **faisal892 said:**
> Here it is

faisal@faisal-laptop:~$ ls /boot/grub
default        installed-version  minix_stage1_5     xfs_stage1_5
device.map     jfs_stage1_5       reiserfs_stage1_5
e2fs_stage1_5  menu.lst           stage1
fat_stage1_5   menu.lst~          stage2
faisal@faisal-laptop:~$

The menu.lst file is present, are you sure that you typed the command properly? Please try again and post the output.

---

### Post by faisal892 on 2008-05-02
Hi all,

I am thankful to all of you for the support and guidance that you people are extendig to newbies like me.

Now there is another problem, I used Grub super disk and restored the grub but when i select Ubuntu from the start menu it says "Error 15, no file found". for Mandriva and Open SUSE it says "Error 17"

By the way using Super Grub CD I login to Windows Xp. Please if you could guide me what to do to get access to Ubuntu. I have 8.04 installed but I have live CD of 7.10 I have also tried


Regards

Faisal.

---

### Post by PmDematagoda on 2008-05-02
Boot the Live CD, then post the output of:-
```
sudo fdisk -l
```

Also what menu.lst file did you instruct the Super GRUB disk to recover? From what drive/partition?

---

