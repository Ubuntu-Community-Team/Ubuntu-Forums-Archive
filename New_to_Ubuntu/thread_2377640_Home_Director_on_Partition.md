---
title: "Home Director on Partition"
date: 2017-11-15
forum: New to Ubuntu
---

### Post by gamendorf on 2017-11-15
I am brand new to Linux, and chose Ubuntu 17.10 as my first distribution.I decided to go all-in and wiped Windows from my HP during installation. Please forgive my ignorance on some of these basic things. I am at the point where I am so overwhelmed that I don't even know what to Google.  I followed an online guide to set up the partition table, and ended up with 8Gb swap, 20Gb for the OS, and 472 Gb for a Home partition.

The thing I don't understand is how to associate my Home folder with the Home partition. Right now, when I open the File Manager and right click->Properties on Home, it shows that I only have 10 Gb of free space. However, if I go to Other Locations -> 472 Gb volume, there is a directory with my user name and all of the Home Folder directories in it (Downlaods, Music, etc.)

It appears that the directory is there, but the file system does not associate the two together. How can I change this? If there is a way to accomplish it through the GUI, I would rather do it that way. I am by no means scared of the terminal, but learning it is further down on my to-do list.

---

### Post by TheFu on 2017-11-15
Congratulations!  

Most people New to Linux should only run LTS releases.  17.10 only gets 8 months of support.  16.04 is the current LTS release. For a desktop, many business people would say that LTS is important.  Home users, can take more risks with their stability.

For servers, almost everyone would agree that choosing an LTS is best for 98% of users.  There are exceptions, of course.

Your partition setup seems reasonable, though I find that more 4G of swap is seldom useful. The old rules of thumb for 2x RAM simply don't apply. If you use hibernation, a swap that is slightly larger than RAM is required.  If you care about security, hibernation is a bad idea.

Onto the question.  To make a partition mount as /home, there is 1 method - and only 1 method.  Modify (use an editor) the /etc/fstab.  No GUI.   Use "sudoedit /etc/fstab" and follow the instructions [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) explains.  Basically, you'll want to determine the UUID for the partition (470+G) and put that into the file following the pattern for each line.  Leave an extra, empty line at the bottom of the file.

For more help, post the contents of the **current /etc/fstab** and the output from ```
$ ls -l  /dev/disk/by-uuid/
```. Then someone can provide the exact line to be added.  If there is already a /home mount point in the file, then it is already handled by the installer.  BTW, it isn't hard to have the installation do this, but YOU have to take manual steps and "do something else" at the partition creation questions.

If you used LVM in the setup, things are slightly more flexible and more complicated. The output from **lsblk** would clearly show how disks and partitions are being used.

When posting output, please, please, use code tags. Adv Reply (#).

---

### Post by leunam12 on 2017-11-15
Your home folder with your Desktop, Music, Documents, etc. is /home/yourusername/
The /home directory is similar to the C:\Users\ directory in Windows

---

### Post by gamendorf on 2017-11-15
Thanks TheFu. That got me where I needed to be. I had actually installed 16.04.3 yesterday, but kept getting all sorts of system errors when I tried to install anything from the Ubuntu Software program, so I decided to give 17.10 a try. I am not having any of those issues with 17.10.

After I saw your comment about a fresh install handeling this if I did an extra thing, I decided to just re-install from scratch. I found the option to mount my large partition to /home within the partition table options.

---

### Post by TheFu on 2017-11-15
Great.  If you don't know what you are looking for, it is easy to miss.

BTW, if this is solved, please mark it that way in the "Thread tools" - that helps people looking for solutions AND people who want to help.

---

