---
title: "New to Ubuntu"
date: 2017-05-01
forum: New to Ubuntu
---

### Post by jared1179 on 2017-05-01
Tried jumping the gun and loaded about 3.5TB of media on to a HD...out of laziness and lack of understanding Ubuntu I decided to just have it formatted and then recopy the files again.  I have Ubuntu 17.04 now loaded on a 4TB HD, and it created another 3.8TB partition.  In 17.04, how am I able to created 2 additional partitions and format them in NTFS for media purposes? I eventually plan on making this an embedded system but want to take 1 step at a time.  Only info I found was from 2010 using GPART, I have my USB boot disc in currently and I tried to format the second partition however it says i can't because it is mounted....it will not let me unmount the disc...I am sure this is basic and i am sorry for the questions but I am totally new to Ubuntu and only experience with Linux is from the RPIs.

Thanks in advance,

Jared

---

### Post by yancek on 2017-05-01
Are you using GParted from a usb to modify partitions on one of your hard drivesw?  If that's the case, you should be able to simply click the partition to highlight in the main windows and then right click to unmount it.  You can't modify a partition from a running system.

---

### Post by ian-weisser on 2017-05-01
> **jared1179 said:**
> how am I able to created 2 additional partitions and format them in NTFS for media purposes?

Use the 'parted' (command line) or 'gparted' application (GUI), both in the Ubuntu repositories.
EDIT: Hooray for yancek, who beat me to it! Well done!

---

### Post by DougieFresh4U on 2017-05-01
Welcome to ubuntu forums!
You have come to the right place as there is so much
information to be found here.
The 'search' function will help you find answers to a lot
of questions you may/will have, it'll be your best friend,:)
I'm not a linux 'guru' but I love ubuntu and hope you enjoy 
using it.
Again, welcome to the forum.

---

### Post by jared1179 on 2017-05-02
Thanks for the help - I was able to run it off the USB stick.  I used Gpart to get my partitions the way that I wanted them and then mounted the discs again.  When I did that It basically asks me to do a fresh install of again rather then just booting up from the location that it should.  I don't mind doing a fresh install as I didn't have much installed yet on it but I don't want to jack up my partitions.  What is the best way to handle this?

---

### Post by LastDino on 2017-05-02
Did you perhaps edit partition labeled as "boot" and or "/"?

It would help if you could post the screen-shot of the current partition scheme, it would be easier to decipher what is actually happening from there.

---

### Post by jared1179 on 2017-05-02
[ATTACH=CONFIG]274909[/ATTACH]

This is the error I get without running the USB stick with it.  Restarting now with it in

---

### Post by jared1179 on 2017-05-02
[ATTACH=CONFIG]274910[/ATTACH]

Here is the directory of disc partitions.  The other pic came out blurry - It will not boot from SDA1 - should I just do a fresh install over it and will it keep the rest of the partitions in tact?

---

### Post by ian-weisser on 2017-05-02
sda1 shows only 33MB used and fat32.
I don't know where you installed Ubuntu to, but it certainly wasn't to tiny 500MB sda1.

---

### Post by LastDino on 2017-05-02
You should probably do fresh install as it is not a problem and during installation please do proper partitioning.

If you're dealing with MBR
500MB label boot
ext4> 25Gb label "/" (i.e.  root)
ext4> 100+Gb label /home (this is not necessary unless you want to store stuff on Linux)
I don't use swap since I've RAM of 4Gig+ but if you've less, make "swap" partition as well, which is usually equal or half of RAM size, assuming you've RAM of at least 1Gb+

You other partitions.
Should follow later if you want Linux as only operating system.
Which may be of size as per your need.

---

### Post by jared1179 on 2017-05-02
> **LastDino said:**
> You should probably do fresh install as it is not a problem and during installation please do proper partitioning.

If you're dealing with MBR
500MB label boot
ext4> 25Gb label "/" (i.e.  root)
ext4> 100+Gb label /home (this is not necessary unless you want to store stuff on Linux)
I don't use swap since I've RAM of 4Gig+ but if you've less, make "swap" partition as well, which is usually equal or half of RAM size, assuming you've RAM of at least 1Gb+

You other partitions.
Should follow later if you want Linux as only operating system.
Which may be of size as per your need.

I would like to do a fresh instal and run Linux only.  I don't understand what you mean as  ext4>25GB label

I have a 4 TB drive in there and would like 1 boot drive with 2 partitions for media in NTFS format.  What is the best way of doing this? Sorry, total noob and don't understand the terminology you used.

---

### Post by oldfred on 2017-05-02
Are  you also planning on installing Windows?
NTFS sometimes requires maintenance like chkdsk or defrag. And you cannot run those repairs from Linux. 

Is system UEFI or BIOS?
Generally you use gpt partitioning with UEFI and MBR(msdos) partitioning with BIOS.
And any drive over 2TiB must be gpt partitioned. 
Windows can only boot from gpt with UEFI. 
Ubuntu can boot in BIOS mode from gpt drive, if you also add a tiny 1 or 2MB unformatted partition with the bios_grub flag. 
But if dual booting always have all installs booting in same boot mode.

---

### Post by ian-weisser on 2017-05-02
> **jared1179 said:**
> Sorry, total noob and don't understand the terminology you used.

Lesson #1:You WILL LOSE ALL YOUR DATA at some point in the process. Noobs frequently do. Experts do, too. 
Backup all your data before starting.
Backup all your data before starting.
Backup all your data before starting.

Your plans for this-and-that partition don't matter much yet.
Backup all your data before starting.
Backup all your data after finishing, too.
 
Lesson #2: You WILL MAKE LOTS OF MISTAKES. It's a normal part of learning.
See lesson #1 for how to mitigate the inevitable damage.

---

### Post by jared1179 on 2017-05-02
No, this will be Linux only, I picked NTFS as this will be a media server - most clients will be Linux based however it is possible they may add a mac or PC client.  

Which ever you feel would be ideal - I am not against UEFI or MBR.
Basically I want one boot partition with some extra room for misc programs, and then 2 larger partitions for the media.

---

### Post by jared1179 on 2017-05-02
> **ian-weisser said:**
> Lesson #1:You WILL LOSE ALL YOUR DATA at some point in the process. Noobs frequently do. Experts do, too. 
Backup all your data before starting.
Backup all your data before starting.
Backup all your data before starting.

Your plans for this-and-that partition don't matter much yet.
Backup all your data before starting.
Backup all your data after finishing, too.
 
Lesson #2: You WILL MAKE LOTS OF MISTAKES. It's a normal part of learning.
See lesson #1 for how to mitigate the inevitable damage.

I tried copying all the media to the drives before loading Linux and lost all the data already so its not a big issue.  Just have to copy over the files again.  Rather not have to pay another windows licensing fee and would also like to make this a truly embedded system that only runs the media server and local player eventually.

---

### Post by ian-weisser on 2017-05-02
Why does your data need to be NTFS?
That seems like needless complexity.
NTFS is not an open-source standard. Microsoft can change that standard any time they wish, causing all kinds of problems.
Embedded media servers generally use their native filesystem (like ext3/ext4), serving the files over a filesystem-agnostic network connection.

---

### Post by jared1179 on 2017-05-02
> **ian-weisser said:**
> Why does your data need to be NTFS?
That seems like needless complexity.
NTFS is not an open-source standard. Microsoft can change that standard any time they wish, causing all kinds of problems.
Embedded media servers generally use their native filesystem (like ext3/ext4), serving the files over a filesystem-agnostic network connection.

They will be large media folders.  NTFS files can be read on MAC PC Linux, etc.
I have no idea at all what I am doing and tried clicking a few things and made the situation worse.  Putting the drive back in the PC to format how I know how and then trying to reinstall again.  

What is the best way to install on a 4TB HD and have multiple partitions? Should i have the partitions in place before hand and add them after?

---

### Post by ian-weisser on 2017-05-02
You can make partitions (except the Ubuntu partition, of course) at any time using 'parted' or 'gparted' or several other fine tools.
The easiest way is to use the Ubuntu installer to create, format, and install the Ubuntu partition.

Pro tip: Don't format the same drive in different machines during this process. It won't hurt the drive, but the human can easily lose track of which partition is which and format the wrong partition.

Don't race around trying to do expedient shortcuts - as you have learned, they are often counterproductive. Ubuntu is a whole new OS that's nothing like Windows. Take time and learn it. Build your system incrementally.

---

### Post by LastDino on 2017-05-02
> **jared1179 said:**
> I would like to do a fresh instal and run Linux only.  I don't understand what you mean as  ext4>25GB label

I have a 4 TB drive in there and would like 1 boot drive with 2 partitions for media in NTFS format.  What is the best way of doing this? Sorry, total noob and don't understand the terminology you used.

ext4 is a latest Linux system under which you can format a drive. It will not be readable by windows but you are not installing one it will not be a problem.

Label is a nomenclature under which your system identifies each partition on device and you really need to read up on this before you do any formatting.

Please go through this before you do fresh install.

---

### Post by jared1179 on 2017-05-02
I tried making it easy so i can shuffle around partitions later. I keep getting an unable to install GRUB in dev/sda
executing grub install/dev/sda failed
this is a fatal error.

How can I format my drive back to the regular version so that I don't have BIOS vs UEFI conflicts and this critical error.  Spent 2 days on this so far and honestly thinking about giving my money to windows again.

---

### Post by ian-weisser on 2017-05-02
BIOS vs UEFI is not about formatting. Totally separate issue. The Ubuntu installer will happily install a UEFI-bootable system.

Where should grub be installing to? 
Use the method in Answer #2 of [https://askubuntu.com/questions/143678/](https://askubuntu.com/questions/143678/) to tell grub where to install at.
The answer is not always 'sda'  - you must use the actual designation of your disk.

Be calm. Everyone must learn. I've installed many systems on lots of different hardware. These little issues pop up occasionally. I got through them my first time. You will too.

---

### Post by oldfred on 2017-05-02
Since drive is  over 2TiB you have to use gpt.
And with gpt you have to have either the ESP or the bios_grub partition for grub to correctly install. I actually make the first two partitions those partitions, but now only install in UEFI mode using the ESP. The bios_grub is only 1 or 2MB so does not take any space and would let me convert a drive to BIOS boot easily if I later wanted to. But you only need one or the other depending on how you will boot.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):

if gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
if gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)

for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)

---

