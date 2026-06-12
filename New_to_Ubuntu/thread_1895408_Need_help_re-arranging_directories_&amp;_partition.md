---
title: "Need help re-arranging directories &amp; partitions"
date: 2011-12-14
forum: New to Ubuntu
---

### Post by JLB39401 on 2011-12-14
I am a complete newbie to Ubuntu, and Linux in general.  In the midst of  other computer woes, I finally decided to can windows (Vista 64 Home  Premium).  My installs have all been from a 10.10 (Natty Narwhale) Live  CD, and updated from there -- I am currently at 11.10.  When installing  Ubuntu as my exclusive OS, I put all my old Windoze files in one place  with the intention of moving them later, and repartitioned the disk to  which I was installing.

I did that about five times, with two  separate hard disks, and no understanding at all of how to actually  arrange or manipulate the resulting file-system tree.

Now I have  three disks, plenty of space, no real idea exactly where all my data is  or is supposed to be, and frequent 'low on disk space' messages.  I need  help understanding what is going on, and how to re-arrange things to  take advantage of my available resources.

/dev/sda -- older internal 750 GB SATA hd
/dev/sda1:  LABEL="/" UUID="e9cef76e-41ec-4e42-ad41-ac84c60fa610" TYPE="ext4"  --  bootable partition, mounted at /, is 6.4 GB but needs (I think) to be  bigger, intended to be the permanent home for all the operating system  files, extensions, libraries, etc
/dev/sda2:  UUID="8e5fd3c3-82d3-4036-ad21-e228fd08a26d" TYPE="swap" -- definitely  needs to be bigger, as I have recently upgraded from 6 GB RAM to 16 GB  RAM, doesn't say whether it is mounted or not
/dev/sda3:  LABEL="/home" UUID="362c3a5d-2564-4971-a333-56227b681077" TYPE="ext4" --  mounted at /media/_home -- not where I want my home directory to be,  I'd prefer to have the users homes be on /dev/sdb3, not sure exactly  what is here
/dev/sda4: LABEL="/tmp"  UUID="ac83b624-dffd-4cb1-9e43-83785a3f667a" TYPE="ext4" -- mounted at  /media/_tmp, I'd like all my cache and temporary files to be stored here  but no idea if that is what is actually happening

/dev/sdb -- new internal 2 TB SATA hd
/dev/sdb1:  UUID="fab7223e-bd96-436b-bf2c-434910c9d566" TYPE="ext4" -- I think this  is an old attempt to install 10.10 but the partition isn't mounted or  marked as bootable so it needs to go away
/dev/sdb2:  UUID="6facbb7d-a2a6-4579-afb7-44b910d29940" TYPE="swap" -- intended as a  swap area for the OS in /dev/sdb1, not mounted and needs to be replaced  by an expanded /dev/sda2
/dev/sdb3:  UUID="b5a4bf9a-50be-4bb1-ba48-cfe570a2ca8a" TYPE="ext4" -- 1.6 TB  mounted at /media/b5a4bf9a-50be-4bb1-ba48-cfe570a2ca8a, I'd like this to  be for all the users homes, and to expand this to as much of the 2 TB  disk as can comfortably be addressed, no idea if anything is actually  written here at the moment
/dev/sdb4 -- Extended partition containing  /dev/sdb5, no indication of whether or not it is mounted, or where, not  sure this partition is needed (it may have been placed to make  partitions small enough for the OS to handle, as such it is probably  unneeded at this point)
/dev/sdb5: UUID="d996e1f6-162c-4f45-a375-699c7cc55a0c" TYPE="ext4" -- unmounted (& empty, I think) logical partition

/dev/sdc -- external 1 TB USB hd
/dev/sdc1:  UUID="8C17-BBF9" TYPE="vfat" --  mounted at  /media/8C17-BBF9, contains my files from the Win era, I'd  like to move much of this information into my /user/home
/dev/sdc2 --Extended partition containing /dev/sdc5 and /dev/sdc6, no indication of whether or not  it is mounted, or where, not sure this partition is needed (it may have  been placed to make partitions small enough for the OS to handle, as  such it is probably unneeded at this point)
/dev/sdc5:  UUID="f86f182c-6638-40e1-9a0c-b2d6987ee8d4" TYPE="ext4" -- don't know  what happened to /dev/sdc3 or /dev/sdc4, mounted at  /media/f86f182c-6638-40e1-9a0c-b2d6987ee8d4, not sure if anything is  stored here but would like this to be an area for 'transportable'  programs and files (things I might want to take to a friends house, or a  LAN party -- games, movies, music, pics, save-games, documents for  collaborations and projects, etc) 
/dev/sdc6:  UUID="9882a572-8e9a-4dd9-8989-cc19917b541c" TYPE="swap" -- I really have  no idea why this is here, probably useless & needs to go away.

Where  do I even start?  How can I safely move these bits around?  Are there  any dependencies/permissions/things the OS or FS expects that I could  mess up if I just dive into this?  What commands would I need to read  the man pages for?  How can I ensure that the next time I boot my  machine, it will remember the arrangement I have chosen?

Sorry for the wall of text; any assistance or advice will be appreciated.  Thanks.

---

### Post by cortman on 2011-12-14
Whoa. That is convoluted.
My recommendation? You appear to have all your files backed up to the external drive. If that is the case, I would say re-install Ubuntu 11.10, and when you're installing it tell it to use the whole disk and just wipe out all the old stuff.
You can create a new partition table quite easily when installing Ubuntu. it'd be a snap at that point to make the partitions for the various system folders you have.
You have a ton of storage. I'd install the OS on the 2 TB. Put all your system folders on the same HD.
IMHO, this system begs for a format and fresh installation... But MAKE SURE you have all your things backed up and the backup drive disconnected if/when you do.

---

### Post by JLB39401 on 2011-12-14
[QUOTE=cortman]Whoa. That is convoluted.[/QUOTE]Yeah :)

[QUOTE=cortman]I would say re-install Ubuntu 11.10[/QUOTE]I was kinda hoping to avoid that, but it may end up being the simplest solution.  My previous installs were all in various stages of rebuilding/troubleshooting my computer -- since everything works & is all installed now, just re-installing should be much simpler than the initial install.

[QUOTE=cortman]I'd install the OS on the 2 TB. Put all your system folders on the same HD.[/QUOTE]I'd like to dedicate a whole HD just to the OS and its necesarry support files, swap & etc -- but was thinking of using the smaller 750GB drive for it.  Are there disadvantages to that approach?

---

### Post by cryptotheslow on 2011-12-14
You'll have to be really going some to require even the whole 750GB disk for just the OS and supporting files. Even a third of that is on the extreme large side for the vast majority of desktop installs.

I think my approach if really wanting to go to town on the system partition size would be something along the lines of:

_750GB drive_
250GB partition for the root filesystem /
492GB partition for the home filesystem /home
8GB swap partition (sized to suit your installed RAM of course)

_2TB drive_
1 partition across the whole thing that can be mounted into the filesystem as something like /media/2ndDrive - and used for media files etc. and somewhere to put backups of stuff from /home
[U]
External[/U]
Probably NTFS partition across this whole thing for portability to other Win based systems if required. Obviously don't do this bit until you have the new install up and running and you have copied everything off the external to the internal!


But it really does depend how many users on the system and what they tend to do. The above is just a sane way to keep /home separate from / which can help avoid some headaches when doing OS upgrades or re-installs.

Given what you have now - and presuming you can backup everything to that external drive, then as above, back it all up to the external drive and disconnect it completely (stick it in a drawer or something to be sure :D )

Then fire up a LiveCD and nucleate from space all the partitions on the 2 internal drives before proceeding to a fresh install with the new partition structure.

That's just my suggestion as I think it would be way quicker and safer than trying to shuffle everything around from the state it is in now. Not that there's any particular reason that couldn't be done if you have some time to kill.

---

### Post by oldfred on 2011-12-14
I like having room for extra / partitions as I do a clean install and keep my old install in case I did not copy something over.

I do not like huge partitions unless it is for large media files, but that is a trade-off on the issue you now have of reorganizing when things change. But I figure by then it is time for a new drive anyways as they do not last forever.

I have a copy of Ubuntu on every drive except my old XP drive. I used this logic but used Ubuntu instead of Knoppix:
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

If you install Ubuntu to the 2TB drive, it will probably convert to gpt which is the new/better partitioning scheme, but many do not know it yet. Required for most drives over 2TiB. 

Do not backup system files to NTFS as you will lose ownership & permissions. You can compress or use tar and still copy to NTFS if required. But I have some data still on my NTFS shared partition even though I do not use XP much anymore.

There was/is a bug in grub on very large drives/partitions. It just does not work. So best to keep / partition smaller. It is somewhat like the old BIOS system limit of 137GB as the highest location a bootable partition could be. It may be a combination of grub & BIOS settings.

---

### Post by cortman on 2011-12-15
I like cryptotheslow's recommendation. And as far as using the 2 TB for storage, it might not be a bad idea to create a number of partitions- one for movies, one for music, one for pictures, etc. Not only do you avoid the huge partition bug but that way if one would become infected it you wouldn't lose everything, unlikely as that is with Linux.

---

### Post by JLB39401 on 2011-12-16
Alrighty.  I made both a 11.10 Live CD and a bootable USB 11.10 intall stick.  The plan is to reinstall with the following partitions:

/dev/sda -- 750 GB HD
/dev/sda1 -- 125 GB 'primary' bootable, mounted at /
/dev/sda2 -- 25 GB 'primary' swap area (I have 16 GB RAM, this includes some slack space)
/dev/sda3 -- 600 GB mounted at /tmp

/dev/sdb -- 2 TB HD
/dev/sdb1 -- 125 'backup' bootable, not usually mounted
/dev/sdb2 -- 25 GB 'backup' swap (for when /dev/sda dies and I have to run by booting off of /dev/sdb)
/dev/sdb3 -- 1850 GB mounted at /home

/dev/sdc -- 1 TB external
/dev/sdc1 -- 1TB mounted at /portable (probably to include both /media and /archive)

I don't plan on touching /dev/sdc until I get sda and sdb sorted out -- which may take a bit.  Neither the stick nor the liveCD want to behave correctly.  Will post details later.

---

### Post by oldos2er on 2011-12-16
Why such huge swap partitions?

---

### Post by cortman on 2011-12-16
No need for a swap partition larger than the amount of RAM on your PC.

---

### Post by N00b-un-2 on 2011-12-16
it's a good practice to make your swap the same or exactly twice the size of your RAM.  25GB of swap is a waste of space in ANY configuration because EVEN IF you have 16GB of RAM, you will never use anywhere close to that much swap.  I have 2GB of ram, 2GB of swap and I have rarely seen swap ever get used, and when it does usage never goes above 50MB, so I've considered just formatting it as it seems relatively superfluous.

---

### Post by N00b-un-2 on 2011-12-16
> **JLB39401 said:**
> Yeah :)

I was kinda hoping to avoid that, but it may end up being the simplest solution.  My previous installs were all in various stages of rebuilding/troubleshooting my computer -- since everything works & is all installed now, just re-installing should be much simpler than the initial install.

I'd like to dedicate a whole HD just to the OS and its necesarry support files, swap & etc -- but was thinking of using the smaller 750GB drive for it.  Are there disadvantages to that approach?

this is a complete waste of space.  I've never had an ubuntu install use any more than 15GB for everything (excluding my home directory of course).  And 15GB is MASSIVE fro a linux install, typically footprint weighs in at under 8GB

---

