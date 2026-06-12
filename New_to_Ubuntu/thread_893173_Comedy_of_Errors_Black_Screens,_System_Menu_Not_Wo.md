---
title: "Comedy of Errors: Black Screens, System Menu Not Working, Error 17..."
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Anonymong on 2008-08-18
Three days ago I installed Kubuntu without any problems on my machine. Then yesterday I encountered a chain of possibly unrelated issues with Kubuntu that cascaded into one horrible mess.

1) The System Menu on the panel refused to work, instead of opening any folder (whether it is ‘Documents’, ‘System Media’, ‘Root’ and ‘User Home’; all of them) it asked me what program I wish to use to open them with? The System Menu option has also disappeared from my panel.

2) I rebooted the machine. After the log-in I was taken to a black screen. Could not see or do anything from here. The same happens after I picked the recovery mode from the GRUB menu after the next reboot.

3) After I rebooted the machine after what must have been a third or forth time, GRUB refuses to work. Instead of the menu where I could select my OS, I get a message that reads “GRUB loading please wait” then “Error 17”.

I’m using another computer to type all this, though I understand that I could have used my live CD to access the internet. 

I guess I must have foolishly jumped right into the deep-end; I cannot be sure what I’ve done to have gotten here. I think I’d prefer to remove Kububtu altogether from my machine, maybe start over another time, but would also lose the partition I’ve made? I have only one physical HD that was split into four virtual drives, Kububtu furthermore divided two into one (possibly as a result of an accident on my part).

I’m a total newbie and utter moron, so please if you could help, explain in a way that myself and others would understand.

---

### Post by nicedude on 2008-08-18
You will have to give everyone more info for us to help you figure out what you have done. For starters boot the a live cd on the PC in question and type the following command in a terminal and post its output here.

sudo fdisk -l

That will list what all partitions are currently on the drive. Also any info as to what changed from the PC working to not working would help, such as anything you installed and any use of the disk partitioner. Anything you can think of would be helpful to us all.

---

### Post by Anonymong on 2008-08-18
Sorry if I haven't been very descriptive, post was written in a hurry.

I've booted up the live disk and now in the OS. I'm not too sure where to type the command, I suspect you mean in the Konsole terminal (sorry, like I said I'm new to all this) and I got this output:

> ubuntu@ubuntu:~$ sudo fdisk -1
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION     Give partition size(s) in blocks
       fdisk -v     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
ubuntu@ubuntu:~$


Cannot recall any other information sorry. All I know is that I haven't been playing around with anything that I don't have 100% knowledge on how it works.

---

### Post by nicedude on 2008-08-18
that was supposed to be "sudo fdisk -l" as in L not a 1 one ( I know they look just alike ) running that command will list all of your partitions and let everyone see what is up.

Please post with same command with a small L. Without seeing all your partitions we can't tell you anything about what to do to try and fix anything you have messed up.

---

### Post by Anonymong on 2008-08-18
Ach! Sorry, I'm such a moron. Just typed in the correct command and got this:

>  
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4dc22187

Device Boot Start  End     Blocks    Id  System
/dev/hda1 *       1   2502    20097283+  c  W95 FAT32 (LBA)
/dev/hda2   2503   8040    44483985   f  W95 Ext'd (LBA)
/dev/hda5   2503   5005    20105316   7  HPFS/NTFS
/dev/hda6   5006   5404     3204936   b  W95 FAT32
/dev/hda7   5405   7414    16145293+  83  Linux
/dev/hda8   7415   7508      755023+  82  Linux swap / Solaris
/dev/hda9   7509   8040     4273258+   b  W95 FAT32
ubuntu@ubuntu:~$ 

Sorry about the headache inducing post. I suspect that hda refers to my hard drive, right?

---

### Post by nicedude on 2008-08-18
Whoa you are the winner of most partitions I have seen yet on one disk. That isn't a good award to win by the way. Yes hda stands for your disk and the numbers after that are each signifying a partition, I will try to list what all these are, some of this is guessing and I have no idea how you created them all like this.

Device Boot Start End Blocks Id System
OK I am thinking this a Windows 98 or XP partition and is bootable
/dev/hda1 * 1 2502 20097283+ c W95 FAT32 (LBA)

This sda2 is the is an extended partition which means it contains nothing but other partitions, these are called logical partitions and you have allot of them inside sda2 
/dev/hda2 2503 8040 44483985 f W95 Ext'd (LBA)

These 2 sda5 & sda6 most likely contain some system restore partition and utilities, these 2 were on your PC from the beginning and should only be removed if you don't want to ever use them to restore your WIndows XP ( guess on XP ). Although you may run into trouble even trying to use the system restore key ( usually a hotkey at boot up like CTRL+F11 or CTRL+F12 consult your model laptop to be sure ) as these sometimes rely on the disks MBR being intact and Grub overwrites it when you install linux anyway. But once again consult the instructions for you model on how the system restore works etc. I delete these types of partitions on PC's I own but then again I have XP & Vista disks so I don't need them either, so its up to you as to what to do with these
/dev/hda5 2503 5005 20105316 7 HPFS/NTFS
/dev/hda6 5006 5404 3204936 b W95 FAT32

Here is your Kubuntu and then your Swap dont delete these or no more Kubuntu
/dev/hda7 5405 7414 16145293+ 83 Linux
/dev/hda8 7415 7508 755023+ 82 Linux swap / Solaris

This must be the last partition you made and it looks like you did so for storage reasons although it is pretty small.
dev/hda9 7509 8040 4273258+ b W95 FAT32


So hda1 hda2 hda7 & hda8 are all needed to boot both windows and Linux.

I need you to copy your grub menu.lst file and post it here so we can see what grub is trying to load and why it is erroring

here is a command that will copy your grub menu.lst to the desktop then open it with the text editor and paste the whole thing here. I am doing it this way so there is no chance of screwing it up as the one that will be made on your Desktop will be just a copy.

HERE IS THE COMMAND
cp /boot/grub/menu.lst ~/Desktop/menu.lst 

now post the contents of that thing and I will try and crack this problem.

---

### Post by Anonymong on 2008-08-18
I don’t want you to think I’m just wasting your time; I would just like to say thanks for your continued support!  

The situation has now changed for the better, thanks to your last post. You mentioned something about MBR and I don’t think I was even smart enough to have left a system restore point previously, so I looked up on what this MBR means and found almost by accident a way of overriding GRUB using my Windows disk. Inserted the Win boot disk I whacked F11 and at this thing called the ‘recovery console’ I typed ‘fixmbr’. I can get back to XP.

Now when I select Kubuntu and the OS select I get back to GRUB and return to the ‘Error 17’ screen and not Kububtu, except this time, I can now press any button to leave it and return to Windows. 

Yeah there are too many partitions on my poor HDD, originally the machine was split equally between four, kubuntu then further divided two. I was trying to find a way for it to take a whole empty partition, but I made a mistake and somehow divided two into halves. 

hda1 is indeed where I keep my Windows XP-64 system files. No idea why it came up on command line as Win95.

I’m looking at my own command line output, and I think hda9 and hda6 are the leftovers for Windows from my Kubuntu partitions, though not certain. I guess this partition called ‘16g media’ (from the system menu from the live CD) must be the new partition made from the two original partitions? I’m hoping that if I do have to uninstall Kubuntu, it’d get my HDD back to where it was (four), but that will have to wait.

Typed the command but I don’t think it is the output you are looking for, maybe I'm doing it in the wrong place or maybe at this stage it is a bit unnecessary now. 

>  
cp: cannot stat `/boot/grub/menu.lst': No such file or directory
ubuntu@ubuntu:~$

As I said earlier, I can now access XP so the biggest issue is over, ubuntu not working still.

---

### Post by nicedude on 2008-08-18
That error tells me your grub directory has been either deleted or installed to another partition which is why you were getting the boot error. It is a bit complicated but I will try to explain this as simply as I can think of so you can learn how this all works. It is something you should learn as it will help you in the future to figure out this kind of stuff and to know what to avoid doing. As far as your system, if you had just installed Ubuntu then I would think about starting over by first deleting at least all partitions hda7 and up or hda2 and up if you want to get back your system restore partition space ( as in if you have an XP install cd you wouldn't need it anyway )


Here is briefly how this all works 

Windows any version writes code to the MBR to allow it to boot, as the MBR is where the PC looks to see how to start up. With Windows the MBR just loads whatever your windows partition is and that is it.

Linux has to over write this MBR with Grub ( grand unified bootloader ) which like the windows bootloader code is the first stop for the PC on what to load. Now Grub's MBR code unlike Windows does not fit in the very small space of your disks MBR area so it must also write the remainder to a partition on the hard disk, it normally does this on the partition you are installing linux to, but iregardless it cant use a windows system partition to store that data as that would screw up Windows. So once you install Linux & Grub you have taken over the MBR where windows code resided and replaced it with Grubs code, the remainder that doesn't fit will also go to your Linux partition and at this point Grub loads XP with a special command to make it think it just got loaded by its own old MBR code ( ie the one Grub took out ). So if for any reason you /boot/grub/ folder gets trashed then not only will Linux not boot neither will windows, now as you found out on your own you can use a Windows install disk to do a fixmbr and it will just overwrite the grub MBR code with Windows MBR code once again. The other way to solve this would be to use a supergrub bootdisk and reinstall grub to your Ubuntu partition. But if I were you I would start over first since you already have a mess of partitions. If you have a standard XP install CD then I would delete partitions hda2 and up leaving just hda1 which is XP then reboot to reset the partition tables ( that is important ) and use live CD to install ubuntu while making 2 partitions one of 2GB formated as SWAP and the second 20GB-30GB as EXT3 with a mount point of / which will be for Ubuntu. then reboot again so you should now have dual boot working, now use the partition editor in Ubuntu to make the rest of your free space a storage container that you could access form XP or Ubuntu you could format it FAT32 or NTFS ( fat32 max filesize per file 4gb so keep that in mind ). Either of those formats will work well to use them in both Windows and Ubuntu easily. This is how I setup my laptop and I have no worries or problems with this setup and neither will you.


Hope this all helps you wrap your head around how this all works.

---

### Post by Anonymong on 2008-08-18
Thanks for that. I think the way out of this quagmire won't be too long now.

Problem is I hear messing around with the partitions is difficult and fraught with potentialilty for error (as you can already see, me and error go hand in hand). When you say delete partitions hda2 (and the others) did you mean merely format them or use my XP boot cd to remove them? I think I got a copy of Partition Magic somewhere, will this help in any way? If this will return my partitions to four as opposed to seven (or even to just two), that will be amazing!

I will try reinstalling kubuntu at a latter time, from what I gather from your post making the larger partition (the smaller one just for saving stuff right?) the 'mount point' is like where I stick the important guts of the OS right? 

Thanks for all your help!

---

### Post by nicedude on 2008-08-18
What I was trying to say is that if you have XP CD's to do a reinstall with if you should ever need to, then you don't need any of the partitions your manufacturer made to contain restore data ( they do this since they are cheapskates and it takes up drive space that you could use for yourself instead ). If you don't have an XP CD then you might need the data contained on them ( if you do have install CD's you don't for sure ). So assuming you do have an XP install CD then look at the following

YOUR DISK IS 82GB 
Disk /dev/hda: 82.3 GB, 82348277760 bytes

HERE IS 25GB WHICH CONTAINS XP - LEAVE THIS ALONE
/dev/hda1 * 1 2502 20097283+ c W95 FAT32 (LBA)


THIS IS A VIRTUAL CONTAINER THAT CONTAINS ALL THE REST OF YOUR PARTITIONS
/dev/hda2 2503 8040 44483985 f W95 Ext'd (LBA)

HERE ARE 25GB OR SO OF DATA THAT IS PROBABLY SYSTEM RECOVERY - UNLESS YOU MADE THEM FOR DATA YOURSELF, IF THEY ARE SYSTEM RECOVERY RELATED THEY ARE WASTING YOUR SPACE
/dev/hda5 2503 5005 20105316 7 HPFS/NTFS
/dev/hda6 5006 5404 3204936 b W95 FAT32

THESE ARE YOUR LINUX PARTITIONS
/dev/hda7 5405 7414 16145293+ 83 Linux
/dev/hda8 7415 7508 755023+ 82 Linux swap / Solaris

THIS IS LIKE 5GB THAT YOU MUST HAVE MADE FOR DATA
/dev/hda9 7509 8040 4273258+ b W95 FAT32


If you delete hda2 and up with a live cd partitioner you will end up with only Windows XP on hda1, now reboot to reset the partition tables.

Then boot with the live Ubuntu CD again ( I would recommend Ubuntu over Kubuntu but that is my preference I guess ) and now when you install choose manual partitioner when you get to that step 

Make a 2GB SWAP partition and then a 25GB EXT3 with the mount point set as / which means ROOT, this is where Ubuntu/Kubuntu will install to. Once it is installed reboot again.

now you would have 

hda1 25GB XP
hda2 2GB SWAP
hda3 25GB EXT3 containing Linux

And roughly 25GB of free space which you can then format as either FAT32 or NTFS and easily access from both Ubuntu or XP, and it would end up being hda4 when you make it.

That would be all nice and clean way to take care of this situation and leave you with a sweet dual boot setup.

And yes you are a dangerous man with a partitioner ( you are not allowed near my disks :-) ) but just follow this advice and you can do it just fine :-)

Goodluck and feel free to PM me if you get stuck.

---

### Post by cocokiwi on 2008-08-18
> **Anonymong said:**
> Sorry if I haven't been very descriptive, post was written in a hurry.

I've booted up the live disk and now in the OS. I'm not too sure where to type the command, I suspect you mean in the Konsole terminal (sorry, like I said I'm new to all this) and I got this output:



Cannot recall any other information sorry. All I know is that I haven't been playing around with anything that I don't have 100% knowledge on how it works.

OK! The live version allows you to PLAY with it and get used to it,and it by loading tells you it will work on your system!

it can be installed on any drive that has a large space!If you have a DRIVE to spare USE it. 

Notes: #1 Linux uses lowercase...don't like  George--george ok!
       #2 mostly it is much like MS but has a longer learning curve, TWO handy books   Ubuntu rev 8 and Hacking Ubuntu 
       # 3   note what I did below,then you won't get it all working and suddeny find you cannot run it!

Don't be afraid of it have fun, Explore and read a couple of books on Linux!     

can I add something! I HAD the same problem!

**GRUB fix**


TO all ,

 GRUB is an OLD program and as such is a little BEHIND in some newer item's...HARD DRIVES have gone from VERY small to VERY BIG and the way they are setup has changed also,hence the Dreaded ERROR 17   _ PARTITION found but cannot find file!

AH! the problem is!

  80 gig hard drive  listed in AUTO  CYL  =38309 head = 16

  80 gig hard drive  listed in LARGE CYL  =2553  head = 240


and you wonder WHY it don't work right!(grin) AUTO starts the drive at a higher Cylinder location than LARGE do so,GRUB is looking for it down in the LARGE area 2553,it can see the file but cannot find it! (fix change GRUB software to scan BOTH locations)


SET the Hard drive you are using to LARGE instead of AUTO.

Dennis:KS

---

