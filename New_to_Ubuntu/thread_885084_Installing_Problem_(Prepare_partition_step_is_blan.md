---
title: "Installing Problem (Prepare partition step is blank)"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Dragath on 2008-08-09
When I try to install ubuntu on to my computer, I get to the Prepare partiton step, and I can't choose any option or go any further. No hardrive is shown. I have a 500GB SATA Drive Seagate. Please Help.

---

### Post by spiderbatdad on 2008-08-09
How is it connected? Are the jumpers set correctly? Do you have any other operating systems installed on this disk?

---

### Post by Dragath on 2008-08-09
At first I didn't have any other OS installed, but then I installed XP professional. And it works. But the problem still remains when I try to install ubuntu

---

### Post by Dragath on 2008-08-09
bump

---

### Post by spiderbatdad on 2008-08-09
The problem seems a little strange. I'm wondering about the integrity of the cd. You might take a look into burning gparted live cd and running it, to see if you have better luck partitioning.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by pi.boy.travis on 2008-08-09
You should run "Check CD for defects" from the live CD menu.  I have had a few faulty CDs myself

---

### Post by Dragath on 2008-08-09
It said the Cd was fine. I'm downloading from somewhere else right now, and then ill try again

---

### Post by Dragath on 2008-08-09
> **spiderbatdad said:**
> The problem seems a little strange. I'm wondering about the integrity of the cd. You might take a look into burning gparted live cd and running it, to see if you have better luck partitioning.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

Okay so I got gparted, and I started running it, at it clearly shows the available partitions but it says it cant read the part i separated for ubuntu. It doesn't have a format and theres a bunch to choose from. What format should i set it to?

---

### Post by sandysandy on 2008-08-09
for ubuntu u can use ext3.

also a separate one for SWAP.(option there in gparted)

look here for gparted tutorial

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

regards

---

