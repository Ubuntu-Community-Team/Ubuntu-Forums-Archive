---
title: "How to manage partitions when having installed Ubuntu besides first installed Windows"
date: 2016-03-31
forum: New to Ubuntu
---

### Post by nextHawk on 2016-03-31
Hi! I am new to Ubuntu (installed it only today!), but have since many years gotten more and more irritated over Windows attempts to intrude into my whereabouts, and the risk of getting a share of all viruses etc out there on Windows systems. So, now that I finally bought a new ASUS miniPC with some 500+ Gb memory, I wanted to install and use Linux instead of the preinstalled Windows 10 that came with the buy. My colleague pointed me to Ubuntu 14.04 LTS. It was downloaded to a CD, and used for the installation, as below described.

 I did not want to remove the Windows 10, just install Ubuntu beside it, to choose which OS to use whenever I start the computer up.

Now my problems and questions:

1. When I started the computer first time, of course the preinstalled Windows 10 was first launched and prepared. It then divided the memory into two partitions C: and D:, with somewhere around 130Gb in C: and more or less the rest in D:. Then, when I was to install Ubuntu, the installation went seemingly well.


[LIST]
[*]                           :confused: 
[/LIST]
a) But, Ubuntu seems to have used Only C: to install in, same partition as Windows 10 was installed in, leaving the D: unreachable for Ubuntu (?). I was under the impression that Ubuntu would give me the possibility to handle/manage the total memory independent of any other OS installation. How can I do that?


[LIST]
[*]                           :confused: 
[/LIST]
b) Further, out of those 130 Gb in C:, Ubuntu now divided that into about 45Gb for itself (a new partition?), and the rest (about 84Gb, a second partition?) for 'Files'. It seems that my nice and big memory now have been reduced to 'only' about 30-40 Gb, from the initial 500+Gb. How can I change this?


[LIST]
[*]                           :confused: 
[/LIST]
c) I like order. I would prefer (and this is what I have done all the in Windows) to 'partion' and store OS files (for Windows as well as for Ubuntu) into their own folders or partitions, to keep them separated from all other installations and data files, etc. How can I do that?

Thanks for your suggestions!

---

### Post by grahammechanical on 2016-03-31
I only got as far as this when I got concerned about what you actually did:

> When I started the computer first time, of course the preinstalled  Windows 10 was first launched and prepared. It then divided the memory  into two partitions C: and D:, with somewhere around 130Gb in C: and  more or less the rest in D:. Then, when I was to install Ubuntu, the  installation went seemingly well.


Did you by any chance install in Windows 10 something from the Ubuntu DVD called wubi.exe? If you did then that explains a lot of things. Wubi.exe installs Ubuntu inside Windows as if it is another Windows program. Which it is. It fools the user into thinking that they have a true dual boot with Windows & Ubuntu but they do not have that at all.

The purpose of wubi was to allow Windows uses an opportunity to test Ubuntu without changing anything on their hard disk. The wubi program is installed and removed just like any other Windows program.

There are some things important about wubi that you should know. 1) Is is not being developed any more. 2) It is not compatible with Windows versions 8 and later. 3) Because of point 1 & 2 and the fact that hardly any member of this forum has any experience of wubi we do not provide support of wubi installs of Ubuntu.

So, if you did use wubi.exe then remove it using the usual Windows 10 way of removing programs and do a proper dual boot.

[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by nextHawk on 2016-03-31
Hi! I am not sure, but I did go to the BIOS to make sure that when the computer were starting up again after shut down, it would boot from the connected USB-disc_drive. The disc in it was the CD where Ubuntu was downloaded to, for use as installation CD.

---

### Post by Rocky_Bennett on 2016-03-31
Do you have an ISO of Windows 10? It sounds to me like you kind of messed up your installation and you should start over with a clean install of Windows 10. Your last post was very confusing because if you already installed Ubuntu then there would be no need for the installation DVD to be used at this point. Please be clear why you inserted that DVD again and what you hoped to accomplish.

If you really used a CD like your post indicated, then that could be a HUGE problem since a CD will not hold an entire ISO of Ubuntu.

---

### Post by oldfred on 2016-03-31
If you really used DVD and installed run this from live installer.

 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Impavidus on 2016-03-31
Just to prevent confusion: by memory we usually mean RAM. The long-term storage on the hard disk is called disk space.

Both operating systems need their own partition, and they are of different types. Windows cannot access the Linux partition, Linux can access the Windows partition, but only for data files. So your point C is satisfied automatically. As Windows cannot access the Linux partition, it won't give it a "drive letter" – a misnomer, as it's not a drive, but a partition.

For your other points, best to see the details. Use the boot-info summary linked by oldfred.

---

### Post by Ogden on 2016-04-01
> **Impavidus said:**
> Just to prevent confusion: by memory we usually mean RAM. The long-term storage on the hard disk is called disk space.

Both operating systems need their own partition, and they are of different types. Windows cannot access the Linux partition, Linux can access the Windows partition, but only for data files. So your point C is satisfied automatically. As Windows cannot access the Linux partition, it won't give it a "drive letter" &#8211; a misnomer, as it's not a drive, but a partition.

For your other points, best to see the details. Use the boot-info summary linked by oldfred.


When he said 500 gig of memory, I thought he must have a mainframe in his basement.  :)

---

### Post by Rocky_Bennett on 2016-04-01
To the OP, can you include some screen shots so that we can better assist you?

---

