---
title: "Guide me to install Ubuntu 14.04LTS on my old laptop along with Windows7Ult."
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Ankush_Menat on 2014-05-01
Hello,

I am using Lenovo G580 with Windows 7 Ultimate OEM version and now my laptop works very slow. Someone recommended me to install Linux after bit research I've decided to give a try to Ubuntu.
I can't uninstall W7ult and I saw many threads that "Windowd erased while installing Ubuntu!" 
Will Ubuntu help to do basic tasks faster(like browsing and media)?
>I dont anything about booting, installing OS or partitions.
>I cant afford loosing data on laptop. I dont have my OEM CD too! :(

So guide me to...
1)Install Ubuntu alongside Windows 7.
2)Basic setups after installing.

I googled a bit and found that my laptop may not be supported because it doesn't have uefi thing. Here is the specification of my laptop - [http://www.flipkart.com/lenovo-essential-g580-59-358263-laptop-3rd-gen-ci5-4gb-500gb-dos/p/itmdcjhugdtpfzrk?pid=COMDGSR6RUYFGEGH](http://www.flipkart.com/lenovo-essential-g580-59-358263-laptop-3rd-gen-ci5-4gb-500gb-dos/p/itmdcjhugdtpfzrk?pid=COMDGSR6RUYFGEGH)

---

### Post by Bucky Ball on 2014-05-01
Welcome. UEFI has nothing to do with it. Ubuntu will install regardless. Only Win8 has that ludicrous proviso.  

Backup any valuable data before proceeding. When you get to the partitioning section of the Ubuntu install, choose 'Something Else' and partition manually. You can find a lot of info about what is required to do that by a quick search. You will see your Win7 partition clearly; it will be an NTFS partition (and you will also see your NTFS data partitions). Just don't touch them. 

In a legacy install (not UEFI) you are limited to four partitions on one physical drive. So ... you need free space and no more than three existing partitions to make this work. You would then create an extended partition, inside which you would put the Ubuntu partitions (EXT4 filesystems). There are many how-tos with pics online. 

A basic setup:

/ = the Ubuntu OS, 15-20Gb fine;
/home = if you want one, as large as you like, for your personal info. If you don't have a /home partition, then one will be created by default in /;
/swap = 2Gb.

You will find all of these mountpoints as defaults when you choose 'something else'. 

There's a start, but I suggest further research to understand what all this means. ;)

---

### Post by Ankush_Menat on 2014-05-01
I currently have 3 partitions- C, D, E 100GB , 160GB, 160GB respectively. I don't use E: at all, it just have few music files! Can I use it to install Ubuntu?

---

### Post by Bucky Ball on 2014-05-01
> **Ankush_Menat said:**
> I don't use E: at all, it just have few music files! Can I use it to install Ubuntu?

Yep. When you get to the partitioning section of the install, choose 'Something Else', delete that partition so it is free space (or 'unallocated'), create an extended partition with the unallocated space and then refer to my previous post for the mount points you are going to need. 

Put / and /home inside the extended partition as logical partitions (you will get the option of primary or logical, choose logical), both EXT4 filesystem, and leave 2Gb at the end for the /swap partition (you don't need to worry about the filesystem here, when you choose /swap as the mount point Ubuntu will automagically use 'swap space' as the filesystem), and that's about it. 

Once complete, you will be (should be) notified that there is another operating system on your computer (and it should tell you it's Win7) and if this is correct it should be fine to put grub in the MBR of the drive. If this is what happens, and your Win7 install is identified fine, agree and all 'should' be fine.

But as I say, back up any important info before attempting any of this. Good luck and post back with any other questions. ;)

---

### Post by Ankush_Menat on 2014-05-07
Ok I searched a bit but could not find any case like me :p
>I've downloaded Ubuntu amd64 iso on my laptop and verified md5.
>See the current state of partitions in my hard drive in attached screenshot below(capture.jpg)
>E is completely free and formatted.
> I have on USB stick -8gb sandisc cruzer and i think my laptop supports booting from usb.

So guide me how to partition properly and install ubuntu.

>while playing with bios I found that UEFI was enabled? I dont know what is that. will it affect anything?
>I downloaded usb universal installer and burned iso with it, but it shows WUBI and i dont want to run ubuntu by wubi.

---

