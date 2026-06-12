---
title: "how do I change name and ownership on a 3ed hard drive"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by EZZ9 on 2014-04-03
I am new so if I get the wording wrong sorry. I did this once before a long time ago, but it took me days to find the info on the web and to get it right. 
I have installed a 3ed hard drive for video storage, I have set it to ext4 with gparted that's about all. I still need to change its name and change the ownership of the hard drive, so I can place files on it. Can anyone tell me what I need to do or send me the right page off the web. Thank you

---

### Post by TheFu on 2014-04-03
You need to decide where you want it "mounted", that may mean creating a new directory.  Then modify the /etc/fstab as needed for your situation, then run **mount -a**
After mouting, use sudo chown/chmod as needed.

---

### Post by EZZ9 on 2014-04-03
I though mount was the word for turn on? You lost me on that one.

---

### Post by slickymaster on 2014-04-03
Plug in the drive and you should see it appear as a folder in /media, which you will be able to see either using nautilus or with the following command:```
ls /media
```
Make a note of the folder name (/media/name) and then run this command in terminal```
sudo chown username:username /media/name
```
Change username:username for your own username, of course.

_**EDIT:**_
I am assuming you're talking about an external hard-drive. _In case you aren't, then you should proceed with TheFu's advice._

---

### Post by EZZ9 on 2014-04-03
The hard drive is inside the tower dose that matter?

---

### Post by EZZ9 on 2014-04-03
desktop:~$ ls /media
bob  mynewdrive

Tells me nothing? wrong info

---

### Post by EZZ9 on 2014-04-03
sudo chown username:username /media/name
my username is bob so I go
sudo chown bob:bob /media/  so what is (name) on the end get changed to?

---

### Post by slickymaster on 2014-04-03
> **EZZ9 said:**
> The hard drive is inside the tower dose that matter?

Yes, it matters. There's a big difference in the way your system sees and deals with internal drives and external ones.

In your case, and being your hard-drive an internal one, you should proceed as TheFu advised you to do, i.e., firstly decide where should it be mounted. Ubuntu mounts partitions in /media by default, so if you want the partition to be mounted in **/media/MyDrive**, you will need to manually create this folder since fstab will complain if it's not there, so make sure that the folder isn't being used already, and run```
sudo mkdir /media/MyDrive
```Next, you'll need to decided with what options should it be mounted with and you'll have to specify permissions. To specify the permissions, you merely need to declare three things: UID, GID, and umask.
**uid=####** specifies which userid should own the files on the partition. e.g. uid=1000 means that the user with the id "1000" should own the files. You can find out your UID by opening a terminal and running ```
echo $UID
```
**gid=####** specified which groupid should own the files on the partition. e.g. gid=1000 means that the group with the id "1000" should own the files. Ubuntu normally creates a group for every user, with the same ID as the UID, so you can probably use your UID as the GID. However, you can get a list of groups by running in a terminal, ```
cat /etc/group
```
**umask=UGO** is the most important of the three options; it specifies what the permissions will be for the user, the group, and everyone else. The numbers used here need to be between 0 and 7, anything else will probably cause an error.

The next time you boot up, or the next time you run```
 sudo mount -a
``` the partition should be mounted where you want it, with the permissions you want it to have.

---

### Post by oldfred on 2014-04-03
If you prefer to mount in /media use that instead of my example with /mnt/data. Lots of discussions over which is better and it is not critical.

 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

Then unmount and edit fstab so it is a permanent mount.
      
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

This example uses /media/Data, note that Data is different than data as case in Linux matters. Again you can use /mnt/data, /media/Data or whatever you like perhaps /media/myVideos

 fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

   ** To find the correct UUID for your partitions:
sudo blkid -c /dev/null -o list
** You will have to create the mount point yourself, for example:
sudo mkdir /media/WinD
and/or 
sudo mkdir /media/Data
** Then add the template with the correct UUID and mount point to fstab:
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab

   ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

Note:
$USER is internal variable.
in terminal if you run this you will see its value.
echo $USER

---

### Post by EZZ9 on 2014-04-03
Sounds easy, but
 Decide where should it be mounted “I have no clue what that means”
 

 If you want the partition to be mounted in **/media/MyDrive**, you will need to manually create this folder  “where?”
 

 Make sure that the folder isn't being used already “how?”

 

 I have the ID 1000 “what and where and how do I put and use it?”
 

 **umask=UGO** is the most important of the three options; it specifies what the permissions will be for the user, the group, and everyone else. The numbers used here need to be between 0 and 7. “lost me I am the only one using this computer”

---

### Post by oldfred on 2014-04-03
You are actually creating folder with the name you want where you want it.

sudo mkdir /media/MyDrive 
That would create a new folder in the /media folder (which must exist, but it is a default so it does). And you have a new sub-folder MyDrive.
You then can give yourself ownership and permissions to use it. Unless you have other users you should not have to worry about groups. Your default user of 1000 will suffice. 

Linux is a multiuser system by design so it has some more complicated ways to do things. But that also gives better secuity by default. Windows was designed as a single user system and that is why it has more secuity issues by default.

---

### Post by EZZ9 on 2014-04-03
oldfred when you start off with the word if, that dose not work for me and I have no clue on what you wrote. In the beginner area, too much computer talk and not enough English. Just need the basics.

---

### Post by EZZ9 on 2014-04-03
oh the hard drive is dev/sdb1
Don't know why it is the 3ed one, but that's where it is.

---

### Post by TheFu on 2014-04-03
> **EZZ9 said:**
> Sounds easy, but
 Decide where should it be mounted “I have no clue what that means”

It is just an empty directory - can be anywhere you like.

> **EZZ9 said:**
> 
 If you want the partition to be mounted in **/media/MyDrive**, you will need to manually create this folder  “where?”
THAT is a complete path - if this confuses you, perhaps starting with an easier task - like how to make a directory is needed?
 
> **EZZ9 said:**
>  Make sure that the folder isn't being used already “how?”
 If there is anything inside the folder, then it is already being used.
 
> **EZZ9 said:**
>  I have the ID 1000 “what and where and how do I put and use it?”
  That ID isn't needed in 99.999999999999% of the situations on Linux.  You do need to know the userid (name) and which groups that ID is a member of - the "id" command will tell you that data.

Unless this new drive will have a non-Linux file system. Then all sorts of extra complexities happen. Best to just  use ext4 and be done.
 
> **EZZ9 said:**
>  **umask=UGO** is the most important of the three options; it specifies what the permissions will be for the user, the group, and everyone else. The numbers used here need to be between 0 and 7. “lost me I am the only one using this computer”

Just because you are the only person on the computer, that doesn't change the FACT that Linux is a multi-user OS. This is NOT MS-windows. Expecting Linux to behave like MS-Win will just make you unhappy.

At this point, you **NEED** to learn about file and directory permissions. This [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions) will explain enough to get started. This is central to everything on Linux, so learn it sooner than later.

---

### Post by oldfred on 2014-04-03
What name do you want for this?
In Windows it just would be d: or e:, but in Linux we can give it a name that means something. Either just /media/data or /media/myVideos or whatever name you want.

Post these by copying & pasting from terminal
sudo parted -l
sudo blkid -c /dev/null -o list
 cat /etc/fstab



Then I can give you the modified commands that I posted in #9 for you just to copy & paste. All the commands you need are there but do require you to edit them with the name you want.

---

### Post by EZZ9 on 2014-04-04
6 hours on the web and I found how to change the name of the hard drive. Still need a more detailed user friendly instruction for people that don't know what they're doing, to change the ownership. Anyone?

---

### Post by EZZ9 on 2014-04-04
I have always used Ubuntu it is the best! I never used windows so when comparing it to that I have no clue what you're talking about. 
I have only had a computer for 9 years now. 7 of which I just turned it on used it, then turn it off. 
Old guy here so when using computer lingo, I get lost quick, lol, sorry.
Have changed the name of the hard drive to "vidshows" my user name is "bob"

bob@bob-desktop:~$  sudo parted -l
[sudo] password for bob: 
Model: ATA ST3808110AS (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  79.0GB  79.0GB  primary   ext4            boot
 2      79.0GB  80.0GB  1063MB  extended
 5      79.0GB  80.0GB  1063MB  logical   linux-swap(v1)


Model: ATA ST380817AS (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  80.0GB  80.0GB  ext3


Model: ATA WDC WD7500AADS-3 (scsi)
Disk /dev/sdc: 750GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      32.3kB  750GB  750GB  primary  ext2


bob@bob-desktop:~$ sudo blkid -c /dev/null -o list
device      fs_type label    mount point     UUID
---------------------------------------------------------------------------------
/dev/sda1   ext4             /               a0833ad3-f9a6-4f3a-accb-909f0b814b3b
/dev/sda5   swap             <swap>          b4b952e2-ec75-4c88-b51f-7f67c794a2cd
/dev/sdb    ext3    vidshows /media/bob/vidshows 9de58aba-48f2-4f1b-a1c7-89ff78b7ec87
/dev/sdc1   ext2    my_data  /media/bob/my_data 4818bcbe-5b1f-47c0-942b-9530e0f00648
bob@bob-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a0833ad3-f9a6-4f3a-accb-909f0b814b3b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b4b952e2-ec75-4c88-b51f-7f67c794a2cd none            swap    sw              0       0
UUID=4818bcbe-5b1f-47c0-942b-9530e0f00648 /media/bob/my_data ext2 defaults 0 2

bob@bob-desktop:~$ 

Hope this helps, how I did it last time on the other hard drive, only the computer god can know. There was a step by step page on the web I had followed along with, but things change so fast and is probably out of date and gone.
 I thank you all for helping me, as I slowly beat my head on my desk.

---

### Post by EZZ9 on 2014-04-04
I can see it is this one, that's about it off of all that.

Model: ATA ST380817AS (scsi)
Disk /dev/sdb: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

---

### Post by oldfred on 2014-04-04
Your sdb drive with "loop" shows no partitions and just the extended partition. 
Did you have any data on the sdb drive? If not use gparted on live installer or since not your drive with your install you can use gparted from your install. Its just you cannot use gparted on the drive that is your install as all partitions have to be unmounted.
It looks like the label for vidshows is the entire drive. That is why it is shown as loop. 
You need to create partition(s) with format ext4 or ext3 and give the partition a label vidshows in gparted.
Then you can do the same command as below using vidshows instead of my_data

You show you have sdc1 mounted in fstab as /media/bob/my_data.

If you still have permission or ownership issues:

 sudo chown -R $USER:$USER /media/bob/my_data
        sudo chmod -R a+rwX,o-w /media/bob/my_data

      
 # Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.

    That means that you have permissions, but files will not be executable unless you manually change them to be executeable  which is usually not required.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

$USER is bob. I used $USER to just make it generic
if you type this into terminal you will see who is the user.
echo $USER

---

### Post by EZZ9 on 2014-04-06
We will start here how do I "need to create partition with format ext4 or ext3 and give the partition a label vidshows in gparted."?
I am not messing with "my_data" that one is working great. I want the other one to do the same. Everyone is telling me what I need to do. But I'm looking for how to do it. Like I said at the start of this I'm a beginner, don't know what is a loop or 775 0r most of everything said sounded great but where is the how to? I'm looking for step by step instructions.

---

### Post by EZZ9 on 2014-04-06
I found this video it is old, but it's what I want to do, looks easy on the old system 
[h=1]Allow Read Write & Change Drive Name - Ubuntu 9.10[/h]
[http://www.youtube.com/watch?v=k2AyroXHTSI](http://www.youtube.com/watch?v=k2AyroXHTSI)
But when he says click up on the arrow at 1 min mark. I have no arrow and all the tools he has on the top I do not have. What is he using or opening it with?
Still beating my head on my desk.

---

### Post by oldfred on 2014-04-06
That is the old version of Nautilus.

That is just going one level up in your path.
In Nautilus (if Ubuntu not a flavor) you now see each part of path as a button above the files listing. You then can click on where on the path you want to be. Saves hitting up button twice if you want to go up two levels.

But your main issue why none of our directions on setting ownership & permissions are not working is that you do not have a partition, just a formatted drive. While in some cases you can just use a formatted drive, it is like a very large floppy disk or CD. Almost all tools require partitions, so mounting and using a drive without a partition is a problem. 
You need to create a partition on sdb like you have on sdc for my_data. Use gparted and create a new partition, if you have copied any data into sdb, back that up first. Also then label partition to be your vidshows while in gparted. I would use ext4 as format.

         GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)


 gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

---

