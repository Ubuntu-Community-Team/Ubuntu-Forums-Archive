---
title: "Hard Drive Issue"
date: 2016-04-14
forum: New to Ubuntu
---

### Post by anon24 on 2016-04-14
Hello!

This is my first install of Ubuntu or opensource Linux of any kind. I'm not an experienced coder. I have messed around in the terminal here and there. I dabbled in Python and managed to get it to print screen "Hello, world!

I've gone back and forth between Mac and Windows. Most recently, I had Windows 10. I had heard good things about Ubuntu and thought that I'd give it a try.

I have an MSI GS-70. I did a clean install, no Windows partition. Basically, I got my supplementary SATA drive to where it finally showed up as an external drive, it initially wouldn't show up under system monitor. I formatted it as ext4, then, for some dumb assed reason, I decided to try the encrypted version of ext4. Well, now I can't even access the drive...

It's an internal TB drive. It's supplementary to the three 120GB SSD that I have in RAID. I was surprised that Ubuntu kept these three SSD perfectly in RAID. I just need to get this drive out of encrypted mode, back into ext4 and reading as a supplementary internal drive. Should I just do a clean reinstall?

I would appreciate any help! Thanks!

---

### Post by yancek on 2016-04-14
I don't use encryption but as I understand it, you need a password/passphrase to use to decrypt.  Otherwise, it  would be pretty pointless.

---

### Post by grahammechanical on 2016-04-14
Did you install Ubuntu on to the external drive? Do you get a Grub boot menu? Can you load Windows 10 from it? What happens when to load Ubuntu? Are you aware of this information?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you re-install make sure the live session is loading in EFI mode. Then Ubuntu will be installed in EFI mode as well. Which is required because Windows 10 will be installed in EFI mode.

Regards.

---

### Post by anon24 on 2016-04-14
> **grahammechanical said:**
> Did you install Ubuntu on to the external drive? Do you get a Grub boot menu? Can you load Windows 10 from it? What happens when to load Ubuntu? Are you aware of this information?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you re-install make sure the live session is loading in EFI mode. Then Ubuntu will be installed in EFI mode as well. Which is required because Windows 10 will be installed in EFI mode.

Regards.

I do not have Windows in any capacity on the PC anymore. I wanted every bit of Windows to be wiped clean. The three SSDs are in RAID and are my main internal drive and Ubuntu is installed on them. 

Ubuntu loads up fine. I just can't access this internal SATA drive and need a bit of guidance. I'll check out that link and get back to you. Thank you guys for the quick responses!

---

### Post by anon24 on 2016-04-14
Yea, I know the password. The problem is that I don't know how to even get the system to prompt me for the password so that I can access the drive. I can't get it to mount in the terminal and it doesn't show up in the home window.

---

### Post by oldfred on 2016-04-14
I do not know nor use encryption.
But what is it, full drive LVM with encryption or more like an encrypted /home?

While discussing resize, first half is mounting.

 How to: Mount & Resize an Encrypted Partition (LUKS) also mount for repairs
[http://ubuntuforums.org/showthread.php?p=4530641](http://ubuntuforums.org/showthread.php?p=4530641)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
How to Resize a LUKS Encrypted File System.
[http://ubuntuforums.org/showthread.php?t=726724](http://ubuntuforums.org/showthread.php?t=726724)
sudo apt-get update && sudo apt-get install lvm2 cryptsetup
df -h
sudo blkid
sudo fdisk -l
sudo pvdisplay
sudo lvdisplay
mount
sudo vgscan --mknodes
sudo vgchange -ay

---

### Post by anon24 on 2016-04-14
Ok, so I figured out that restarting my machine made the encrypted drive show up. So, I reformatted it to just regular ext4. Now, I'm having the problem that I was having initially. The drive shows up in the terminal, but not anywhere graphically. I want this drive to be always accessible as an internal drive from the File Window... Since it is an internal drive. 

I tried to mount it: 

sudo mount /dev/sdc /media/secondaryhd 

In response, it says, "wrong fs type, bad option, bad superblock, on /dev/sdc, missing codepage or helper program, or other error."

I tried the lsblk command to see what other info I could gather up.

~$ lsblk
NAME                        MAJ:MIN RM   SIZE RO TYPE   MOUNTPOINT
sda                           8:0    0 119.2G  0 disk   
&#9492;&#9472;isw_bbaihhhjf_MSI_RAID    252:0    0 357.7G  0 dmraid 
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID1 252:1    0 512.6M  0 part   /boot/efi
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID2 252:2    0 341.3G  0 part   /
  &#9492;&#9472;isw_bbaihhhjf_MSI_RAID3 252:3    0  15.9G  0 part   
    &#9492;&#9472;cryptswap1            252:4    0  15.9G  0 crypt  [SWAP]
sdb                           8:16   0 119.2G  0 disk   
&#9492;&#9472;isw_bbaihhhjf_MSI_RAID    252:0    0 357.7G  0 dmraid 
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID1 252:1    0 512.6M  0 part   /boot/efi
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID2 252:2    0 341.3G  0 part   /
  &#9492;&#9472;isw_bbaihhhjf_MSI_RAID3 252:3    0  15.9G  0 part   
    &#9492;&#9472;cryptswap1            252:4    0  15.9G  0 crypt  [SWAP]
sdc                           8:32   0 931.5G  0 disk   
sdd                           8:48   0 119.2G  0 disk   
&#9492;&#9472;isw_bbaihhhjf_MSI_RAID    252:0    0 357.7G  0 dmraid 
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID1 252:1    0 512.6M  0 part   /boot/efi
  &#9500;&#9472;isw_bbaihhhjf_MSI_RAID2 252:2    0 341.3G  0 part   /
  &#9492;&#9472;isw_bbaihhhjf_MSI_RAID3 252:3    0  15.9G  0 part   
    &#9492;&#9472;cryptswap1            252:4    0  15.9G  0 crypt  [SWAP]


Just to clarify, I reformatted this drive back to ext4 and now it's not showing up anywhere except in the Terminal. I want it to show up as an internal drive in the Home window. Much like File Explorer lists "Disks" C: D: etc...

---

### Post by anon24 on 2016-04-14
> **grahammechanical said:**
> Did you install Ubuntu on to the external drive? Do you get a Grub boot menu? Can you load Windows 10 from it? What happens when to load Ubuntu? Are you aware of this information?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you re-install make sure the live session is loading in EFI mode. Then Ubuntu will be installed in EFI mode as well. Which is required because Windows 10 will be installed in EFI mode.

Regards.

I didn't quite understand what you were talking about at first. Grub does work... Ubuntu was installed on the primary internal drive. I'm not sure what to do with Grub. 

When I did my install, I followed the EFI instructions. Is there some sort of command line that I'm supposed to be typing into Grub in order to get this drive to show up as an internal drive?

---

### Post by Geoffrey_Arndt on 2016-04-14
Grub is not the issue here.


Can you run the gparted program and post screen shots of your system partitioning?

---

### Post by oldfred on 2016-04-14
Post this, if sdc is the non-RAID drive:
       sudo parted /dev/sdc unit s print
      
 sudo blkid -c /dev/null -o list
        
You need to make a mount point, mount partition to mount, and give yourself ownership & permissions to use that ext4 partition.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

            fstab entry For ext4, copy & paste into fstab with correct UUID & mount point:
```
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /mnt/data ext4 defaults,noatime 0 2

    

```
 ** And when you are done editing fstab and saving it run the following command to test for errors and mount the partitions without requiring a reboot. You will know before you reboot if something is amiss. Make sure you have partition unmounted if previously mounted:
sudo mount -a

---

### Post by anon24 on 2016-04-15
> **Geoffrey_Arndt said:**
> Grub is not the issue here.


Can you run the gparted program and post screen shots of your system partitioning?

sudo gparted
======================
libparted : 3.2
======================
Invalid argument during seek for read on /dev/sda
Invalid argument during seek for read on /dev/sda
The backup GPT table is corrupt, but the primary appears OK, so that will be used.
/dev/sdb: unrecognised disk label
/dev/sdd: unrecognised disk label

I also get an error message saying, Libparted Bug Found! "Invalid argument during seek for read on /dev/sda"

So, I hit Ignore and it comes up with another error, " The backup GPT table is corrupt, but the primary appears OK, so that will be used."

GParted does not even recognize the Terabyte drive that I've been referring to. It just lists the 3 SSDs.

---

### Post by oldfred on 2016-04-15
Gparted will not work on RAID drive(s), only on standard partitioned drives.

If drive sdc is gpt, you can use parted or gdisk.
 sudo gdisk -l /dev/sdc

---

### Post by anon24 on 2016-04-15
sudo gdisk -l /dev/sdc
GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: not present
  BSD: not present
  APM: not present
  GPT: not present

Creating new GPT entries.
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2D89BD75-7940-4AC7-BA96-6C0D1E9F5ED4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1953525101 sectors (931.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

It's interesting that you are saying that GParted won't work on RAID  drives because the only drives that show up are set in RAID. The only  drive that doesn't show up is the terabyte drive, which has never been  set up in RAID to my knowledge.

Look up at my last post, I included a screenshot of GParted which does in fact only show the drives that are set up in RAID. Notice that it says the drive is 300 some odd gigs... That is 3 drives in RAID and it shows up perfectly fine in GParted.

I want to take a moment, again, to thank you, oldfred, and everyone that is helping me get this figured out. I can tell that I'm going to love this OS once I get it all set up right.

---

### Post by oldfred on 2016-04-15
Normally disk type is either MBR or gpt, but you show Sun? I thought they went out of business years ago after Oracle bought them. Are you trying for format for Oracle ZFS? Or XFS or some other than standard ext4 format?

---

### Post by anon24 on 2016-04-15
I have no desire to make this drive a proprietary format. I had formatted it as ext4. I was just experimenting when I changed it to that encrypted form of ext4. It showed up as an external drive, as soon as I changed it back to ext4 it was no longer displayed graphically as an "external drive".

I just want it to be normal ext4 and I want it to show up as an internal drive. Nothing complicated, I just want it to function as intended. I want a graphical representation of the drive to show up in the Home window.

---

### Post by oldfred on 2016-04-15
Do not know Sun type entries, but I do suggest gpt over MBR for all new drives. But  gpt is really only required if UEFI or drive over 2TiB.

Not sure then how to clear Sun setting or if just partitioning with gparted or gdisk will work.
I normally use gparted.
 I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....
With gdisk, you may need zap & then create new partitions.
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html)

I think new versions of gparted now correctly show RAID, but have never used RAID so do not know details. It used to be that gparted did not even show RAID drives.

---

### Post by anon24 on 2016-04-15
Thanks, I'll take a look at those tutorials. I don't know why it's listing it as "Sun". I was just trying to get the drive to be read and I messed around with some of the "partition parameters" in the terminal. 

Unfortunately, GParted doesn't even recognize this drive. If you check out the screenshots I posted here, it doesn't even list a terabyte drive. I don't need a bunch of partitions, I just want the whole terabyte to be available for storage.

I'm not sure what you're referring to when you say gpt and MBR. Are the available hard drive formats not: FAT34, NTFS, ext4, LUKS+ext4?

edit: OMG... I'm such a dumbass. Disks DOES list the drive, I just  didn't realize that there was a drop down menu at the top to select  different drives. I knew that I was probably missing something there.

---

### Post by anon24 on 2016-04-15
Ok, so I reformatted the drive and got rid of the Sun partitioning. Now, it's in gpt and it should be normal. What do I do from here to get the drive to show up as a graphical representation in the Home window? I tried to mount it again after reformatting to gpt to no avail. 

I entered: sudo mount /dev/sdc /media/secondaryhd 

The error read: 

       wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

---

### Post by oldfred on 2016-04-15
MBR & gpt are partitioning types.

But you still within either need to create partition(s) and format them.
Do not try to just format drive as that then become a very large floppy drive and does not always work right as just about everything expects partition table.

You mount a formatted partition like sdc1 not a drive like sdc.

You will also have to give yourself ownership & permissions to use the new partition.

I normally do this first when creating a new partition. Even before I add it to fstab for permanent mounting. And some partitions I do not add to fstab, and only mount occasionally.

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

---

### Post by anon24 on 2016-04-15
Ok, so I write the actual partition(s) in GParted? When I tried that, it said something about overlapping partitions. So, if keeping the whole terabyte in one partition isn't good... What would you suggest? How big should the partitions be? Can you give me a breakdown?

I want to be able to store lots of data, such as a large, uncompressed music library. So, wouldn't it get tricky to try to "split up" the music library between different partitions? 

All of the code that you just included. I'm supposed to have made the partitions on sdc before I started plugging this in? And this is supposed to permanently mount the drive?

As far as fstab goes, I'm not sure how to go about editing that or where it would fit in the process.

---

### Post by oldfred on 2016-04-15
One partition should be ok.
With multiple TB drives I do not always like one large partition as then it can be more difficult to backup.

You should not be getting overlapping partitions unless it is still seeing an old partition somehow?
Post these, to see what is now shown, would expect nothing still:
       sudo parted /dev/sdc unit s print
sudo gdisk -l /dev/sdc

    
Are you using gparted, Disks or gdisk to create & format partitions?

The code above is just to give you ownership & permissions, but you must have created sdc1 first. It is a one time manual mount. You need to manually unmount if adding to fstab. The manual mount will not be kept on reboot, where an fstab entry will be remounted automatically every time you boot.

Then you probably want to mount permanently if internal drive.
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.

---

### Post by anon24 on 2016-04-16
Initially, I tried to make partitions with Terminal before I started this thread. Once I got your help, I tried to make a partition on GParted yesterday. GParted told me there were overlapping sectors or something, so I tried Disks and that wouldn't let me make or delete any partitions. Ok, I understand what fstab is now. First off, I need to figure out how to make a partition of the drive. [U][B] 

parted[/B][/U]

Model: ATA HGST HTS721010A9 (scsi)
Disk /dev/sdc: 1953525168s
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start  End  Size  File system  Name  Flags

_**gdisk**_

GPT fdisk (gdisk) version 1.0.0

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdc: 1953525168 sectors, 931.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 1951A3C1-75FC-414E-B1D3-608A893E436F
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1953525134
Partitions will be aligned on 2048-sector boundaries
Total free space is 1953525101 sectors (931.5 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name

---

### Post by oldfred on 2016-04-16
gdisk does not look like it is complaining.
But sometimes just refreshing helps. Using its w command rewrites partition table structures.
Or you can maybe use gdisk to create partition(s).

gdisk is the fdisk for gpt partitioned drives. But the new fdisk in 16.04 does correctly see gpt where all previous versions of fdisk would not work on gpt at all.

But I have normally used gparted. But just had an issue on an image file restored to a larger flash drive. Gparted & disks totally failed, but just going into gdisk it warned backup partition table was not at end of drive, and w (write) fixed it so everything then worked.

Since you do not yet have any partitions, but do have gpt structure, I do not know if this would help or not:
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
last partition overlaps backup partition table
[http://ubuntuforums.org/showthread.php?t=1956173](http://ubuntuforums.org/showthread.php?t=1956173)
Check start & end, delete and recreate without overlap. Backup vital just in case.
gpt partition table in middle of drive
 launch gdisk, then type x, then type e, then type w to save your changes
Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR.

---

### Post by anon24 on 2016-04-16
Ok, what about in GParted? I opened up make new partition from the drop down menu. What values do I plug in to make the entire drive one partition and keep GParted from giving me the "overlapping sectors" error. 

Keep in mind, I'm an absolute beginner with Ubuntu. I had never even messed with Linux at all until the day that I made this thread. I'm not used to typing in all of these lines of code into the Terminal. So, if there is a GUI way to do something, please elaborate on that first before reverting to the Terminal way of doing it. Screenshots would be one way of doing that. As they say, "A picture is worth a thousand words". 

I seriously love your persistence in helping me with this. I am so thankful and want you to know that I'm saying this because I believe it will save both you and I the frustration of things being lost in translation. I feel like a lot of this stuff is going way over my head. Though, I have learned a lot in terms and am feeling a little bit less scared of the Terminal.

I think that a large part of the teacher / student relationship is on the student to let the teacher know their learning style. I think that now that I am giving you a clearer picture of my learning style, we're going to make some real headway.

[U]From here, what would help me is: 
[/U]
- Pretend you're me and you're creating the partition for this drive

- Go to GParted

- Type the values for my HD in all of the necessary fields in "New Partition" screen

- Take a screenshot of your GParted window after values are typed in

- If you would, explain where you obtained said values along with the screenshot


That should just about do it. After the partition is made, I'll go through some of the instructions that you gave me earlier about permissions, fstab and mounting. I'll let you know if I'm able to get through it or not.

---

### Post by oldfred on 2016-04-16
I find gparted pretty easy.
 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I first change to gpt for every new or totally reformatted drive. With larger drive I want a small bootable install of Ubuntu on every drive. So every gpt drive gets an ESP or 300 to 500MB for UEFI boot and a 1 or 2MB unformatted bios_grub partition. Then I can use about 15-25GB for an Ubuntu install even if a data drive.

      
 First choose drive, in upper right corner.
I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning....

Then if you click on the unallocated and right click new, it should default to entire unallocated space. 
Normally if creating more than one partition, then you change values. You also choose format & I like to label all partitions. If more than one partition you can set location on drive with the space/sectors before or after partition you are creating. 
You have to click on green checkmark to actually have change made.
I do not queue changes, once or twice something went wrong in the middle of multiple change and caused bigger issue as I was not sure where it was at.

It will default to first sector at 2048 which you want and uses 1MiB for rounding. New SSD & 4K drives require that. Gparted then may show small unallocated spaces. Even in old days we had small unallocated at beginning or end of drive but it rounded down and you did not see it.

---

### Post by anon24 on 2016-04-16
Ok, so, I created the partition. Though, it says 14 GB have been used... To my knowledge, everything on the drive had been wiped completely. I also managed to get the drive to mount as an external drive. Now, to permanently mount

I read through the Thread regarding fstab. I opened up fstab with gksu, I have no idea what to do in fstab. Can you give me a step by step breakdown? I found the UUID for my drive.

At this point, it's a matter of what do I do with this info? I want it to permanently mount to media/secondaryhd 


UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

gksu gedit /etc/fstab

sudo mount -a

---

### Post by Geoffrey_Arndt on 2016-04-16
Taken from a recent thread at this forum - - be sure to create the mountpoint directory 1st, and then incorporate following:

 An example entry below to mount a partition with a Linux filesystem on another drive. 


   You would need to replace "/dev/sdb2" with whichever partition you want mounted or you can use it's UUID instead such as in the second example below.  
   The ext4 of course is the filesystem type and the rest is options. You can also mount multiple partitions with separate entries.  
   In the example below, you would first need to create the 'data' directory in the /mnt directory.


   >   /_dev/sdb2 /mnt/data ext4 auto,user,rw 1 2_ 
   >   _UUID=2ae95530-a3d7-43e7-a160-3ef4da2a5904 /mnt/data ext4 auto,user,rw 1 2_

---

### Post by anon24 on 2016-04-16
I created a mountpoint called /media/secondaryhd. Is that sufficient? I used:

sudo mkdir /media/secondaryhd

So, I can copy the UUID and paste it in an fstab file? Then I save it to /media/secondaryhd or?

---

### Post by oldfred on 2016-04-16
Copy this, but with your UUID for that sdc1 partition into fstab.

# sdc1 partition
UUID=[COLOR=#ff0000]076426af-cbc5-4966-8cd4-af0f5c879646[/COLOR] /media/secondaryhd ext4 defaults,noatime 0 2

or this (not both) as noatime is more for SSDs, but can be used. A very few apps like Mutt may complain.

# sdc1 partition
UUID=[COLOR=#ff0000]076426af-cbc5-4966-8cd4-af0f5c879646[/COLOR] /media/secondaryhd ext4 relatime 0 2

Then instead of whatever I used probably /mnt/data use /media/secondaryhd for setting ownership & permissions.

---

### Post by anon24 on 2016-04-16
Ok, so do I create a _new_ fstab file and then save as _secondaryhd_? There are some lines of code already in fstab, which is why I'm asking that, I don't want to mess anything up or put the UUID in the wrong spot.

---

### Post by oldfred on 2016-04-17
Just add at bottom.
Commands were for backing up existing fstab and editing it.


And on setting ownership & permissions, once you have run sudo mount -a it will be mounted at your new mount point, /media/secondaryhd. So do not try to manually mount again. Just run the two lines with chown and chmod. Then you should be able to copy files and use partition.

---

### Post by anon24 on 2016-04-17
So, I don't know which of the commands it was. But, now my computer won't even boot Ubuntu. It just comes up with emergency mode.

---

### Post by oldfred on 2016-04-17
You should not be changing booting.

Did you edit fstab and not run the sudo mount -a to confirm it was correct?

---

### Post by anon24 on 2016-04-17
I was basically following the steps in the exact order that you posted. So, I put the UID in fstab before I did anything. Then I tried to mount it. Recovery mode isn't working. I'm just kind of stuck in the grub 2 loader.

Either way, I messed up somewhere. Any suggestions on getting back up and running? I'll do a clean install if needed. There wasn't any valuable data or anything.

It definitely has to do with the mounting because when I tried upstart mode, it says, 

"The disk drive for /media/secondaryhd is not ready yet or not present. 

Continue to wait, or Press S to skip mounting or M for manual recovery."

---

### Post by oldfred on 2016-04-17
Is sdc an external?
It sounds like you skipped this which you must do after any edit of fstab. It should just return, and have no error message. You mentioned it in post #26.
sudo mount -a 

You should just be able to skip. Or if external wait for it to come up to speed, fully power up and try again.

       But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I believe Boot-Repair works on RAID, but not sure. I do not know RAID.

---

### Post by anon24 on 2016-04-17
Yea, even if I mention a line of code you can't really trust that I know what I'm doing with it yet. Like I said in my very first post, I'm a complete beginner.

I'm not sure how to navigate Grub2. The options are:

Ubuntu
Advanced options for Ubuntu
System setup

When I go to the first option, it just loads and loads until it's in "Emercencymode".

When I try advanced options, I'm not really able to do anything.

System setup I can see the BIOS menu.


No, it's not external. This whole thread we've been trying to get Ubuntu to recognize this drive as internal because it recognized it as external for some reason or another.

Though, I'm starting to think that maybe it was listed as internal all long and that I just didn't know how to see it's graphical representation in the Home Window. Because it was listed in Disks and it was also listed in GParted. So, maybe I just don't understand the file heirarchy and how things are represented graphically. 

Could that have caused the issue?

Edit: 

Let's just start from scratch. I want to completely reinstall Ubuntu? How do I boot from my USB live disk and reinstall? I tried holding right shift during boot up and that didn't work.

---

### Post by oldfred on 2016-04-17
Most UEFI/BIOS will have a one time boot key often f10 or f12. That should also then offer to boot from flash drive. It may be USB or may be a hard drive option. If UEFI install be sure to boot in UEFI mode.

But you showed RAID? I do not know if desktop installer works fully with RAID yet. Perhaps 16.04 which will be released next week?
How did you install before? It used to be only server version supported RAID. And with 12.04 there was an alternative installer that included both RAID & LVM. But then they discontinued alternative installer and said to install server version and add desktop or install 12.04 and upgrade. Then they finally added LVM install to desktop several versions ago. And I do see RAID being better recognized as drivers are included, but often grub would not install correctly.

Is this your machine?
[https://www.msi.com/Notebook/GS70-STEALTH.html#hero-overview](https://www.msi.com/Notebook/GS70-STEALTH.html#hero-overview)
That mentions RAID & nVidia which both complicate installs. I do not know RAID, but have nVidia on one system that requires nomodeset boot option until installed and add proprietary driver from repository.
And if laptop how does it have 4 hard drives? Your 3 RAID and still another sdc?

---

### Post by anon24 on 2016-04-17
Yes, that's it. Solid State Hard Drives are in RAID and then the regular SATA Drive is by its lonesome. This is how Ubuntu recognizes the drives:
 
SDA: SSD1
SDB: SSD2
SDC: Regular SATA 1TB
SDD: SSD3

The install worked just fine before. I made a bootable USB in Windows and used it to "try Ubuntu" then I installed it. It was that easy. I did absolutely nothing special. And it worked fine other than my issue trying to see the other drive. Which, I think that I just didn't know where to look for the graphical representation of the drive.

It not only recognized the RAID. It treated the 3 SSDs just like one hard drive. I had no issues with my NVidia card either. So, I don't think either of those are the issue here. I've also seen several other people online with this exact system successfully install.

I used the 15.10 64-bit version.

F10 Nothing happens
F12 It says No media present

What would be my next step if the USB is not recognized when I try to press either of those F keys? I just want to reinstall.

---

### Post by anon24 on 2016-04-17
Ok, F11 does work and I selected the USB... 

Which seemed to bring up the exact same Grub2 menu and every option behaved in the same way.

EDIT: 

Alright, anyone that comes across this... 

What I did was go to:

**Advanced options**

Then, select the **(upstart version)**

As it's loading, it should give you the option to** skip mounting by pressing S**... 

Do that and you should be up and running.

---

### Post by anon24 on 2016-04-17
Ok, I'm back in Ubuntu and I changed my mind on the reinstall. I was just frustrated because I didn't know what else to do at the time.


EDIT:


Anyway, I went back in the fstab and deleted the UID. 

Btw, when I edited the fstab the first time... 

This is what I typed: 
*UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2*

Now, should I have just done this? 
(I just noticed that when you posted before, you used a red font on that numerical value.)
*076426af-cbc5-4966-8cd4-af0f5c879646*


EDIT:


So, a step by step breakdown of this would REALLY help  

I think that I mixed up the order of these commands, which is probably what caused that crash

This is an example of the kind of breakdown that would make sense to me: 
(Only in the correct order, mind you)


   1)[B] [U]Type this into Terminal to get to fstab
[/U][/B]
gksu gedit /etc/fstab 

2) [U][B]Insert this UUID into the bottom of the fstab
[/B][/U]
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

3) [U][B]Type this into terminal to mount
[/B][/U]
sudo mount -a 

This returned error, "mount: can't find UUID=076426af-cbc5-4966-8cd4-af0f5c879646"

4) [U][B]How is this step not redundant to mount -a? 
[/B][/U][I](If this isn't redundant, explain why and where 
in order of the step by step sequence it would fit)
[/I]
/mnt/data use /media/secondaryhd 

Also, this returned an error saying, "/mnt/data: No such file or directory"

5) [U][B]This is the one that went over my head 
[/B][/U]
"Just run the two lines with chown and chmod."
(I have no idea what chown or chmod do or where to plug them in or even exactly what I'm supposed to be typing in)

sudo chown?
sudo chomod?


EDIT:


When I mount the 1TB drive from Disks, this is where it says the drive is:
Mounted at /media/machinicsnob/18a5d1bb-26ac-437e-bb69-1b83aca17e0e

I thought I would also mention that after placing said UUID in fstab
I typed** sudo mount -a** after that and I received an error:

[I]mount: can't find UUID=076426af-cbc5-4966-8cd4-af0f5c879646


[/I]EDIT:

One more thing, you keep saying that Ubuntu doesn't recognize RAID. 

Look at this screen shot, as you can see, it displays all four drives... 

Then it displays a 384GB BLOCK device (which is 128 x 3) 

That's what RAID does, it treats several drives as one.

Ubuntu is installed on this 384GB block and the Home folder even says under properties that it has 333.8 GB. 

If that isn't RAID working in Ubuntu, then I don't know what working RAID in Ubuntu would look like.

---

### Post by oldfred on 2016-04-17
Once Ubuntu is installed then, RAID should be ok. 
If you were able to install, then they have updated everything to work with BIOS RAID which is the type you have.

I have not been posting exact commands assuming you could edit UUID in example to your UUID. And example was mine with /mnt/data but you created mount point /media/secondaryhd so you have to change entry to use that mount.

If you want exact entry post this:
sudo blkid

Never reboot if sudo mount -a returns an error. The one error it shows is no /mnt/data which is correct, you do not have a mount for /mnt/data. So it is telling you to either create mount (do not) or change/edit entry to the mount you created. You also have to change example from its UUID to the new UUID that was created when you reformatted the partition/drive.

Back in post #19 I posted the chown & chmod commands after manually mounting a partition to /mnt/data. Once you have permanently mounted to /media/secondaryhd, then again you have to edit those commands to use your mount not my mount. If that is too complicated I can post the edited versions. 
But you need to learn that an example is just an example and to use your details where they are different.

---

### Post by mansonfan78 on 2016-04-17
When you mounted the drive with the Disks utility it mounted it at  /media/machinicsnob/18a5d1bb-26ac-437e-bb69-1b83aca17e0e, so that's the  uuid that needs to be in fstab (18a5d1bb-26ac-437e-bb69-1b83aca17e0e).  So, your fstab entry should be "UUID=18a5d1bb-26ac-437e-bb69-1b83aca17e0e /media/Data ext4 defaults,noatime 0 2" (without the quotes).  Try that followed by "sudo mount -a" and if that doesn't work let us know any error messages.

---

### Post by anon24 on 2016-04-17
Awesome, thank you all so much for your help! It worked! 


EDIT:


I also noticed that /mnt/data/ has a folder in it called: lost+found.

Is this something that I need to keep? What is it?

---

### Post by mansonfan78 on 2016-04-17
The lost+found folder is used during file system checks as a temporary location for files.  Deleting it won't really cause any problems, but the system will just recreate it eventually any way.

---

### Post by anon24 on 2016-04-17
Thanks again everyone, ! I really do appreciate all of the work that everyone put into this!

[B][U]Create a Directory / Permissions & Auto-Mount a Drive Partition

[/U][/B][I]Here is a step by step of this process for people that have this issue in the future. 

If there is anything that needs to be edited or added to this step by step. 

Let me know and I'll be happy to do it! [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG][/I]

**1) Open Gparted in Terminal to see which partition you need to mount**

*sudo parted -l*

**2) Make a directory for said partition to mount to**

*sudo mkdir /mnt/data*

**3) Mount the drive the directory you just created**

*sudo mount /dev/sdc1 /mnt/data*

**4) Change permissions  for directory**

*sudo chmod -R a+rwX,o-w /mnt/data*

**5) Change ownership of directory**

[I]sudo chown -R $USER:$USER /mnt/data 
[/I][B]
6) This will display all UUIDs for drives[/B]
*sudo blkid*

You would want to copy it and change the formatting slightly.

Instead of: UUID=&#8221;[COLOR=#000000]18a5d1bb-26ac-437e-bb69-1b83aca17e0e&#8221; 

You want it to be: 

*UUID=*[/COLOR]*[COLOR=#ff0000]18a5d1bb-26ac-437e-bb69-1b83aca17e0e[/COLOR][COLOR=#000000] /[/COLOR][COLOR=#00cc00]mnt/data [/COLOR][COLOR=#000000]ext4 relatime 0 2[/COLOR]*

Keep in mind, the red numbers will be different for your drive
Also, the directory, colored green, will be different as well

 **7) This will download a program that allows you to edit fstab settings**

*sudo apt-get install gksu*

**8) This will take you into the fstab settings outside of the Terminal.**

[I]gksu gedit /etc/fstab 

 **9) **[/I][B]Once there, make sure you insert your UUID in the format included. 
You will then place said UUID at the bottom of the document.[/B][I]

UUID=18a5d1bb-26ac-437e-bb69-1b83aca17e0e /mnt/data ext4 defaults,noatime 0 2[/I]

[B]10) This is the last step, go back to the Terminal. 
Type this command. 
It means that you will be mounting all drives. [/B]

[I]sudo mount -a 

[/I][B]11) If _STEP 10_ does not give you any errors, restart your computer.
Your drive should now automatically mount to the specified directory.[/B]

---

### Post by oldfred on 2016-04-17
Glad you got it working. :)

Linux is also case sensitive. You show /mnt/data in one place and /mnt/Data in another. Those are two totally different mount points. 
I have gotten confused also. Best to be consistent on case when creating new mount points.

---

### Post by anon24 on 2016-04-17
Me too! I wouldn't have gotten it done in that amount of time without your help.

I went ahead and fixed that. ;)

---

### Post by anon24 on 2016-04-17
I do have one last question. 

When the hard drive shows up in the Home Window, there is an eject button as if it was an external drive. 

Is there a way to remove the eject button to avoid accidentally ejecting?

---

### Post by oldfred on 2016-04-17
Normally drives mounted at /mnt do not show up. But drives mounted in /media do show up.

Is this with Unity? I almost immediately change to the old fallback or gnome-panel which is the old menu style.

---

### Post by anon24 on 2016-04-17
I want the Drive to show up in the Home Window. 

I went into the Disks settings and changed it to always show.

I want that accessibility of being able to get to the files in the drive quickly.

I just don't want the eject button right next to it as if it were an external drive.

---

### Post by mansonfan78 on 2016-04-17
You could bookmark the drive and then set it not to show, that way you would get direct access through the bookmark.

---

### Post by Geoffrey_Arndt on 2016-04-18
Is the OP's original request an unusual circumstance, . . . an anomaly?    On all my Ubuntu machines (& Kubuntu, Xubuntu), all internal drives (hdd, ssd) and external drives (flash sticks, SD cards) show up by default in the file manager (nautilus ,dolphin, etc.) and all I do is click on it once and it mounts and therefore is available for full use until I log out or shutdown.  Ditto if I have multiple partitions on the same or other physical drives.

I understand the point of automatic mounts . . . but for pete's sake, one mouseclick to mount . . takes one second or less for drive to be available . . . so, on a single machine not networked, why all the fuss for such a low-benefit feature??

---

