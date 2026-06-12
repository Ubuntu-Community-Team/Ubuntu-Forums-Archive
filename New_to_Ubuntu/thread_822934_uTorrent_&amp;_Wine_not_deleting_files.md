---
title: "uTorrent &amp; Wine not deleting files"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Joe_Ipsen on 2008-06-08
So, I've been trying to hunt down what was hogging all of my diskspace.  My wife is using uTorrent on Wine to download the internet.  Okay, so not that bad but the way she can fill my 250 Gb HD is scary.

Anyway, I believe I've found that when she selects "delete .torrent and data" from within uTorrent it moves the file to the following directory, but this directory is not referenced by the Trash bin and the files are not deleted.

/home/lindsey/.local/share/Trash/files

Within this folder, the permissions are set such that no one but Root (I think) can delete the files, so I have been deleting the files using the following commands:

sudo rm 1*
sudo rm 2*
etc.

So, here are my questions.  
-Do you know how to set this combination of programs to actually delete this files the first time around?  
-Is this a bug?  If so, where's the best place to report it?
-Is there a better way to clean this folder out?* 

-Joe

* - I suppose I could run a very destructive script aimed just at that folder, but creating a script that does "sudo rm 1*, sudo rm 2*, etc.) could be easily pointed at the wrong directory and wipe out "good stuff".

---

### Post by Joe_Ipsen on 2008-06-08
Oh, one other thing, it was a complete PITA actually finding these files.  I tried using the search tool for files > 10 mb, baobab, df -h and finally du -ha.  

Here's the combo that revealed these files

$sudo du -ha | egrep "M|G" | more

The last command (run as Sudo from root) and some brute parsing of the output is what eventually found them by running the below command and just looking through the output until I found something useful.

Here are the permissions of one of the files:

-rw-r--r-- 1 lindsey lindsey      37122 2008-01-30 08:30 UFO Files.txt

---

### Post by ThreeLies on 2008-06-08
This is standard uTorrent behavior to move files to the trash which goes to wine tash bin.

Just go into Options -> Preferences -> Advanced

In there find the variable "gui.delete_to_trash" change that to false.

Now uTorrent will directly delete files.

---

### Post by RequinB4 on 2008-06-08
You can delete root-owned files easily by running ```
gksudo nautilus
```

I have no idea why they changed the trash setup.  I haven't had many issues, but I know people that have. :shrug:

---

### Post by Joe_Ipsen on 2008-06-19
Thank you both for the tips.  I will put them to good use.

---

### Post by tjwoosta on 2008-06-19
why use Utorrent in wine?

there are plety of torent clients available on linux

i reccomend either transmission or Bittornado

transmission is simple and straight forward whereas Bittornado is a bit more of an advanced interface with more options

---

### Post by RiceMonster on 2008-06-19
Try out Deluge as a replacement for uTorrent on Linux. It suites my needs perfectly.

---

