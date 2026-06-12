---
title: "[SOLVED] Can't figure out how to use gparted effectively"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by masterofthemelee on 2008-10-29
I can't seem to unmount my ext3 partition (where ubuntu is), and I don't see anything to resize my existing ext3 partition when I boot from my install cd.

I want to shrink the ext3 partition to 50 GB (or as close as possible), move it to be directly next to the windows partition, and get rid of that blank space inside of the blue box made by the ext3 partition (what is that, anyway?)

[IMG]http://img.photobucket.com/albums/v118/masterofthemelee/Screenshot.png[/IMG]

---

### Post by bumanie on 2008-10-29
You need to use gparted via a live cd. Before you can alter partitions, they must be unmounted. Thus, if you are trying to alter a partition that is mounted gparted will not do anything. You can use a live ubuntu cd or download the dedicated gparted cd. If using the ubuntu live cd in terminal > sudo apt-get install gpartedThen go to System --> Administration --> Partition editor.

---

### Post by Xiong Chiamiov on 2008-10-29
Grey space is unallocated, or blank space that's not formatted or being used.  The part surrounded in cyan is an extended partition, which, in short, means that it's a group of partitions.  If you want to move it, you'll have to click on /dev/sda3.

You probably have /dev/sda5 mounted, which is why you can't resize it.  You'll need to boot off of the live cd to resize it.

---

### Post by masterofthemelee on 2008-10-29
Thank you, bumaine, I did not realize you could install software during a live cd session.  When everyone said "use gparted on the live cd" I figured they meant go to install and use the partition editor in the installer.

---

### Post by bumanie on 2008-10-29
No problems - we all started with little knowledge, asking questions is one way to learn.

---

### Post by masterofthemelee on 2008-10-29
Oh Jesus Christ 14 hours remaining what the hell, man.

---

