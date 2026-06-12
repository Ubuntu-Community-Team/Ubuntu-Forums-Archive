---
title: "Ubuntu 12.04 and harddrives/Windows/partitions"
date: 2012-07-12
forum: New to Ubuntu
---

### Post by IncurableHam on 2012-07-12
Hello everyone!

So I had been using Windows XP and Wubi for a while. I chose Wubi because I didn't really understand how memory and partitions worked. So this summer I started trying out some new OS's and ended up downloading and installing Windows 8 Consumer Preview. Well that didn't really work (no sound, scrolling, app access, etc.), so I decided to install Ubuntu, which I felt comfortable enough with to run by itself. When I started to install Ubuntu from the disc that I burned it onto, an option came up to dual boot with Windows 8...So I did that. I remember just dragging the line that shows the size of the partitions and created some memory for Ubuntu.

Ubuntu works perfectly, but now when I try to start Windows 8 from GRUB, I get a message saying computer is trying to repair, and then it goes to a lightish blue screen that says "Automatic Repair couldn't repair your PC". I don't really care about this as I don't want Windows 8 anymore, but I was just a little confused.

Anyways, the point is I really do not understand how hardware and partitioning work, so I had a few questions:

1.) I have access to Windows 7 which I would like to dual boot with Ubuntu. When installing Windows 7, how can I ensure that it overwrites Windows 8, but leaves Ubuntu? Do I have this option when installing Windows 7?

2.) When I click on my folder button in Ubuntu, I can access my 221GB Filesystem. I guess my question is why can I access this? It's not part of the Ubuntu partition. And why can't I copy/paste files from it, but I can still access and open the files directly?
EDIT: I can copy/paste them to any folder, but I'm still confused as to why I can access all of the folders from my Windows partitions when using Ubuntu

3.) When I use the sudo parted -l command, I get this:

Model: ATA Hitachi HTS72322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  221GB  221GB   primary   ntfs            boot
 3      221GB   249GB  27.5GB  extended
 5      221GB   245GB  23.3GB  logical   ext4
 6      245GB   249GB  4190MB  logical   linux-swap(v1)
 2      249GB   250GB  1078MB  primary   fat32           lba

Can someone explain what this all means? I think these are my partitions, but I don't know what they are all. Also, is it possible to make my Ubuntu partition bigger?

Thanks for any help in advance. I'm obviously super confused about partitions and such because schools apparently think that CS students only need to know about software...

---

### Post by tacobellington on 2012-07-12
i can answer the first question for you.

if you want windows seven on your computer, then what i would do is back up ubuntu to ubuntu one.
 then i would run the windows 7 installer from the disk and set it to take up the whole hardrive, then run the ubuntu disk and run it along side windows 7 and partion the disk to about half or put more memory on whichever side you would like to use more often. then run the backup and restore program, sign into your ubuntu one account and click restore or something like that...that should work for you.

Hope i helped a little...bye

---

### Post by NikTh on 2012-07-13
> **IncurableHam said:**
> 

1.) I have access to Windows 7 which I would like to dual boot with Ubuntu. When installing Windows 7, how can I ensure that it overwrites Windows 8, but leaves Ubuntu? Do I have this option when installing Windows 7?

2.) When I click on my folder button in Ubuntu, I can access my 221GB Filesystem. I guess my question is why can I access this? It's not part of the Ubuntu partition. And why can't I copy/paste files from it, but I can still access and open the files directly?
EDIT: I can copy/paste them to any folder, but I'm still confused as to why I can access all of the folders from my Windows partitions when using Ubuntu

3.) When I use the sudo parted -l command, I get this:

Model: ATA Hitachi HTS72322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  221GB  221GB   primary   ntfs            boot
 3      221GB   249GB  27.5GB  extended
 5      221GB   245GB  23.3GB  logical   ext4
 6      245GB   249GB  4190MB  logical   linux-swap(v1)
 2      249GB   250GB  1078MB  primary   fat32           lba

Can someone explain what this all means? I think these are my partitions, but I don't know what they are all. Also, is it possible to make my Ubuntu partition bigger?

Thanks for any help in advance. I'm obviously super confused about partitions and such because schools apparently think that CS students only need to know about software...

**Hello and Welcome to Ubuntu Forums ! **

1) I don't really think so. Why ? Because windows 7 are older than windows 8 and maybe (maybe i am not sure) you will not have this option for replace. 
The best thing (imho) its to delete windows 8 partition and then install windows 7 there. 
You must know something that probably you will face : Windows 7 will overwrite MBR with their boot-loader so you will not be able to boot  Ubuntu. You must do a boot-repair process with this automatic tool --> [http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482) from a Ubuntu LiveCD ,so Grub2 (boot-loader of Ubuntu) return to its place (Mbr). 
Grub 2 has the ability to recognize most of Operating systems (include windows) , unlike windows boot-loader it has the ability to recognize ONLY windows Operating Systems. 

2)You can access windows files and all files , because Ubuntu has the ability to recognize all filesystems. Those are your partitions but are also your Disk. If windows had the same ability as Ubuntu (and could access ext4 filesystem native) then probably would see Ubuntu's partition from windows installation , but windows recognize ONLY their filesystems (Ntfs , Fat32).

3)First partition is windows primary partition (Ntfs) , windows 8 i guess.
2nd is just an Exntedend partition (there you can place as many logical partitions as you want)
3d is your Linux(Ubuntu) partition .Ubuntu installation
4th its linux swap . Swap memory . Swap memory used by the system when physical memory extinct .
5th is a Fat32 filesystem but i don't know what you have in there. 

I hope answered your questions.
Thanks

---

### Post by Shadius on 2012-07-13
Installing Windows 7 on your current system which has Windows 8 Consumer Preview and Ubuntu might take over the entire hard disk drive and leave you with just Windows 7. I'm not sure if Windows gives you the option of installing to a partition. I think it should have that option, if my memory serves me right. I agree that you should just delete the Windows 8 Consumer Preview partition and then see if Windows allows you to install Windows 7 to that former Windows 8 Consumer Preview partition. NikTh pretty much summed up everything. Also, just a friendly tip, when posting code from the Terminal, use the "#" symbol to wrap the code in [CODE] tags. It's a lot easier to read that way. :)

---

### Post by IncurableHam on 2012-07-13
Thanks for the replies everyone, you are all lovely human beings.

When you say to delete Windows 8 from the hard drive, does this just happen automatically when I install Windows 7, or is it something I need to do manually beforehand? I don't mind uninstalling Ubuntu and then installing it after I have Windows 7 installed because I don't really have any new files on Ubuntu yet (that isn't on an external harddrive). 

So it's easier to just install Windows 7 on the entire drive, then reinstall (or boot-repair) Ubuntu, creating a partition?
Also, when I reinstall Ubuntu, GRUB will automatically be reinstalled and set as the primary boot loader, correct?

Also, does anyone with an HP know what the HP Tools drive is for? It seems like it has a lot of wasted memory there...

Thanks again!

---

### Post by NikTh on 2012-07-13
> **IncurableHam said:**
> Thanks for the replies everyone, you are all lovely human beings.

When you say to delete Windows 8 from the hard drive, does this just happen automatically when I install Windows 7, or is it something I need to do manually beforehand? I don't mind uninstalling Ubuntu and then installing it after I have Windows 7 installed because I don't really have any new files on Ubuntu yet (that isn't on an external harddrive). 

So it's easier to just install Windows 7 on the entire drive, then reinstall (or boot-repair) Ubuntu, creating a partition?
Also, when I reinstall Ubuntu, GRUB will automatically be reinstalled and set as the primary boot loader, correct?

Also, does anyone with an HP know what the HP Tools drive is for? It seems like it has a lot of wasted memory there...

Thanks again!

Hi, 
well these are different circumstances. 
If delete entire disk and install windows 7 on entire disk , then you don't need to do a boot-repair . After windows 7 install finish, you can install Ubuntu and Ubuntu will put grub boot-loader in MBR . So you will have no problem. 
I think this is the best solution.  

If delete only windows 8 (gpated tool from Ubuntu LiveCD/Usb can do this job successfully) , then you must install windows 7 on deleted partition . When install finish you must run boot-repair(from LiveCD)  to correct MBR , to be able boot Ubuntu. 

For HP-Tools partition , read official HP-forum --> [http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/What-is-inside-the-quot-HP-Tools-quot-partition/td-p/216428)
Thanks

---

### Post by IncurableHam on 2012-07-13
> **NikTh said:**
> 
If delete entire disk and install windows 7 on entire disk , then you don't need to do a boot-repair . After windows 7 install finish, you can install Ubuntu and Ubuntu will put grub boot-loader in MBR . So you will have no problem. 
I think this is the best solution.  

Thanks

Great, thanks NikTh! To delete entire disk, will it just do that  automatically when I install Windows 7? I think this will be the easiest  way, and since I don't care about keeping any Ubuntu files, I will just  install Ubuntu after Windows 7.

And thanks for the link

---

### Post by NikTh on 2012-07-13
> **IncurableHam said:**
> Great, thanks NikTh! To delete entire disk, will it just do that  automatically when I install Windows 7? I think this will be the easiest  way, and since I don't care about keeping any Ubuntu files, I will just  install Ubuntu after Windows 7.

And thanks for the link

Yes you can do that. I think first you must select and delete the  partitions that include Ubuntu and windows ([COLOR=Red]careful [/COLOR]do not delete HP recovery or tools partitions)
In the window that asks you " Where do you want install windows?" you first pick the partition and then click [COLOR=Red][COLOR=Black]"[/COLOR]X[/COLOR] delete" . You will notice, when delete partitions, disk united and space stated as unallocated. 
Then you can choose to install windows to your new united partition. Windows will create a NTFS filesystem and proceed with installation.

---

### Post by oldfred on 2012-07-13
Windows 7 default install to a empty drive is two primary partitions. One small 100MB boot/repair and the main install. But 7 has always over installed to Vista and in that case just uses one partition with the boot files. One reason for the separate boot partition was so you could encrypt the main partition as the boot files could not be encrypted.

So if you leave the sda1 as NTFS with the boot flag, Windows 7 should just install to that partition. 

I often suggest only 25G for / (root) if you have a separate /home or use a separate data partition for all or most of your data. And if dual booting I suggest a separate NTFS shared data partition for any data you may want to use from both systems. I still have my Firefox & Thunderbird profiles and all photos for Picasa in my shared NTFS even though I almost never boot XP now.

You can shrink your sda1 to leave room for a NTFS partition if you want. Windows 7 needs 30GB as a working minimum but if you install lots of large games it may need a lot more. But 50 to 100GB should be plenty and then you can use the remaining 122GB for shared data.

---

