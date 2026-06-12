---
title: "Deleted one partition, resized the other, now I get an error, hmmmmmmmmmmm"
date: 2008-04-16
forum: Other OS Talk
---

### Post by maniheer on 2008-04-16
```
Log of fsck -C -R -A -a 
Wed Apr 16 16:47:46 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=ed10315a-4521-4945-9924-686c5fd4cfca'

fsck died with exit status 8 
```

I get this and a terminal prompt thingy, everytime I start my computer, after I deleted a spare partition and resized by old one to take up the rest of the HDD, using the GParted Live CD. If I type exit at the prompt everything starts up as usual. I'm using Linux Mint 4.0, which is the reason I am in this part of the forums.

Thanks in advance

---

### Post by maniheer on 2008-04-16
Found my own answer, had to delete the partition entry from /etc/fstab  
:):):):):):):):)

---

