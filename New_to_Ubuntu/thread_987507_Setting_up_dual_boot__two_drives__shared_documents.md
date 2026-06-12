---
title: "Setting up dual boot / two drives / shared documents?"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Cliff.Forster on 2008-11-19
Hello there,

I have used Ubuntu before and loved it (there is no better way to squeze some extra life out of an old corrupt windows machine if you ask me), but certain requirements for work, and gaming force me to keep my old copy of XP going for my personal machine.

I have two SATA II hard drives on my system, both sized equaly, and I was thinking, what I would love to do is set up a dual boot so Ubuntu has its own space on the 2nd drive, away from XP,  can this be done?  Going a step further, can I set it up so XP still has acess to some of the space on the 2nd drive, since the bulk of my files will still be there?

Also, is there any way to get the my documents files shared between Ubuntu and XP?  I would like to be able to just drop a file in my documents, and have redundancy over both OS partitions, so they each share the same data without me having to do and manual file updates.  In other words, if I add a photo to the my documents file in ubuntu, or xp, I want it sitting ready for my other OS as well.  Is this madness possible?

Thanks all.

Cliff

---

### Post by wolfen69 on 2008-11-19
just make the shared space fat32. ubuntu and xp will both be able to read it.

---

### Post by dracayr on 2008-11-19
of course everything you mentioned is possible. to get the ext3/ext2 fs working: fs-driver.org. to install ubuntu on one of the hdd's: install, and when it comes to partitioning, check "use entire disk" and check the disk you want to install ubuntu on _Always install windows before ubuntu_

Of course you can also game with linux.. And which requirements for work would that be? nearly for everything, theres an opensource linux alternative

dracayr

---

### Post by kestrel1 on 2008-11-19
Yes, you can have XP on one drive & Ubuntu on another, you can even have some of the second drive kept for your files.
It is possible to share your files, Ubuntu is able to read your NTFS drive & I have  feeling that there is now a utility that will allow XP to see Linux drives.
It just depends on how things are set up.

---

### Post by kansasnoob on 2008-11-19
Well, there's lots of useful information here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

and here:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

I personally don't care for using separate drives for different operating systems. I've found it much easier to have both (or more) operating systems on one drive and then I can add drives infinitum for data, but that's only a personal preference!

But, as far as sharing files, Linux is now quite capable of reading and writing to NTFS. I prefer adding ntfsprogs but ntfs-config is a great alternative.

You can read more about ntfsprogs here:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

Both ntfsprogs and ntfs-config are in Ubuntu's repos so they can be installed from synaptic or by apt.

---

### Post by Cliff.Forster on 2008-11-19
> **dracayr said:**
> of course everything you mentioned is possible. to get the ext3/ext2 fs working: fs-driver.org. to install ubuntu on one of the hdd's: install, and when it comes to partitioning, check "use entire disk" and check the disk you want to install ubuntu on _Always install windows before ubuntu_

Of course you can also game with linux.. And which requirements for work would that be? nearly for everything, theres an opensource linux alternative

dracayr


My main issue for work is in how they set up the virtual private network for remote acess.  Its a decent system, but it absolutely requires Internet Explorer over XP or 2000, wont work in Vista even.  I have tried it through firefox and even on a MAC with Safari, and it just wont allow you to acess that web portal.  So at bare minimum I am stuck with that.

3D gaming on WINE is interesting, It's just a bit of work, so if I am stuck on XP for my VPN, Id just as well game there too, but for everything else, Ubuntu feels nice, snappy, clean.  Plus, I love toying around with it a bit.  

On the other machines I have used, I have had friends who had older systems, that they were going to trash due to the massive corruption on the windows OS, a couple of 98 machines, one XP where the OEM would not support them with a restore disk, so I salvaged the files by slaving thier old drives into another system, unloading onto a external disk, then wiping it clean and installing ubuntu, and its like having a brand new machine, they can't belive how nice it works.

I have never done a dual boot set up though, and I have XP up and running nice now, so adding Ubuntu 64 bit 8.10 is in my near future, I just have to plan the set up as best I can.

---

### Post by caljohnsmith on 2008-11-19
> **Cliff.Forster said:**
> 
Also, is there any way to get the my documents files shared between Ubuntu and XP?  I would like to be able to just drop a file in my documents, and have redundancy over both OS partitions, so they each share the same data without me having to do and manual file updates.  In other words, if I add a photo to the my documents file in ubuntu, or xp, I want it sitting ready for my other OS as well.  Is this madness possible?

I think you could easily share your Windows "My Documents" folder with Ubuntu by first putting your Windows partition in your /etc/fstab so it is automatically mounted on start up, and then simply create a "symbolic link" in your home directory to your "My Documents" folder in Windows. Then whenever you put something in your Ubuntu "My Documents" folder, it will actually be put in the Windows "My Documents" folder. In other words, you'll have true file sharing. 

If you would like more specifics of how to do any of that, let me know, but it will be easier to give directions specific to your setup once you actually have Ubuntu installed. So let us know how it goes. :)

---

