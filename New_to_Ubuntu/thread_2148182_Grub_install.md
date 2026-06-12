---
title: "Grub_install"
date: 2013-05-24
forum: New to Ubuntu
---

### Post by adityaharish on 2013-05-24
I installed Ubuntu 12.04 over another version of Ubuntu 12.04 in another partition.

When I installed new Ubuntu 12.04 it showed the error message 

**      cannot run grub-install/dev/sda6: Choose another device to install Boot-loader **

I tried installing the boot-loader on all the available disks.

One solution is to install boot-repair .The  internet which I'm using has some restrictions . It is not able to add repository i.e the following commands cannot run successfully.          

                         *sudo add-apt-repository ppa:yannubuntu/boot-repair*

Moreover it is my mentor's PC . So I shouldn't mess up with his data .. 

Please help me this ..

---

### Post by lethall1 on 2013-05-24
Excuse me, English is not my native language and maybe that's why i do not understand the whole problem )
You had installed new ubuntu on the same partition, where another one was?
and what is the problem? 

[B]sudo fdisk -l

[/B]
output please.
and describe the problem please.

---

### Post by adityaharish on 2013-05-24
On  another partition Sir ..

When I run the command 
[I]sudo fdisk -l
[/I]
The Output is :

  Device Boot      Start         End      Blocks   Id  System /dev/sda1   *        2048   577941500   288969726+  83  Linux /dev/sda2       577941502   976771071   199414785    5  Extended /dev/sda5       968568832   976771071     4101120   82  Linux swap / Solaris /dev/sda6       577941504   968568831   195313664   83  Linux

---

### Post by lethall1 on 2013-05-24
You have 2 partition: first partition is linux (let me guess -  that is old ubuntu), then is extended partition whith swap and /dev/sda6 is your fresh installed linux.
You have to run
[B]sudo grub-install /dev/sda
sudo update-grub2[/B]
it should find the old ubuntu kernel from another partition, and you will be able to boot new ubuntu, and old ubuntu distro

---

### Post by adityaharish on 2013-05-24
I tried running the commands using Live CD - "Try Ubuntu"

When I run the command  [B]sudo grub-install /dev/sda

[/B]The Output is[B] : /usr/sbin/grub-probe : errror : cannot find a device for /boot/grub (is /dev mounted?).
[/B]

---

### Post by ajgreeny on 2013-05-24
So are you saying you can not boot to either of the installed OSs, only to a live system?  If you can boot to either there is no real problem, as you can run **sudo update-grub** which should add both OSs to the grub menu and allow booting to either.

You should have let the installer put the new grub on to the MBR of /dev/sda, not to the sda6 partition on which you installed.  If you had later wanted to return control of grub to the first installation it could have been done with a single **sudo grub-install /dev/sda** command from that first install, booted from the grub menu of the second install.

---

### Post by adityaharish on 2013-05-24
Yes .. I can boot only to a live system.. 

I tried installing Boot-repair but my network shows some certificate error.

So boot-repair isn't an option for me . I can't install it through command line .. 

So what should I do now ??

---

### Post by grahammechanical on 2013-05-24
Do you get a Grub boot menu? Press shift repeatedly after switching on the machine. At the Grub menu select Ubuntu and tell us what happens. That will give us clues as to what is going wrong.

At the Grub boot menu look for Ubuntu on sda 1 and boot that. And then run

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

Where is your mentor? Why is he not helping you?

Regards.

---

### Post by lethall1 on 2013-05-24
Yea, no one is able to install grub this way from live CD, because this is virtual file system, you need to mount bind:
 in livecd terminal type  &#8203;sudo -I
Mount /dev/sda1 /mnt
Mount --bind /dev /mnt/dev
Mount --bind /proc /mnt/proc
Chroot /mnt
Grub-install /dev/sda
Reboot
&#8203;when you boot in to os, make update-grub2

---

### Post by ajgreeny on 2013-05-24
Go to the **Grub 2 basics** in my signature and look for section 13 where you can see how to re-install grub from a live CD.  That may help.

---

### Post by adityaharish on 2013-05-27
[FONT=arial][SIZE=2]graham mechanical , My mentor isn't familiar with ubuntu .
when I told him about this problem , he told me to google it &  find the solution myself.
[SIZE=2]T[/SIZE]hanks ajgreeny & lethall1 .I fol[SIZE=2]lo[SIZE=2]wed your metho[SIZE=2]ds.
[/SIZE][/SIZE][/SIZE]
But the commands I ran are :

[FONT=arial black]sudo su
Mount /dev/sda1 /mnt
Mount --bind /dev /mnt/dev
Mount --bind /proc /mnt/proc
Chroot /mnt
sudo update-grub[/FONT][/SIZE][FONT=arial black]
Grub-install /dev/sda
sudo update-grub2[/FONT]

Now I can login to the new Version of ubuntu I installed but I cannot see the old version of ubuntu now.[SIZE=2]
[/SIZE]
Any how one problem has been solved.
Thank You all for helping me in solving the problem.
[/FONT]

---

