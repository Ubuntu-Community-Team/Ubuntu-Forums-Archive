---
title: "auto mount all drives"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by expatCM on 2008-05-07
I just migrated from 7.10 to 8.04.  No real problems at all.

With 7.10 all the hard drives on my system were detected and mounted.  Now only the primary drive is mounted.  The others are listed as removable media and are mounted when clicked.

I would like them to be auto mounted at start.  Is the proper way of doing this to add a line for each in fstab or is there another approach?

---

### Post by tamoneya on 2008-05-07
yes they needed to be added to fstab.  It should be pretty easy to figure out how to add them if you just look at the file but if you want help just post the contents of /etc/fstab and the output of ```
sudo fdisk -l
```Then we should be able to get it fixed right away.

---

### Post by expatCM on 2008-05-07
Thank you for the fast response.

Now that is confirmed I will have a go.  If I make a mess I will post the output of fdisk -l and fstab.  

I may get it right for once, it has to happen sooner or later .....  :)

---

### Post by Xiong Chiamiov on 2008-05-07
There is also a GUI fstab editor of sorts in the repos, called pysdm.  I haven't quite figured out how it works, but it looks promising.

---

### Post by Bloch on 2008-05-07
Upgrading online (not fresh install) from Gutsy to Hardy Heron can break automount. It is a recognised problem.


[http://ubuntuforums.org/showthread.php?t=773996](http://ubuntuforums.org/showthread.php?t=773996)

---

### Post by expatCM on 2008-05-07
pysdm looks like an interesting tool to play with.  I wondered what on earth it was all about until I clicked the Assistant button and that gave lots of check boxes to play with.  

The only danger I see here is that you really need at least half a clue to know what to select and what to leave alone.  But it does seem to have the potential of sorting things out rather quickly .....

It does not seem to use uuid's though ...  guess this is not a problem ... 

Something to play with tomorrow ....

---

