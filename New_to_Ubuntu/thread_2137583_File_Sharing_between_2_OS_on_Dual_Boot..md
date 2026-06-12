---
title: "File Sharing between 2 OS on Dual Boot."
date: 2013-04-21
forum: New to Ubuntu
---

### Post by JonthueM on 2013-04-21
The other week I ask this question on AskUbuntu.com which was "this: How can I access and edit ubuntu files from a windows 7 partition?  should I start saving my files on windows partition so it becomes more  accessible to both partitions or just create a separate partition  accessible to both OS's?" got some predicted answers but a user posted something up that I need help in understand ways of going about it. This is what the user posted.

 "If what you are trying to do is [share files]("http://askubuntu.com/questions/282434/how-can-i-access-and-edit-ubuntu-files-from-a-windows-7-partition/282441#")  between partitions then I would create a FAT32 partition purely for  that purpose. That way you would be able to access the information from  both Win7 and Ubuntu. For example if your /home partition in Ubuntu was a  separate partition to your /root then you could format it as FAT32 and  mount it via fstab. When logged into Win7 you would be able to access  and read/write to this partition as normal."

So my question is why FAT32 and not NTFS? And can my /home partition be separate from /root? Is it wise to do that? Which method is wise to use?

My System  
Dell Inspiron N5050 Intel 
Pentium CPU B950 @ 2.10 GHZ 
4 GB RM
64 Bit System

Windows 7 and Ubuntu 12.10 Dual Boot.

---

### Post by Cheesemill on 2013-04-21
There is no reason at all to use FAT32 instead of NTFS for a shared data partition. I always go for NTFS in this situation.

You ***cannot*** have a separate /home partition on a FAT32 or NTFS partition as these filesystems don't support the Linux permissions structure which is needed for a home directory.

I have my system set up as follows, my / and /home partitions are both ext4 and live on my SSD. I then have a large NTFS data partition which I mount as /mnt/data which contains all of my music, videos etc. I then have the usual ~/Music, ~/Videos, ~/Pictures directories set up as symlinks pointing to this data partition.

This way I get the speed increase of having my home partition on an SSD, but as all of my media is on the data drive I can get away with having a 15GB home partition without any danger of it filling up. You can see what my home folder looks like....
```
rob@quantal:~$ ls
total 12K
lrwxrwxrwx 1 rob rob   14 Apr 17 20:24 bin -> /mnt/data/bin/
drwxr-xr-x 2 rob rob 4.0K Apr 17 19:44 Desktop
lrwxrwxrwx 1 rob rob   20 Apr 17 20:24 Documents -> /mnt/data/documents/
lrwxrwxrwx 1 rob rob   20 Apr 17 20:24 Downloads -> /mnt/data/downloads/
lrwxrwxrwx 1 rob rob   15 Apr 17 20:24 Emulation -> /mnt/emulation/
lrwxrwxrwx 1 rob rob   15 Apr 17 20:24 ISOs -> /mnt/data/isos/
lrwxrwxrwx 1 rob rob   16 Apr 17 20:24 Music -> /mnt/data/music/
drwxrwxr-x 4 rob rob 4.0K Apr 15 22:09 Notebooks
lrwxrwxrwx 1 rob rob   19 Apr 17 20:24 Pictures -> /mnt/data/pictures/
drwxrwxr-x 2 rob rob 4.0K Apr 17 21:02 Ubuntu One
lrwxrwxrwx 1 rob rob   17 Apr 17 20:24 Videos -> /mnt/data/videos/
lrwxrwxrwx 1 rob rob   14 Apr 17 20:24 VMs -> /mnt/data/vms/
rob@quantal:~$ 
rob@quantal:~$ 
rob@quantal:~$ df
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/ssd-root   14G  5.3G  7.9G  41% /
/dev/sdb1             147G  113G   27G  81% /mnt/data
/dev/sdc1             910G  825G   85G  91% /mnt/emulation
/dev/mapper/ssd-home   14G  666M   13G   5% /home
rob@quantal:~$ 
```


[[IMG]http://ompldr.org/taTY2MA[/IMG]]("http://ompldr.org/vaTY2MA")

---

### Post by Frogs Hair on 2013-04-21
See the shared data partition section. Both Windows and Ubuntu can read and write from fat 32 making things like common email possible.  [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by JonthueM on 2013-04-21
Interesting! so you can sent the /folders under different partitions. Is your SSD external or internal? @Cheesemill

---

### Post by Cheesemill on 2013-04-21
I have an internal SSD with my / and /home partitions on. My 2 large mechanical drives are mounted at /mnt/data and /mnt/emulation, but because of the symlinks I set up then /mnt/data/music for example appears to be the standard Music folder in my home folder.

You can also change the location of your folders in Windows as well (right-click and select 'change location'). In this way both my ~/Music folder in Linux and my C:\Users\Rob\Music folder in Windows both point to the same location on my shared NTFS drive.

---

### Post by JonthueM on 2013-04-21
According from my quick read the /folders would still be directed to the current partition, but the only difference is that you will see another filesystem on the folder navigation bar. Question for both of you how would you link /pictures to the picture folder in the shared files partition for ubuntu?

---

### Post by oldfred on 2013-04-21
I do the same as Cheesemill.

I have two data partitions. I originally was dual booting Ubuntu & XP and back then used FAT32 for a shared partition. I had my Firefox & Thunderbird profiles in the FAT32 partition. But I tried saving some larger files and did not know the limit was 4GB and it totally corrupted them. I since converted my shared to NTFS and still use it even though I now do not use XP. I now have a ext3 data partition that I use for all my new shared data. I have the shared data partitions primarily since I multi-boot and want access to the same data from all systems.

       Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

### Post by Cheesemill on 2013-04-21
If you want to link your users ~/Pictures folder to a different directory....

First back up any existing contents of the ~/Pictures directory as we need to remove it, then delete the folder...
```
rm -rf ~/Pictures
```
Then create the symlink using 'ln -s <TARGET> <LINKNAME>' for example...
```
ln -s /mnt/data/pictures Pictures
```

This is exactly the method I use, you can see from the following output of my ls command that the Pictures directory in my home folder is just a shortcut to where the actual files are stored on my other drive...
[[IMG]http://ompldr.org/taTY3dQ[/IMG]](http://ompldr.org/vaTY3dQ)

---

### Post by JonthueM on 2013-04-21
So ext3 better then NTFS since I am also aware of FAT32 limits?

---

### Post by Cheesemill on 2013-04-21
Windows can't read ext formatted partitions.

The main reason to use NTFS for a shared data partition is that it can be read by Ubuntu and Windows without having to install any extra software.

---

### Post by JonthueM on 2013-04-21
Wow you guys are awesome :popcorn: this is better then askubuntu. Making me seriously consider on learning the unix language so I can learn to truely harness ubuntu! I will definitively take everything I learned here and try it out when I have time. Do you happen to know where I can learn the unix language interactively like Codeacdemy.com?

---

### Post by Cheesemill on 2013-04-21
I'm not sure about interactively but the best place to start is the [Command Line Resources]("https://help.ubuntu.com/community/CommandLineResources") page on the Ubuntu wiki.

---

