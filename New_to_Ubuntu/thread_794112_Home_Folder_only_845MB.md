---
title: "Home Folder only 845MB?"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by LinuxFox on 2008-05-14
I recently installed Ubuntu via Wubi onto a 40GB Partition (I wanted to keep it separate from my Windows files), and my Home folder is only 845MB.

My question, is there any way I can make this bigger?  I notice it keeps going down slowly.  Currently I'm only storing artwork I do on GIMP, but I'm just worried I might not have enough space for other stuff I want to store or do.  Please help and thanks.

Edit: If it helps, I'm using Ubuntu 8.04 LTS Desktop Edition.

---

### Post by Paqman on 2008-05-14
How much space did you allocate for Ubuntu when you installed using Wubi? Wubi creates a virtual hard drive that will expand in size up to that maximum figure. If you selected 40GB then your Ubuntu installation (including your /home) can keep expanding up to that ammount.

---

### Post by LinuxFox on 2008-05-14
> **Paqman said:**
> How much space did you allocate for Ubuntu when you installed using Wubi? Wubi creates a virtual hard drive that will expand in size up to that maximum figure. If you selected 40GB then your Ubuntu installation (including your /home) can keep expanding up to that ammount.Thanks for replying, I chose 10 GB.  I thought that was for the operating system, not the partition.  Would it be a good idea to reinstall with Wubi?

---

### Post by SunnyRabbiera on 2008-05-14
the overall install of ubuntu should be no less then 10gigs, or at least 8 gigs to get a base system, I just suggest 10 to get some breathing room in ubuntu.
how did you partition?

---

### Post by t0p on 2008-05-14
When you click on **Places > Home Folder**, the contents of your home directory are displayed, and in the bottom left corner of the window should be a message saying how many items are in the directory and how much free space there is.  Mine says "35 items, Free space: 2.6 GB".  What does yours say?

A user's home directory is usually dynamically sized.  Mine is currently 2.8 GB; if I add a 1 GB file, it will become 3.8 GB.  What happens when you add files to your home directory - does its size increase by the size of the new file?

---

### Post by LinuxFox on 2008-05-14
> **SunnyRabbiera said:**
> the overall install of ubuntu should be no less then 10gigs, or at least 8 gigs to get a base system, I just suggest 10 to get some breathing room in ubuntu.
how did you partition?I used Partition Magic in Windows.  I just simply wanted to keep Windows files/games separate from Ubuntu.

---

### Post by LinuxFox on 2008-05-14
> **t0p said:**
> When you click on **Places > Home Folder**, the contents of your home directory are displayed, and in the bottom left corner of the window should be a message saying how many items are in the directory and how much free space there is.  Mine says "35 items, Free space: 2.6 GB".  What does yours say?

A user's home directory is usually dynamically sized.  Mine is currently 2.8 GB; if I add a 1 GB file, it will become 3.8 GB.  What happens when you add files to your home directory - does its size increase by the size of the new file?Mine says "8 items, Free space: 840.0MB".  It goes back to 845 when I quit Firefox.  A few pictures downloaded lowers it until I delete it.  At least it seems that way to me.

---

### Post by Paqman on 2008-05-14
> **LinuxFox said:**
> Thanks for replying, I chose 10 GB.  I thought that was for the operating system, not the partition.  Would it be a good idea to reinstall with Wubi?

That's your problem. That's the total size allowable for your installation, meaning 30Gb goes to waste.

You can try using [LVPM](http://lubi.sourceforge.net/lvpm.html) to adjust the size of your virtual partition, but I don't believe it's been tested on Hardy yet. Use the "resizehome" and "resizeroot" options. If that doesn't work then you might have to reinstall.

---

### Post by t0p on 2008-05-14
> **Paqman said:**
> That's your problem. That's the total size allowable for your installation, meaning 30Gb goes to waste.

You can try using [LVPM](http://lubi.sourceforge.net/lvpm.html) to adjust the size of your virtual partition, but I don't believe it's been tested on Hardy yet. Use the "resizehome" and "resizeroot" options. If that doesn't work then you might have to reinstall.

Do you have a LiveCD?  You should be able to use that to resize your partitions.  Well, you can with the Gutsy LiveCD - I'd imagine that the Hardy CD will do it too.

**EDIT:** *Whoops!!* You're talking about *virtual* partitions!  Sorry, I didn't realize.  Please ignore my posts.

---

### Post by Paqman on 2008-05-14
> **t0p said:**
> Do you have a LiveCD?  You should be able to use that to resize your partitions.  Well, you can with the Gutsy LiveCD - I'd imagine that the Hardy CD will do it too.

That won't work. It's not a disk partition, it's a loopmounted virtual partition created by Wubi.

Wubi is brilliant, but it does business in a slightly different way to a normal install, due to sharing a partition with another OS (namely Windows).

---

### Post by LinuxFox on 2008-05-14
> **Paqman said:**
> That's your problem. That's the total size allowable for your installation, meaning 30Gb goes to waste.

You can try using [LVPM](http://lubi.sourceforge.net/lvpm.html) to adjust the size of your virtual partition, but I don't believe it's been tested on Hardy yet. Use the "resizehome" and "resizeroot" options. If that doesn't work then you might have to reinstall.I tried the program and it didn't work.  So I reinstalled Ubuntu, changed it to the maximum avalible size (30GB), and I now hav 3.4GB avalible.  Enough to store artwork and small downloads on.  Thanks a lot Paqman! :D

---

### Post by Paqman on 2008-05-14
No probs, happy to help!

---

