---
title: "Ubuntu 11.10 unable to boot due to the unconfigured fstab"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by sanjeevcvh on 2012-04-28
Hello everyone,

Ubuntu 11.10 is unable to boot with the error :

"press s to skip mounting and M for the manual recovery "

when tried manual recovery and tried to see the fstab contents its "#unconfigured fstab for the base system "

the fstab has no details about the mount devices so failing to mount ...

Please help me in this issue .
Thanks in advance......

---

### Post by joetait on 2012-04-28
I don't know how much you already know, so please ask for clarification if needed. 

Firstly, this post ([http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)) should help you understand what fstab does.

Can you access the fstab file to edit it? It sounds like you can, but if you can't then you should probably use a live cd and then you will be able to access it.

When you edit it, try looking at the examples in the above post, but at the very least you will need to load your root partition (you should be able to use gparted on a live cd to work out which one that is, in case you don't know). This ([http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)) is a much much shorter guide to fstab, and should be enough for you to get everything in the right place. You will probably need to load up your swap partition too.

If this makes no sense do say and I will start a lot more basic.

---

### Post by sanjeevcvh on 2012-04-28
Thanks for the information ....I had installed ubuntu using the Windows installer I m afraid to make any changes as I dont want to lose any data on ubuntu as well as on windows ..

Is there a way to know the boot partition details to be entered in the fstab and need how to edit the fstab by running the live CD ..
Or its just the drive on which i installed Ubuntu ...In my PC windows on local C and ubuntu on drive E (dev/sda3),,,

I used - Sudo blkid /dev/sd??

Could you tell the possible reasons for this issue ...

Thanks ...

---

### Post by sanjeevcvh on 2012-04-29
Hello ,


Could someone tell me how to recover the files atleast so that i can recover my important files ..i need them badly ....please help ..

thanks in advance

---

### Post by joetait on 2012-04-29
This article - [http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/](http://www.omgubuntu.co.uk/2011/06/access-ubuntu-from-windows-7/) and this article - [http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html](http://www.ubuntugeek.com/tools-to-access-linux-partitions-from-windows.html) both describe how to access ubuntu files from windows. I haven't used WUBI, so I am not sure they will work. But try them at least.

To edit fstab using a live cd download Ubuntu 12.04 and burn it to a disc. Then restart with the disc in. It should load and ask if you want to install or try ubuntu. Go for trying ubuntu. When it has loaded, press ctrl+alt+T to load the terminal. In to the terminal type
```

sudo gedit /etc/fstab

```This should load a new window, that looks a bit like Windows notepad. You may not need to write sudo at the start (this gives you extra permissions, like admin on Windows, but since you are on the live cd I don't know if this is needed). 

It should already look something like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

```
Add the following two lines:
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda3 / ext4 defaults,noatime 0 2

```This should let it load up your root directory.

If you have a swap partition, in, say /dev/sda?, also add
```

/dev/sda?       none            swap    sw              0       0

```Leave anything else that is already there. I also HIGHLY, HIGHLY recommend reading the articles I already posted, so that you understand and can double check with your machine what you are doing to the fstab file.

I also HIGHLY HIGHLY recommend trying to access and back up your files before doing this, in case anything goes wrong. And back up everything else, just to be safe.

---

### Post by sanjeevcvh on 2012-04-29
Please some one help me ......!!

on mounting the drive partition  /dev/sda3 i m notable to edit the fstab as it says there is no such directoy exists ...:confused::confused:

Now I am trying to recover my files ......i m not able to access the root folder of the partition whatsoever from the Ubuntu live cd after mounting the partition ..... 

root@ubuntu:/mnt# ls -al 
total 241
drwxrwxrwx 1 root root  12288 Apr 29 22:46 .
drwxr-xr-x 1 root root    260 Apr 30  2012 ..
-rwxrwxrwx 1 root root  91136 Jan  8  2010 autorun.exe
-rwxrwxrwx 1 root root     29 Jan  8  2010 autorun.inf
drwxrwxrwx 1 root root   4096 Jan 25  2010 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 Jan 23  2010 System Volume Information
drwxrwxrwx 1 root root      0 Nov 19 17:49 ubuntu
-rwxrwxrwx 1 root root 134976 Nov 19 17:49 wubildr

gksu nautilus failed to provide the access or i m not able to understand how to access the ./home/sanjeev/ folder ...please help me asap..... :confused::confused::confused::confused:

---

### Post by sanjeevcvh on 2012-05-03
Thanks for the information it help me ..... cheers..!!

---

