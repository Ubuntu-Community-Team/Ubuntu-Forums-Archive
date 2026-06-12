---
title: "A way to have my &quot;shared data&quot; load on startup"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by epicbattle on 2011-10-20
Alright, so I am dual booting Ubuntu 11.04 with Windows 7. Currently I have it set up so I have some 100 gigs to Windows 7, 50 gigs to Ubuntu, and the remainder (about 300gigs) is set to a "data" partition. It's nice because I can put all my media or school pdf files on "data" and I can access it with both Windows 7 and Ubuntu. However, when I want to listen to music on Ubuntu I always have to open the data drive (so it appears on the desktop), and then drag my media into the music player, because it doesn't know where it is otherwise. 

It's not a big deal, but I was wondering if there was a way I could have the "data" partition already "mount" upon start-up? I don't see any blatantly obvious preferences that say "launch at start-up". But it wouldn't surprise me if there was, and I'm just not seeing it. Any help would be appreciated.

PS Sorry for all the quotation marks but, I lack the technical vocabulary to describe what's going on :) Thanks.

---

### Post by agillator on 2011-10-20
You need to make an entry in /etc/fstab (as root, of course). Check the man page for fstab and use the existing entries as guides. Your entry would possibly be something like:

/dev/sda3 <tab> /mnt/data <tab> ntfs <tab> defaults <tab> 0 <space> 0

assuming your data partition is /dev/sda3, you want to mount it at /mnt/data and the directory exists, and the partition is formatted with an ntfs file system. Of course there are several types of file systems is could be, you will have to check that with gparted or the disk utility or something else. Basically, as the man page says, you are putting the information you use to manually mount the partition into the fstab file. Then, unless you include noauto as an option, it will be automatically mounted.

---

### Post by ArgusVision on 2011-10-20
You could also check this thread. Similar instructions + Symbolic links to make accessing the folders more transparent.

[http://ubuntuforums.org/showthread.php?t=1865750](http://ubuntuforums.org/showthread.php?t=1865750)

Go to post #6

---

