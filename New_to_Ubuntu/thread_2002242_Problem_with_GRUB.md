---
title: "Problem with GRUB"
date: 2012-06-12
forum: New to Ubuntu
---

### Post by nitrox26 on 2012-06-12
Good morning to everyone,

I have recently installed CentOS and Windows 7 as a dual boot system on my computer. However, during the installation of CentOS, I unfortunately selected the USB stick (which contained the Linux files) to install the GRUB on. Now the problem is that whenever I start my computer, it requires that USB stick to boot from. Without the stick it gives me a "error: unknown file system" and a "grub rescue" prompt. 
I put Ubuntu on another USB stick and tried to start from that stick to make a fresh install with only Ubuntu this time. However, my computer of course still boots from the Grub-stick and ignores the Ubuntu-stick. Without the Grub-stick, I get the same error message as above. 

Is there any method to fix this problem? I am fairly new to Linux etc, so all my research on that topic didn't quite lead to anything... 
I appreciate any help and I apologize in advance if this thread already exists or if it's in the wrong category etc. 
Also, if you need more information like device specifications or something similar, just ask me. I am sorry if I ask more of those stupid questions, but that problem there really annoys me for some time now :P

Thank you very much in advance! :)

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> Good morning to everyone,

I have recently installed CentOS and Windows 7 as a dual boot system on my computer. However, during the installation of CentOS, I unfortunately selected the USB stick (which contained the Linux files) to install the GRUB on. Now the problem is that whenever I start my computer, it requires that USB stick to boot from. Without the stick it gives me a "error: unknown file system" and a "grub rescue" prompt. 
I put Ubuntu on another USB stick and tried to start from that stick to make a fresh install with only Ubuntu this time. However, my computer of course still boots from the Grub-stick and ignores the Ubuntu-stick. Without the Grub-stick, I get the same error message as above. 

Is there any method to fix this problem? I am fairly new to Linux etc, so all my research on that topic didn't quite lead to anything... 
I appreciate any help and I apologize in advance if this thread already exists or if it's in the wrong category etc. 
Also, if you need more information like device specifications or something similar, just ask me. I am sorry if I ask more of those stupid questions, but that problem there really annoys me for some time now :P

Thank you very much in advance! :)

Try booting from the GRUB USB Stick and then reinstall GRUB but this time on your fisrt harddrive using grub-intstall

e.g : grub-install /dev/sda1

I think this would work as it would install the grub on first harddrive.

---

### Post by nitrox26 on 2012-06-12
Thank you very much for your answer

I booted into CentOS from the GRUB stick and tried the "grub-install" in the terminal, but somehow I get this:

[INDENT][nitrox@localhost ~]$ grub-install /dev/sda1
rm: cannot remove `/boot/grub/stage1': Permission denied
[/INDENT]
And with sudo I get:

[INDENT][nitrox@localhost ~]$ sudo grub-install /dev/sda1
[sudo] password for nitrox: 
nitrox is not in the sudoers file.  This incident will be reported.

[/INDENT]On another website ([http://wiki.centos.org/HowTos/GrubInstallation#head-6a2e40aff22b2f6dc2c8fc7b74007a53c9e53076](http://wiki.centos.org/HowTos/GrubInstallation#head-6a2e40aff22b2f6dc2c8fc7b74007a53c9e53076)) I found a tutorial on how to install grub in centOS, but the "find" command wont find my usb stick (the location where the grub is); looks like this then:

[INDENT][nitrox@localhost ~]$ grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
[/INDENT]What am I doing wrong there then? :/

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> Thank you very much for your answer

I booted into CentOS from the GRUB stick and tried the "grub-install" in the terminal, but somehow I get this:

[INDENT][nitrox@localhost ~]$ grub-install /dev/sda1
rm: cannot remove `/boot/grub/stage1': Permission denied
[/INDENT]
And with sudo I get:

[INDENT][nitrox@localhost ~]$ sudo grub-install /dev/sda1
[sudo] password for nitrox: 
nitrox is not in the sudoers file.  This incident will be reported.

[/INDENT]On another website ([http://wiki.centos.org/HowTos/GrubInstallation#head-6a2e40aff22b2f6dc2c8fc7b74007a53c9e53076](http://wiki.centos.org/HowTos/GrubInstallation#head-6a2e40aff22b2f6dc2c8fc7b74007a53c9e53076)) I found a tutorial on how to install grub in centOS, but the "find" command wont find my usb stick (the location where the grub is); looks like this then:

[INDENT][nitrox@localhost ~]$ grub
Probing devices to guess BIOS drives. This may take a long time.


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename.]
grub> find /boot/grub/stage1
find /boot/grub/stage1

Error 15: File not found
[/INDENT]What am I doing wrong there then? :/

Let me answer both one by one:

Sudo is not working for you because your user nitrox is not in the /etc/sudoers file. For adding your user to /etc/sudoers you have to switch to root account and then add the user. So either add the user to /etc/sudoers file or simply su in to root and then install grub.

For the second option you have to actually go into grub console and run the commands manually, however since grub is not actually loaded into MBR in your case i think that won't work as you said that grub is installed in uSB stick. 

One for thing for some reason i assume that you have made a live USB for centos.

---

### Post by nitrox26 on 2012-06-12
Okay, so when I now try to install grub it gives me another message like this:

[INDENT][nitrox@localhost ~]$ su
Password: 
[root@localhost nitrox]# grub-install /dev/sda1
/dev/sdc3 does not have any corresponding BIOS drive.
[root@localhost nitrox]# 
[/INDENT]Why does it refer to sdc3 there? I thought sda1 is my hard drive and sdb1 the usb stick..?
Also, using one of the methods on some other websites, I tried the "find /boot/grub/stage1" in the grub console at startup and it gave me (hd1,2) as a result. Is that the second partition on my usb stick?
Sorry for the dumb questions...

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> Okay, so when I now try to install grub it gives me another message like this:

[INDENT][nitrox@localhost ~]$ su
Password: 
[root@localhost nitrox]# grub-install /dev/sda1
/dev/sdc3 does not have any corresponding BIOS drive.
[root@localhost nitrox]# 
[/INDENT]Why does it refer to sdc3 there? I thought sda1 is my hard drive and sdb1 the usb stick..?
Also, using one of the methods on some other websites, I tried the "find /boot/grub/stage1" in the grub console at startup and it gave me (hd1,2) as a result. Is that the second partition on my usb stick?
Sorry for the dumb questions...

Yes, (hd1,2) is your usb stick and it is /dev/sdb2. What does df -h shows you, does it show /dev/sda. Could you please post the output of df -hT here. Also the output of find /boot/grub/stage1 when you are in terminal console.

No question is a silly/dumb question. I am also in learning phase  only. So thats totally okay i may also learn alot from this.

Thanks,

---

### Post by nitrox26 on 2012-06-12
The output of df -h is this:

[INDENT][root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc3             9.8G  5.0G  4.8G  52% /
tmpfs                 1.5G  284K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[/INDENT]MULTIBOOT is what I called the usb stick with the grub on and sdc3 would then probably be the linux partition. My harddrive has 2 partitions (4 with swap and mbr), the first is for the Windows boot loader (which disappeared I guess), the second for Windows itself, the third for Linux and the fourth for the swap space.
Output of find ...:

[INDENT][root@localhost nitrox]# find /boot/grub/stage1
[/INDENT][INDENT]/boot/grub/stage1
[/INDENT]However, in the grub console it shows something else (hd1,2)

Also, grub-install /dev/sdc3 gives the same error message as before:

[INDENT]root@localhost nitrox]# grub-install /dev/sdc3
/dev/sdc3 does not have any corresponding BIOS drive.
[/INDENT]

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> The output of df -h is this:

[INDENT][root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdc3             9.8G  5.0G  4.8G  52% /
tmpfs                 1.5G  284K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[/INDENT]MULTIBOOT is what I called the usb stick with the grub on and sdc3 would then probably be the linux partition. My harddrive has 2 partitions (4 with swap and mbr), the first is for the Windows boot loader (which disappeared I guess), the second for Windows itself, the third for Linux and the fourth for the swap space.
Output of find ...:

[INDENT][root@localhost nitrox]# find /boot/grub/stage1
[/INDENT][INDENT]/boot/grub/stage1
[/INDENT]However, in the grub console it shows something else (hd1,2)

Also, grub-install /dev/sdc3 gives the same error message as before:

[INDENT]root@localhost nitrox]# grub-install /dev/sdc3
/dev/sdc3 does not have any corresponding BIOS drive.
[/INDENT]


Try this command 

grub-install --recheck /dev/sdc

This should probably fix the error for you i assume.

---

### Post by nitrox26 on 2012-06-12
Alright, I get this after running the command:

[INDENT][root@localhost nitrox]# grub-install --recheck /dev/sdc3
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdc
[/INDENT]So...is that correct now?
I will try booting without usb stick now, Ill post if it works or not. brb

---

### Post by nitrox26 on 2012-06-12
Hm, it still gives me the "grub rescue>" prompt when starting without the usb stick...
Do you have another idea how to fix that?

---

### Post by BeenLikeFlynn on 2012-06-12
no

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> Hm, it still gives me the "grub rescue>" prompt when starting without the usb stick...
Do you have another idea how to fix that?

did u run grub-install /dev/sdc after grub-install --recheck /dev/sdc ?

---

### Post by nitrox26 on 2012-06-12
Nope, I havent done that; I did it now though ;)

For some reason, my linux partition was renamed to sdb3; I tried the commands you posted and it seems to work. I will try to boot after posting this.
Output:

[INDENT][root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             9.8G  5.0G  4.7G  52% /
tmpfs                 1.5G  124K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[root@localhost nitrox]# grub-install --recheck /dev/sdb3
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[root@localhost nitrox]# grub-install /dev/sdb3
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT]

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> Nope, I havent done that; I did it now though ;)

For some reason, my linux partition was renamed to sdb3; I tried the commands you posted and it seems to work. I will try to boot after posting this.
Output:

[INDENT][root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             9.8G  5.0G  4.7G  52% /
tmpfs                 1.5G  124K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[root@localhost nitrox]# grub-install --recheck /dev/sdb3
Probing devices to guess BIOS drives. This may take a long time.
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[root@localhost nitrox]# grub-install /dev/sdb3
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT]

You need to run grub-install /dev/sdb not /dev/sdb3 or what ever is the linux partition is.

---

### Post by nitrox26 on 2012-06-12
:/ It still doesnt work...same error as before.
what I did was this:

[INDENT][nitrox@localhost ~]$ su
Password: 
[root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             9.8G  5.0G  4.7G  52% /
tmpfs                 1.5G  284K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[root@localhost nitrox]# grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT]So Im running this console as root user, then I print what filesystems are there, sdb being the linux partition and sda being the usb stick with the grub right now. Then I try to install the grub on the linux partition and it still doesnt work.
Shouldnt I install the grub into the MBR? What dev would that be? /dev/sda0 ?

---

### Post by rohit4739 on 2012-06-12
> **nitrox26 said:**
> :/ It still doesnt work...same error as before.
what I did was this:

[INDENT][nitrox@localhost ~]$ su
Password: 
[root@localhost nitrox]# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb3             9.8G  5.0G  4.7G  52% /
tmpfs                 1.5G  284K  1.5G   1% /dev/shm
/dev/sda1             7.5G  2.9G  4.6G  39% /media/MULTIBOOT
[root@localhost nitrox]# grub-install /dev/sdb
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
[/INDENT]So Im running this console as root user, then I print what filesystems are there, sdb being the linux partition and sda being the usb stick with the grub right now. Then I try to install the grub on the linux partition and it still doesnt work.
Shouldnt I install the grub into the MBR? What dev would that be? /dev/sda0 ?

Well there is nothing as /dev/sda0, it starts from 1 only. Here is one last thing that you can try. Boot from USB, at grub menu press 'e' to edit and then follow the on screen instructions to go into grub console, at grub console run the following commads,

grub>root
   This would output your current root something like (hd0,1)
Now use find to find the partition where /boot/grub/stage1 is

grub> find /boot/grub/stage1
 again this would output something like (hd0,2), exact location could be different also.

Now set this aprtition as your root with the followng command
grub> root (hd0,2)
grub> setup (hd0)
>quit
 and reboot

Let us know if it works

---

### Post by ashwinrao on 2012-06-12
Not intended to hijack this tread. Haven't you tried [Boot repair]("https://help.ubuntu.com/community/Boot-Repair") yet?

---

### Post by nitrox26 on 2012-06-13
I have thought of another way that brought me a little closer to my goal, however now there is another problem that actually has nothing to do with the old one, so this post might be in the wrong place.
Anyway, I found a Windows XP CD which I used to boot (still with the grub stick) and to install windows xp. This worked okay except for a number of files that could not be copied, but the installation still worked. I booted into Windows once, shut the computer down and booted with the Ubuntu stick into a live session from where I installed Ubuntu on the whole hard drive. The first problem that occurred here is that halfway through the installation, I got an error message saying that an apt configuration is broken or so, but I found a workaround for that:
[INDENT]sudo rm /usr/lib/ubiquity/apt-setup/generators/40cdrom
[/INDENT]After this, the installed worked and I proceeded with a reboot, however, this time the Ubuntu splash screen would really only splash and then turn black, followed by not quite a prompt but just a list of checks that were all OK except something like Stopping automatic crash report generation: fail
The screen would then just stay there and do nothing. With a new reboot I can still boot into a live session, thats where I am right now btw.
Now, I found this problem online again with a little workaround which...didnt work. Ctrl+Alt+F2 opens a command line log in, from there i should run "sudo gdm" which doesnt work for some reason, so the whole boot repair thing doesnt work. Well.

Ive tried a new install and this time I got the same apt error, fixed it and now the installation doesnt even go up to that error. Something might be wrong with the usb stick or the Ubuntu version or so, so Im downloading Ubuntu 12.04 right now and put it on another usb stick. lets see what that will do.

Also, I have just now read about Boot-repair and I will try that too now. 

Thank you very much for your help, I really appreciate this. It's good there are nice people in this world too, not just youtube commenters ;)

---

### Post by wilee-nilee on 2012-06-13
Use the boot-repair tool to run the bootinfo summary and post the HTTP address.

I would just do that to start with.

---

### Post by nitrox26 on 2012-06-13
[http://paste.ubuntu.com/1039461/](http://paste.ubuntu.com/1039461/)

---

### Post by wilee-nilee on 2012-06-13
So you are missing the grub files from the sda1 partition, it has been awhile since I used centos, so I'm not sure I would go to the IRC ##centos channel to get the direct info, It is on freenode you can use xchat to get there.

---

### Post by bodhi.zazen on 2012-06-13
Easiest fix is to boot Centos and:

```
su -
grub

#Install grub from the grub prompt
#grub prompt looks like 'grub>'

setup (hd0)
```

See also : [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by wilee-nilee on 2012-06-13
I got this link from the #centos channel, I would get familiar with them and their forums as well.
[http://wiki.centos.org/TipsAndTricks/ReinstallGRUB](http://wiki.centos.org/TipsAndTricks/ReinstallGRUB)

You will get the unregistered channel if you do not register, I would register.

---

### Post by bodhi.zazen on 2012-06-13
Looking up, I do not think the problem is with re-isntalling grub.

The problem is that /boot and /boot/grub are on the flash drive, and thus not available unless the flash drive is present.

Either make a /boot partition on the first hard drive, or re-install the windows boot loader and select which device to boot from in you BIOS.

---

### Post by nitrox26 on 2012-06-14
I have now made a fresh Ubuntu 11.10 installation. After a restart I encountered the same problem again, Ubuntu booted up and then only gave me a list of system checks that were all okay except that "Stopping automatic crash report - fail"
I have then logged in and deleted apport, which unfortunately didnt do anything. Also, I fixed the boot with boot-repair but all that did was create a boot menu that lets me select between Ubuntu, recovery mode, memory test and so on. However, the system still doesnt boot up. 
Is there any other way to get a functional system? I have a Windows 7 and a WinXP cd at home, I am about to create another usb live stick with Ubuntu 12.04 and maybe another one with Linux Mint or similar. Could it also be that there is something wrong with my hard drive? Also, would it help to completely wipe the hard drive (take it out, connect it to another computer via an adapter and then format it) or would this only harm the hard drive (I could imagine there is no boot sector left then)?
I am sorry that this topic kind of changed now, but I am kind of stressed out now because the school year is almost over and I still need to write a few docs and make 3 presentations....so well. 
Anyway, I really appreciate all your help! :)

---

### Post by bodhi.zazen on 2012-06-14
> **nitrox26 said:**
> I have now made a fresh Ubuntu 11.10 installation. After a restart I encountered the same problem again, Ubuntu booted up and then only gave me a list of system checks that were all okay except that "Stopping automatic crash report - fail"
I have then logged in and deleted apport, which unfortunately didnt do anything. 

This does not sound like a grub or boot problem. You are stating that the system boots and that you log in.

Is this a problem with your graphics card ? Does your system boot to a command line ?

---

### Post by nitrox26 on 2012-06-14
Now it does boot to command line. After the actual boot the screen turns black and gives me a list of system checks afterwards, like: "Checking Battery...OK". Whenever it gets to that Automatic crash report, it shows "fail" and stops there, leaving me at that screen unable to type or do anything other than shut down the computer. I can however log in with a command line by switching to Ctrl+Alt+F2. 
I dont know what should be wrong with my graphics card, it was still working perfectly with Linux Mint 12 and ubuntu 11.10 (that was like a month ago).

---

### Post by bodhi.zazen on 2012-06-14
> **nitrox26 said:**
> Now it does boot to command line. After the actual boot the screen turns black and gives me a list of system checks afterwards, like: "Checking Battery...OK". Whenever it gets to that Automatic crash report, it shows "fail" and stops there, leaving me at that screen unable to type or do anything other than shut down the computer. I can however log in with a command line by switching to Ctrl+Alt+F2. 
I dont know what should be wrong with my graphics card, it was still working perfectly with Linux Mint 12 and ubuntu 11.10 (that was like a month ago).

Well, the system boots as you can "log in with a command line by switching to Ctrl+Alt+F2". 

So it is not a grub problem.

Your graphical system is failing, what video card is it ?

---

### Post by nitrox26 on 2012-06-15
It's a Nvidia GeForce Go 7300, so there are drivers available. sudo apt-get install nvidia-current would be the command to install them right?

---

### Post by nitrox26 on 2012-06-16
Alright, I did another install with Ubuntu 12.04 LTS and it worked this time :)
Thank you very much for your help again guys! :)

---

