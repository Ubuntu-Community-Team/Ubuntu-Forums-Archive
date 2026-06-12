---
title: "Partitioning and FS advice needed"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Sabata on 2008-05-21
Hello folks. I'm getting ready to install Hardy and seek advice and opinions on partition sizes and the best file systems to use. BTW, other than messing around with a LiveCD session the other night, my Linux experience consists of a couple installs of Mandrake years ago. IIRC, back in those days, people were arguing whether ext2 or Reiser were better. :lol: Anyway, on to the important part.

My current setup is 1.5GB RAM and a 160GB SATA hard drive with XP. I want to do a dual boot with XP and Hardy. I have a new 320GB SATA drive that I haven't installed yet.

I intend to leave the XP drive as is and use the new drive for the Ubuntu install and as a storage place for both XP and Ubuntu files. So my questions are:

1. What are some recommendations for partition sizes on the 320GB drive (figuring /, /home and /swap)?
2. Which file system should I use on /home, since I need both XP and Linux to read and write to it?  FAT32, NTFS or ext3 (and install FS-Drive in XP)?


TIA!

---

### Post by nick_h on 2008-05-21
First a link for you to read - [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

> 1. What are some recommendations for partition sizes on the 320GB drive (figuring /, /home and /swap)?
/ you only need about 10GB
/swap normally twice your physical memory = 3GB
/home the remaining space

> 2. Which file system should I use on /home, since I need both XP and Linux to read and write to it? FAT32, NTFS or ext3 (and install FS-Drive in XP)?
Which OS will you use most?  If Windows then use NTFS, if Linux then ext3.

---

### Post by neurostu on 2008-05-21
So I am not sure but I think /home needs to be in ext3, but I could be wrong.  The best format to use to make a drive readable and writeable by both linux and windows is Fat32.  NTFS is only partially supported by ubuntu and sometime (I say SOMETIMES) you can have problems working with a NTFS partition from linux.

I would recommend creating a install partition, a /home partition a bridge partition (Formatted fat32 for sharing between boots) and a swap partition.

---

### Post by nick_h on 2008-05-21
> a /home partition a bridge partition (Formatted fat32 for sharing between boots)
Yes, fat32 is another option.  I have used this approach myself.  The main drawback is the 4GB file size limit.

Another link - [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

---

### Post by Bodsda on 2008-05-21
Please tell me if i'm wrong but i thought /home ** has ** to be ext3?

---

### Post by neurostu on 2008-05-21
> **nick_h said:**
> Yes, fat32 is another option.  I have used this approach myself.  The main drawback is the 4GB file size limit.

Another link - [http://en.wikipedia.org/wiki/Comparison_of_file_systems](http://en.wikipedia.org/wiki/Comparison_of_file_systems)

Thats right... I keep forgetting about that as I haven't used windows in a long time....  so I guess you could make a NTFS partition if you are going to be using a lot of space.

---

### Post by Sabata on 2008-05-21
> **nick_h said:**
> First a link for you to read - [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

/ you only need about 10GB
/swap normally twice your physical memory = 3GB
/home the remaining space

Which OS will you use most?  If Windows then use NTFS, if Linux then ext3.
Nick, I actually had that psychocats link open in another tab when I posted the original question. Been reading all I can on the subject. :) 

As to which OS will I be using most, that is a good question. When I used Mandrake in the past, I tended to boot it most of the time, only going into Windows when necessary. But I do need to have Windows for certain tasks and may use it almost exclusively for days at a time.

> **neurostu said:**
> So I am not sure but I think /home needs to be in ext3, but I could be wrong.  The best format to use to make a drive readable and writeable by both linux and windows is Fat32.  NTFS is only partially supported by ubuntu and sometime (I say SOMETIMES) you can have problems working with a NTFS partition from linux.
I was thinking about starting out with FAT32 in /home. I could always convert it to NTFS in XP if the urge arose. Is there a way to convert ext3 to FAT32 or NTFS? That is something to think about if for some reason I decided to get rid of Ubuntu. What would happen to my files if I went back to only XP? Not saying it's likely to happen, but you just never know. Sometimes things don't work out as planned. ;)

---

### Post by nick_h on 2008-05-21
> Is there a way to convert ext3 to FAT32 or NTFS?
I don't think so.  You would have to make a backup of the data, reformat and then restore the data.

---

### Post by neurostu on 2008-05-21
No, you cannot convert Fat32 to Ext3 or ext3 to NTFS.  So if you're worried about losing data, just create a big NTFS partition that you can copy too if you need to delete your ubuntu install.  I would also recommend against making your /home partition anything but ext3.  You really don't need a dedicated /home partition. You can just create a / partition for installation and home will be created under /

---

### Post by Sabata on 2008-05-21
> **Bodsda said:**
> Please tell me if i'm wrong but i thought /home ** has ** to be ext3?
You very well may be right but I don't remember seeing that written in any of the stuff I've read. <shrug> 

At any rate, if that is the case, it looks like neurostu's suggestion of...
> I would recommend creating a install partition, a /home partition, a bridge partition (Formatted fat32 for sharing between boots) and a swap partition.
...would make sense. And if I went that way, what is a good size to make /home, assuming a large FAT32 "/data" partition to hold junk from Ubuntu and XP?

---

### Post by neurostu on 2008-05-21
Unless your going to be storing a lot of multimedia you really won't need more then a few gigabytes.  10-20 gb should be plenty for an install and /home partition.  If you are going to have a lot of mp3s, videos, etc... create a 150-200gb ntfs partition for that.

---

### Post by nick_h on 2008-05-21
> ...would make sense. And if I went that way, what is a good size to make /home, assuming a large FAT32 "/data" partition to hold junk from Ubuntu and XP?
With a separate data partition your /home would only hold application settings and would be very small.  It might not be worth creating a separate partition for it.  A separate partition would make a re-installation slightly easier.

---

### Post by Sabata on 2008-05-21
> **neurostu said:**
> Unless your going to be storing a lot of multimedia you really won't need more then a few gigabytes.  10-20 gb should be plenty for an install and /home partition.  If you are going to have a lot of mp3s, videos, etc... create a 150-200gb ntfs partition for that.
Gotcha. One more quickie. I see people talk about possible problems with Linux and NTFS, but nobody explains what these issues are. Even the "official" Ubuntu 8.04 documentation says
> Common filesystems used in a dual boot system include NTFS, FAT32, and ext3. **NTFS, to which Linux cannot safely write data, is the default filesystem used by Windows. Ubuntu treats this filesystem as read-only.** ext3 is a native Linux filesystem that can be accessed from Windows using various tools such as ext2fs. FAT32 (also know as vfat) is a filesystem to which Linux can write safely. Hence, in a dual system, a FAT32 filesystem is commonly used as a way of sharing files between Linux and Windows.
OTOH, the psychocats partitioning page says
> Ubuntu now has a pretty reliable mechanism for reading from and writing to NTFS, but some people like to play it extra safe and have a separate FAT32 partition for both Windows and Ubuntu to work from.
Oy! Who does one believe? :confused: 

BTW, thanks to all of you who've answered my questions! :cool:

---

### Post by Paqman on 2008-05-21
NTFS on Linux is pretty good now. The only problem i've heard of people having is that sometimes the NTFS drive won't be cleanly shut down. This results in a flag being set on that partition that prevents it from mounting. The solution is to simply boot into Windows and shut down. This clears the flag and allows you to mount it in Linux.

I'd say always go with NTFS over FAT32. It supports larger files and picks up significantly less fragmentation.

---

### Post by Sabata on 2008-05-21
Thank you Paqman, nick_h and neurostu!

---

### Post by neurostu on 2008-05-21
Just in case you didn't know, you can publicly thank people by clicking the little star on the bottom right of their posts.

---

### Post by Sabata on 2008-05-21
> **neurostu said:**
> Just in case you didn't know, you can publicly thank people by clicking the little star on the bottom right of their posts.
Cool, some of you guys definitely deserve it! :)

---

