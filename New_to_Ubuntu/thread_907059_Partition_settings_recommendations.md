---
title: "Partition settings recommendations"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by Nimbled on 2008-09-01
Hi all, 

I've been reading up on partitioning [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/partitioning").

Since then, I've been in a dilemma on which of the following two settings to choose from.

1) 
[IMG]http://www.psychocats.net/ubuntu/images/partitioning4.png[/IMG]

or

2) 
[IMG]http://www.psychocats.net/ubuntu/images/partitioning5.png[/IMG]


Any advice is greatly appreciated.
Thanks a lot.

---

### Post by aloshbennett on 2008-09-01
I would suggest option 1 if you boot to XP frequently. Give your /home atleast 5GB to work with.

On a longer run, I realized that I havent booted into XP in a really really long time and I wish I had gone for Option 2. Infact, I am toying around with the idea of removing XP completely :)

---

### Post by bumanie on 2008-09-01
Now that ubuntu has read/write to ntfs (known as ntfs-3g), that is stable, I would not even consider having a FAT 32 due to its inherent file size limitations. It is a good idea to have a separate /home and / You can have a shared ext3 if you wish, but it the read/write function from ntfs to ext3 is not as stable as ntfs-3g. Most users tend to have a shared ntfs partition rather than a shared ext3 for this reason. Personally, I go for ntfs-3g and enable ntfs-config so that I have read/write to windows from ubuntu and don't have a specific shared data partition.

---

### Post by Nimbled on 2008-09-01
Thanks for the quick replies.
So basically, the general consensus is option 2 i guess.

Does the tutorial [[COLOR="Red"]here[/COLOR]]("http://www.psychocats.net/ubuntu/installing") tell me how to create my partition in the same way as shown in option 2?

---

### Post by Bucky Ball on 2008-09-01
I would avoid having EXT3 shared partition. Not stable. Fat32 or (not that I use it myself) NTFS.

---

### Post by bumanie on 2008-09-01
If you really want a shared data partition, choose ntfs as stated in the two posts above, ntfs-3g is more stable than writing to ext3 from windows - there is a program available, but as said, it is generally seen as less stable than ntfs-3g.

---

### Post by MasterSander on 2008-09-01
I had the same problem. I now have a 85 gb data ntfs partition, 12 gb ubuntu (ext3) and 20 gb xp (ntfs) and 30 gb vista (ntfs). I like to try different OS, so that's why I still run both xp and vista (had vista and ubuntu before). The best option really is ntfs, although you can also access ext3 filesystems in xp, but ntfs is really more handy. FAT32 I would not ecommend because of the huge limitations . When I ran MacOsX (version for x86), it also wasn't a problem.

---

