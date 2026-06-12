---
title: "Installing Ubuntu as Third OS on same SSD."
date: 2015-01-02
forum: New to Ubuntu
---

### Post by brennon3 on 2015-01-02
I have a SSD that currently has Windows 8.1 and Windows 10 tech preview installed. I'm an experienced Windows user and am finally ready to give Linux a try. 

I'm looking for simple information on installing Ubuntu as the tertiary OS. As I understand it form my searches so far, the Windows boot manager will not work for 3 operating systems and I will need to use GRUB 2. My question is exactly what is the process for this, and which format should I use for the Ubuntu partition?

Thanks!

---

### Post by grahammechanical on 2015-01-02
The Windows boot manager, for all I know, may well boot more than 3 operating systems. What Windows boot managers do not do is recognise any OS other than a Microsoft OS. So, you do need the Linux bootloader, Grub. Please read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The question is, what installation method are you going to use? The "Install Alongside" option, which is the easiest? Or the "Something Else" option, which means creating the partitions yourself. So, informing you that the usual Linux partition format is Ext 4 does not help you much.

I suggest that you run the Ubuntu live session. And then try to install and see if you get the option to Install Alongside. At that point you are not committed to installing. You can back out. The installer will install Grub 2. But it will need space on the SSD for a Ubuntu partition (minimum 7GB but 10 - 15GB preferable) and a swap partition.

Regards.

---

### Post by Bucky Ball on 2015-01-02
Welcome. Ubuntu will install grub and that should pick up your Win installs and add them to the boot menu. If you choose 'Something Else' and partition rather than 'Alongside' you will be asked where to install grub. Make it 'sda'. Ubuntu uses sd* for drives and sda1 (example) for partitions on that drive rather than the Win syntax hd0 etc.

If you go for 'Something Else' you will see your Win partitions clearer in there. They will be NTFS partitions. Just don't touch them and you should be fine. If you need to shrink them to create space to install Ubuntu, do so by booting into Win and using its disk management software, NOT the ubuntu Gparted software. That can screw things up royally with Win OS partitions.

You would have a UEFI install I imagine with Win 8 and 10, so Ubuntu needs to be installed UEFI also.

---

### Post by brennon3 on 2015-01-02
Thanks a lot guys. I'll try this out shortly and get back to you with results. I did attempt to install a few months ago using the Something Else option but things didn't make a lot of sense. I'll try the Alongside method and hopefully things will be better.

Cheers.

---

### Post by Bucky Ball on 2015-01-02
Obvious, but _backup any valuable data_ prior to attempting the install. ;)

With the 'Something Else' option, you need to create this mount points at least:

/ = where the OS goes. 20Gb plenty if you are storing or linking to your data on another partition, otherwise, large as you like;
/swap = 2Gb. Equivalent to the Win pagefile. If you intend to hibernate often, then should be the same size as your installed RAM or larger.

You can also add a /home partition and make this a big as you like. This is where your /Documents, /Videos, etc. personal data directories would go. If you don't create one, they go to a /home directory inside /.

All these mountpoints you will find as defaults inside the manual partitioner. The / and /home partitions need to be EXT* file systems (EXT4 recommended). 

If you already have a data partition or data inside the Windows partition, we can help you create links to it in Ubuntu which will help save space and prevent redundancy. 

Good luck. ;)

---

### Post by brennon3 on 2015-01-02
I've got a 3TB NAS drive that has a few different system images and everything important is on alternate drives. This particular SSD (128GB) is strictly for operating systems so even if things go south it isn't a big deal. There's a secondary 256GB SSD for games I play frequently, a 1TB 7200RPM HDD for other games, and a 1.5TB 7200RPM storage drive for music and programs. 

Thanks for the warning though. :)

I'll try the Something Else option again. If I recall correctly I was getting errors that there was no mount point or that it was wrong. When you stated I'll need to create those mount points does the position of the partition or mount point matter? For example I already have Windows 8.1 at the front of the disc and Windows 10 behind it. Would adding the / point in the third partition cause any foreseeable problems? I've read the boot loader needs to be at the start of the disc. 

I was hoping to only use about 8GB of space for Ubuntu. I have 32GB of RAM so matching that isn't possible, but I do not use hibernate. Ever. I don't plan on doing much besides browsing and tinkering, and I have a 64GB flash drive I can use for anything that needs to be saved or add a storage partition on one of my other drives if I change my mind.

Can you provide details on creating these mount points? (Again, total newbie here, sorry.)

---

### Post by Bucky Ball on 2015-01-02
All good, then. ;)

I have added a few more things to my last post which might help you along, whichever way you go.

---

### Post by brennon3 on 2015-01-02
As have I.

---

### Post by Bucky Ball on 2015-01-02
[This]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") might clear some things up. I'm old school and always put the /swap at the very end of the disk, but that just me and might not be poss in your case. 

You create the partition and assign it a mount point in the process. You will find / as a default there when you're doing it. Just select it. Same for /swap and a number of others. 

8Gb is v. small and not sure of the minimum, but you are going to need a 2Gb /swap partition also, so that leaves you 6Gb to install a full Ubuntu on. Not ideal or perhaps not possible. There are other spins that will operate in such a confined space, but either way, you will need to link to data on other partitions and not store any personal data in /.

In the attached screenshot, see where it says 'Mount point'? If you click the arrow, you will find the defaults. ;)

---

### Post by yancek on 2015-01-02
The link below has a lot of useful information on Linux partitioning and if you scroll about half way down the page, a detailed tutorial on installing Ubuntu and selecting partitions using the manual (Something Else) method.  Windows can boot multiple systems of windows as long as you install the most recent windows last but not Linux unless you install third party software to boot.  Grub can boot or chainload as many systems as you can fit on your hard drive.

 [http://forums.justlinux.com/showthread.php?143973-A-grub-menu-booting-100-systems-of-Dos-Windows-Linux-BSD-and-Solaris](http://forums.justlinux.com/showthread.php?143973-A-grub-menu-booting-100-systems-of-Dos-Windows-Linux-BSD-and-Solaris)

---

### Post by brennon3 on 2015-01-02
I guess my confusion here is that you're saying I need multiple mount points but what I'm seeing only lets me use one per partition. I just don't understand the logic of needing multiple partitions for one operating system.

---

### Post by Bucky Ball on 2015-01-02
Yep, one per partition. You create the / partition (whatever size you want) then you create the /swap partition (2Gb size). Two separate partitions with two separate mount points.

Unsure of the logic, but that's how it is: you need a small /swap partition as this does not get installed inside the OS (unlike Win pagefile). If you install another Linux OS, you can use the existing /swap partition for it too, don't need to create another.

You could possibly get by without a /swap with that much RAM, though (did you say 32Gb?) as it would doubtfully ever be used. That is a LOT of RAM that will also probably never get used, depending on what you get up to (running virtual machines or other RAM intensive stuff?). 8Gb is generally plenty for the average user. Rest is overkill unless it's there for a reason.

---

### Post by brennon3 on 2015-01-02
I've done as you suggested but I'm getting an error saying I do not have a swap partition. Which I made 2gb. The /swap mount point wasn't an option so I typed it in manually. Potentially why its not recognized?

I went with roughly 16gb for the os and 2gb for the swap

Edit - figured it out. Didn't see swap was a file system selection. Not a mount point

---

### Post by Bucky Ball on 2015-01-02
> **brennon3 said:**
> 

Edit - figured it out. Didn't see swap was a file system selection. Not a mount point

Yep, you got it. It is explained on [the link]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352") I gave earlier. ;)

Making it 'swap space' will give it the /swap mountpoint by default.

---

### Post by brennon3 on 2015-01-02
Thanks! It's now installed and running. It looks like GRUB is showing Windows 8.1 and Windows 10 by there boot loaders. (Windows 8 and Windows 7 respectivly) Is there a way to change this so that the names reflect the actual operating systems and set Windows 8 as the default?

---

### Post by Bucky Ball on 2015-01-02
You could try [Grub Customizer]("http://ubuntuhandbook.org/index.php/2014/04/install-grub-customizer-ubuntu-1404/"). I think Ubuntu Tweak might work for that, too, but don't and haven't ever used it (haven't used straight Ubuntu in some years but UTweak might be installed by default, don't know so check). ;)

Great news you got there and all is running. If you need help linking to other directories in existing partitions (as you have no room for data if you are on a 6Gb partition) post a new thread with a descriptive title and post a link to it here and I'll have a look. 

For starters,[ here's ]("http://www.herikstad.net/2009/07/creating-symlink-in-ubuntu.html?showComment=1275427925979")how to create a symlink and their syntax. You can install programs from the Software Centre. Always look there first as the stuff there is fully supported by Ubuntu.

Also, run the Software Updater if you haven't already as first cab off the rank. That will get things totally up to date. ;)

---

### Post by brennon3 on 2015-01-03
Thanks. Reading into Grub Customizer now. 

Thanks again for the help.

---

### Post by brennon3 on 2015-01-03
Edit - Resolved.

---

### Post by Bucky Ball on 2015-01-03
A pleasure. I like it when a plan comes together, even when it's an improvised one! ;)

You might want to have a look in Gparted (if it's not installed by default install it from Software Centre) and check how much unused space you have on /. That would be your main future possible issue at this stage. I'd keep an eye on the unused space as you start installing stuff as you need/want it.

If you do install something and don't like, uninstall it from Software Centre to save space. There are also a few commands you can use in a terminal:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
```

... Should clean things us some. 

Please follow the second link in my signature to mark the thread as solved. This won't close the thread, just helps future travelers. ;)

---

