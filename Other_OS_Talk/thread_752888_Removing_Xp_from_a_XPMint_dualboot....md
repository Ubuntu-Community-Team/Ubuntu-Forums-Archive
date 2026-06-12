---
title: "Removing Xp from a XP/Mint dualboot..."
date: 2008-04-12
forum: Other OS Talk
---

### Post by p10 on 2008-04-12
I have been running a dualboot XP/Mint for some time now. As time has past, I no longer use my XP-install, and want to remove it an go solo on Linux Mint.

I have two options:
[list]Fresh install
Use Gparted to delete XP and reformat the partitions.[/list]

I think a fresh install would have the highest probability of sucess, but it would meen that many months of tweeking the system to my liking would be wastet!

Using Gparted would hopefully save me a lot of work, but I fear that it would be to difficoult to do? Or am I wrong??

---

### Post by agurk on 2008-04-12
Nah, shouldn't be too difficult I think. Boot from a Gparted live cd, delete the XP partition and resize your Linux partition(s).

---

### Post by K.Mandla on 2008-04-12
You might even be able to do that from the Ubuntu side without going to a GPartEd live CD -- just start it from the Gnome menu. You might have to unmount that partition though.

But you know, I've never actually done that. Live CD is probably best. Ignore that suggestion. :roll:

---

### Post by p10 on 2008-04-12
This is what i ended up doing:

Booted a Live-cd and used Gparted to remove my XP-partition and make a new xt3-partition out of the freed-up space.

I then got the idea to use this new partition to host my homefolder. So i followed this how-to:

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

Only problem was that I forgot to change this addition "/dev/hda7 /home ext3 nodev,nosuid 0 2" to the fstab so that it pointed to my new homepartition "sda5"... Result: Unable to login after the reboot!

Had to go back and redo the fstab so that it pointed to the right place!

But in the end I got it all to work (so far at least) and I am pretty pleased with the result: Got ridd of XP and kept my tweeked Mint 4.0 the way I liked it! :D

---

