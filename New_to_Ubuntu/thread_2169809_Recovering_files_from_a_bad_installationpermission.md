---
title: "Recovering files from a bad installation/permission denied"
date: 2013-08-23
forum: New to Ubuntu
---

### Post by iclethian-p on 2013-08-23
I was using 12.04 for awhile, until I did something to screw up the installation. It doesn't really concern me, because I needed to update anyway. However, there are a few files on the harddrive that I would like to recover before reinstalling ubuntu. I created a live usb, and booted from that, but when I go to transfer the files to external storage, it is giving my permission denied. Is there any way to retrieve these files? Can I gain administrative privileges on a liveCD? Please be specific, I am still very new to ubuntu. Thanks in advance

---

### Post by rai_shu2 on 2013-08-23
Boot the USB drive, then [start a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and type:

gksudo nautilus

That should give you all the permissions you need.

---

### Post by iclethian-p on 2013-08-23
Ok, but now it opened up what I assume is the live usb's files, not the computers harddrive. I cant find my the folder containing the files I need to recover like I could before.

---

### Post by iclethian-p on 2013-08-23
Ok, I had to remount my computer hdd, but it renamed it from 15 GB Harddrive to a long random string of characters. When I navigate to my files, I get to the folder that is my name, but inside there is only a file called "Access-Your-Private-Data.desktop", and a readme text file. The Access program doesnt appear to do anything (no changes in permissions), and the terminal command it gives me in the readme file ```
 ecryptfs-mount-private
``` gives me the result ```
ERROR: Encrypted private directory is not setup properly
``` 
anybody know how to set the directory up properly?

---

### Post by iclethian-p on 2013-08-24
bump?

---

### Post by rai_shu2 on 2013-08-24
Maybe try this:

[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

---

### Post by iclethian-p on 2013-08-24
It appears to have work somewhat, but I get an error message in the graphical interface stating 
```
 **This location could not be displayed.** 
Sorry, could not display all the contents of "ecryptfs.kqzSHqx2": error when getting information for file '/tmp/ecryptfs.kqzSHqx2/.java': Input/output error
```
I can access some of my previously hidden files, but not nearly all of them, and not the folder I wanted.

---

### Post by iclethian-p on 2013-08-24
and one of my pictures i found was graphically glitched out, if that means anything.

---

### Post by rai_shu2 on 2013-08-25
If you're getting input/output errors, I'm guessing you have a corrupted file system or crashed drive.

---

