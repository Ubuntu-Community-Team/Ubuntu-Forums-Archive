---
title: "The &quot;computer&quot; partition is to small"
date: 2014-12-17
forum: New to Ubuntu
---

### Post by petermartin2 on 2014-12-17
Hello,

I am new to Ubuntu and I have just finished installing it. Prior to the installation I made a partition for 350gb for Ubuntu alongside my smaller windows partition but when the installation was finished I discovered that the ubuntu partition I had selected has been shopped up into smaller partitions. I've downloaded gparted but for some reason it will only let me increase the size of the computer-partition (the partition where all the ubuntu software is to be installed as I understand it) to 100gb. I guess 100 gb might be enough for a while but there's also this warning appearing saying that Ubuntu will have trouble booting if I resize the partition and it says that I'm actually trying to move it although on the previous screen it says it's resizing it. 

What should I do?

Regards

---

### Post by oldfred on 2014-12-17
Post these:
sudo parted -l
Click on any unmounted partitions then run this:
df -h

I create 25GB / (root) partition and use about 11GB of that. And my /home is about 2GB of the 11GB. But I have all my data in data partition(s).
If you are dual booting and will use both systems, you may want a shared NTFS data partition. When I still had XP I had both a NTFS and a Linux formatted data partition.

---

### Post by petermartin2 on 2014-12-18
This is the partitioned harddrive with windows and Ubuntu:
```
Model: ATA Samsung SSD 840 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   349GB  349GB   primary   ntfs
 3      349GB   488GB  138GB   extended
 5      349GB   350GB  257MB   logical   ext2
 6      350GB   354GB  4095MB  logical   linux-swap(v1)
 8      354GB   378GB  24,0GB  logical   ext4
 7      378GB   488GB  110GB   logical   ext4
 4      488GB   500GB  12,6GB  primary   ntfs            diag
```
These are also the partitions showing in gparted and in the installation partition option. I've now reinstalled once more but no matter what I do the installation software changes the computer partition to 25 gb. I've tried reverting and pressing the minus button in installation partition but invariably the installation software changes it back to 25 gb. 

I have all my data as music and such on other harddrives but can I also install software on the other harddrives? In that case how?

---

### Post by sudodus on 2014-12-18
How do you install?

At the partitioning window in the installer, you can select ***Something else*** to get 'full control' of selecting partitions for the root file system and swap (and if you wish a home partition). It should be possible to select partition number 7 as root partition, the symbol **/**

```
Number  Start   End    Size    Type      File system     Flags
...
 7      378GB   488GB  110GB   logical   ext4
...
```

---

### Post by petermartin2 on 2014-12-18
If I take the something else option will that result in an upgrade of my current installation or clean installation? I looked at it but didn't dare use it because I didn't know what it would do. Will it keep my windows? I deleted a couple of smaller partitions in "something else" and pushed "back" afterwards but the installer then created a new 25 gb partition to put the os.

Can it still upgrade when it's on a different partition?

Also I would prefer a way in which I could keep my current installation as I already installed Ubuntu After Install and editet hosts file and set preferences in a dozen programs..

---

### Post by petermartin2 on 2014-12-18
Is there anyway I could merge 7 and 8? they are both logical filesystem "ext4". I tried resizing them in Gparted but nothing seems to happen - I can make 76 GB unalocated but it won't allow me to add them to the "computer" partition

---

### Post by sudodus on 2014-12-18
> **petermartin2 said:**
> If I take the something else option will that result in an upgrade of my current installation or clean installation? I looked at it but didn't dare use it because I didn't know what it would do. Will it keep my windows? I deleted a couple of smaller partitions in "something else" and pushed "back" afterwards but the installer then created a new 25 gb partition to put the os.

Normally you would format the root partition. If there is a home partition, you can select to leave it or format it, which makes a difference between saving your settings or not (the hidden files and directories in the home directory).

You must know which partitions belong to Windows, and avoid touching them.
> 
Can it still upgrade when it's on a different partition?

What do you mean different partition? If you install Ubuntu into a partition, that's it, it is there, will be run there and upgraded there. You can have several installed systems alongside each other (in different partitions). Normally you would like the let all linux partitions share one swap partition.
> 

Also I would prefer a way in which I could keep my current installation as I already installed Ubuntu After Install and editet hosts file and set preferences in a dozen programs..

> **petermartin2 said:**
> Is there anyway I could merge 7 and 8? they are both logical filesystem "ext4". I tried resizing them in Gparted but nothing seems to happen - I can make 76 GB unalocated but it won't allow me to add them to the "computer" partition

You can merge partitions that are neighbours (adjacent to each other). 7 and 8 seem to be possible to merge. But you do that by removing one of them and growing the other partition in the unallocated space.

Remember that such operations are risky! You should ***backup*** all important data before starting with such operations. Backup to another drive (for example an external drive).

---

### Post by grahammechanical on 2014-12-18
You have a MSDOS partition scheme, which only allows us 4 primary partitions. You have 4 primary partitions. They are

#1 367MB NTFS Boot
#2 349GB NTFS
#3 138GB Extended
#4 12.6GB NTFS  diagnostics

Partitions 1, 2, and 4 are Windows related partitions and a quick calculation shows that they take up 361.6 GB of the 500 GB total size of the hard disk.

Partition #3 is a special primary partition called Extended and that allows us to create as many logical partitions inside it as we please but the total size of those logical partitions cannot be greater than the size of the Extended partition. In your case the extended partition size is 138GB.

Partitions #5, #6, #7 and #8 are logical partitions inside #3 and they are the Ubuntu partitions. To increase the size of one of those Ubuntu logical partitions we must first decrease the size of one of the others. Or delete it entirely. The total size of the logical partitions cannot be greater than the size of the Extended partition. That is why your operations are failing.

If you desire, you can, using Windows utilities, decrease the size of partition #2. Then, using Gparted from a live session,  you will be able to increase the size of Extended partition #3. That will create space inside partition #3 that one of the logical partitions can be expanded into.

It is my guess that Ubuntu is installed in partition #8. That is 24GB in size. This is more than adequate for Ubuntu for the normal user even with additional applications installed. If your data is going into partition #7 110GB, then 24GB should be more than enough for Ubuntu. But if you start storing audio and video files in Ubuntu on #8 then it will start filling up.

Oh, by the way the warning from Gparted about losing data that is a normal warning. We get that every time we change or move partitions. I have created, deleted, moved and resized partitions many times. I have never lost any data or found Ubuntu failing to load. I have found other ways to break the OS. But Gparted does not break Ubuntu unless I tell it to do something that I later regret doing.

Regards.

---

### Post by petermartin2 on 2014-12-18
I know which one is which because of the size and I've been looking a lot at them today..

What I mean is that if I install it on a different partition I'm guessing it will be a clean install and none of my software and settings will be stored - unless they are in the linux-swap partition?

I also don't understand why I can't merge 7 and 8. When I try to delete 7 entirely it asks me to unmount any logical partitions higher than 7. I wanted to try it from the installation USB once because I read somewhere you could unmount the "computer" partition (#8) there but the computer dosen't seem to want to boot from the USB once Ubuntu is installed?

---

### Post by petermartin2 on 2014-12-18
I still have 10 gb after installing a lot of the apps I will probably need and the OS is working great but still.. Feels stupid to have a lot of discspace just sitting there doing nothing having been separated both from the windows and the ubuntu partition.

---

### Post by yancek on 2014-12-18
> I also don't understand why I can't merge 7 and 8. When I try to delete 7  entirely it asks me to unmount any logical partitions higher than 7. 

You should be able to unmount the partitions from the system (as long as your Ubuntu install is not on sda7 or sda8, use a Live CD/flash drive) and merge 7 and 8.  These are logical partitions and if you delete 7, then the current sda8 will become sda7, if you have sda9 it will become sda8.  That's just the way it works.

---

### Post by petermartin2 on 2014-12-18
> **yancek said:**
> You should be able to unmount the partitions from the system (as long as your Ubuntu install is not on sda7 or sda8, use a Live CD/flash drive) and merge 7 and 8.  These are logical partitions and if you delete 7, then the current sda8 will become sda7, if you have sda9 it will become sda8.  That's just the way it works.

How do I know which partition my ubuntu install is on? I thought it was on the one called "computer" where all the software goes? This is the one with 23gb it's #8

---

### Post by petermartin2 on 2014-12-18
But [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") said that four of them are ubuntu partitions, i don't understand why there are so many different and all the files just goes in the small one

---

### Post by oldfred on 2014-12-18
If you type the mount command you get a long list, but the one that is / (root) is your install, so my install is in sda3:

fred@trusy-ar:~$ mount
/dev/sda3 on / type ext4 (rw,noatime,errors=remount-ro)


Then it has a long list of logical and other internal mounts. And any other partitions you may have added to fstab to also be mounted by default.

---

### Post by petermartin2 on 2014-12-18
> **oldfred said:**
> If you type the mount command you get a long list, but the one that is / (root) is your install, so my install is in sda3:

fred@trusy-ar:~$ mount
/dev/sda3 on / type ext4 (rw,noatime,errors=remount-ro)


Then it has a long list of logical and other internal mounts. And any other partitions you may have added to fstab to also be mounted by default.

Ok, I understand that there are different internal mounts but they seem to be restricted to their size anyway? 

Update: I think I managed to delete or format the one with 102gb sda 7. It dissapeared from the filewindow. However it still appears in gparted and now with a red expressionmark infront of the now "unknown" filesystem. I still can not delete it from gparted or make sda 8 with the software on it bigger. I tried using a CD but when I chose the first option with partition it started executing commands or something and there were a lot of error signs (this happened I think before I formated sda 7). Ubuntu works just as before

---

### Post by oldfred on 2014-12-18
If you in gparted right click on the red icon gparted will tell you more about the issue. Often file corruption and if Linux ext4 you need to run fsck to repair it, or if NTFS you have to run chkdsk from a Windows repair disk.
You should only be running gparted from a live installer as you cannot work on mounted partitions and you cannot unmount the one you are booted into.

---

### Post by petermartin2 on 2014-12-19
Thanks!
This is from right clicking:

> Unable to detect file system! Possible reasons are:
- The file system is damaged
- The file system is unknown to GParted
- There is no file system available (unformatted)
- The device entry /dev/sda7 is missing

I'm going to try and make another CD today and try and merge them again like you say see if this one works better

---

### Post by petermartin2 on 2014-12-19
I have refrained from taking any more action as the partition that now appears as "unknown" in gparted actually seems to have merged with the partition with grub? It still appears as unknown only in gparted. Why does it appear different in the two different places? Is it still a good idea to merge it with the small OS-partition (if possible)?

---

### Post by oldfred on 2014-12-19
May be best to see details, since you are not sure what is where.

Do not run auto fix, just run the summary report and post link.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by petermartin2 on 2014-12-20
> **oldfred said:**
> May be best to see details, since you are not sure what is where.

Do not run auto fix, just run the summary report and post link.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

The first USB I made didn't do anything - it was not detected at all. With the second one I made I was taken to ubuntu like it looked right after installation. I have tried making also CD:s but it won't burn it I'm guessing it is to small and I really need a DVD but will the computer detect it? The CD is 800 minutes. I will keep working on this

I am thinking of copying my ubuntu install entirely to another harddrive and format the SSD drive it is on and copy it back instead. Is it enough to copy only the 9.4 gb big OS partition or should I copy also the grub partition?

---

### Post by petermartin2 on 2014-12-20
Also I am experiences maybe one crash every 5 hours at the computer. The screen freezes entirely and I can move the mouse cursor but do nothing else and have to restart the computer. Is this something that might be fixed in future updates or is my installation maybe corrupted in someway? I haven't really done anything complicated except merging the grub partition and installing well known apps mainly ubuntu after installation

---

### Post by sudodus on 2014-12-20
Crashes can be caused by many things, hardware as well as software.

- Check the RAM with ***memtest*** from the grub menu (let it run for several hours, for example overnight. One single error is too much).

- Check that the file system is good, and that the hard disk drive is good (the physical blocks), and try to repair it.

Boot from another drive, for example an Ubuntu desktop install drive, unmount all partitions on the internal drive and check them.

```
sudo e2fsck -cf /dev/sdxy
```

where x is the drive letter and y is the partition number. See ```
man e2fsck
``` for details explaining the command. This command takes hours for a big partition.

---

### Post by petermartin2 on 2014-12-25
I finally deleted the whole partition using windows and am now running all my space in one big folder that encompasses the "computer" folder as well as all the ubuntu folder for personal files etc. It's working great hopefully the crashes are gone also with this install but it could also be my graphic card as I've had a lot of trouble with it in ubuntu

---

