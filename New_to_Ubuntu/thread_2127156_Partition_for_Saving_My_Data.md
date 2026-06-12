---
title: "Partition for Saving My Data?"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by jayaq32 on 2013-03-19
Noob here. So I've installed Ubuntu 12.04 Desktop (64-Bit) and need some guidance on how to access my partitions. When I was using Windows, I always had at least 1 drive or array for the OS install and dedicated additional drives/arrays for my data. 

My current setup: I have a total of 3 drives: x1 drive configured as RAID0 and x2 drives configured as RAID1. This is a Gateway system with an internal RAID card.  During Ubuntu 12.04 installation, the array's showed up nicely. I configured the  partitions manually where the RAID0 array (even though it is 1 drive) as a boot partition with a dedicated swap area. Next, I configured the RAID1 array as EXT4 and and would like to use it for storage.

I've installed Gparted and the arrays show up as:

/dev/sda

    /dev/sda1 = ext4
           Mount point = /
   /dev/ sda2 = extended
          sda5 = unknown 

/dev/sdb

     /dev/sdb1 = ext4
          Mount point = /home

When I look under "/home" for the "storage" partition, I don't see any indication of "sdb1" which I'd like to use as storage. I know this is a total noob thing but how do I access this partition to save my files? In Windows, I was able to go to My Computer and access the Drive letter.

 Did I configure/setup correctly?

Any guidance would be helpful! Thank you for the patience and understanding.

---

### Post by Cheesemill on 2013-03-19
If you have mounted sdb1 as your /home directory (which is what gparted is saying) then anything that is saved in this directory (which is all of your user data) will be on your sdb1 partition.

Linux is unlike Windows in that there is only one filesystem structure. In Windows different partitions show up as different physical drives, whereas in Linux all mounted partitions appear in the same directory tree. Your /home directory ***is*** your sdb1 partition.

To make sure that everything is as it should be there are a couple of commands you could use. The mount command will give you a list of all filesystems that are mounted on your system, you should see a line similar to...
```
/dev/sdb1 on /home type ext4 (rw)
```
Another command you can use is df, if you type 'df -h' into a terminal it will give you a rundown of the mounted filesystems and their usage.

---

### Post by AlecJ on 2013-03-19
Install Samba for sharing with windows [https://help.ubuntu.com/community/Samba](https://help.ubuntu.com/community/Samba)
Install NFS for sharing with linux           [https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

look under /media/ for the mounted drives
create folders you with to share on the drive you wish and add the path to the config files for SMB or NFS
There  is a GUI share program called Share Folders that makes life easy, if  it's not in the menus find it /usr/share/applications/
Don't forget to set the permissions on the folders, mine are all owned by me and group messagebus has access.
I still have to issue a   chmod -R 777 /media/store1/Videos/*.*     after windows has been ripping dvds here

---

### Post by jayaq32 on 2013-03-19
> **Cheesemill said:**
> If you have mounted sdb1 as your /home directory (which is what gparted is saying) then anything that is saved in this directory (which is all of your user data) will be on your sdb1 partition.

Linux is unlike Windows in that there is only one filesystem structure. In Windows different partitions show up as different physical drives, whereas in Linux all mounted partitions appear in the same directory tree. Your /home directory ***is*** your sdb1 partition.

To make sure that everything is as it should be there are a couple of commands you could use. The mount command will give you a list of all filesystems that are mounted on your system, you should see a line similar to...
```
/dev/sdb1 on /home type ext4 (rw)
```
Another command you can use is df, if you type 'df -h' into a terminal it will give you a rundown of the mounted filesystems and their usage.

I see! I chose "/home" during the partitioning b/c I thought that's where I could access an icon of the drive/partition (as in Windows). What would have been the correct way to setup the "storage" partition during installation so that it is empty? I noticed that "/home" uses about 350mb of  space on the partition to store the /home files. Is there a way to change the configuration so I could set everything up as close to how I had Windows setup? I want the RAID1 (array aka sdb1) to be the sole place I save my files and I only want my files within that partition. 

So essentially, what I want to do is have the OS on one physical drive and my data/files on another set of physical drive(s) that utilizes RAID redundancy. What is the best way to accomplish this in Ubuntu?

 I have Ubuntu 12.04 installed on one drive (sda) and the sdb1 partition is allocated but it is mounted to "/home" - how do I change this? How was I supposed to set this up originally during installation? Was I supposed to specify "/" as the mount point? Or not specify anything? Or..?

---

### Post by AlecJ on 2013-03-19
So you have 3 drives? 
1 for the system and 2 for the raid that will be one drive so to speak?

I use 1 32Gb SSD to hold the system /dev/sdc1 mount point /
and 3 sata drives and 1 USB drive
/dev/sda mount point /media/store2
/dev/sdb mount point /media/store
/dev/sdd mount point /media/store3
/dev/sde mount point /media/1Tb      USB drive

making 6Tb for storage and shares over the drives

The drives are mounted at boot with /etc/fstab using UUID
I can post this if it will help you

the shares are folders on each drive and the paths are /media/store/Music
/media/store/Videos      etc
but you can share the whole drive if you like.

---

### Post by Bashing-om on 2013-03-19
jayaq32; Hi !

Be advised when you get into partitioning and raid ----you are jumping into deeper waters than at the "noob" level. All to the good.
May I suggest a bit of reading to understand what you are attempting. Very much so doable.
[https://help.ubuntu.com/community/NewDocs](https://help.ubuntu.com/community/NewDocs)

This is the latest compilation of all things ubuntu - Thanks to BlinkingCat and others  -In this page is a search box in the upper right corner; Enter the term "raid" (with out the quotes) -> many results --read to your heart's content, Then do the same for "partitioning".

Now ask any question on here, there are no dumb questions when one is making an effort to learn.[INDENT=3]
this will help

[/INDENT]

---

### Post by jayaq32 on 2013-03-19
> **AlecJ said:**
> 
The drives are mounted at boot with /etc/fstab using UUID


Thank you for the insight! As quoted above...could you explain this in a bit more detail? I don't quite understand what is meant particularly "UUID" and "fstab." During installation, I determined the array/partition to install Ubuntu (sda) together with a swap area. I believe I chose "/" as the mount point b/c when I tried to proceed with install I was given a warning that (paraphrasing) "no boot drive was specified" - so I chose "/" from the "add or change" option and everything was fine. Then with the 'storage' array (sdb) I chose "ext4" as the type and mounted it to "/home" where subsequently, the "home" files are now stored. I am curious what I should have chosen as the 'mount point' for sdb so that it is accessible to me as an 'empty' partition to store my files into? And, is there a way after install to re-configure this in Ubuntu so that sbd is no longer associated/mounted to "/home" directory?

---

### Post by Bashing-om on 2013-03-19
jayaq32;

links to shed light on fstab:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.comunity/Mount/](https://help.ubuntu.comunity/Mount/)

-they say lots more than I can say -

---

### Post by arpanaut on 2013-03-19
It is not bad to have your /home directory on a separate partition, it makes reinstalls and upgrades easier.
You could boot from a live dvd/usb and with gparted reduce the size of your /home part. and then use that space as a separate data partition.
Just giving you options.

---

### Post by jayaq32 on 2013-03-20
> **arpanaut said:**
> It is not bad to have your /home directory on a separate partition, it makes reinstalls and upgrades easier.
You could boot from a live dvd/usb and with gparted reduce the size of your /home part. and then use that space as a separate data partition.
Just giving you options.

So currently, "/home" is mounted to my sdb partition. Is that anywhere near equal to having say the "My Documents" directory in Windows XP target set to a 'storage' partition (i.e. "D: drive")? If so, that's what I am trying to accomplish. Obviously, I am coming from Windows where "c: drive" was the bootable OS and "d: drive" is where I put all of my Data (i.e. downloads, music, docs, etc.). I can't tell you how many times Windows went to #*&@! and I was soo relieved that my data was on a separate drive/partition. This meant I could wipe the Windows OS on "c: drive" and re-install without ever worrying about my data. 

Again, I just want the OS separate from my Data. And, if the OS goes wonky or say a meteor is about to drop onto my town and I have 15 mins to evac, I could pull out the actual HDD's with my Data and get running (OS drive be damned).

Is "/home" the directory to mount to my data array/partition? Or is there a more optimal way to configure this???

---

### Post by mastablasta on 2013-03-20
> **jayaq32 said:**
> So currently, "/home" is mounted to my sdb partition. Is that anywhere near equal to having say the "My Documents" directory in Windows XP target set to a 'storage' partition (i.e. "D: drive")? If so, that's what I am trying to accomplish. Obviously, I am coming from Windows where "c: drive" was the bootable OS and "d: drive" is where I put all of my Data (i.e. downloads, music, docs, etc.). I can't tell you how many times Windows went to #*&@! and I was soo relieved that my data was on a separate drive/partition. This meant I could wipe the Windows OS on "c: drive" and re-install without ever worrying about my data. 

yeah /home is sort of the same as My Documents. if you enable hidden files you will see that there is plenty of folders there which are configuration files for your applicaitons. the upgrade is doen by backip up /home (just in case) and then reinstalling the os to /. os will reinstall (or you can format and install new version there) while /home will not be touched.


you have setup the disks as i would like to have them setup. but no money to create the raid. :-)


otherwise you could have installed / and /home to first disk and then cretae a data disk which would then be completely separate. no system files would be there. which is how i have it now where a small old disk is for OS+home+swam and big disk is there for data.

anyway  i would keep it as you have it. most applicaitons store to home by default and when you want to open something they will offer home. so that will save you some setting up. besides the /home is ment for user's data.

---

### Post by AlecJ on 2013-03-20
There are many way to do this, I'm sure

what works for me as it's based on Mythbuntu and it's that box that does the sharing as well as TV around the house.

This box has a fixed IP, so we don't lose it, google that for your setup.

My the system is held on a 32Gb SSD on a sata cable mounted "/" so the normal folder structure is here including /Home

The other sata drives are mounted at boot by the system and they appear here /media/store    etc

I don't use RAID just single drives, but I believe they act as 1 drive?

if you just plug a drive in a sata socket on the motherboard it will not be mounted, you have to find it here /dev/disk/by-uuid, so note the contents before adding the drive then shutdown power off, add drive, power on and look in folder for the new drive, note the new uuid
make a partition (not bootable) and format the drives to  ext4 or whatever, note if you want to use NFTS then make sure you  ```
sudo apt-get install ntfs-3g
``` before you start ( I don't  know your flavour of ubuntu).

*OR* skip all that and use the _Disk Utility_ app, with this you can create the partition, format it and give the uuid number


then ```
sudo gedit /etc/fstab
```or mousepad or nano or whatever

here is mine
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a642cc20-2157-4e48-ad6c-1be3460ec138 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=93bf7305-2fd8-4693-acf7-393b3240df3a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=d151f967-4d72-45ee-aab3-f6c3d2dc86d2 /media/1Tb auto auto,user,rw,exec 0 0
UUID=73ca5900-af74-4cd1-a27d-fa1f4b0c0ae1 /media/store auto auto,user,rw,exec 0 0
UUID=f9914fdf-690d-4054-be45-1d0d5f5088ac /media/Store2 auto auto,user,rw,exec 0 0
UUID=8973fd63-a792-47f1-a31c-ddd0931e9a78 /media/store3 auto auto,user,rw,exec 0 0


```

The bottom 4 lines are what I have added and 1Tb is a USB external drive ( the boot will hang waiting for user input if this drive is not here, like powered off after a power out)
note the uuid=, then the path and the type of mount, which is explained in more detail on one of the link provided by Bashing-om

The path bit /media/store etc are folders created in /media and act as access point to the drives, you can call them what you like eg. /media/fred

after you have found your drives uuid's and added it, you can test the fstab before reboot to check for errors with ```
sudo mount -a
```

make folders on your new drives at /media/store/my stuff for sharing
set the permissions as I explained earlier 
I used the share folders app to create the shares, either reboot after or restart the services to start the shares.

now from a windows machine (samba share)
browse the network, find your new server and the folder that you shared and enter it.
Then map the drive as Z:\ or whatever and windows treats this as another drive on it's system.

From another linux machine,(NFS share) create a folder in /Home/yourname/Music1 as an access point to the shared drive on the server then
in a terminal ```
sudo  mount 192.168.1.100:/media/Store2/Music /home/yourname/Music1
```
change the IP address and yourname to suit

now by going to /Home/Music1 your on the shared drive, here the permissions need to be correct so you can see/read/write/create files.

Hope this helps explain it more clearly.

---

### Post by Bashing-om on 2013-03-20
jayaq32; 

Here is another option.
 I have set up my data harddrive as on demand; I feel that my data is more secure if the disk is not mounted 'till I want to access the data.
All my systems are 'buntu's of some flavor thus my disk are formatted to ext4.
I made a mount point in the /mnt directory:
```
mkdir /mnt/data
```
and I explicitly mount the device:
```
sudo mount /dev/sdb1 /mnt/data
``` sdb1 = my second drive and the 1st partition on that drive.
I insure only I have access to my data:
```
sudo chown your-user-name:your-user-name /mnt/data/<desired_directories>
```

Remember (tie a string around your finger) that the device MUST be (un)mounted when access is no longer needed and prior to logging off or shutting the system down. Failure to do so can result in filesystem corruption. In the linux file system disk writes are cached; the cache is not written to the device 'till the device is (un)mounted.

```
sudo umount /mnt/data
```[INDENT=5]
ubuntu is just wonderfull

[/INDENT]

---

### Post by purza on 2014-02-09
I realize this thread is almost a year old, but I wanted to make a note that would have saved me a lot of time.  when entering the auto,user,rw,exec above to AlecJ's post of his "fstab" file don't put spaces after the comas

---

