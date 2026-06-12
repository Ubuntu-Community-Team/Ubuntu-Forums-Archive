---
title: "partitioning for dual boot"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by biggiemokey on 2008-04-21
Hi, I think this is a fairly simple question and I have seen the answers online but don't really understand the language.  Basically I am going to reformat my computer, clearing the hard drive, and dual boot both Windows XP Professional and Ubuntu.  I know that Windows will create it's own partition, and on my 160GB hard drive I should have about 148GB left.  I plan on installing Ubuntu 8.04 a couple weeks after it comes out, and I'm hoping by then I'll find information on how much room I should partition for Ubuntu and updates, etc.  But can I install Ubuntu on the rest of my Hard Drive along with shared files that will open in both Windows and Ubuntu?  I know certain things will only work in one OS, but when I double click a .doc file I want it to open from either OS in whatever office suite I am using on that OS.

What I am looking for is just a clear answer to:  Do I need to create three sections on my Hard Drive?  Or will two work, one for Windows and one for Ubuntu and all other files?

Thanks in advance for any help

---

### Post by joshrobinson on 2008-04-21
> **biggiemokey said:**
> Hi, I think this is a fairly simple question and I have seen the answers online but don't really understand the language.  Basically I am going to reformat my computer, clearing the hard drive, and dual boot both Windows XP Professional and Ubuntu.  I know that Windows will create it's own partition, and on my 160GB hard drive I should have about 148GB left.  I plan on installing Ubuntu 8.04 a couple weeks after it comes out, and I'm hoping by then I'll find information on how much room I should partition for Ubuntu and updates, etc.  But can I install Ubuntu on the rest of my Hard Drive along with shared files that will open in both Windows and Ubuntu?  I know certain things will only work in one OS, but when I double click a .doc file I want it to open from either OS in whatever office suite I am using on that OS.

What I am looking for is just a clear answer to:  Do I need to create three sections on my Hard Drive?  Or will two work, one for Windows and one for Ubuntu and all other files?

Thanks in advance for any help

you will want 3 partitions on your drive, say 100 to 120 for windows,
45-55 for ubuntu, and whatever you need your swap partition to be (usually 2x your ram is the general rule)

ubuntu will be able to read and write to your windows drive, and as you said a .doc file will open in both operating systems office suite

i would delete all partitions on the drive, create the size for windows you want (dont set it to use all 160), install windows, leaving what you want for ubuntu unpartitioned
then install ubuntu second, using the free space on the drive

---

### Post by Rocket2DMn on 2008-04-21
You need:
1) windows partition (ntfs)
2) linux root partition (ext3)
3) linux swap partition (swap)
You can read/write ntfs from linux with the ntfs-3g driver, installed by default in Gutsy and newer.  In windows, you can read/write ext2/3 drives using the driver from [http://fs-driver.org/](http://fs-driver.org/)

It would probably be easiest to lay out your partitions now rather than having to resize the XP partition.

---

### Post by laffinet on 2008-04-21
I would recommend separate partitions for root and home, which will leave you with the following partitions

xp
/ (root) 
/home
swap
another partition which will be accessed by both windows and ubuntu (fat32 will do the trick)

---

### Post by sam_delta on 2008-04-21
simply install windows, use the whole hard drive, insert ubuntu CD, click install, and during the installation you will be asked if you want to resize windows partition, you resize windows partition to whatever size you want and ubuntu will use the freeded space and will also create the swap partition

dont worry its ez 

sam

---

### Post by Brian96 on 2008-04-21
I agree with posts 2 and 3. I also recommend setting up your Windows XP partition to the size you want when you install Windows, rather than using the resize feature in the Ubuntu install (although I've never had problems with this).

As an alternative to the 3 partitions (Windows XP, Ubuntu, and Swap) suggested, I would suggest 4 partitions:

1. Windows XP (NTFS, setup with Windows installer) ~20 GB
2. File Storage (NTFS, set up with the Ubuntu install partitioner) ~120 GB
3. Ubuntu (EXT3, set up with Ubuntu install partitioner) ~ 20 GB
4. Swap (1.5--2x the size of your RAM)

There is nothing wrong with the other recommendations, this is just the one I like. (Except that I also have a couple of extra partitions for playing around with other Linux distros. I generally have 2 ~20 GB partitions for Linux, and when the new version of Ubuntu rolls out every 6 months I install it there for testing and to take my time with setup, while keeping my old install in place for "production purposes" in case I run into problems.)

---

### Post by sam_delta on 2008-04-21
> **Brian96 said:**
> I agree with posts 2 and 3. I also recommend setting up your Windows XP partition to the size you want when you install Windows, rather than using the resize feature in the Ubuntu install (although I've never had problems with this).

As an alternative to the 3 partitions (Windows XP, Ubuntu, and Swap) suggested, I would suggest 4 partitions:

1. Windows XP (NTFS, setup with Windows installer) ~20 GB
2. File Storage (NTFS, set up with the Ubuntu install partitioner) ~120 GB
3. Ubuntu (EXT3, set up with Ubuntu install partitioner) ~ 20 GB
4. Swap (1.5--2x the size of your RAM)

There is nothing wrong with the other recommendations, this is just the one I like. (Except that I also have a couple of extra partitions for playing around with other Linux distros. I generally have 2 ~20 GB partitions for Linux, and when the new version of Ubuntu rolls out every 6 months I install it there for testing and to take my time with setup, while keeping my old install in place for "production purposes" in case I run into problems.)


i would recomend Fat32 as the file system of the 2nd partition (file storage) you mentioned , ubuntu handles FAT32 way better than ntfs

---

### Post by ssican on 2008-04-22
More informations about Partitioning Windows and Ubuntu:
[http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

EDIT 1: For an How To Edit Manually Partitions using GParted:
[http://www.easy-ubuntu-linux.com/resize-windows-partition.html](http://www.easy-ubuntu-linux.com/resize-windows-partition.html)

EDIT 2: How To Dual Boot Windows XP and Linux:
[http://apcmag.com.au/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com.au/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by billgoldberg on 2008-04-22
It's fairly simple.

Format the drive and install windows xp first.

After that put in you ubuntu 8.04 cd and let it install (pick how much room you want) it should make the swap by itself and format it as ext3.

Ubuntu has no problem reading the windows partition (you might need to do "gksudo nautilus").

If you have a .doc in your windows partition and you open it on ubuntu, the .doc file will open with openoffice.

---

### Post by stalkingwolf on 2008-04-22
I agree with the previous post . format your drive first.
I would make the xp partition 30gb. Having found recently that 20
can git filled up quickly.

Then 10 - 30gb for /.
1.5-2 x your ram for swap.
split the rest for /home and shared.

---

### Post by brettg on 2008-04-22
I would like to second the idea that you need a separate home partition. You WILL really appreciate it if/when you decide to reinstall your OS.

---

### Post by biggiemokey on 2008-04-29
thanks for all the help guys.

i think ive got it figured out, but im not quite sure what a /home or swap partition is.  i think i understand that to upgrade to a new version of ubuntu, i can uninstall ubuntu on the / partition, while the /home partition would keep all my shared files and settings, if i was to do:

160 GB hard drive, 2.00 GB RAM
1) Windows (NTFS) (? GB)
2) /home (Ext3) (Rest of Hard Drive) 
3) / (Ext3) (10 GB)
4) Swap (4.00 GB)

so when ubuntu 9 comes out, just uninstall everything on the / partition and install ubuntu 9.  The /home partition holds the shared files and the /home settings.  I would use FS drive to allow windows to read and write to the /home partition.

ill google somewhere else how much room to leave for windows xp partition.  what i want to know is, what exactly is a swap partition?  i know it helps with memory or something, but how do i make it a swap partition?  i know you can format as ntfs, ext3, fat32 etc. but is there an option to format as swap?

---

### Post by Rocket2DMn on 2008-04-30
That setup seems like it should be OK.  Swap partition is hard drive space that gets used as RAM if you start to fill up your real RAM.  It is also where memory is stored if you hibernate the computer.  It is like a windows pagefile.  Swap is formatted as "swap" and has no mount point on the filesystem.

---

### Post by acelin on 2008-04-30
I wouldnt do it with a ntfs though if you can- ntfs doesnt like being shared with an ext 3 file system.

---

### Post by Rocket2DMn on 2008-04-30
The ntfs is for his windows partition.  His /home and root partitions are ext3.  With ntfs-3g, ntfs filesystems share pretty well, anyway, you just don't want them as part of your main filesystem.

---

### Post by biggiemokey on 2008-05-01
thanks, but do i need ntfs-g3?  i thought i could just use FS drive to have windows read ext3

---

### Post by biggiemokey on 2008-05-01
thanks, but do i need ntfs-g3?  i thought i could just use FS drive to have windows read ext3

---

### Post by Rocket2DMn on 2008-05-01
ntfs-3g comes preinstalled in Gutsy and newer (so Hardy included).  Using the driver from [http://fs-driver.org/](http://fs-driver.org/) will allow you to read/write your ext3 linux partitions, but you need to have them setup before you install the driver so that you can assign drive letters.  You probably don't need to mount your root partition in windows, just your /home one, but it's up to you.  I usually assign my linux partition to drive L, for linux :)

---

### Post by andybob on 2008-05-01
Alright, quick question.  I am pretty sure I am going to install a duel boot with XP Pro and Ubuntu.  I have 25 GB free and if I install Ubuntu I will let it have 8 GB on it own partition.  I have defragged a million times so there is plenty of room.  Question is, what are the chances it will write over my Windows info?  Here is a screenshot of what my HD looks like.

[IMG]http://i51.photobucket.com/albums/f391/andybob1001/Defrag.jpg[/IMG]

Any help is appreciated.

Thanks,



Andybob

---

### Post by Rocket2DMn on 2008-05-01
The installer should not allow you to resize to the point that it overwrites data, so you should be OK.  It may just not let you resize larger than that empty space at the end, but you should be OK to install.  As always, make sure all your important data is backed up before you proceed, partially in case the resizing fails, but mostly in case you accidentally screw up.

---

### Post by andybob on 2008-05-01
> **Rocket2DMn said:**
> The installer should not allow you to resize to the point that it overwrites data, so you should be OK.  It may just not let you resize larger than that empty space at the end, but you should be OK to install.  As always, make sure all your important data is backed up before you proceed, partially in case the resizing fails, but mostly in case you accidentally screw up.

Alright, thanks.  I think I might just wait until I have a back-up drive, although, I would love to install it today.  lol


Andybob

---

### Post by biggiemokey on 2008-05-04
Thanks for all the help everyone.  I think I have all the information I need.  I'm marking this solved.

---

### Post by manosdvd on 2008-05-04
A bit of a deviation from the topic but out of curiosity...
What is the swap partition for? What does it do?

---

### Post by Rocket2DMn on 2008-05-04
> **manosdvd said:**
> A bit of a deviation from the topic but out of curiosity...
What is the swap partition for? What does it do?

Swap partition is a portion of the hard drive that can be used as RAM if you use up all your available physical RAM.  Also, if you hibernate your computer, the entire contents of RAM are written to the swap space and recovered the next time you boot the computer.

---

### Post by jward3010 on 2008-05-04
I don't mean to create a situation here by putting one last nail in the coffin and changing the ideas here but I don't understand the need for creating a seperate /home partition when he will probably want all files he creates to always available to both OS's and hence on the NTFS drive which contains Windows. Basically whats the point in saving anything under Ubuntu when Windows can't get at it.

In fact I would go one further and would recommend the following:

Windows XP - 1st partition (30GB - NTFS)
Data Partition - 2nd partition (100GB - NTFS)
Swap partition - 3rd partition (twice the size of your RAM - SwapFS)
Ubuntu 8.04 - 4th partition (20GB - ext3)

Now all you have to do is whenever you download anything in either OS is save it to the DATA partition which is safe from the point of you not having to access the partition that Windows is on which could be dangerous one day if you accidentally delete something to do with the OS.

Also, if XP or Ubuntu ever needs to be reinstalled they can be without harming the DATA partition and the data which is always available to both OS's.

---

### Post by jward3010 on 2008-05-04
By the way a handy programme to use is GParted - short for "Gnome Partition Editor" which comes on the Live ubuntu 8.04 CD. Just boot up the CD in Live mode which I think is "Try Ubuntu without making changes" and when the desktop fully loads click on the "System" menu at the top and then go into "Administration" and in that menu you will see "Partition Editor". This will let you completely wipe all partitions off your drive and create the new ones the way you want to. It supports lots of filesystems including ext3, NTFS and Swap.

---

### Post by biggiemokey on 2008-05-04
Thanks for the suggestion jward.  So I realized I messed up before.  What I found at [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning) was:
1) Windows NTFS
2) Ubuntu ext3
3) Swap SwapFS
4) Shared Data (FAT32)
5) /home ext3

I liked this config because of the separate /home partition.  The reason I like it is on the site:
"The benefit of having a separate /home partition? Well, it means you can reinstall Ubuntu as many times as you'd like and do a clean install (instead of an upgrade) when a new version of Ubuntu comes along. When you first start using Ubuntu, you usually have no idea what you're doing, and you end up breaking something. Now, if you're a veteran, you know how to fix whatever you've broken. If you have a lot of time, you could probably ask around and find out how to fix it. Sometimes, though, it just seems easier to reinstall (the installation takes anywhere from 20 minutes to an hour), and not having to re-do all your settings is a good thing. "
I thought that /home had your settings or something, but now after using Ubuntu through Wubi I realize it's just like My Documents in Windows.  I understand why it's good to be able to change Ubuntu without changing this, but I would really like to consolidate My Documents on XP and Documents on Ubuntu to make things easier.  /home isnt' what I expected it to be...
So you say make the Shared Data NTFS...is this supported natively by Ubuntu?  If it is I can go with that, but I could also go FAT32 or even ext3 but that doesn't really matter.

My main concern now is, do I need a /home partition?  I plan on using /home instead of Documents and Settings since I want to use mainly Ubuntu.  I'm not worried about hard drive space, since most of my data is music/movies which I will be putting on a home server.  But after all the trouble I'm having with Ubuntu (can't even get my wireless to work) it seems to make sense to have a separate /home partition, just for safety.  I don't think I'll be backing up often, even though I have a terabyte home server I just don't see myself doing it.

Anyway, sorry for the large post.  Any help is appreciated as always.

---

### Post by jward3010 on 2008-05-04
In relation to the first point you made you're completely right and you didn't mess up. The /home partition is a great idea on a ubuntu alone system, in fact it's what I do on my laptop - a "/" (root) partition of 20GB's (the OS goes here) and an 80GB /home partition for personal files but for your particular setup and mainly due to the narrow mindedness of Microsoft it's not going to suit, in fact that configuration will only waste space. Here's the reason: Say you download wallpapers off the internet, some music, a few videos through torrent or whatever and you do this through ubuntu and save all these things on a ext3 /home partition. Then you boot into Windows and say to yourself "I'd love to watch that video I downloaded yesterday with Ubuntu". But then you realise it's on the /home partition which is an ext3 filesystem which Microsoft can't understand, so you end up booting back into Ubuntu and watching the video there, or copying that video from your /home onto your Windows partition which is accessible through ubuntu but that ends up creating duplications on the system where you have this video on your /home partition taking up 1GB of space and also on your Windows partition taking up 1GB of space. So then you realise that you should really save everything onto your NTFS drive but you created a big 50GB /home partition thats now useless because one OS can't utilise it and for that reason you made the NTFS partition small so you end up scrubbing the whole drive again and starting from scratch. So you may as well have one place where both OS's can recognise the partition and that is NTFS and that also gives you the flexibility to be able to scrub both OS's if you need to as well and reinstall without harming data. Think of the Shared NTFS DATA partition as a universally understood /home partition.

Can Ubuntu natively support a Shared NTFS DATA volume - Absolutely, Ubuntu can recognise lots of file systems, NTFS included (pity it's not the other way around as well) and it's all automated so you won't have to be pumping commands in to bring it up (and thats easy anyway), the partition should just appear under the "Places" menu in Ubuntu.

Do you NEED a /home partition? - No, because you simply can't use it with Windows and anything you save on it won't be accessible when you're in Windows, Also you don't REALLY need one even if you just have Ubuntu on a PC, it's safer if you do create one in normal circumstances for reasons of being able to reinstall the OS without destroying your personal files but because this situation is different and you're having to work with a moody OS like XP it's not relevant. And you're right "/home" is really just a data storage area for your files, just like My Documents. It stores some settings files (they're hidden) but there is no harm done if they get lost during a reinstall of Ubuntu, Ubuntu can be working just the way you like pretty quickly. Whatever you do don't go with FAT32, it's old technology, inefficient and doesn't support large drive sizes. Also you can't go with a separate ext3 partition because XP won't recognise it and you won't be able to do anything within XP with it so make a DATA partition NTFS. This is an unfortunate situation because Microsoft are backing you into a corner and making you do things there way (so much for choice within the free market!) because realistically ext3 is the file system to use, it's very efficient, quick and generates little fragmentation.

Last thing, don't worry about the big post - the more info. the better.

---

### Post by biggiemokey on 2008-05-05
thanks for all the info.  I heard with FS drive though, you can make Windows read from an ext3 filesystem, and I wanted that since liek you said, it's faster

But anyway so I'll do:
1) Windows - NTFS
2) Data - NTFS
3) Ubuntu - ext3
4) Swap - SwapFS

thanks for all the info bro I'm looking forward to getting this done

---

### Post by jward3010 on 2008-05-05
I heard about that too but there putting a big emphasis on ext2 on there site as opposed to ext3 and I wonder if it supports ext3, you might know about that.

No problem - I aim to help, that configuration above looks not bad - give it a blast and see how you go. Report back on how it goes.

EDIT: In fact I'm going to install FS Drive in Windows now to try it out.

EDIT: Ignore me, it does support ext3.

---

