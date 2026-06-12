---
title: "silly question?"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by mrbrettmurphy on 2012-05-19
Hi Guys,
I'm new to  Linux/Ubuntu and have a problem.
I'm running widows vista on my laptop but I'm also now running Linux/Ubuntu from my D drive. How do i take the partition down so that i can access my other stuff from my C drive? I have a shortcut on my D drive to go to my C drive but it wont work.
Any suggestions would be much appreciated.
Cheers,
Brett

---

### Post by grahammechanical on 2012-05-19
Open file manager and in the left panel under Devices tell us what you see. In Ubuntu this is. Not in Windows.

We need to find out if there is confusion caused by the differences in the terms being used in Windows and Linux.

What do you mean by "take the partition down?"

What is this short cut on your desktop supposed to do?

Regards.

---

### Post by roelforg on 2012-05-19
I've got a similar setup.

My C drive is labeled ACER
In the file manager in ubuntu, it shows under "Devices" as [hd icon] ACER
Click on that and it opens.

---

### Post by mrbrettmurphy on 2012-05-19
Hi Grahammechanic and Roelforg,

Under Devices is a Data folder and inside this folder are 3 further folders, Downloads : Recycle Bin and System Volume Info. There is also a System(C) Shortcut.lnk which doesn't open.
What I'm trying to do is access my files that are in my C drive i.e. music, videos etc and all these run on Vista.
I thought there was maybe a partition between the C and D drives and this was what was preventing me getting to my stuff on the C drive while operating Linux/Ubuntu on my D drive.
Cheers guys.

---

### Post by coffeecat on 2012-05-19
Did you install Ubuntu using wubi? If you are not sure, then open a terminal and post the output of these three commands:

```
mount
sudo fdisk -lu
sudo blkid
```

That at least will help us get an overview of your partition layout. Ubuntu (Linux) does not use the C:, D: "drive" naming convention, which is a purely Windows one. If you did install via wubi, your Ubuntu pseudo-partition will be in a file in either your Windows C: or D: partition and the above commands will tell us which, and we will then be able to tell you how to access all your Windows partitions. After the second command you will be prompted for your password, which you will not see echoed to the screen as you type it in. Don't worry - keep typing. It is going in.

Also - if you highlight the terminal output with the mouse, you can right-click -> copy in order to be able to paste it into your post.

---

### Post by bodhi.zazen on 2012-05-19
I assume from your post you are using wubi.

In that case , see 

[https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_access_the_Windows_drives.3F)

If not, Linux does not identify drives with letters, so we need more information.

[http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018)

---

