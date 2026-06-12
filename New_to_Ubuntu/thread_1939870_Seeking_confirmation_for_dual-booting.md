---
title: "Seeking confirmation for dual-booting"
date: 2012-03-12
forum: New to Ubuntu
---

### Post by Mithost on 2012-03-12
Hello.

This summer, I am going to purchase a laptop for college. I really want to run ubuntu, but I need to keep windows on it for easy access to programs like flash, photoshop, 3DS max, etc. I can't use the free substitutes because they are being taught in class and I need to use the same program as the class is.

I've done some research into dual booting, and I just wanted to collect my thoughts and seek confirmation that this will work. My plan is to create a recovery CD with windows 7 and use it to create a new partition on my hard drive, then bring up the ubuntu installer through the CD or USB method and simply install it onto the partition I made. I'm going for a 500 GB hard drive, with windows have 200 GB, Ubuntu having 200 GB, and have 100 GB as storage.

My question with the storage partition is, will I be able to put files such as pictures and video onto this partition from one OS, and view them on the other one (without third party programs or converting)?

Another question I have is regarding security. I plan on getting virus protection for the Windows side of the machine. If it fails, will Ubuntu be at risk of viruses? Do I even need virus protection for the windows side?

One unrelated question...

How much would a laptop cost with 3GB of ram, Intel Core Duo, with it NOT being Acer/Emachines?

Thanks. I have no experience with Ubuntu, very little with partitioning, but I have windows down pretty good.

---

### Post by mikewhatever on 2012-03-12
I think you've got it pretty much figured out. 
The storage partition is a good idea. It would have to be NTFS, to be usable for both Ubuntu and Windows.
Windows malware doesn't work on Lunux, so you don't need an AV, and, IMHO, it's also not needed on Windows.
As for the cost, depends on where you are in the world. Different countries have different prices due to taxes, demand, wages, etc. Just shop around before buying.

---

### Post by madjr on 2012-03-12
> **Mithost said:**
> Hello.

This summer, I am going to purchase a laptop for college. I really want to run ubuntu, but I need to keep windows on it for easy access to programs like flash, photoshop, 3DS max, etc. I can't use the free substitutes because they are being taught in class and I need to use the same program as the class is.

I've done some research into dual booting, and I just wanted to collect my thoughts and seek confirmation that this will work. My plan is to create a recovery CD with windows 7 and use it to create a new partition on my hard drive, then bring up the ubuntu installer through the CD or USB method and simply install it onto the partition I made. I'm going for a 500 GB hard drive, with windows have 200 GB, Ubuntu having 200 GB, and have 100 GB as storage.

My question with the storage partition is, will I be able to put files such as pictures and video onto this partition from one OS, and view them on the other one (without third party programs or converting)?

Another question I have is regarding security. I plan on getting virus protection for the Windows side of the machine. If it fails, will Ubuntu be at risk of viruses? Do I even need virus protection for the windows side?

One unrelated question...

How much would a laptop cost with 3GB of ram, Intel Core Duo, with it NOT being Acer/Emachines?

Thanks. I have no experience with Ubuntu, very little with partitioning, but I have windows down pretty good.

Hi there.

**storage partition**:
For the storage partition, usually the problem is with windows not being able to see it (ubuntu can see any type of partition), so just create this new partition as NTFS or fat32 (both windows can see).

**New user and dual booting**:
Now if you're new to ubuntu and partitioning i would recommend you use **Wubi** (install ubuntu inside windows) for now till you get more experience.
instructions here:
[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)
If you use Wubi you can access the windows partitions anyway. Is not as optimized or secure as its own partition, but is far easier to maintain, reinstall and learn (you will want to experiment a lot in the first months.). Performance is not that bad either.

**Viruses and spyware/malware:**
yes, windows needs mandatory **antivirus and spyware** programs. Specially at school.
Ubuntu doesnt need it. Try to use ubuntu for everything else, so you dont catch malware and use windows when you need it or at school.

**Laptops:**
you can get one of those for about $500 bucks or less. Asus, lenovo or dell may be good options. HP laptops are good too, but have used your 4 primary partitions with some crap so is a little trickier to create a dual boot.

---

### Post by Mithost on 2012-03-12
Wow, you guys replied fast! I was expecting at least a few hours for a reply. I could get used to this. :D

I live in Ontario, Canada.

I heard Wubi is kinda like a "lite" version of ubuntu. I want to learn as much as I can about Ubuntu, and I want as many features of it was I am able to learn. If I am able to install it as a full OS, I might as well go along for the full ride.

I'm glad partitioning in windows will work. I saw a tutorial where a guy had a third party program running through the live CD to parition the system. I didn't like that. D:

---

### Post by papibe on 2012-03-12
Hi Mithost. Welcome to the forums!

Yes, dual boot is very possible. I have successfully set up dual boot system with XP, Vista and Windows 7.

Although it is for the most part a safe process, it is always a good idea to backup your important data. In case of you be want to super extra safe, I would recommend creating an image of your disk using something like [Clonezilla]("http://clonezilla.org/").

> **Mithost said:**
> I'm going for a 500 GB hard drive, with windows have 200 GB, Ubuntu having 200 GB, and have 100 GB as storage.

That is very similar to what I did for my Toshiba laptop. If I can suggest something would be to create 3 adjacent partitions for Ubuntu:
```

/     20-25Gb (for the OS).
swap  match your RAM
/home all the rest (for your personal files)
```
> **Mithost said:**
> 
My question with the storage partition is, will I be able to put files such as pictures and video onto this partition from one OS, and view them on the other one (without third party programs or converting)?

From Ubuntu you'll have full access to your Windows files. You can browse, read, copy, and modify them.

Unfortunately, that is not true for Windows. If you formatted the 100Gb data partition to NTFS, that would be the best way that Windows would have access to "share data".

> **Mithost said:**
> Another question I have is regarding security. I plan on getting virus protection for the Windows side of the machine. If it fails, will Ubuntu be at risk of viruses? Do I even need virus protection for the windows side?

Nothing to worry about. Windows viruses won't even have access to your Ubuntu partitions. 

Hope that helps, and tell us if you have more questions.
Regards.

---

### Post by gdea73 on 2012-03-12
With the previous answers you should have the information you need. Now granted if you'd like, you could have your /home partition be that 100GB, and make it ext2/3, and use [EXT2 for Windows](http://www.fs-driver.org/) to make it cross-compatible. It's worth a try, I used it on my old partition tabling of my workstation.

Windows does sort of need antivirus. But please don't get something annoying like McAfee or Norton, they're really just a scam to have people pay money for "internet security" and "protection!" I mean, they both *work* too, but the way they "alert!" you if your database is 3 seconds out of date will drive you insane. You can use [ClamWin](http://www.clamwin.com) to scan any suspicious files manually. It's free, it doesn't use constant scanning of every file you access, and it's a fairly good A/V. It doesn't block connections to potentially dangerous websites, however.

If you'd rather have more protection, I would consider Malwarebytes. I use it on my XP workstation and it's nice because it's $25 for a lifetime license, it has the OPTION to have an auto-protect module (on-access scanning), and it doesn't try to make you want to die, like McAfee or Symantec. :)

Dual-boot setup should be fairly easy. You don't even need a Win7 recovery CD to partition the drive - it's pretty easy to do either from the Ubuntu CD or using a utility such as Partition Wizard (freeware). If you decide to do it from the Ubuntu CD, or even if not, when you configure your drive, remember to install the GRUB bootloader to the *drive itself,* and not a partition (/dev/**sda**, not /dev/sda1, etc.). Otherwise you'll run into problems booting.

Good luck!

PS: Regarding laptop deals, I recently bought a Lenovo IdeaPad Z575 off of Newegg for $529. It's a quad-core A-series APU, with 6GB of DDR3, and a 1GB dedicated Radeon 6650M. Will be here in the mail soon, seems sweet. The less expensive IdeaPad might be a good laptop for you, which has a dual-core A-series (A4-XXXX), 4GB of RAM, and a slightly less powerful GPU. Just an idea. The other one's $499, it has a 1.9 GHz A4, while mine's a 1.5 (up to 2.4) A6.

---

### Post by Mithost on 2012-03-12
I'm not quite understanding the 3 Ubuntu Partitions. How would I assign each of them to /home or /swap (or whatever they are called D: )

---

### Post by madjr on 2012-03-12
> **Mithost said:**
> Wow, you guys replied fast! I was expecting at least a few hours for a reply. I could get used to this. :D

I live in Ontario, Canada.

I heard Wubi is kinda like a "lite" version of ubuntu. I want to learn as much as I can about Ubuntu, and I want as many features of it was I am able to learn. If I am able to install it as a full OS, I might as well go along for the full ride.

I'm glad partitioning in windows will work. I saw a tutorial where a guy had a third party program running through the live CD to parition the system. I didn't like that. D:

Wubi is ok, is full OS. you can try it.

Am using it on my hp laptop, since hp took over all the primary partitions, so i will have to do some arrangements, but i didnt really had much time with this one (i have 3 more computers), so i just installed wubi in 35 minutes and everything is good.

I will indeed try to fix the partition mess that hp made later, but things are working. :)

have fun!

---

### Post by madjr on 2012-03-12
> **Mithost said:**
> I'm not quite understanding the 3 Ubuntu Partitions. How would I assign each of them to /home or /swap (or whatever they are called D: )

with a wubi install everything is done for you.

So these options for swap, home, / , etc only appear in the custom partitioning dialogue on a partition install. But recommended after you get a bit more experience.

---

### Post by papibe on 2012-03-12
> **Mithost said:**
> I'm not quite understanding the 3 Ubuntu Partitions. How would I assign each of them to /home or /swap (or whatever they are called D: )

Sorry If I created some confusion.

Previous to the installation you are doing the right thing by reserving the 200Gb in advance to the Ubuntu intallation.

Then, while installing you can  choose (optionally) to 'customize' your installation by creating the 3 mentioned partition over the space that you reserved.

It's not really necessary, and if it complicates things too much for you, take it out of the equation (for now).

Another thing just came to mind: 'virtual playground'.

If you want play with the installation software in a pretty safe way, you can install the software [VirtualBox]("https://www.virtualbox.org/") in Windows. Then you can install Ubuntu as a virtual machine. You would have the chance of going through the steps of the installation process several times, and without taking the risk of actually doing it in your machine.

Regards.

---

### Post by gdea73 on 2012-03-12
> **Mithost said:**
> I'm not quite understanding the 3 Ubuntu Partitions. How would I assign each of them to /home or /swap (or whatever they are called D: )

It's fairly simple, the setup program will kind of guide you through it. If you choose to "specify partitions manually" it will ask you which partitions you would like to use for which purposes.

Select a partition, check off "Format," and label it as "/" for your root installation. For a separate home partition, do the same, but label it as "/home." Now when you browse the Linux filesystem, /home is a symbolic link of sorts that will "jump" to your other partition. It's the way I set up my dual-boot so I can share files between OSs, but only user-files. I don't need access to /usr/bin from WinXP :P

And then you would need to make a relatively small partition for your swapfile. You would choose to label it as "swap," and the installer configures the rest.

Does that make more sense?

Edit: Also, a WUBI install is alright for testing out Ubuntu, but running it inside a Windows (FAT32/NTFS) partition can be problematic regarding disk space. In 9.04, I had problems where I would run out of space on a WUBI install, even though there was a fair amount left on its partition.

---

