---
title: "about dual systems - Windows &amp; Ubuntu"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-08-14
Hello there, I had ubuntu installed on my computer. Today I tried to install Windows on it, but I can't get the selection menu when start-up the computer. 

I guess when I installed windows, it made Ubuntu system inactive.

Could anyone let me know how to get the selection menu at the begining? I mean I can choose if I go into Ubuntu or Windows?

Thanks,

---

### Post by tangibleorange on 2008-08-14
> **Unewbeginner said:**
> Hello there, I had ubuntu installed on my computer. Today I tried to install Windows on it, but I can't get the selection menu when start-up the computer. 

I guess when I installed windows, it made Ubuntu system inactive.

Could anyone let me know how to get the selection menu at the begining? I mean I can choose if I go into Ubuntu or Windows?

Thanks,

you need to re-install GRUB to your MBR. Follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
GRUB should detect your windows install and create a menu entry for it.

---

### Post by ercferret18 on 2008-08-14
windows overwrote your MBR, you need to reinstall GRUB to it.

---

### Post by Unewbeginner on 2008-08-14
Thanks, I will try it now to make it work.

---

### Post by mandrill on 2008-08-14
> **Unewbeginner said:**
> Hello there, I had ubuntu installed on my computer. Today I tried to install Windows on it, but I can't get the selection menu when start-up the computer. 

I guess when I installed windows, it made Ubuntu system inactive.

Could anyone let me know how to get the selection menu at the begining? I mean I can choose if I go into Ubuntu or Windows?

Thanks,

It is always easier to install Linux after Windows, because Grub does its thing, and you don't have to do much of anything, except make sure you installed it in the Windows MBR.

---

### Post by Unewbeginner on 2008-08-14
I tried it but I don't know how to get the terminal(sorry I'm pretty new).

I only got a list as below:

Install in text mode
Text mode install for manufacturers
......
......
......
Memory test
Boot from first hard disk


How could I get the terminal and input my command?

THanks



> **tangibleorange said:**
> you need to re-install GRUB to your MBR. Follow the instructions here:
[http://ubuntuforums.org/showthread.php?t=224351]("http://ubuntuforums.org/showthread.php?t=224351")
GRUB should detect your windows install and create a menu entry for it.

---

### Post by mandrill on 2008-08-14
> **Unewbeginner said:**
> I tried it but I don't know how to get the terminal(sorry I'm pretty new).

I only got a list as below:

Install in text mode
Text mode install for manufacturers
......
......
......
Memory test
Boot from first hard disk


How could I get the terminal and input my command?

THanks

OK, lets start at the beginning. Presumptives: You are using Ubuntu, Gnome desktop, and have successfully installed it or are you trying to figure out how to install it. Gimme a holler back on that.

---

### Post by Unewbeginner on 2008-08-14
> **mandrill said:**
> OK, lets start at the beginning. Presumptives: You are using Ubuntu, Gnome desktop, and have successfully installed it or are you trying to figure out how to install it. Gimme a holler back on that.

Yes, I've installed ubuntu successfully. I installed it a couple of days ago. Now I'm trying to install Windows as my second system. I'm more familiar with Windows. I insert the Ubuntu CD and restart my computer, but I didn't get the Ubuntu Desktop.

Thanks,

---

### Post by tangibleorange on 2008-08-14
> **Unewbeginner said:**
> Yes, I've installed ubuntu successfully. I installed it a couple of days ago. Now I'm trying to install Windows as my second system. I'm more familiar with Windows. I insert the Ubuntu CD and restart my computer, but I didn't get the Ubuntu Desktop.

Thanks,

I think you're using the Alternate CD install. You need the Desktop Live CD for these instructions. Download it here:
[http://releases.ubuntu.com/8.04/]("http://releases.ubuntu.com/8.04/")

---

### Post by Unewbeginner on 2008-08-14
> **tangibleorange said:**
> I think you're using the Alternate CD install. You need the Desktop Live CD for these instructions. Download it here:
[http://releases.ubuntu.com/8.04/]("http://releases.ubuntu.com/8.04/")

No way to do that with Alternate CD?

Thanks

---

### Post by Riffer on 2008-08-14
You need to rewrite your MBR (Master Boot Record) this is where the computer looks for basic OS start up "stuff".  There are a few programs out there that will do this for you, one being "SuperGrub".  There are some HOWTO's on this forum describing how you would use this program.

If you haven't done much in terms of setup for your Ubuntu, I would just install it again.  The installation procedure will make sure "grub" is loaded.  You will find that you will have a start up menu asking you which OS you want to use (Windows or Ubuntu).

---

### Post by tangibleorange on 2008-08-14
> **Unewbeginner said:**
> No way to do that with Alternate CD?

Thanks

I'm sure there is a way with the Alternate CD but I don't about it I'm afraid. As suggested above, you could just reinstall Ubuntu if you're happy with that (this will also reinstall GRUB), otherwise your best bet is to download a Live CD and run those instruction I mentioned earlier :).

---

### Post by mandrill on 2008-08-14
> **tangibleorange said:**
> I'm sure there is a way with the Alternate CD but I don't about it I'm afraid. As suggested above, you could just reinstall Ubuntu if you're happy with that (this will also reinstall GRUB), otherwise your best bet is to download a Live CD and run those instruction I mentioned earlier :).

I agree. You have got to get to a command line, (which I did not find a way to just now) or, best option, simply download the live cd, **install Windows** **first**, then re-install your Ubuntu - it will be nearly painless. Easiest would be find a command line from where you're at, but......
 
Have fun, and good luck!

---

### Post by tarun.winlin on 2008-08-14
Ok guys I am a N00b with ubuntu too, I guess I am facing the same issue, I followed the instructions in that link & this is the result.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> 

These outputs I thought would be useful
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf71bf71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       13003    53247442+   f  W95 Ext'd (LBA)
/dev/sda3           12749       13003     2048256   82  Linux swap / Solaris
/dev/sda4           13004       60800   383929402+   7  HPFS/NTFS
/dev/sda5            6375       12748    51199092   83  Linux

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

Can someone please have a look at it & tell me whats going on with my box.

---

### Post by tangibleorange on 2008-08-14
> **tarun.winlin said:**
> Ok guys I am a N00b with ubuntu too, I guess I am facing the same issue, I followed the instructions in that link & this is the result.

ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> find /boot/grub/stage1
 (hd0,5)

grub> root (hd0,5)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 22: No such partition

grub> 

These outputs I thought would be useful
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbf71bf71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       13003    53247442+   f  W95 Ext'd (LBA)
/dev/sda3           12749       13003     2048256   82  Linux swap / Solaris
/dev/sda4           13004       60800   383929402+   7  HPFS/NTFS
/dev/sda5            6375       12748    51199092   83  Linux

ubuntu@ubuntu:~$ cat /etc/fstab
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda3 swap swap defaults 0 0

Can someone please have a look at it & tell me whats going on with my box.

EDIT:
found someone having the same problem as you. here are the steps he went through:
[http://ubuntuforums.org/showthread.php?t=644892&page=3#24]("http://ubuntuforums.org/showthread.php?t=644892&page=3#24")
i suggest you try the same

---

### Post by tarun.winlin on 2008-08-14
Thanks, will try that & let you know.

---

### Post by dnns123 on 2008-08-14
there is a utility called Super Grub ([http://www.supergrubdisk.org/](http://www.supergrubdisk.org/))

which u can download and burn a bootable CD.

---

### Post by mandrill on 2008-08-14
> **tangibleorange said:**
> EDIT:
found someone having the same problem as you. here are the steps he went through:
[http://ubuntuforums.org/showthread.php?t=644892&page=3#24]("http://ubuntuforums.org/showthread.php?t=644892&page=3#24")
i suggest you try the same

I just used super grub disk yesterday to solve the same kind of problem on a triple boot Vista/Kubuntu/Xp. But, unless you really know what you're doing, things can get more confusing. Since you are working with a 500gb drive, you've lots of room to play with. One thing I also did yesterday was download EasyBcd, which is like Grub in reverse - Windows handles everything, but best of all, it will restore your Vista winloader. Anyway, it looks to me like you tried a manual partitioning session that didn't work out. If windows is already installed, use the grub disk to restore MBR to Windows, and, in a perfect world, re-install Ubuntu and let it do all the partitioning (ie, guided, use entire disk) for you -it usually makes the right choices - and you'll be back in the saddle. Always easier to install Ubuntu after windows - comes out right just about every time. Good luck, and shout back if you have more qustions.

---

### Post by Ptero-4 on 2008-08-14
In the alternate CD you can get a commandline by starting the installer as if you were to install and then when it reaches the partitioner you press the "esc" key to get a menu and from it you select the option that says something like "command line" or "shell". That´s it you got a shell.

Note that you can bring up the menu at any time, but it´s recommended to do it from within the partitioner because that´s the point where the /dev folder gets populated properly with the HD device files.

---

