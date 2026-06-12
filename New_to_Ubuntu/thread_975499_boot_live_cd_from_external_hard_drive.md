---
title: "boot live cd from external hard drive"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by rhaven on 2008-11-08
Hi, I've been searching for quite a while for a way to boot a live cd from an external hard drive. I only come across methods such as using unetbootin. However, I don't want to boot from a usb flash drive, and this method doesn't work for my hard drive. 


This is what I currently have:
a 20gb external hard drive formatted fat32, when I select it as the first device to boot, after running unetbootin, I get: 

Grub loading stage 1.5
Grub loading , please wait
Error 22

Any help is much appreciated!

---

### Post by rhaven on 2008-11-09
bump

---

### Post by caljohnsmith on 2008-11-09
So you installed the Live CD to your external drive using UNetBootin, and then when you boot that drive you get that Grub error? Do you have the Live CD burned to disk and can boot from it? If so, how about booting it up, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -lu
sudo grub
grub> find /boot/grub/stage1
grub> quit
```
And for whichever is your external drive, say sdb, do:
```
sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
sudo dd if=/dev/[COLOR="Red"]sdb[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And post the output of those commands. We can work from there. :)

---

### Post by rhaven on 2008-11-09
Hi,
Thanks for the reply. That's exactly the problem. When I boot from the drive I get that Grub error.

I couldn't run the grub command, "command not found". I have grub 2. Not sure what command I would have to run in that case. I also searched with synaptic to try and find some userspace package but not sure which they are. 

I ran the two dd commands, and here is the output:

```
sudo dd if=/dev/sdc count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
GRUB 
sudo dd if=/dev/sdc bs=1 skip=1049 count=2 2>/dev/null | hexdump
0000000 ff01                                   
0000002 

```

---

### Post by rhaven on 2008-11-10
Hi, I'm still not sure what the problem is. Do I need to format the drive in a special way? 

I've continued to search for solutions to boot the live cd  from the hd. I've come across mentions of people booting from the ISO files. Does anyone know how to do this? 
I've come across:
poor mans install
grub4dos, which may or may not boot iso files

-boot iso from hdd
[HTML]http://ubuntuforums.org/showthread.php?t=273114[/HTML]

- emulate cdrom or soemthing (not sure)
[HTML]http://www.linuxquestions.org/questions/linux-desktop-74/installing-without-cd-592527/[/HTML] 

-boot raw iso
[HTML]http://www.linuxquestions.org/questions/linux-software-2/booting-of-raw-iso-from-grublilo-though-preferably-grub-367901/[/HTML]

being able to boot raw iso's would be fantastic

--Edit
Latest find
[http://bayanijuan.blogspot.com/2007/07/howto-boot-ubuntu-fiesty-fawn-livecd.html](http://bayanijuan.blogspot.com/2007/07/howto-boot-ubuntu-fiesty-fawn-livecd.html)

I've just found this link. If it works that would be great. Can anyone confirm this? Can I extract multiple isos to different folders and boot them from a unified bootloader? I dont think there is a menu.lst created when you use unetbootin, but Im assuming there is an equivalent?

---

### Post by rhaven on 2008-11-11
I was able to finally boot from my hdd after a bit.

First I copied the boot sector from a flash drive that was booting and was setup with unetbootin. This removed "error 22" however left me with "Operating System Not found"

After that I ran unetbootin again, this time from linux instead of windows. Now its booting.

---

