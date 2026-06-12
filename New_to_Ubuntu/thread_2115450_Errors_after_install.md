---
title: "Errors after install"
date: 2013-02-12
forum: New to Ubuntu
---

### Post by guitarnick on 2013-02-12
I recently installed 12.04 as a dual boot on an old, but perfectly functional, Windows XP machine. The install went fine. Upon completion, it told me to remove the install disc, hit Enter and it will reboot. When it reboots, I get BOOT ERROR and it stalls there. I have it configured to boot off the DVD drive first. If I power power down and place the install disc back in it boots up off of the disc and gives me the Try Ubuntu/ Install option. I never get the option to choose which OS to boot up. I tried a reinstall of Ubuntu and got the same result. I tried to boot off of my Windows XP disc and it went through its install process. I'm considering blowing the whole thing out and reformatting starting with Windows and trying it all again, but I'd rather not.

Any suggestions?

---

### Post by fdrake on 2013-02-12
> **guitarnick said:**
> I recently installed 12.04 as a dual boot on an old, but perfectly functional, Windows XP machine. The install went fine. Upon completion, it told me to remove the install disc, hit Enter and it will reboot. When it reboots, I get BOOT ERROR and it stalls there. I have it configured to boot off the DVD drive first. If I power power down and place the install disc back in it boots up off of the disc and gives me the Try Ubuntu/ Install option. I never get the option to choose which OS to boot up. I tried a reinstall of Ubuntu and got the same result. I tried to boot off of my Windows XP disc and it went through its install process. I'm considering blowing the whole thing out and reformatting starting with Windows and trying it all again, but I'd rather not.

Any suggestions?
boot with the ubuntu cd and use the "try ubuntu" option . At the ubuntu session start the terminal (press ctrl+ alt+t) and type:
```

sudo fdisk -l

```
post here the output. You can use the internet too while trying ubuntu.

---

### Post by lincoln32 on 2013-02-12
lots of ways to fix it-- I suspect a grub error rare but it happens from time to time. you might try ubuntu boot cd it can easily repair grub issues
[http://www.ultimatebootcd.com/index.html](http://www.ultimatebootcd.com/index.html) this the one I used last time):P

---

### Post by guitarnick on 2013-02-13
> **fdrake said:**
> boot with the ubuntu cd and use the "try ubuntu" option . At the ubuntu session start the terminal (press ctrl+ alt+t) and type:
```

sudo fdisk -l

```post here the output. You can use the internet too while trying ubuntu.

Here's what I got. What option do I want?

ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ 


Thanks!

---

### Post by Bucky Ball on 2013-02-13
Boot from the LiveCD, get to a desktop and install Boot Repair and run it. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The 'sudo fdisk -l' command is a small L, not a 1, but not sure why that would be of help.

---

### Post by guitarnick on 2013-02-13
> **Bucky Ball said:**
> Boot from the LiveCD, get to a desktop and install Boot Repair and run it. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The 'sudo fdisk -l' command is a small L, not a 1, but not sure why that would be of help.

Oops, thought it was a 1. Here are teh results with l:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd82cd82c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    92705316    46352627    7  HPFS/NTFS/exFAT
/dev/sda2        92706814   160835583    34064385    5  Extended
/dev/sda5       158808064   160835583     1013760   82  Linux swap / Solaris
/dev/sda6        92706816   158808063    33050624   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

---

### Post by guitarnick on 2013-02-13
> **Bucky Ball said:**
> Boot from the LiveCD, get to a desktop and install Boot Repair and run it. 

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The 'sudo fdisk -l' command is a small L, not a 1, but not sure why that would be of help.

I get 'command not found' when I try to run boot repair.

---

### Post by Bucky Ball on 2013-02-14
> **guitarnick said:**
> I get 'command not found' when I try to run boot repair.

You have installed Boot Repair? You can do that running from a liveCD. If it fails it gives a report with much more info about where your grub is installed, etc. ...

How are you trying to run it exactly?

---

### Post by fdrake on 2013-02-14
> **guitarnick said:**
> Oops, thought it was a 1. Here are teh results with l:

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders, total 160836480 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd82cd82c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    92705316    46352627    7  HPFS/NTFS/exFAT
/dev/sda2        92706814   160835583    34064385    5  Extended
/dev/sda5       158808064   160835583     1013760   82  Linux swap / Solaris
/dev/sda6        92706816   158808063    33050624   83  Linux

Partition table entries are not in disk order
ubuntu@ubuntu:~$

try this:
boot from the live ubnut cd, open the terminal and type:
```

sudo umount /dev/sda6
sudo mount /dev/sda6 /mnt
sudo apt-get install  grub2-common
sudo grub-install --root-directory=/mnt/ /dev/sda

```
reboot; You should be able to boot into ubuntu BUT not Windows . To fix the problem, boot normally into your ubuntu partition (not the live cd) and open the terminal
```

sudo update-grub

```
reboot and you should option to boot into windows or ubuntu. 

Note : I am assuming that you have already installed windows!

---

### Post by Bucky Ball on 2013-02-14
+1. This is the plan.

---

### Post by guitarnick on 2013-02-14
> **fdrake said:**
> try this:
boot from the live ubnut cd, open the terminal and type:
```

sudo umount /dev/sda6
sudo mount /dev/sda6 /mnt
sudo apt-get install  grub2-common
sudo grub-install --root-directory=/mnt/ /dev/sda

```
reboot; You should be able to boot into ubuntu BUT not Windows . To fix the problem, boot normally into your ubuntu partition (not the live cd) and open the terminal
```

sudo update-grub

```
reboot and you should option to boot into windows or ubuntu. 

Note : I am assuming that you have already installed windows!

Yes, I have Windows installed.  I entered in what you said at a terminal and tried to reboot and I get "Read Error."
Does that speak to a hardware issue?

---

### Post by guitarnick on 2013-02-14
> **Bucky Ball said:**
> You have installed Boot Repair? You can do that running from a liveCD. If it fails it gives a report with much more info about where your grub is installed, etc. ...

How are you trying to run it exactly?

I went to the link you gave me for Boot Repair and added it the Ubuntu CD as the instructions led me to. I ran it as you instructed and that's when I got the Command Not found error.

---

### Post by Bucky Ball on 2013-02-15
Boot Repair should be in your Applications menu if you have it installed. Can you see it there and run it from there?

Again, how are you trying to run it to get the 'Command not found' error? Sounds like from a terminal. You shouldn't need to do that.

You might be better to download the Boot Repair ISO, burn it to a bootable CD and boot from it. It will give you a regular desktop with the option to run Boot Repair. That will then give us a heap of info if it doesn't fix your issue.

---

### Post by fdrake on 2013-02-16
> **guitarnick said:**
> I went to the link you gave me for Boot Repair and [COLOR="Red"]added it the Ubuntu CD as the instructions led me to[/COLOR]. 
what do you mean by that? When you boot into the ubuntu live cd You are online right? That is how you are communicating with the forum, right? or not?.

---

### Post by Bucky Ball on 2013-02-16
+1. I don't understand 'added it the Ubuntu CD' either. You can't add anything to the LiveCD. But you can install Boot Repair when online booting from the LiveCD and then launch Boot Repair from the Applications menu ... ?

---

### Post by lincoln32 on 2013-02-16
the boot repair disk has the utility’s to repair his boot issues, it runs as a live cd and follow directions it will automatic fix the grub on his main install so when he reboots not using the boot disk the original install should be fixed. the boot repair disk just replace's grub2 on the original disk. it is not the same disk as a normal live install disk,:p
 do not worry xp should still be there unless you told the install to remove it. 
  
:p

---

### Post by guitarnick on 2013-02-17
> **fdrake said:**
> what do you mean by that? When you boot into the ubuntu live cd You are online right? That is how you are communicating with the forum, right? or not?.

No, I am communicating with the forum through another computer. 

When I say I added it to the CD, I mean it told me that was burned to the Ubuntu LiveCD. The message said it was added. Yes, I tried to run BootRepair from a terminal. I am a total noob with Ubuntu. That's why I'm in this Absolute Beginners section. If there's something I should be doing, please give specific instructions how to do this. Otherwise I'm flying by the seat of my pants here.

---

### Post by Bucky Ball on 2013-02-17
When you install Boot Repair while running from a LiveCD it appears in your applications menu, no need to run from a terminal (I don't know how to do that myself).

---

### Post by guitarnick on 2013-02-17
> **Bucky Ball said:**
> When you install Boot Repair while running from a LiveCD it appears in your applications menu, no need to run from a terminal (I don't know how to do that myself).

I've installed Boot Repair twice now and it does not appear anywhere in my installed applications. When I try to run boot repair from the Terminal it says 'command not found.'

---

### Post by Bucky Ball on 2013-02-17
That is mighty odd. So, as mentioned earlier, your best bet might be to download the Boot Repair ISO, burn that to a disk and boot from it. That way you can't really miss. Boot Repair is the only app on the disk then. Just to clarify. You need these commands one after the other:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```

If you are not getting the Boot Repair GUI after the final 'boot-repair' command I suspect you are doing something wrong, possibly the syntax in one of the commands. 

Have a look here:

[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

---

### Post by guitarnick on 2013-02-17
> **Bucky Ball said:**
> That is mighty odd. So, as mentioned earlier, your best bet might be to download the Boot Repair ISO, burn that to a disk and boot from it. That way you can't really miss. Boot Repair is the only app on the disk then. Just to clarify. You need these commands one after the other:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```

If you are not getting the Boot Repair GUI after the final 'boot-repair' command I suspect you are doing something wrong, possibly the syntax in one of the commands. 

Have a look here:

[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

Ok, I'll try to make a bootable cd with Boot repair. So I'm clear, do I run these commands from a terminal AFTER I run boot repair or are these commands used to actually run the repair application? Will Boot Repair give me a terminal to enter these commands?

---

### Post by Bucky Ball on 2013-02-18
These commands are to install it while running from a live CD or hard drive.

If you make and boot from a CD you don't have to do anything. It is a desktop environment and Boot Repair. That's it.

No, Boot Repair uses a GUI, no terminal. You only launch it from a terminal, if you want to, that is.

---

### Post by guitarnick on 2013-02-18
> **Bucky Ball said:**
> These commands are to install it while running from a live CD or hard drive.

If you make and boot from a CD you don't have to do anything. It is a desktop environment and Boot Repair. That's it.

No, Boot Repair uses a GUI, no terminal. You only launch it from a terminal, if you want to, that is.

Well, I made a bootable CD, ran Boot Repair, and then rebooted. I got "Read Error." Does that speak to a hardware issue? I wasn't having any hard drive or any other issues before I installed Ubuntu.

---

### Post by fdrake on 2013-02-18
1.
first boot into the UBuntu CD.
[https://www.youtube.com/watch?v=I5DeLLXd5gs](https://www.youtube.com/watch?v=I5DeLLXd5gs)

2. select "TRY OUT UBUNTU". Make sure that you are online! And then follow either my suggestions or Bucky Ball's advice;


PS: to make a Ubunut boot live cd  see here:
[http://www.youtube.com/watch?v=wpALe245EOQ](http://www.youtube.com/watch?v=wpALe245EOQ)

---

### Post by guitarnick on 2013-02-18
> **fdrake said:**
> 1.
first boot into the UBuntu CD.
[https://www.youtube.com/watch?v=I5DeLLXd5gs](https://www.youtube.com/watch?v=I5DeLLXd5gs)

2. select "TRY OUT UBUNTU". Make sure that you are online! And then follow either my suggestions or Bucky Ball's advice;


PS: to make a Ubunut boot live cd  see here:
[http://www.youtube.com/watch?v=wpALe245EOQ](http://www.youtube.com/watch?v=wpALe245EOQ)

Now you're just confusing me. Why do I want to do that? I've already installed Ubuntu and I've already run boot repair. Why do I want to go in to the "try Ubuntu" environment? Shouldn't it be working now? I feel like I'm repeating the same steps over and over and not getting any where. Which suggestions are you telling me to follow? You've both given several steps to follow, which I appreciate. But I'm confused on which to do and why.

---

### Post by guitarnick on 2013-02-20
So no more suggestions or clarification on which set of steps I should be following??

---

### Post by Bucky Ball on 2013-02-21
Mate, just burn Boot Repair, boot from the disk and run it. That simple. We've given pleny of suggestions ...

---

### Post by guitarnick on 2013-02-24
> **Bucky Ball said:**
> Mate, just burn Boot Repair, boot from the disk and run it. That simple. We've given pleny of suggestions ...

That's what I did. I made a bootable CD, booted from the cd, ran the utility and nothing changed. It still doesn't boot. I get Read Error. I can only boot from the Ubuntu cd. I can't even get to Windows.

I very much appreciate everyone's help, but honestly I've pretty much given up. I've spent a lot of time on this project and I can't get it to work. I've moved on. Back to Windows. It would have been cool to make it work, but it apparently just wasn't meant to be. Thank you everyone who contributed for your help.

Cheers!!

---

### Post by Bucky Ball on 2013-02-24
In that case, please mark thread as solved from 'Thread Tools' at top right to help others (and save some time).

---

