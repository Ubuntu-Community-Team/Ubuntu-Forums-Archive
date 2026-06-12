---
title: "Partitioning advice for Dual-Boot setup"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by krokonoster on 2012-01-02
Hi,
I installed and used ubuntu before but wanted to ask some expert advice as for how to partition my hard drives, since I am a bit at lost as what's the purpose of all the different partition.
Pls. keep in mind I want to dual-boot with windows (want to do a fresh install of windows7, so feel free to tell me which one first.)

About my machine (not sure what info is relevant, so...):

i7 64bit with 6GB Ram (I downloaded ubuntu-11.10-desktop-amd64, though 32 bit seems to be recommended?)

1 TB hard drive (would be nice if windows and Ubuntu can sit in the "minimum" sized partitions required and the rest of the drive is accessible by windows and Ubuntu.  If possible of course)

Thanks in advance!

ps: Purpose of all this:  I'm a typical .net developer,but had a good run with php/mysql a few years back.
Getting bored and want to dabble back to php and since I like to add something new to my skill-set I figured I want to go with LAMP instead of WAMP.   :)  (Plus I am fed up re-installing my "trial" windows every few months.)

---

### Post by Elfy on 2012-01-02
(want to do a fresh install of windows7, so feel free to tell me which one first.)Windows

If I were you I would do this - > windows and Ubuntu can sit in the "minimum" sized partitions required and the rest of the drive is accessible by windows and Ubuntu

Absolutely no idea how much space win7 would need, but I would be inclined to 20 Gb for ubuntu - assuming that you keep data in the "rest of the drive"

If you want to hibernate then you'll need swap=RAM 

So - perhaps 

space for w7 - extended - logicals for ubuntu - swap - shared data

32bit is only recommended so that people not knowing what they are using don't get the wrong one ;)

---

### Post by QIII on 2012-01-02
Just by the by....
If you plan to resize your Windows partition, use the tools in Windows.


Windows is a messy house keeper, so you never know where it will leave stuff lying around.  Defrag three times and resize the partition with the Windows tools after you install it.

That's sometimes easier than using a partitioning tool first.

---

### Post by rectec794613 on 2012-01-02
I'm not quite clear as to what exactly you need to know. So more info or maybe a rephrasing would help. Nevertheless, I've given what suggestions I could.

Each OS requires it's own partition. It all depends on what you plan to use the partitions for. I have about a 250GB hard drive. I store a bunch of games on my Windows partition, plus the default Windows install is pretty big. So I've allocated about 150 gigs to it. A default Ubuntu install can require as little as 2GB. I've allocated 20GB to each of my 3 Ubuntu installs. If Ubuntu all-of-a sudden turned into a major gaming OS, I'd probably allocate more. 

So basically, if you plan to have a lot of data on the Ubuntu partition, allocate more space.

AMD64 is my choice. Helps take advantage of a 64Bit processor. The amount of AMD64 packages is equal if not greater than i386.

---

### Post by larrypg on 2012-01-02
Hello,

Since this looks like you will be doing a clean install of everything here is what I would do.  

First install windows 7.  It will take over the whole disk.  I would then defrag the drive several times after it is installed.  The next thing I would do is to use windows disk utility to shrink Windows 7 to around 60 GB or so and make the rest of the space unallocated.

I think although not positive that Windows 7 will actually make two partitions so that will leave you with two more to go.  

I would then make a large (maybe as large as 800 GB) NTFS Data partition.  This way both windows and ubuntu can use it.  

The last primary partition I would make as an extended partition and install a 30 GB / EXT4 , a 12 GB swap and the rest for /home also EXT4.

Just how I would do it.

---

### Post by Elfy on 2012-01-02
Why would you got to all the trouble of > It will take over the whole disk. I would then defrag the drive several times after it is installed. The next thing I would do is to use windows disk utility to shrink Windows 7 I find it hard to believe that the windows installer doesn't give the option to use as specific sized partition.

---

### Post by larrypg on 2012-01-02
Just my experience when installing Win 7 not sure if it gives an option of not using the whole disk.

---

### Post by pierreyy on 2012-01-02
hello,

i would suggest wiping the entire hard disk first, then use  a GPARTED live cd to partition  the hard disk in two parts ( ntfs for windows, and ext for linux)
after that install windows on the ntfs partion then install ubuntu on the ext partition.

 this is a link to download the GPARTED live cd 
> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

it should go pretty smooth, good luck.

---

### Post by cortman on 2012-01-02
There's been a lot of advice posted, but I'll leap into the fray anyway...
1. Install Windows FIRST. Windows can't natively "see" most Linux partition formats, and so if you install Ubuntu first you stand a good chance of having Windows wipe out your whole installation.
When you install Windows it does give you the option to create your own partitions (which will allow you to limit the Windows partition to whatever size you want, rather than have it take up the whole drive). If you feel experienced enough to do that, go for it- it's quite simple, and honestly with a fresh disk you don't have much to lose if something would go a bit wacky.
If you need help setting up the partition table with Windows, just ask, though- it's not hard.
Depending how much software you install on Windows, I'd recommend anywhere from 80-250 GB. The Ubuntu OS partition will be fine with 40 or so.
2. It appears you want to create a separate partition that is accessible from both OS's. That's very easy to make and extremely handy. I would recommend you make it from Windows, though, after you've installed Windows and Ubuntu. I can re-direct you to some threads on that, when you need that instruction. Or I've been contemplating writing up a little tutorial on it. We'll see.

Any questions at all feel free to post. Best wishes!

---

### Post by audiomick on 2012-01-02
Without wanting to disagree with anyone who has posted, I would suggest reading these:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I know it is a lot, but I thing you are better served getting a bit of a feel for why you do things rather than jsut following a set of instructions blindly.

Regarding the last link, I would strongly recommend using the setup with / and /home on seperate partitions.

---

### Post by Mark Phelps on 2012-01-02
While you can certainly use GParted to create an empty NTFS partition, from my experience, I would recommend the following instead:
1) Create a 30GB NTFS partition with GParted
2) Format the remainder of the drive Ext4

NOTE: Both of these are temporary ...

NOW, remove the NTFS partition using GParted and install Win7 into the unallocated space.  IT will create its own NTFS partition -- which will work better in the long run.

Then, remove the Ext4 partition and let the Ubuntu installer partition the rest of the drive.

---

### Post by oldfred on 2012-01-02
Just to throw a monkey wrench into the works. 

If you have an i7, you almost for sure have a motherboard with UEFI/BIOS. Are you installing Windows in UEFI/gpt mode or BIOS/MBR?

Windows only works on the newer gpt drives with UEFI. Ubuntu works on gpt with either UEFI or MBR(msdos). You really only need gpt if you have drives over 2TiB or about 2.2TB, but I use gpt on my BIOS system with my new SSd, an old 160GB drive and even a USB flash drive.

I now partition my drives with a 300MB efi partition for future use as it has to be first, a 1MB bios_grub partition as Ubuntu needs that to boot in BIOS mode, but do not install Windows on the same drive as Ubuntu, so I have no issues with Windows.

If in BIOS/MBR mode all of the advice above is fine. Each of use has different suggestions and none are wrong. Even my own partitioning scheme is not correct a year or two later, but after several years I get a new drive as I know the older drive will be less reliable and new drives are always a lot larger,s o I can backup & reorganize.

My 2 cents worth is never mount a system partition as read/write from another system. Keep data separate from systems and just because a drive is huge, large partitions may not be best. If ever damaged, chkdsk, or file recovery can take forever from a large partition. But if storing a lot of data multiple partitions can force reorganization if one fills and the other is empty. Some use LVM to avoid the issue, but that adds a level of complication.

If running NTFS for a data partition run chkdsk regularly, as the Ubuntu fstab will not fsck (autocheck) a Windows formated partition.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up.

Do not create a large >500GB / partition as grub used to have a bug on very large / partitions, and I do not know if it is fixed yet. Best to stay in the 25 to 50GB range and use a separate /home or data partition(s).

---

### Post by GreenRaccoon on 2012-01-02
I would install Windows 7 first, because Windows doesn't like to have other operating systems on your computer.  I've never reinstalled Windows 7 on my computer while having other operating systems on it, but it may overwrite your other partitions.  Back up just in case.

When I reinstalled Windows Vista on my old computer, it overwrote GRUB with the Windows boot loader.  When this happened, I couldn't start up Ubuntu until I used a Live USB to overwrite it with the GRUB boot loader again (GRUB lets you choose between all of your operating systems on your computer, Linux and Windows).

Use 64 bit Ubuntu (amd64), cause otherwise you're wasting 2GB of your 6GB RAM.

When you install Ubuntu, there should be an option to "Install Alongside Windows" (the wording might be slightly different).  If you want to manually change the partitions, it's a little more confusing but definitely doable.  I used this really thorough walkthrough:
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/~herman546/p23.html")

You should read that walkthrough because it explains it better, but this is the gist of it.  Basically, you would change the size of your Windows partition (make it smaller, creating enough free space for your Ubuntu partition and a small swap partition).  Then choose the free space, create a new partition as a Linux swap partition (you'd probably want 6GB to match your 6GB RAM).  Then choose the rest of the free space and create an ext4 partition, and mount it as "/".  Then your bootloader will most likely be "dev/sda" (which is the whole hard disk, not a single partition).

Here's a couple threads I made when I was manually adding partitions to my computer:
[http://members.iinet.net.au/~herman546/p23.html]("http://members.iinet.net.au/~herman546/p23.html")
[http://ubuntuforums.org/showthread.php?t=1873849]("http://ubuntuforums.org/showthread.php?t=1873849")

Hope this helps!

---

