---
title: "New installation of Ubuntu 17.04 - Swap not Available"
date: 2017-04-20
forum: New to Ubuntu
---

### Post by Niccolo999 on 2017-04-20
I'm a brand new user to Ubuntu and Linux based desktop OS's. I am now dual booting Windows 10 and Ubuntu 17.04 and they are installed on different partitions of the same SSD. I also have a HDD for data. My PC has 8GB of RAM.

On installation I did not create a swap partition, and I'm assuming Ubuntu created a Swap file for me.

When I start **System Monitor** it says **Swap Not Available**. I also tried various commands I found on the internet and all show that Swap is not being used. I tried opening all LibreOffice apps and 10 instances of Google Chrome, but I can't get Swap to be shown as working. I tried SuperTuxKart and also Suspend. Nothing.

Is something wrong with my installation? I'm asking because I was trying to change Swappiness, but before I try that I want to confirm the swap file is being used and I want to see if increasing swappiness makes a difference to performance...

Thanks!

---

### Post by sp40140 on 2017-04-20
Nothing wrong. with this release of 17.04 Ubuntu have done away with swap partition. If your system needs swap space, you can easily create swap file.
Swap partition was needed in old days when RAM was limited. You have 8Gigs of RAM, you don't need swap.

---

### Post by RobGoss on 2017-04-20
You can also read about the changing of swap partition for swap file here on OMG Ubuntu [http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files](http://www.omgubuntu.co.uk/2016/12/ubuntu-17-04-drops-swaps-swap-partitions-swap-files)

---

### Post by Niccolo999 on 2017-04-20
Thanks for the quick replies!

I understand what a swap partition and swap file is. But isn't the swap file created automatically on a clean install? And if yes why isn't it showing in System Monitor?

---

### Post by RobGoss on 2017-04-20
I haven't installed any of the newest 17.04 so I can't really say, I would think the swap file would be created on the new installation. Did you see if the swap file was created?

---

### Post by Niccolo999 on 2017-04-20
I don't know how to do that. I found some terminal commands on internet and all show there is no swap, but maybe they were looking for a swap partition, not file.

---

### Post by Dennis N on 2017-04-20
My Lubuntu 17.04 included an existing swap partition when making /etc/fstab on installation, and the system monitor shows that swap in use. So perhaps the swap file is only used when there is no swap existing?

---

### Post by sp40140 on 2017-04-20
Swap file isn't created automatically (during install process). You have to explicitly create it after install.

---

### Post by Dennis N on 2017-04-20
> **sp40140 said:**
> Swap file isn't created automatically (during install process). You have to explicitly create it after install.

And how do you do that? Just wondering.

---

### Post by sp40140 on 2017-04-20
@Dennis N,
Please look at following link. Section #7.
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Cheers,

---

### Post by Dennis N on 2017-04-20
> **sp40140 said:**
> Swap file isn't created automatically (during install process). You have to explicitly create it after install.

This doesn't seem to be correct. I did an install yesterday of Xubuntu 17.04 using Gnome Boxes, and looking at that, we see a swap file was created on install. Here is /etc/fstab from that full disk install:

```
dmn@Zotac-vm:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=ff13fe3a-1458-441f-8ee7-60725efb008f /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
```

It is a file in the root directory:

```
dmn@Zotac-vm:/$ ls
bin    dev   initrd.img  lost+found  opt   run   srv       tmp  vmlinuz
boot   etc   lib         media       proc  sbin  [COLOR="#FF0000"]swapfile[/COLOR]  usr
cdrom  home  lib64       mnt         root  snap  sys       var

```

And it is a regular file:

```
dmn@Zotac-vm:/$ file swapfile
swapfile: regular file, no read permission
```

Hope that answers some questions you might have.

---

### Post by Frogs Hair on 2017-04-20
More info here.

[https://askubuntu.com/questions/904372/swap-partition-and-swap-file](https://askubuntu.com/questions/904372/swap-partition-and-swap-file)

---

### Post by sp40140 on 2017-04-20
I stand corrected.

---

### Post by howefield on 2017-04-21
> **Niccolo999 said:**
> Is something wrong with my installation?

What's the output of 

```
swapon -s 
```

---

### Post by Niccolo999 on 2017-04-21
Ok so I ran the same commands as Dennis N, and this is what I got (if I did it correctly).

> 
niccolo999@Niccolo999-Ubuntu:~$ cat /etc/fstab# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda5 during installation
UUID=822a4ec5-ccc8-4662-84a5-7dca5909695a /               ext4    errors=remount-ro 0       1
/swapfile                                 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
UUID=7CA0-06A2    /boot/efi    vfat    defaults    0    1

niccolo999@Niccolo999-Ubuntu:~$ ls
Desktop    Downloads         ?exit                  Music     Public     Videos
Documents  examples.desktop  linux_signing_key.pub  Pictures  Templates

niccolo999@Niccolo999-Ubuntu:~$ file swapfile
swapfile: cannot open `swapfile' (No such file or directory)


However through file explorer I can see a file:

[https://drive.google.com/file/d/0B8tr6Tnucf_RU2JVMHJoZGZQbFk/view?usp=sharing](https://drive.google.com/file/d/0B8tr6Tnucf_RU2JVMHJoZGZQbFk/view?usp=sharing)

---

### Post by Niccolo999 on 2017-04-21
> niccolo999@Niccolo999-Ubuntu:~$ swapon -s
niccolo999@Niccolo999-Ubuntu:~$ 


Gives me nothing at all, not even an error!

---

### Post by Niccolo999 on 2017-04-22
I followed the instructions here and now I have a working Swap File! No idea why it wasn't working by default.

[https://askubuntu.com/questions/904628/default-17-04-swap-file-location](https://askubuntu.com/questions/904628/default-17-04-swap-file-location)

---

### Post by Dennis N on 2017-04-22
> **Niccolo999 said:**
> I followed the instructions here and now I have a working Swap File! No idea why it wasn't working by default.

[https://askubuntu.com/questions/904628/default-17-04-swap-file-location](https://askubuntu.com/questions/904628/default-17-04-swap-file-location)

In your post #15, your ls command was run from your home directory. The swapfile is in the root (/) directory, so you didn't see it. It was most likely in / all time, since it shows in /etc/fstab.

run from root (/)
```
dmn@Zotac-vm:/$ ls
```

run from home (~)
```
dmn@Zotac-vm:~$ ls
```

see the difference? Same reason why the file command didn't find it.

---

### Post by Niccolo999 on 2017-04-22
Tried it and I see the difference, I didn't know the / and ~ made a difference in the terminal! I'm a complete newbie. What is sure is that before System Monitor and swapon -s didn't show an active swap file, and now they do. I have no idea why it wasn't active, but at least it's fixed.

---

### Post by Dennis N on 2017-04-22
> **Niccolo999 said:**
> Tried it and I see the difference, I didn't know the / and ~ made a difference in the terminal! I'm a complete newbie. What is sure is that before System Monitor and swapon -s didn't show an active swap file, and now they do. I have no idea why it wasn't active, but at least it's fixed.

What's in front of the $ is the directory you are in (current working directory). So, a more obvious example:
```
dmn@Sydney:~$ cd Documents
dmn@Sydney:~/Documents$ 

```
cd Documents changes the current working directory from home (~) to ~/Documents.

pwd (print working directory) will output the current working directory without the symbolic abbreviation ~/ (which also represents home): 
```
dmn@Sydney:~/Documents$ pwd
/home/dmn/Documents
```

Enjoy your new swapfile!

---

### Post by Niccolo999 on 2017-04-22
I just open the terminal from the launcher. I get ~/. I didn't realise opening it from elsewhere made a difference!

---

### Post by Dennis N on 2017-04-22
Here is the well-known guide to learning to use the terminal. From basics to more advanced things.

[http://linuxcommand.org/lc3_learning_the_shell.php](http://linuxcommand.org/lc3_learning_the_shell.php)

---

### Post by Niccolo999 on 2017-04-22
Thanks!

---

### Post by russkyca on 2017-04-22
> **Niccolo999 said:**
> I'm a brand new user to Ubuntu and Linux based desktop OS's. I am now dual booting Windows 10 and Ubuntu 17.04 and they are installed on different partitions of the same SSD. I also have a HDD for data. My PC has 8GB of RAM.

On installation I did not create a swap partition, and I'm assuming Ubuntu created a Swap file for me.

When I start **System Monitor** it says **Swap Not Available**. I also tried various commands I found on the internet and all show that Swap is not being used. I tried opening all LibreOffice apps and 10 instances of Google Chrome, but I can't get Swap to be shown as working. I tried SuperTuxKart and also Suspend. Nothing.

Is something wrong with my installation? I'm asking because I was trying to change Swappiness, but before I try that I want to confirm the swap file is being used and I want to see if increasing swappiness makes a difference to performance...

Thanks!How large is your partition for Ubuntu 17.04?   How much disk space do you have left?  Just curious.

Edit:   Nevermind... :-/

> **Niccolo999 said:**
> I followed the instructions here and now I  have a working Swap File! No idea why it wasn't working by default.

[https://askubuntu.com/questions/904628/default-17-04-swap-file-location](https://askubuntu.com/questions/904628/default-17-04-swap-file-location)

---

### Post by Niccolo999 on 2017-04-23
My SSD is 250GB. I created a 150GB partition for Windows 10 (wife uses photoshop so she needs windows). That left a 90.8GB partition for Ubuntu. I used up 10.8GB, including a 4GB partition I created. The computer also has an NTFS formatted HDD of 2TB.

---

