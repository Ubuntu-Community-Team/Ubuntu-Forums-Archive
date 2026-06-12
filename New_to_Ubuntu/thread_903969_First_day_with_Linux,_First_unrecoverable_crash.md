---
title: "First day with Linux, First unrecoverable crash"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by J0hnnyBr@v0 on 2008-08-28
OK...so with all my poking around, I am sure it was something I F'd up.  But now I have a couple of questions.

1.  I reinstalled Ubuntu and asked it to use the entire disk.  But now the old version of Ubuntu is still hanging around.  How do I recapture those partitions as blank space?  I know within BackTrack there was a program I ran to do it...is there one within Ubuntu?

2.  Backing up the system.  Is there a way to backup the system once a week or so in case I have another such crash (which with my lack of expertise is 99.999%)

3.  Can't get VMWare to install.  When I try to run the install-vmware.pl nothing happens.  So I installed VirtualBox from JAVA's website and I couldn't created a VHD for Vista, or XP, kept telling me I didn't have the proper module.  Which module is required for Windows OS?  There is a list of like 50 or so in Synaptic and I don't want to load all of them.

Hey...I'm learning...learn quickly when you have to redo a bunch of things

Thanks to anyone who can further my knowledge!!

Eric
](*,)

---

### Post by nicedude on 2008-08-28
To get back old partition you are not using just use the partition editor to delete the partition in question and you can resize your current partition to take that empty space or make a new data partition to use it again.

To find the partition editor go to top menu bar System -> Administration -> Partition Editor

As to the Vmware question I have no idea as I don't use it, for system backup there are programs in the repositories to do that just search for system backup by name and description and see what you find.

---

### Post by J0hnnyBr@v0 on 2008-08-28
> **nicedude said:**
> To get back old partition you are not using just use the partition editor to delete the partition in question and you can resize your current partition to take that empty space or make a new data partition to use it again.

To find the partition editor go to top menu bar System -> Administration -> Partition Editor

Partition Editor is not showing up there...I'll look in Synaptic for the install??

Thanks,
Eric

I found parted is installed, but is that a CLI that I have to use?  Cannot find any other partition editing, nothing in any of the menus anyway...

---

### Post by robert shearer on 2008-08-28
> **J0hnnyBr@v0 said:**
> OK...so with all my poking around, I am sure it was something I F'd up.  But now I have a couple of questions.

1.  I reinstalled Ubuntu and asked it to use the entire disk.  But now the old version of Ubuntu is still hanging around.  How do I recapture those partitions as blank space?  I know within BackTrack there was a program I ran to do it...is there one within Ubuntu?

2.  Backing up the system.  Is there a way to backup the system once a week or so in case I have another such crash (which with my lack of expertise is 99.999%)

3.  Can't get VMWare to install.  When I try to run the install-vmware.pl nothing happens.  So I installed VirtualBox from JAVA's website and I couldn't created a VHD for Vista, or XP, kept telling me I didn't have the proper module.  Which module is required for Windows OS?  There is a list of like 50 or so in Synaptic and I don't want to load all of them.

Hey...I'm learning...learn quickly when you have to redo a bunch of things

Thanks to anyone who can further my knowledge!!

Eric
](*,)


Point 2  backup.  

You could make a live cd/dvd of your existing installation.
This could then be used as an re-install disk. 
It would be like installing from the original Ubuntu disc only with the programs, settings and updates you have chosen to use.

See these links for more..

[http://www.remastersys.klikit-linux.com/](http://www.remastersys.klikit-linux.com/)

[http://www.ubuntugeek.com/creating-c...mastersys.html](http://www.ubuntugeek.com/creating-c...mastersys.html)

[http://loscompanion.com/forums/index.php?topic=4249.0](http://loscompanion.com/forums/index.php?topic=4249.0)

[http://loscompanion.com/forums/index.php?board=58.0](http://loscompanion.com/forums/index.php?board=58.0)

---

### Post by nicedude on 2008-08-28
the actual program is called "parted" but I would say I like "gparted" better but they both do the same thing.

You can install with this command

sudo apt-get install gparted

and then just 

sudo gparted

to use it.

---

### Post by panhandle on 2008-08-28
As for more information on backups, there is considerable information on this site.

The following is an often-used link with a choice of tutorials:

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

---

