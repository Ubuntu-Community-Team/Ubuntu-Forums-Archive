---
title: "Question about disks"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by Luc_Lacombe on 2013-10-18
Hello  Pardon me but I'm not ready to be considered a Linux thinker...not yet!  I have a question.  In Windows all disks are visible in Windows Explorer.  I have a newly installed Ubuntu 12.04 and have an extra HDD and a memory card reader.  How and where can I see these? What's the software name?  Thanks!    Luc    PS. Gee I don't believe this...It's installed and updated since 5 minutes and I have access to one of my computer for sharing in my home network!!!

---

### Post by Bashing-om on 2013-10-18
Luc_Lacombe; Hi !

Hard disk: much like "explorer" is ubuntu's nautilus. Click on the folder icon at the top of the "launcher" to activate "nautilus" as the file manager. All drives/partitions are represented in the left pane.

Card reader: insert a card into the reader and an icon should appear on the desk top.

The developers put a lot of work and effort into making ubuntu as simple/intuitive as possible. The learning curve, however, is still present. Hang in there and you may be amazed where you go from here !

We are always here to help you over the rough spots.

[INDENT][INDENT]ubuntu, greatest operating system the world has ever seen
[/INDENT][/INDENT]

---

### Post by Luc_Lacombe on 2013-10-19
Hello Bashing-OM  Thanks for answer and encouraging kind words! OK. Nautilus is the folder-icon on the top. 1) If I insert a SD or FC memory card in the card reader nothing appears but if I insert a USB key in the same reader the volume is shown on the left-side application icons.      Why SD or FC card does not shows? 2) I don't quite understand the way the Files & folders are arranged. Like going into  the "Firefox" folder to copy the "places.sqlite" file recovered from an Acronis  backup from last Windows computer that died...  Luc

---

### Post by Bashing-om on 2013-10-19
Luc_Lacombe; Well.
As to why the icons do not appear with a  SD or FC memory card in the card reader; presently do not know.
Let's see if the device is recognized by the operating system. 
Terminnal commands - key combo ctl+alt+t yields a terminal - 
post back the outputs od terminal command:
```

lsusb

``` with the card reader not plugged in and then repeat with the card reader plugged in .. looking for an entry for the card reader.

Do not forget to "safely remove" - as in eject - the device prior to removal ! Else file system corruption at some level will result .. ububtu uses a cache for write operations and this cache is not written to disk prior to "safely removing" said device, nor is that device file closed in the operating system until that action is performed.
 
Ubuntu file system: Takes a bit of an adjustment and a bit of a learning curve. Libraries are installed in one place, executable Binary files in another, your personal files yet another and on and on ...partitions for a particular purpose, containing directories as well as files, containing more directories and files-> going deeper and deeper.
To the situation at hand: "places.sqlite" file ... If this is a Windows' file you are thinking to copy onto the ubuntu FireFox (??); no can do as the system files are not compatible - one operating system to the other. Data files may be exchanged to some extent, but not system files. 
For copying files in general, copy and paste works very well between 2 open windows. Click drag and drop.  Test first to see what results. Depending on default settings in the file manager .. a drag/drop operation may be interpreted as a "move" where the original is not retained, or as a "copy" where both the original and the copy are retained.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by Impavidus on 2013-10-19
If I'm correct places.sqlite is a file containing the bookmarks in firefox or something like that. In Ubuntu it is in ~/.mozilla/firefox/some_random_code.describing_your_profile/places.sqlite. Not sure whether putting your backup would work, but you can try. I would make a backup of the profile directory though before trying.

---

