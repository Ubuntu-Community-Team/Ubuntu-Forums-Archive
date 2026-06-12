---
title: "Lost data but didn`t get hard disk space - is it somewhere around?"
date: 2011-12-30
forum: New to Ubuntu
---

### Post by BigUnlucky on 2011-12-30
Hello!
I`ve made 2 partitions on my disk, one small for system (35gb) and big for data (around 400gb). Because bigger partition I`ve made later, my system partition got full (some movie clips, photos, docs, etc. So today I`ve decided to move all my files to bigger partition. However it seems that copying files didn`t finished, after reboot my files were not on bigger partition - but they`ve perished also from my home folder! :( (before copying I`ve made folder on big partition as root (sudo) and I`ve gave premission for myself to read/write, then I`ve copied files to it - didn`t saw any bar, so I`ve thought that it was so fast - my fault, I should think that 20gb of files should take more time to copy).
However - my files aren`t in home folder, they arent at bigger parttion (even folder that I`ve made as root perished!) - but after login system gave me message, that there is onl;y 300mb free space on device - so my files must be somewhere around! they are not in trash, and "locate" don`t show me lost file names. Can I get back my files? What is taking free space? 
Help!
small partition is ext4, bigger is ext3
I`ve mounted bigger partrion at start-up with MountManager - maybe that`s why? I can`t get why already created folder as super user perished! and I`ve made new folders again and don`t persished anymore...

After copying files to bigger partition I`ve made symlinks to the home folder - but after restart they are broken

---

### Post by The Cog on 2011-12-31
Was your /home folder originally on the system partition, and you then made the bigger partition mount as your /home folder? If this guess is wrong then the rest of this post is probably no use to you.

If so, then I guess that your original files are still in the /home folder on the system disk. Bit you can't see them because the bigger partition is mounting there and hiding the original contents. 

You will find it difficult to unmount the /home folder while you're logged in, so I think the best thing to do is to fire up a live CD and use the file manager from there to look on these partitions. You should be able to see both home folders then, and be able to copy files between them.

---

