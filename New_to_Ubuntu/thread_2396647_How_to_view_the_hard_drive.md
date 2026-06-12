---
title: "How to view the hard drive"
date: 2018-07-18
forum: New to Ubuntu
---

### Post by cortimi12 on 2018-07-18
I will try to be as simple and clear as I can. I have a total of three hard drives. My concern is with one of my external drives. One is named Backup. The other is named Storage. Storage is a new hard drive. It has been formatted with ext4.

The problem: Storage does no show up in the list on the left the way that Backup does. In the screenshot, in the left window, you can see Documents, etc, Backup, but not Storage. To view Storage I must go to "other locations". I do not want to go to "other locations" I wish for Storage to be listed in there with Backup. What is the fix for this?

[https://s33.postimg.cc/uvvianczz/Screenshot_from_2018-07-18_20-09-10.png](https://s33.postimg.cc/uvvianczz/Screenshot_from_2018-07-18_20-09-10.png)

---

### Post by wildmanne39 on 2018-07-18
Hello and welcome to the forum!

Please use the attachment facility by clicking on the paperclip or  use url's for images because apart from bandwidth issues for some, it makes it difficult for those using mobile devices to browse the forum.

---

### Post by Skaperen on 2018-07-18
_Storage_ is already under _On This Computer_, a primary position.  does it not work there, for you?  can you open a terminal and do the command _**[FONT=courier new]cat /proc/{partitions,mounts}|egrep -v 'gvfsd|tmpfs'[/FONT]**_ and post the output (in _[CODE] tags_ around that text such as the _**#**_ icon can do for you).  that will show the system perspective of your hard drives.  sorry for such a long command.  hope you can copy and paste it.

---

### Post by cortimi12 on 2018-07-18
I can use it just fine. I don't want to have to go to "Other Locations", I want it to be listed on the left hand side like the other one, like Documents/Trash/etc. Backup is listed in the left hand list, I want Storage to be too, not buried under Other Locations

---

### Post by ajgreeny on 2018-07-19
The simplest way may be for you to add its mountpoint to the Bookmarks in your file browser.

What is its mountpoint?
Normally any external disk/partition that automounts in /media will show automatically but if it is mounted in /mnt or elsewhere from /etc/fstab it will not show unless you either first mount it or add it as a bookmark.

---

### Post by oldfred on 2018-07-19
Did you label partition as Storage?
Post this:
lsblk -f

---

### Post by leunam12 on 2018-07-19
Open the file browser and press CTRL+L and type /media/cortimi/ and press enter, 
then drag the "Storage Folder" to the left side pane to create a shortcut.

---

