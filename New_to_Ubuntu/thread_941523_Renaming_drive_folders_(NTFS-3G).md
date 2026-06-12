---
title: "Renaming drive folders (NTFS-3G)"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by Tony Williams on 2008-10-08
Okay, so in the '/media' I have a folder which is a drive-folder but I want to change it's name to something else.

Under Computer it's called 'Movies, Torrents' but when I access it I am taken to '/media/Educational' which contains all the right files and is the correct drive but '/media/Educational' should be '/media/Movies, Torrents'

It would save me alot of hassle in uTorrent if I could change the name.  So how does one go about unmounting the drive and changing the name?  The mv command tells me it's busy, so I need to unmount it first?

This is a NTFS drive.  I had a separate drive called 'Educational' in the right folder and everything however after removing the drive one of my drives has it's name.


[[IMG]http://img523.imageshack.us/img523/8800/screenshotcomputerfilebzr7.th.png[/IMG]](http://img523.imageshack.us/my.php?image=screenshotcomputerfilebzr7.png)[[IMG]http://img523.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

[[IMG]http://img146.imageshack.us/img146/1442/screenshoteducationalfikk2.th.png[/IMG]](http://img146.imageshack.us/my.php?image=screenshoteducationalfikk2.png)[[IMG]http://img146.imageshack.us/images/thpix.gif[/IMG]](http://g.imageshack.us/thpix.php)

---

### Post by Orange_and_Green on 2008-10-08
dear Tony,

open up a terminal and write:

```
mount | grep "/media/Entertainment"
```

It should return a line starting with "/dev/something". ("something" is likely to be something like "sdb1" but that depends on your system's setup). Make a note of it.

Then type:
```
umount /media/Entertainment
sudo mkdir /media/Movies,\ Torrents
mount /dev/thatSomethingYouMadeANoteOfBefore /media/Movies,\ Torrents

```

If the above does not work, try putting a "sudo" in front of the "mount" and "unmount" commands. Good luck:KS

[EDIT] please note, however, that it is potentially unsafe to use file or directory names with spaces in linux. Some programs might have problems with that.

---

### Post by Tony Williams on 2008-10-08
Big thanks, fixed.

---

### Post by Orange_and_Green on 2008-10-08
Glad it worked :) Just another thing,

The above will work for the current session, but when you log in again the partition will most likely get re-mounted to Entertainment.

To make these changes permanent, you can try
```
sudo mkdir /media/Movies,\ Torrents
sudo cp /etc/fstab /etc/fstab.backup
gksu gedit /etc/fstab
```

Scroll to the line that mentions "/media/Entertainment" and replace the text ```
/media/Entertainment
```
with ```
/media/Movies,\040Torrents
```

If there is no such line, please post again. Good luck!

---

