---
title: "To SWAP or not to SWAP?"
date: 2017-02-15
forum: New to Ubuntu
---

### Post by lysander6662 on 2017-02-15
Apologies for my third thread and for what will most likely turn into a barrage of questions, but I'll try to keep it modest. 

I've been thinking about partitioning my main 70GB SSD. Now I know that's not a lot of space to work with, but I've had it for a few years and it's proved ample. Let's just say I've got good at deleting stuff. I think it would be a good idea to partition the drive in case I screw up the installation [which I will be careful not to do], so I can be up and running again.

My questions are:

1. Can I partition the drive while I'm using it? Do I have to reinstall the OS with the new partitions or can I create them without doing so?
2. Is it necessary to have a SWAP partition? I'm not sure if I need it, RAM never seems to be an issue.
3. I take it all I have at the moment is a /home partition. As far as I understand, Linux does not label drives C, D, E etc but uses the / prefix, is this correct?
4. I understand that if I have a home, SWAP, data partition, they can all 'talk to each other', i.e. I can put stuff on the data partition easily from the /home. How do I set this up or does it happen automatically once the partitions are in place?
5. In the event that I screw up the installation, how do I get things up and running again? It is just a matter of reinstalling Ubuntu back on the /home partition from my flash drive?
6. I am considering dedicating about 20GB to /home and 50GB to data [without SWAP]. Does this sound reasonable or would it be better to adjust these sizes?

Thank to everyone here for the great help so far.

---

### Post by termibuntu on 2017-02-15
1. no, you cant partition it while your using it. the reason is because the os will be using it. 2. it is not necessary to use a swap partition. the only thing a  swap partition does is make your computer run faster whith more peformance. 3. yes, linux does use the / prefix and names it ramdomly. 4.  it does it automatically. 5. yes, you reinstall and use the same partitions! like i always say, if something os related happends, just reinstall the os! 6.yes and no. yes because you keep them separated. no because every ubuntu upgrade you do, will take up more disk space, and potentialy, the system may take up the whole 20gb space, though if you have a ubuntu live usb or disc, you can always resize the partitions with gparted! i hope this helps with that list of questions. :)

---

### Post by RobGoss on 2017-02-15
You might want to limit how many question you add to a thread it's kind of hard to answers them all, I try to answer as much as I can, your questions are always welcome

Question #1
You cannot partition your drive while using it, you'll have to run the live desktop and use gparted to do any partitioning

Question #2
Having a swap partition is a good thing to have if you use hibernation for your system it will help your system from lagging, some may say it's not  necessary to have one but that will be clearly up to the user

Question #5
That would depend how screwed up the system gets if something goes wrong. In most cases things can be fixed with the help from this community 

Question #6
Seeing you don't have a lot of space to work with I would give more space to the home directory this is were I feel it will be needed

---

### Post by The Cog on 2017-02-15
> 1. Can I partition the drive while I'm using it? Do I have to reinstall the OS with the new partitions or can I create them without doing so?
It can be done with extreme care. Sometimes. But it is far easier to boot a USB stick, try out rather than install, and use gparted to edit the partitions.
> 2. Is it necessary to have a SWAP partition? I'm not sure if I need it, RAM never seems to be an issue.
In that case, probably not.
> 3. I take it all I have at the moment is a /home partition. As far as I understand, Linux does not label drives C, D, E etc but uses the / prefix, is this correct?
You have to have a / (called the root) partition, and that is probably all you have. I always allocate 20-30G for the / partition, and lots of space for a separate home partition. The home partition holds the user's home directories (in /home) of course, which contains all their files and personal application settings. I would regard the home partition as what you refer to as a data partition.
> 4. I understand that if I have a home, SWAP, data partition, they can all 'talk to each other', i.e. I can put stuff on the data partition easily from the /home. How do I set this up or does it happen automatically once the partitions are in place?
Swap (if you have it) is not directly visible to the users, it's just used by the OS as temporary memory overflow storage. If you set up as I do with a / partition and a /home partition, they all look like one big filesystem. It's just that all the files within the /home folder are stored on a different partition to everything else which is stored in the / partition. 
> 5. In the event that I screw up the installation, how do I get things up and running again? It is just a matter of reinstalling Ubuntu back on the /home partition from my flash drive?
I regularly install updated OS versions. I always format and install to just the / partition which wipes and reinstalls all the OS. You can tell the installer to use the home partition as /home **but not format it**.  When the home partition mounts, the original contents of the /home folder (the almost empty one created in the root partition) become invisible and are replaced with the contents of whatever is stored in the home partition. This is what mounting is: replacing the contents of an existing folder with the contents of a separate disk partition. It' s not a separate entity like D: in windows, it's a completely seamless part of the directory/file structure that you see. When you reinstall, you just replace the system files on the root filesystem - you don't overwrite the home partition. 

Actually, I always install onto just the root partition, and only after the new install is working to my satisfaction, I mount the home partition into the /home folder.
And I use two partitions for / and alternate between them so I always have a copy of the previous OS version to fall back on if the new one doesn't work, but you don't really need to do that if space is tight. 
> 6. I am considering dedicating about 20GB to /home and 50GB to data [without SWAP]. Does this sound reasonable or would it be better to adjust these sizes?
Sounds about right to me.

---

### Post by lysander6662 on 2017-02-15
OK great, thanks for the answers and sorry for all the questions. 

In response

1 - Understood, I will use GParted from a USB. Presumably I can create SWAP, data and home with it.
2 - Not sure, may not include SWAP since I don't have speed issues. And any change would be incremental.
3 - Understood - seems I has getting confused between root and home. 
4 - Understood. That's very clear and well explained, thank you.
5 - Understood and thanks, this community is very helpful.
6 - OK, seems that 20GB for root and 50GB for home would work

So after partitioning I would just have root [20GB] and home [50GB] partitions?

EDIT: I posted the above having not read Cog's responses, updated now.

---

### Post by termibuntu on 2017-02-15
though remember! if you need a bigger root partition, you can always boot from an usb and use gparted to move/resize the partition, if you later dont have enough space. hope this helps :)

---

### Post by howefield on 2017-02-15
> **lysander6662 said:**
> Apologies for my third thread and for what will most likely turn into a barrage of questions, but I'll try to keep it modest.

Don't apologise for asking questions, it's the reason for the forums existence :)

> Can I partition the drive while I'm using it? Do I have to reinstall the OS with the new partitions or can I create them without doing so?

You'll need to use a Live media so the disk to be partitioned is unmounted, ie not in use. The partition editor "Gparted" comes with the Live media so you'll can use that to resize and create new partitions. Just remember to back up all important data, although it is normally safe enough you never know what might happen during such a potentially risky operation.

> Is it necessary to have a SWAP partition? I'm not sure if I need it, RAM never seems to be an issue.

It's probably advisable to have a swap partition although with enough RAM it'll likely never get used unless you hibernate the computer or have a misbehaving application. The swap can be on a separate disk. For info, Ubuntu is moving to using swap files instead of swap partitions when 17.04 is released.

> I take it all I have at the moment is a /home partition. As far as I understand, Linux does not label drives C, D, E etc but uses the / prefix, is this correct?

/ is the root of your file system. Drives in Linux tend to be sdX, where X is the drive letter. First disk might be sda with the first partition on it being sda1, second partition on the same disk sda2 and so on. 

> I understand that if I have a home, SWAP, data partition, they can all 'talk to each other', i.e. I can put stuff on the data partition easily from the /home. How do I set this up or does it happen automatically once the partitions are in place?

If you are installing afresh you would mount the appropriate partitions during the installation process which would add them to your fstab file (tells the system which disks to mount during the boot process).

If you create extra partitions after the install you would either have to mount them manually after booting or more preferably add them to your fstab file which is easy enough and involves getting the UUID for the disk and adding a line or two to the /etc/fstab file.

An example of an entry in the fstab file for a disk mounted at installation...

```
# /Data was on /dev/sda3 during installation
UUID=d09a686d-f34a-4ebf-8014-b1cd13ccccc1 /Data           ext4    defaults        0       2
``` 

> In the event that I screw up the installation, how do I get things up and running again? It is just a matter of reinstalling Ubuntu back on the /home partition from my flash drive?

You would probably install into the / partition and mark it for formatting and mount the Data partition but not mark it for formatting. For info, installing over an existing Ubuntu installation but not marking it for formatting will leave your /home intact.

> I am considering dedicating about 20GB to /home and 50GB to data [without SWAP]. Does this sound reasonable or would it be better to adjust these sizes?

Your base OS installation is going to be in the region of 6 to 8 GB - so you need that plus whatever you think you'll need for installing applications. 20GB sounds minimal but very reasonable.

---

### Post by lysander6662 on 2017-02-15
Great advice, thank you very much. I intend just to create a partition for /home and then resize / to about 20GB or so. It should be a straightforward operation. 

In the past few days I've unmounted my other hard drives - by pulling out the SATA cables just in case I do something wrong during install and mess them up! It would be nice not to have to do that anymore but I'm concerned about losing data on them during reinstalling the OS. But since I'm not reinstalling anything today, just partitioning, it shouldn't be a problem.

I'll attempt partitioning tonight. If I don't know what I'm doing I'll take a photo/screenshot and post it here.

---

### Post by HermanAB on 2017-02-15
Howdy,

If you don't have swap space and the system needs it, then the machine will slow down and stop.  It is therefore better to always have swap space.  

Note that you don't need to have a swap partition.  A swap file works just as well.  Read the swapon man page for details.

---

### Post by RobGoss on 2017-02-15
This may help you with the concerns you may have about adding a swap partition [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by The Cog on 2017-02-15
> **lysander6662 said:**
> In the past few days I've unmounted my other hard drives - by pulling out the SATA cables just in case I do something wrong during install and mess them up! It would be nice not to have to do that anymore but I'm concerned about losing data on them during reinstalling the OS. But since I'm not reinstalling anything today, just partitioning, it shouldn't be a problem.


Noooooooo!!!
Make backups! Always have backups. 

Partitioning should be easy but any error, by human or machine, often loses everything.

Backup, backups, backups.
</lecture>

---

### Post by RobGoss on 2017-02-15
+1 The Cog

Partitioning can be problematic and in some cases you can also wipe your entire system out

It is always a good idea to backup your files and data, just in case something goes wrong

---

### Post by lysander6662 on 2017-02-15
Thank you all, yes, backups! I have backed up my most important work. I pulled the SATA leads out for extra security but realise this is not the best way!

I am now in the live session and on GParted. This is the snapshot of my SSD

[img]http://i.imgur.com/WyRYr1Y.png[/img]

I got a message saying I have to unmount the main drive first, is this standard?

Can anyone let me know what the three partitions are here?

---

### Post by The Cog on 2017-02-15
Sorry, I don't see the screenshot. Can you list the table of partitions below the pretty graphic? Or better still, run this and post the output.
```
sudo parted -l
```

---

### Post by lysander6662 on 2017-02-15
OK, I will try. Is this right?

```
lysander@psychopig-xxiii:~$ sudo parted -l
[sudo] password for lysander: 
Model: ATA SAMSUNG HD160JJ (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      1049kB  106MB  105MB  primary   ntfs         boot
 2      107MB   160GB  160GB  extended               lba
 5      107MB   160GB  160GB  logical   ntfs




Model: ATA Hitachi HDP72503 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End    Size   Type      File system  Flags
 1      8225kB  320GB  320GB  extended               lba
 5      8258kB  320GB  320GB  logical   ntfs




Model: ATA INTEL SSDSA2M080 (scsi)
Disk /dev/sdc: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 


Number  Start   End     Size    Type      File system  Flags
 1      1049kB  512MB   511MB   primary   ext2         boot
 2      513MB   80.0GB  79.5GB  extended
 5      513MB   80.0GB  79.5GB  logical                lvm




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-swap_1: 5365MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system     Flags
 1      0.00B  5365MB  5365MB  linux-swap(v1)




Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/ubuntu--vg-root: 74.1GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 


Number  Start  End     Size    File system  Flags
 1      0.00B  74.1GB  74.1GB  ext4

```

---

### Post by The Cog on 2017-02-15
That's messy. Your linux drive is sdc. 
Unfortunately you have an LVM based installation, which makes things more complicated.

The first partition sdc1 is a boot partition, and just contains the system bootloading code.
The second partition sdc2 is an "extended" partition which just acts as a container for "logical" partitions. This fills all of the rest of the disk.
The third partition sdc5 is a "logical" partition that completely fills the container sdc2. This is formatted as LVM - Logical Volume Manager.

Here's the complicated bit. LVM allows you to group one or more physical partitions (just sdc5 in your case) together. This group can then be divided into one or more "logical volumes" that the OS sees as separate drives. In this case, the group has been divided into two logical volumes - a 5G swap volume and a 74G root volume. 

I *think* you should be able to use a graphical tool called system-config-lvm from the live CD to make the changes you want. I've never used it, but from a bit of googling, I think you will need to use these two commands to get it running, after booting up a live CD:
```
sudo apt install system-config-lvm
sudo system-config-lvm
```

---

### Post by lysander6662 on 2017-02-16
Indeed, I know that it's not quite the tidiest of setups, seems to work very efficiently though. Could you elaborate on what is messy [and in what way]?

I think this is going to be a steady and slow process. But there's no rush. I chose LVM as an option on install because it seemed like it would be useful later on down the line - not that I knew *exactly* what it was. Kind of a shame it will complicate things at this point. 

I'll open up system-config-lvm and post a screenshot here [weird that you couldn't see the screenshot, I'll post a link too if needs be]. I could just reinstall Ubuntu without LVM but I think it would be useful to learn doing it the LVM way for now.

---

### Post by lysander6662 on 2017-02-16
Unfortunately Ubuntu live couldn't get system-config-lvm. I kept getting a message saying it was unable to install the package. 

That's no big problem at the moment though. I am considering rolling back to 14.04 for the better graphics drivers for my ATI card, and in the process I'll just not choose LVM when installing. My only question is - are superior ATI drivers not on the cards at any point soon [they don't seem to be for 17.04]? I've read good things about 14.04 as a version. Or is it worth sticking with 16.04 for now?

EDIT: I find it rather amusing that Ubuntu is the only distro officially supported by Steam yet since 14.04.5 they don't have proper ATI drivers [might be why they only recommend 12.04].

---

