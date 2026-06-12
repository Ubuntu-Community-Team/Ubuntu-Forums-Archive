---
title: "Can I access my NTFS partition?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by deleyd on 2008-05-23
I set up a dual-boot. Vista & Ubuntu 8.04. When I boot into Ubuntu, is there a way I can access files on my NTFS (Windows) partition?

And vice versa?

(On Ubuntu I used, that three letters and the number 3 format. [Man am I novice. But Vista forced me to switch.])

Right now I have a memory stick I use to shuttle files back and forth. Both Vista & Ubuntu have no problem with the memory stick. I wonder what format the memory stick uses? Never thought of that until now. That's a good question! Why does it work?

---

### Post by Monicker on 2008-05-23
When I set up my new laptop to dual boot with Vista and 8.04 all of my Windows partitions show up under the Places menu.

---

### Post by nkri on 2008-05-24
If you go into Places>Home Folder, both of your partitions and a bunch of other stuff should show up on the left side of the window.  Double-click on your windows partition and enter your password to access it.

Your memory stick is almost certainly formatted as FAT32.  This can be read by Windows (NTFS), Mac (HFS), and Linux (Ext3) formats so it is great for going between different computers or partitions.

---

### Post by ans5685 on 2008-05-25
Alternatively you may want to read through 

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

to automatically mount your windows partitions every time you boot.

---

### Post by sayakb on 2008-05-25
Ubuntu can automatically read your NTFS partitions thorough the pre-installed ntfs-3g module. 
For Vista to read the ext3 partitions, install the EXT2IFS driver from here: [http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

---

### Post by deleyd on 2008-05-28
That's pretty neat. I see it's right there and I am able to access my NTFS files!


Now, let's see, how do I mark this thread as Solved?

---

### Post by phread59 on 2008-05-28
Simple, log into this thread and you will see at the top a red (I believe) link called thread tools.  Click on it.  Down at the bottom you will see "Mark thread as solved".  Click it and the forum's software will do it's magic and mark it solved.  You can only do this to threads you started.  Glad you have your problem solved.

Mark Shuman

---

