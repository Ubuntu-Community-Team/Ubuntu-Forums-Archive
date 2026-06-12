---
title: "Questions about partitions..."
date: 2008-05-05
forum: New to Ubuntu
---

### Post by abenrob on 2008-05-05
Hey folks. I just recently made the XP-Ubuntu switch, and for the most part it went off without a hitch. One thing has been an issue though. I have an external HD that I am trying to use for file backup for my xp (work) partition, my ubuntu partition, and my other computer (osx tiger.) I was unable to use gparted (nor the gparted live cd) to create hfs+ partitions, so I created all three with the mac disk utility. It created the windows and the mac partition fine, but couldn't do the ext3, so I created one as undefined. With gparted I was able to re-allocate the undefined as ext3 and all looked good. However, in trying to move files onto the ext3 partition, I get an error saying I don't have the proper permissions to write to said partition. I searched in vain for an option that would allow me to change the permissions, but was unsuccessful. Does anyone have experience with this situation? Advanced thanks, because all my other issues and questions have been easily (and energetically!) resolved, and the support community has been amazing.

---

### Post by amohanty on 2008-05-06
Once you mount the partition (i am assuming names and locations - fill in with what you have):

sudo mkdir -p /mnt/ext3-bkup
sudo mount -t /dev/... /mnt/ext3-bkup
sudo chown -R username:username /mnt/ext3-bkup

If it is already mounted at boot, simply do the last one.

HTH
AM

---

### Post by abenrob on 2008-05-06
So in changing the file structure, it renamed the device '85.9 GB Media'
when I put that name in, I get errors. Do I need to rename it? how?

---

### Post by amohanty on 2008-05-09
sorry for the late response, a couple of questions:
1. What do you mean "changing the file structure"?
2. When you say renamed it to "85..." is that the name of the icon you see on the desktop? 
3. Can you post what you did?

AM

---

### Post by abenrob on 2008-05-15
So when I used GParted to define the undefined partition as ext3, it didn't allow a naming, but re-named it 85...
This is on the desktop, but also in the disk properties. 
Maybe I'm confused (very possible...)
Thanks for the help, again.

---

### Post by Bakon Jarser on 2008-05-16
you can use

gksudo nautilus

to open the file manager as root.  This will give you unlimited access to all drives.  This probably isn't the solution you are looking for, though it is a quick way to get you write access to all drives.  It isn't a great idea because you will also be able to delete files that you shouldn't delete.  I'm kinda new to all this to but I will look up how to change permissions on a drive and get back to you.

---

### Post by Bakon Jarser on 2008-05-16
It might take a little reading but I think this page will help get you where you want to be.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

