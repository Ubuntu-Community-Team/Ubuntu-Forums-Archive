---
title: "some question which i want know before install"
date: 2014-12-01
forum: New to Ubuntu
---

### Post by Sakanage on 2014-12-01
Well I have some question about the system , but i already installed it before and already took a look in that , `cause i`m looking to change my main operating system from windows to some linux and which most interested me was ubuntu since first look in that . Well if u guys can answer some question to me i'll be very grateful .
[COLOR=#800080]
1 - Need know some programmer language since somethings things are intalled by commands

2 - If i want make a Multi-OS have a medium-high chance to damage the hard disk (i know all these operation have risk and keep in my mind all the time when i made anything with hard disk)

3 - well most linux use OpenGL since i searched a little with about it but have any kind to use DirectX to use with games for exemple

4 - related with the last question have wine in Ubuntu to "Emule" windows progams but it really work?

[/COLOR]well if anyone can help me i`ll be very grateful :D

---

### Post by newbie-user on 2014-12-02
1. You don't need to know any programming languages. Most common terminal usage can be found online and are usually simple commands.
2. Make at least two partitions on your hard drive. Install Windows first into one partition, and then install Ubuntu later onto the second partition.
3. You can install DirectX using Wine.
4. Some Windows software will run well in Wine, while others will not. Check the appdb at winehq.org to see which programs will work.

---

### Post by sudodus on 2014-12-02
> **Sakanage said:**
> [COLOR=#800080]
2 - If i want make a Multi-OS have a medium-high chance to damage the hard disk (i know all these operation have risk and keep in my mind all the time when i made anything with hard disk)
[/COLOR]

Installing operating systems and editing partitions are risky operations. You should always ***backup everything important*** before doing such things, at least your personal files (documents, pictures, ...) but it might be a good idea to make a compressed image of the whole internal drive before starting with the risky operations. Clonezilla can be used for that purpose. There are several tools for more or less complete backups.

1. Most of the time it works well to shrink the Windows partition with Windows tools.

2. Boot from a separate drive, for example the Ubuntu desktop install DVD/USB drive (created from the Ubuntu ISO file).

3. Create partitions with ***gparted***

4. Install: at the partitioning window you should select ***Somthing else***, which may look more complicated, but gives you much better control of what will happen.

---

### Post by Gordonbp531 on 2014-12-02
> **sudodus said:**
> 

1. Most of the time it works well to shrink the Windows partition with Windows tools.


If the machine has Windows 8 on it then the received wisdom is to always use the tools available in Windows to create the unallocated space - using GParted has been known to bork the Windows install for some reason...

---

### Post by Impavidus on 2014-12-02
1: The command line has nothing to do with programming – although you can program in the language understood by the command line if you wish so. In fact, you rarely need the command line, and only to get low-level access to fix thing if they are broken. On these forums we like the command line, because it's easier to give instructions and pass output that way, using forum posts as an interface.

2: Read the excellent advice by sudodus.

3: DirectX is designed for Windows. Graphical programs (including native Linux games) running on Ubuntu have been designed to use OpenGL.

4: Wine is a compatibility layer to make Windows programs run on Linux. It works very well for some applications and not at all for others. Check [https://appdb.winehq.org/](https://appdb.winehq.org/) to see whether other people had success with your favorite applications. In general your best hope is finding native Linux alternatives.

---

### Post by grahammechanical on 2014-12-02
> [COLOR=#800080]2 - If i want make a Multi-OS have a medium-high chance to damage the hard disk (i know all these operation have risk and keep in my mind all the time when i made anything with hard disk)[/COLOR]

There is very little chance of damaging the hard disk. The risk is to any data, including operating systems, already on the hard disk. And the greatest hazard is from us (the user) instructing the installer to use the entire disk or to install Ubuntu in the wrong partition.

I have two hard disks. Both disks have multiple partitions and I often install different versions of Ubuntu for testing purposes. I am not experiencing damage to the hard disks. I am also very careful about the instructions I give to the Installer program to make sure that my carelessness does not cause data loss.

Will you be dual booting with Windows 8? Please read this.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

