---
title: "What is wrong with my steps to configure kdump/kexec?"
date: 2010-05-27
forum: Programming Talk
---

### Post by wolaile on 2010-05-27
Hi! I used linux-2.6.31.13 on Ubuntu 9.10 on my VMware to configure kdump &kexec, but I failed. And I don't know why. 
 
I uncompressed linux-2.6.31.13.tar.bz2 twice, and got 2 source code. I named it as linux-2.6.31.13-system and linux-2.6.31.13-capture , i.e., the "system kernel" and "capture kernel".

And then my steps were:

---

### Post by wolaile on 2010-05-27
1.I first compiled the "system kernel" with the following options:
CONFIG_KEXEC=y
CONFIG_SYSFS=y
CONFIG_DEBUG_INFO=Y
local version: -system
 
2.I executed these commands:
make install
make modules_install
And then I produced file:
initrd.img-2.6.31.13-system .
 
3.I edited grub to add the parameter: crashkernel=128M@16M
 
4.I executed the command: update-grub2
Then I reboot my computer with my "system kernel", everything is right!

---

### Post by wolaile on 2010-05-27
5.I compiled the "capture kernel" with the following options:
local version: -capture
CONFIG_KEXEC=y
CONFIG_SYSFS=y
CONFIG_DEBUG_INFO=Y
ONFIG_CRASH_DUMP=y
CONFIG_PROC_VMCORE=y
CONFIG_HIGHMEM64G=y
CONFIG_SMP=n
CONFIG_RELOCATABLE=y
CONFIG_PHYSICAL_START=0x1000000
 
6.I executed the command: make modules_install
And then I produced file: initrd.img-2.6.31.13-capture
 
7.I executed the command: apt-get install kexec-tools
 
8.I copied ./linux-2.6.31.13-capture/vmlinux to /home/administrator/
And I copied initrd.img-2.6.31.13-capture to /home/administrator/
 
9.I executed the command:
kexec -p /home/administrator/vmlinux --initrd=/home/administrator/initrd.img-2.6.31.13-capture --args-linux --append="root=/dev/hda1 1 irqpoll maxcpus=1 reset_devices "
And this command was finished with no messages.

---

### Post by wolaile on 2010-05-27
Finally I triggerred a "panic(...)" sentence added by me in the kernel file tun.c , shortly I saw that the kernel was dead and the mouse and keyboard were all dead.

But the screen remained unchanged from then on, and I couldn't see the "capture kernel" to replace "system kernel" to work. I mean, the screen was always the same as the system just crashed.

Could anyone help me? Thanks a lot!

---

### Post by lisati on 2010-05-27
Please do not start duplicate threads.

---

### Post by bluedream_zqs on 2010-07-14
hi, guy.

I have the same problems with you, except that test it in VirtualBox rather than VMWare.

Is it that kdump cannot work for Virtual Image? or cannot work for Ubuntu ?

My OS is: ubuntu 8.04.

---

### Post by bluedream_zqs on 2010-07-14
Ahh, it is because that you trigger the oops under X. Try to stop the gdm,
and switch to console mode, then, trigger the oops, it works fine.

---

