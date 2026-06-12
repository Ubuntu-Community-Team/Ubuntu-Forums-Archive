---
title: "Delete Windows AFTER install"
date: 2012-06-10
forum: New to Ubuntu
---

### Post by JiuJitsu500 on 2012-06-10
So, I ran into a problem I don't want to start if I can avoid it.

In short, I created a new partition (/sda4) inside a Toshiba's HDD to install the Gnome-Shell Remix of Precise on.

Short and sweet, it's configured, and everything is migrated over to where the ubuntu installation is.... now comes the big question. The owner of said Laptop decided she does not want windows anymore, and would like the entire HDD to be Ubuntu.

So, if I were to open up GParted on a Live USB, remove the sda1,2,3 (Windows Loader, OS, and Recovery crap), would the installation be mounted as sda1? or remain as sda4?

And, if it does become sda1 (I have no need for Swap, she has 8GB of RAM and I have /tmp mounted in RAM in the fstab).... what would I have to change in Fstab or GRUB, or anything else for everything to work as is?

I want to essentially remove the rest of the HDD, and move ubuntu to fill the whole thing up. I have converted another one, boys!

---

### Post by Enigmapond on 2012-06-10
Since there is already a mount point, you should just be able to resize and then format the partition. After which you just need to update grub.

---

### Post by black veils on 2012-06-11
yes i think you should be able to boot the ubuntu live cd/usb, load the desktop, open **gparted**, delete the windows partitions, **apply** one action at a time, to make sure they get completed successfully, and have ubuntu use all the free space.

then in the terminal ```
sudo update-grub
```if you have boot problems, try this:

1. boot into the Ubuntu live cd/usb, choose the try option, to load the virtual desktop environment.

2. open the terminal and copy-paste the following commands individually (press the Enter key after each and wait).

```
sudo add-apt-repository ppa:yannubuntu/boot-repair
``````
sudo apt-get update
``````
sudo apt-get install boot-repair
```3. find and launch **boot-repair**, then choose recommended repair.

---

### Post by YannBuntu on 2012-06-11
Hi
Here is a tool based on Boot-Repair that may be useful: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

---

### Post by oldfred on 2012-06-11
Some find they have one application they cannot live without. They come back and want to reinstall Windows.  It would not hurt to make a full image backup of Windows, just in case or the recovery partiton,  if you later want to sell it and buyer only wants Windows. It has taken me years to essentially get rid of XP.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Then rather than trying to move & expand sda4,  I would just format the space to ext4 and use it as a data partition or move /home to it if you do not have a separate /home.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

---

