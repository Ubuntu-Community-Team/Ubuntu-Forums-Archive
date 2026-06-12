---
title: "Windows 7 on /dev/sda3, Ubuntu 12.04 on /dev/sda1. Con only boot into Win 7."
date: 2013-12-15
forum: New to Ubuntu
---

### Post by RayArdia on 2013-12-15
I installed Windows 7 simply because Sketchup Make refuses to run properly under Wine.
I used Gparted to resize and make a new partition /dev/sda3, leaving(I HOPE!) Ubuntu 12.04 on the original (resized /dev/sda1). Windows boots up and runs fine, but I don't know how to get back into Ubuntu.
I did at one stage get a screen which offered me a choice of OS - Win 7 or _BLANK_, Ubuntu was not there.
Have made a copy of all my Ubuntu files etc on an external HDD, but I could use some help getting back into Ubuntu!

---

### Post by 3rdalbum on 2013-12-15
Run Boot Repair from the Ubuntu Desktop CD or the Boot Repair Live CD.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by RayArdia on 2013-12-16
> **3rdalbum said:**
> Run Boot Repair from the Ubuntu Desktop CD or the Boot Repair Live CD.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thank you. Now have CD of Boot Repair, booted from it and followed its instructions; sadly, although I now have a screen giving me options to boot into Ubuntu (normal or repair modes), some other options and Win7. The ONLY one which results in a booted OS is Win7, very smooth. Choosing Ubuntu give a screen 'running in low definition' or similar wording with 4 options listed, only the top one 'run in this definition once', or something similar is selected (the others cannot be selected). 'Enter' gives a further screen at which point the system freezes, the only option being a 'hard shut down'.
Sorry to be a bit vague about screen contents but of course I can't take screen shots nor open the sequence whilst using Win 7 to get to this forum!
It would seem that my Ubuntu 12.04 installation is still in /dev/sda1 but I can't get it running. As I have copies of all the important 12.04 system files, I could, in the worst case format the sda1 partition and reload Ubuntu - perhaps moving on to 13.04. Trouble is I don't feel competent to do all that without a 'guiding hand'.
In a nutshell, I'm stuck and could use some help.

---

### Post by tfrue on 2013-12-17
RayArdia,

I would suggest booting into Gparted from a live boot or live boot something like Ubuntu so you can do some partitioning. If you have backed up all your files and aren't worried about starting over, I would just delete the partition on /dev/sda1 and making a new Linux partition for 13.04. I'm going to use fdisk, since I'm more familiar with that rather than Gparted which means you would need to live boot Ubuntu, to begin you will need root privileges so use "sudo" (Also note that I'm using sdc as an example, you would type sda):

```
sudo fdisk /dev/sdc
```

You should see "Command (m for help)" and if you press "m" you will see: 
```
Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)
```

Since we want to delete the first partition, type "d", I have only one partition on my example drive, but it would ask which partition number 1-4 and you would type "1".

Now we should have three available primary partitions to use. Lets now create a new primary partition, so type "n", then "p" for primary, then "1" for first partition, then take the default first sector by pressing enter, then the default last sector or +size example below:

```
Command (m for help): nPartition type:
   p   primary (0 primary, 0 extended, 4 free)
   e   extended
Select (default p): p
Partition number (1-4, default 1):
Using default value 1
First sector (2048-61424639, default 2048):
Using default value 2048
Last sector, +sectors or +size{K,M,G} (2048-61424639, default 61424639):
Using default value 61424639
```

On the question about the Last Sector, this is where you specify how large that partition will be. So if you wanted to use the same exact size of your first Ubuntu install, then you would type(We will use 50GB for example):

```
Last sector, +sectors or +size{K,M,G} (2048-61424639, default 61424639):+50G
```

Now we have successfully deleted and created a new partition, so we must now give the partition a type. Type "p" to list the partition, and if the new partition has an ID of 83 and a System of Linux, then you don't have to worry about creating a type, but for the sake of it (Note that you can type "l" to list all the FS types, but for Ubuntu, the Hex code 83 will work.):

```
Command (m for help): t
Selected partition 1
Hex code (type L to list codes): 83
```

Now write the changes by typing "w" and now we can begin to make a file system on the new partition so we can use it.

To make a file system, you need to be root so we use "sudo":

```
sudo mkfs.ext4 /dev/sdc1
```

I want to note that I changed the size of my partition so it would format it faster but you will still get similar results. Here is the output of that command:

```
mke2fs 1.42.8 (20-Jun-2013)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
Stride=0 blocks, Stripe width=0 blocks
2560 inodes, 10240 blocks
512 blocks (5.00%) reserved for the super user
First data block=1
Maximum filesystem blocks=10485760
2 block groups
8192 blocks per group, 8192 fragments per group
1280 inodes per group
Superblock backups stored on blocks:
        8193


Allocating group tables: done
Writing inode tables: done
Creating journal (1024 blocks): done
Writing superblocks and filesystem accounting information: done
```

So you should now be able to use that partition! Live boot 13.04, just be sure to install it to the proper partition (/dev/sda1) and I hope that fixes your problem.

---

### Post by RayArdia on 2013-12-18
Thank you. I decided to use the gparted route as it seemed simpler to a dumbo like me!
Result!  - However I now have Win 7 in an ntfs partition and Ubuntu 13.04 in an ext4 prtition, both work fine but the Ubuntu partition is too small. There are two other 'Volumes ' listed_ in the Ubuntu file system_, one of 24GB which I assume from its contents to be the Win 7 one and another of 210GB which I don't seem to be able to access from either OS.
Have tried to use fdisk to show me more but get confused - man fdisk and help are a bit too obscure for me I regret.
 The screenshot of 'Details' shows the HDD as only 13.1GB, [ATTACH=CONFIG]248724[/ATTACH] I assume this refers to the Ubuntu 'volume??' only. Actual HDD total is 320GB.

Can you help by telling me how to help you to help me?

---

### Post by oldfred on 2013-12-18
Post these commands from the terminal, click on Windows partition in Nautilus or file browser first as second command only shows mounted partitions:

       sudo parted /dev/sda unit s print
df -H

---

### Post by fantab on 2013-12-18
Apart from 'df -h' it will also help if you can post the output of the following commands as well:
```
sudo parted -l
sudo fdisk -l
```

---

### Post by RayArdia on 2013-12-19
> **oldfred said:**
> Post these commands from the terminal, click on Windows partition in Nautilus or file browser first as second command only shows mounted partitions:

       sudo parted /dev/sda unit s print
df -H
Thank you oldfriend
Screenshot of result:-
[ATTACH=CONFIG]248731[/ATTACH]

---

### Post by RayArdia on 2013-12-19
> **fantab said:**
> Apart from 'df -h' it will also help if you can post the output of the following commands as well:
```
sudo parted -l
sudo fdisk -l
```

Thank you fantab
Screenshots as a result:-
[ATTACH=CONFIG]248734[/ATTACH][ATTACH=CONFIG]248735[/ATTACH]

---

### Post by fantab on 2013-12-19
> **RayArdia said:**
> 
Result!  - However I now have Win 7 in an ntfs partition and Ubuntu 13.04 in an ext4 prtition, both work fine but the **Ubuntu partition is too small**. There are two other 'Volumes ' listed_ in the Ubuntu file system_, one of 24GB which I assume from its contents to be the Win 7 one and another of 210GB which I don't seem to be able to access from either OS.

   .............Actual HDD total is 320GB.

According to 'parted -l', your HDD is 250GB and not 320GB as you think.
Your 2nd partition NTFS is Windows (23.7Gb) and your partition No.5 is Linux swap (3Gb).

There are two Linux partitions, partition No. 1 (210Gb), and No. 6 (13.5Gb).
Not sure which of the two is your '/' root partition. Post the output of:

```
df -h
```

---

### Post by RayArdia on 2013-12-19
> **fantab said:**
> According to 'parted -l', your HDD is 250GB and not 320GB as you think.
Your 2nd partition NTFS is Windows (23.7Gb) and your partition No.5 is Linux swap (3Gb).

There are two Linux partitions, partition No. 1 (210Gb), and No. 6 (13.5Gb).
Not sure which of the two is your '/' root partition. Post the output of:

```
df -h
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        13G  9,0G  2,7G  78% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,5G  4,0K  1,5G   1% /dev
tmpfs           297M  884K  296M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,5G  212K  1,5G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sdc1       294G  179G  101G  64% /media/raymond/Phillips

You're correct re HDD size this laptop is 250GB, my wife's is the 32oGB!
output is
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda6        13G  9,0G  2,7G  78% /
none            4,0K     0  4,0K   0% /sys/fs/cgroup
udev            1,5G  4,0K  1,5G   1% /dev
tmpfs           297M  884K  296M   1% /run
none            5,0M     0  5,0M   0% /run/lock
none            1,5G  212K  1,5G   1% /run/shm
none            100M   24K  100M   1% /run/user
/dev/sdc1       294G  179G  101G  64% /media/raymond/Phillips

---

### Post by fantab on 2013-12-19
13.5Gb partition is Ubuntu root, '/', which is partition No. 6 or /dev/sda6.

Yes, IMO its bit small, but its more than what is needed for default ubuntu install.
Ideally it should be 20-25Gb.

If you are open to re-installing Ubuntu then you can set up the partitions suitable for your needs. 

I have recently helped my friend install Ubuntu as dual boot with Win8 and I partitioned the HDD as:
> 50Gb Primary NTFS Win7
20Gb Primary Ext4 Ubuntu
20Gb Primary Ext4 Free (I case we want to install another distro or another flavor or version of Ubuntu)
160Gb EXTENDED
156Gb Logical Ext4 DATA or /home
4Gb Logical LinuxSWAP

---

### Post by RayArdia on 2013-12-19
Thanks fantab.
The Win7 partition doesn't need to be big - I only use windoze for running Sketchup, as it doesn't like Wine. Ideally I want as big a Ubuntu partition as possible, and as l made a horlicks of it last time and ended up with 'strange' partitions * I could use a bit of a guide*!

---

### Post by oldfred on 2013-12-19
My partition suggestions would almost match fantab's as those are very good. 

But partitions are very personal and depend a lot on your needs. And I find my own optimal partition plan is obsolete a year or two later as I change.

---

### Post by RayArdia on 2013-12-19
Thanks fantab.
The Win7 partition doesn't need to be big - I only use windoze for running Sketchup, as it doesn't like Wine. Ideally I want as big a Ubuntu partition as possible, ansly made a horlicks of it last time and ended up with 'strange' partitions * could use a bit of a guide*!

---

### Post by fantab on 2013-12-19
> **RayArdia said:**
> Thanks fantab.
The Win7 partition doesn't need to be big - I only use windoze for running Sketchup, as it doesn't like Wine. Ideally I want as big a Ubuntu partition as possible, ansly made a horlicks of it last time and ended up with 'strange' partitions * could use a bit of a guide*!

It is a good idea to have atleast 30% 'Free Space' in your Windows C: partition for optimal performance. So you know best how much space you need.

If reinstalling Windows is an option then I would reinstall it on a first partition, and leave rest of the HDD space for Linux/Ubuntu. If you go this way then "Backup all Important DATA" before you re-install Windows.

You don't have enough room in your current EXTENDED/Logical Parittion to adjust or resize partitions. So re-creating partitions and re-installing Ubuntu will help.

You can use Gparted from Ubuntu DVD/USB to manage partitions. 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

NOTE: If you create a NTFS partition for Windows with Gparted then when re-installing Windows use Windows installer to reformat the partition with NTFS.

---

### Post by RayArdia on 2013-12-20
> **fantab said:**
> According to 'parted -l', your HDD is 250GB and not 320GB as you think.
Your 2nd partition NTFS is Windows (23.7Gb) and your partition No.5 is Linux swap (3Gb).

There are two Linux partitions, partition No. 1 (210Gb), and No. 6 (13.5Gb).
Not sure which of the two is your '/' root partition. Post the output of:

```
df -h
```
Apologies for delayed reply - output of df -h is:-[ATTACH=CONFIG]248754[/ATTACH]

---

### Post by fantab on 2013-12-20
Didn't you post 'df -h' information in your post #11?

Good Luck

---

### Post by oldfred on 2013-12-20
Rather than post screenshots, for terminal or text just copy & paste. If a long output use code tags, # in advanced editor adds the tags easily.

---

### Post by RayArdia on 2013-12-20
Still having trouble. Booted from live Boot Repair CD and, with gparted, deleted the small 13.1GB partition which contained Ubuntu 13.04.
Rebooted 13.04, same result as before Ubuntu installs on /dev/sda6 as before, leaving dev/sda1 empty.
How do I  get Ubuntu 13.04 to install on sdA1?

---

### Post by fantab on 2013-12-20
Don't let the Ubuntu's installer do the automatic install to the disk, you should take control manually. 
To do this you have to choose the option "SOMETHING ELSE" at the 'Installation Type' dialog during installation. And then guide the installer to install on /dev/sda1 or whichever partition you like.
After choosing 'Something Else' option you are presented with a dialog showing your HDD partitions, select the partition you want to install Ubuntu to and click 'Change' button, that partition settings will be revealed. Use following settings:
Use as : Ext4 Journaling system....
Mountpoint : /
Format : check it to format

Ubuntu installer just does the basic job of partition, ie it creates a '/' partition and swap.
If you want to keep your data separate make a separate '/home' partition. Use following settings for the partition to be used as /home:
Use as : Ext4
Mountpoint : /home
Format : check to select

If you have Swap partition already then you don't have set it up again, it will be found by the installer and put to use.

Thats it, the rest of the installing is done by the installer.

If you don't want to partition your HDD as suggested earlier and want to continue with what you have then:
Delete partition No's. 3, 6 and 5, as shown in your 'parted -l' output,  with Gparted.
This will leave you with an 'Unallocated space' of about 16.6 Gb.
Add all that 'Unallocated space' of 16.6Gb to your NTFS, Windows C: partition (do this operation from Windows only).
From Gparted select your 1st partition of 210Gb and resize it to 20Gb and format it as Ext4, now you'll have 190Gb of 'unallocated space'.
Make a small 4Gb partition Primary and format it as SWAP, you still have about 186Gb of 'Unallocated Space'.
Make a partition with all 186Gb and format it as ext4. Apply changes and quit Gparted.
Install Ubuntu and manage partitions as instructed earlier.

Your final Partitions will look like:
1 /dev/sda1 20Gb Primary Ext4 '/' (Ubuntu)
2 /dev/sda2 4Gb Primary SWAP
3 /dev/sda3 186Gb Primary Ext4 '/home' (to store your personal DATA)
4 /dev/sda4 40Gb Primary NTFS Windows C:

Good Luck...

---

### Post by RayArdia on 2013-12-21
Thanks fantab, a very helpful reply. Will print it and use as a checklist to make sure I don't miss anything!
Watch this space........
Regards, Ray

---

### Post by RayArdia on 2013-12-22
After some false starts using GParted, where I kept getting bits of unallocated space whic I couldn't remove (or so it seemed) I created a new partition table andset up anew as near as d....t to your instructions. Can't show any terminal output as having to use windoze.
When installing Ubuntu 13.04, after choosing"install Ubuntu _inside[U] Windows" -why does it say [U]inside[U] BTW and not[U] beside_? -I selected that option and 'continue'.
Then came a black screen (which always happens when I've done something stupid I've found :( ) 
udev [4755] 'sbin/blkid -o udev [5879] terminated by signal 15'   (terminated)  acpid: exiting
Installation CD ejected.
I imagine that it is something to do with boot on /dev/sda1 which is the 20GB Ubuntu partition,may I ask for your advice , please?

---

### Post by fantab on 2013-12-22
That option is for WUBI. It installs Ubuntu "inside" Windows as a 'program'. Its a BAD option. WUBI is more or less deprecated.
Follow the instructions on how to remove it: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

The option you need to choose is "Something Else" and guide your install to the partition you want to install Ubuntu to as suggested.

---

### Post by RayArdia on 2013-12-22
> **fantab said:**
> That option is for WUBI. It installs Ubuntu "inside" Windows as a 'program'. Its a BAD option. WUBI is more or less deprecated.
Follow the instructions on how to remove it: [https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)
The option you need to choose is "Something Else" and guide your install to the partition you want to install Ubuntu to as suggested.
 
Have tried to follow the wiki's instructions but they don't seem to work for me- perhaps I don't now have enough brain cells left to do this sort of thing! 
To make things simpler for old duffers, how would it be if I re-formatted /dev/sda4 to ntfs thereby removing Win 7 _and_ wubi? Could I then install Ubuntu, followed by a win 7 install?  I know its long-winded, but so am I.
BTW output from Boot Repair is at *[http://paste.ubuntu.com/6618835](http://paste.ubuntu.com/6618835)*

---

### Post by mansonfan78 on 2013-12-22
> **RayArdia said:**
> Have tried to follow the wiki's instructions but they don't seem to work for me- perhaps I don't now have enough brain cells left to do this sort of thing! 
To make things simpler for old duffers, how would it be if I re-formatted /dev/sda4 to ntfs thereby removing Win 7 _and_ wubi? Could I then install Ubuntu, followed by a win 7 install?  I know its long-winded, but so am I.
BTW output from Boot Repair is at *[http://paste.ubuntu.com/6618835](http://paste.ubuntu.com/6618835)*

If you decide to reinstall everything, partition as previously mentioned using Gparted.  Then reboot and install Windows 7 FIRST.  After that's done install Ubuntu using the "something else" install option and choose partitions manually.

---

### Post by fantab on 2013-12-22
> **RayArdia said:**
> Have tried to follow the wiki's instructions but they don't seem to work for me- perhaps I don't now have enough brain cells left to do this sort of thing! 
To make things simpler for old duffers, how would it be if I re-formatted /dev/sda4 to ntfs thereby removing Win 7 _and_ wubi? Could I then install Ubuntu, followed by a win 7 install?  I know its long-winded, but so am I.
BTW output from Boot Repair is at *[http://paste.ubuntu.com/6618835](http://paste.ubuntu.com/6618835)*

Why don't they work? What kind of errors, if any, do you get when you try to remove WUBI?

Yes you can re-install Windows if its not a problem.
However, it you want to re-install Windows as well, then it will be better if you can make your First partition as NTFS, rather than have your last partition as NTFS.
Also like mention in the post above, it is a good idea to install Windows first and then install Ubuntu.

---

### Post by RayArdia on 2013-12-24
Sorry for delay in replying, I reinstalled Win7 on sda4, ubuntu 13.04 on sda1 but then the laptop booted directly into Win7 without giving the 'options' screen to allow selection of OS.
When I tried to get back to this forum (using Win7 of course) I couldn't login via the SSO screen because the screen was kind of 'split' with the bottom half somehow overlaid so that the 'I am a returning user' box was hidden, as were any further options after entering the email address.
To cut a long story short I finally found that using the Advanced options from boot repair I reloaded GRUB (I THINK!) then rebooted, got the OS options OK and (fingers firmly crossed), all's well.

A very big thank you for your patient help,
Happy Christmas!
Ray

---

### Post by RayArdia on 2013-12-26
[QUOTE=fantab;12879241

Your final Partitions will look like:
1 /dev/sda1 20Gb Primary Ext4 '/' (Ubuntu)
2 /dev/sda2 4Gb Primary SWAP
3 /dev/sda3 186Gb Primary Ext4 '/home' (to store your personal DATA)
4 /dev/sda4 40Gb Primary NTFS Windows C:

Good Luck...[/QUOTE]

Re. 3 above - HOW do I "make this partition '/home' ", can I do it from Terminal or must I use the GParted or Boot Repair .iso disk?

---

### Post by oldfred on 2013-12-26
You normally make /home as part of your install. You can create partition in advance but must format and mount as part of install. Or if reusing an existing /home you must be sure NOT to reformat it. Only Something else gives you the choice to create more than the default of / & swap.

You can create a partition as ext4 and move your /home from inside your / (root) to the new partition. But I prefer to just use another partition as a data partition.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

      
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by fantab on 2013-12-26
> Ubuntu installer just does the basic job of partition, ie it creates a '/' partition and swap.
If you want to keep your data separate make a separate '/home'  partition. Use following settings for the partition to be used as /home:
Use as : Ext4
Mountpoint : /home
Format : check to select

During installation after choosing 'Something Else' option, you should go about it as quoted above.

If you have already installed Ubuntu without '/home' and now want '/home' then follow what oldfred suggests in the post above.

I too don't use separate '/home' partition. I have simple DATA partiton and keep all my DATA on it. 
I mount the Data partition manually when I need it, by just clicking on the partition in the launcher. I have changed the default 'save' path in application to save files to the Data partiton.
For instance, I have changed the default 'save' path of Downloads from Firefox to save directly to Data partition.
LibreOffice saves Documents directly to the DATA partition and so on.

Another way to use DATA partition is to mount it with /etc/fstab and 'bind' the Home folders.
For more details:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[http://ubuntuforums.org/showthread.php?t=283131&p=1653968#post1653968](http://ubuntuforums.org/showthread.php?t=283131&p=1653968#post1653968)

The following info shows how to mount the Data Partition and bind respective folders:
[http://ubuntuforums.org/showthread.php?t=2117020&p=12514856#post12514856](http://ubuntuforums.org/showthread.php?t=2117020&p=12514856#post12514856)

---

### Post by RayArdia on 2013-12-27
Thank you. I read the Community doc and found it quite baffling! I'm sure the fault lies in my ancient brain, not in the document.
I decided that since a move to a new Ubuntu distro is not a frequent occurence, I'd rather have all my Ubuntu bits in one lump, (in sda4 (Ext4)).
I deleted the empty sda3 and grew sda4 to a little over 205GB, leaving sda1(Win7) and sda2 (Linux swap) as they were. Despite the grim warnings, boot went OK and hopefully 'all's well that ends well' as the Bard would say.

At the risk of repeating myself can I say once again that this must be about the friendliest forum of which I'm a member. 

Many, many thanks to all who give their time to help to flounderers like me

---

### Post by fantab on 2013-12-27
Whatever suits you, is your best option.

However, I cannot accentuate any less the importance of keeping your DATA separate from '/' partition. The rationale being, at some point you will have to upgrade Ubuntu (and as we've seen here upgrades do go awry and we end up recommending re-install, clean and fresh). In such a senariio, if your data is not separate, you will have to backup all your data safely, before you do a clean install as the fresh install will format the partition before install. If you had your data separate on a separate partition then re-installing becomes less cumbersome a process by just formatting and re-installing new Ubuntu to its '/' partition, without worrying about data loss.

Good Luck.

---

