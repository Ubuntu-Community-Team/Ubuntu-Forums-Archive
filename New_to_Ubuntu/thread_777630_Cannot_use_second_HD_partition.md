---
title: "Cannot use second HD partition"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by Jay Car on 2008-05-01
I did a reinstall of Ubuntu last month. For the original installation the 250GB drive had not been partitioned (I didn't do the original installation).

For the reinstall I decided to partition the drive, but didn't realize that, Ubuntu Live CD (being the well-mannered and careful installer that it is), kept the old Ubuntu system files intact on one of the partitions.  My intention had not been to keep that old system at all.

The problem now is that, no matter what I do, there's a 116 GB partition that absolutely will not allow me to use it.  Can't even paste new files or folders into it.  I get messages that I don't own that partition and don't have permission to access it. It will mount, but it won't allow anything more.

I decided to try gparted to just delete that partition and get rid of those old system files (thinking they might be the problem).  But that didn't help either.  

Decided to try a Partition Editor.  But it shows 4 partitions, instead of two, but gives no further info (like size?) that I can use to identify the partition I want to gain access to, so I'm afraid to do anything for fear of mucking up my Ubuntu partition.

I'm soooo frustrated.

I should mention here that my Ubuntu computer works beautifully in all other ways, even updated to Hardy with no problem. I love my Ubuntu machine...if I can just find a way to get the other half of my hard drive back it would be Practically Perfect in Every Way (sort of like Mary Poppins, only without the umbrella :) ).

Help? Please?

---

### Post by phr0ze on 2008-05-01
I don't even know where to start with this one. gparted should be all you need. Have you tried gparted on a bootable CD? If not you should. Download the ISO from the gparted web site. I think on Hardy CD there is even a partition editor. You could just boot your live CD and then get your partition back.

Good luck.

---

### Post by bluefrog on 2008-05-01
I assume you successfully wipe the partition with gparted and formatted it as ext3 filesystem.

I will show you how to create a data mount point and mount that partition.
I will assume the partition is /dev/sda4.
Adapt to your case/likings.

open a terminal

sudo mkdir /data
sudo chown $USER.$USER /data

edit /etc/fstab (sudo nano /etc/fstab) and add the following line
/dev/sda4 /data ext3 defaults 0 2

ctrl O and enter to save the file. ctrl X to exit

sudo mount -a

you can now use your /data file system

---

### Post by Jay Car on 2008-05-01
Hi bluefrog, 

Yes, wiping the partition using gparted seemed successful.  It wasn't hard to do.  The first thing I did after using it was to mount that partition and try to move (copy/paste) a file onto it.  Still got the message that I didn't own it and had no permission.  

To answer your question about formatting it as ext3, I apparently didn't. According to my System Monitor the partition I cannot access is described as:
Device:  /dev/sda1 
Directory: /media/disk
Type: ext2

The partition that boots Ubuntu is described as:
Device:  /dev/sda3 
Directory: /
Type: ext3

This computer has never had Windows installed, the hard drive's never known life without Ubuntu :) But I don't understand the difference between ext2 and ext3.  Did I do something wrong when reinstalling Ubuntu and making the new partition?

When I follow your instructions to create a data mount point, I will replace /dev/sda4 with /dev/sda1 

I'm going to try it right now...

---

### Post by Jay Car on 2008-05-01
Hello again,

It's taken a while to do the task...I had a work assignment come in. But I did get to follow bluefrog's instructions after work. I did changed /dev/sda4 to /dev/sda1 before I pasted...and saved it, then exited. 

Then opened that partition and tried to copy/paste a small text file into it, but "create folder", "create document", and "paste" are all still unavailable...grayed out. Dragging a file into the partition also fails and gives the error again. (I took a screenshot...I think it's attached, if not I'll try attaching it again)

It occured to me that the partition had been mounted during the terminal task (I don't know what else to call it :) ) so I unmounted that partition and tried it again, but the line was already there, so there was no need to edit it again.

What would cause that partition to totally lock me out? (lol, not that I'm taking it personally) Could I somehow have ruined that partition when I reinstalled Ubuntu?  Do you think it's lost for good?  And what do you suppose is in that mysterious Lost & Found folder that's on it? (It won't even let me look in it)

If I don't "own" that partition and have no permission to use it, then who does?  I'm sure the solution is spectacularly simple...maybe?

This is the first time I've sort of missed Windows, where I could log into the Administrator account and give my user account permission to do stuff, when needed.  I understand and appreciate Ubuntu's security, but all I want to do is save files to a second partition...that shouldn't require an escalation of privleges, should it?

It's more likely caused by something I've done. 

Should I just start over from scratch and get rid of the partition all together, and let Ubuntu have the whole 250GB drive?

---

