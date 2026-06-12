---
title: "Ubuntu partition size, and mounting drives"
date: 2016-01-30
forum: New to Ubuntu
---

### Post by joakimvr on 2016-01-30
Hi everyone,

I've recently installed Ubuntu 14.04 LTS on my Asus laptop in a dual-boot with Win 10, and after a few attempts of installing I now have most things working (had issues with crashing during install when connected to wifi, and with the drivers for my NVidia GTX960M). The laptop comes with a 126GB SSD drive, and an addition 1TB HDD. Basically, I want both Win10 and Ubuntu (along with software) running from my SSD for best performance, and I'll use the 1TB drive for documents. I'll need most space for Windows, as that's where I will also be running a few heavier Adobe programs, and I'm a beginner in Ubuntu so I'm just toying around and learning the basics for the time being.

As this is my first Ubuntu installation, I think I might've underestimated the filesize of the basic OS a little. I had originally set aside approx 12 GB for all things Ubuntu. Upon install, I was *already* short of space, as the default setup from Ubuntu had somehow left me with only 80MB left of space in / root, the rest (a few GB) was a seperate partition. I used GParted and managed to edit this a little, but I'm still running short. I have attached a picture of the partitions and I would really appreciate some advice. Please bare with me as I'm totally new to Linux and a few of these expressions.

1) Does this look like a normal setup? I'm assuming the obvious fix needed is more space to _sda5_ as I'm assuming this is my main Ubuntu root for OS and software?

2) What exactly does mounting do, and how does this work in Linux? I can see that _sda7_ has a "Mount Point" and a **long** destination name. If anyone has a simple way of explaining this for me, I'd be very grateful. Is there a point in keeping this separate from _sda5_?

3) Are there any disadvantages I need to be aware of in terms of using the 1TB HDD for files for ***both*** Windows 10 and Ubuntu? I don't plan to install applications or software on it - it'll primarily be documents, projects and files I'm working on. Would I still be best advised to keep a dedicated extra partition for stuff I'm working on in Ubuntu?

4) Is swap size OK at 1GB? I have 16GB RAM on my computer, so I can't really see the need for a bigger swap - but again; I could've misunderstood the whole point of it.


Any other general advice on my first setup is **much** appreciated. I'm sure a few of these things are rather obvious, but I'd like to get this right from the very start.

Best regards

---

### Post by sandyd on 2016-01-30
For some reason, you have an additional partition (/dev/sda7) that is using 4.88 G of space

For a better understanding:
At the *minimum* for a reasonably reliable ubuntu installation, you will need two partitions.

One is called "root", and it's mount point should be "/"

The second partition is called "swap" and has no mount point. The swap partition is used in the same way that Windows uses the paging file. Its mainly a safeguard to prevent your computer from crashing immediately if you use all the RAM. If you do hibernation, the swap space must be equal or greater size than the RAM.

Since you just installed, you can boot into the livecd, and remove sda5,sda6,sda7. You can then create the partitions as noted above and install using "Something Else" when choosing partitioning.

Some people like to keep a separate partition for /home (equivalent to C:\Users) to keep their data in case of a reinstall (they simply re-use the /home partition), but as you have a tiny disk and are already storing the data on the 1TB HDD, there is not much reason to need one.

Please note that the /home folder _must_ be kept on Linux, and not mounted onto a NTFS partition. By default, NTFS does not support the ownership system used in linux, which will cause all sorts of odd issues.

---

### Post by oldfred on 2016-01-31
With 16GB of RAM, you will never need swap unless you edit videos or some other application that uses unlimited RAM. Many users with 16GB do not have swap, but system seems to be better if you just have some.
I might just add a 2GB swap on the HDD. If ever used it will not be fast on HDD, but you will never use it.

When I had XP I had two data partitions, one /mnt/data that was Linux formatted and one /mnt/shared as NTFS format with my Thunderbird & Firefox profiles & photos for Picasa. Those apps I installed and used in both systems, but used data from shared partition.

Windows auto mounts another NTFS partition as D:. In Linux you have to give it a name, like data or something more useful than d:. And you have to mount it. If you have not labelled it, it mounts with the UUID. I normally label partitions that I do not auto mount with fstab. And your shared data partitions need to be auto mounted with fstab entry which you have to manually add. Linux also has ownership & permissions which NTFS does not have. You have to set defaults for NTFS and tell system that you are the owner and have permissions for your Linux partitions.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

    
 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

---

### Post by joakimvr on 2016-01-31
Thank you so much for the answers, both sandyd and oldred. This gives me a much better understanding of how to set things up. I have since booted up on livecd and used gparted to make the changes necessary, so I removed the /dev/sda7 and moved swap to the right (kept 1GB, just to be on the safe side) in order to increase the root size. I no longer have /home/ but for the time being will be using my shared HDD.

I will actually reconsider the amount of space on my SSD I originally intended for Windows as well, as I can probably see myself using Ubuntu for more projects than I had anticipated if I get a good setup going. So far I'm loving it, I just need to read about basic differences from Windows and how to use the terminal. Thank you very much for the links attached. I will read up on fstab and how to auto mount the DATA drive.

A bit of a basic question, but is the purpose of the /mnt/ directory in my root simply a filepath where devices and partitions can be mounted?

Best regards,
Joakim

---

### Post by oldfred on 2016-01-31
There is lots of discussions on where to mount other partitions. With your own system you can do anything you like. I prefer /mnt, system automounts in /media/$USER but that usually is temporary mounts like a flash drive. Some directly mount into /home.

If you look at the definitions of /mnt & /media they are not a lot different.
       [http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/](http://www.tecmint.com/linux-directory-structure-and-important-files-paths-explained/)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)
[http://www.pathname.com/fhs/pub/fhs-2.3.html](http://www.pathname.com/fhs/pub/fhs-2.3.html)
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)
[http://en.wikipedia.org/wiki/Linux_Standard_Base](http://en.wikipedia.org/wiki/Linux_Standard_Base)
[http://en.wikipedia.org/wiki/Unix_directory_structure](http://en.wikipedia.org/wiki/Unix_directory_structure)

My standard installs are to 25GB / (root) partitions including /home with data on HDD. And I use about 13GB including 2GB for /home. But most of the /home is .wine for the Windows version of Picasa. The user settings in /home are tiny.

You can see the sizes of files in /home. For me .wine, and if I have Thunderbird and Firefox in /home those are the large folders.
sudo du -hc --max-depth=1

---

