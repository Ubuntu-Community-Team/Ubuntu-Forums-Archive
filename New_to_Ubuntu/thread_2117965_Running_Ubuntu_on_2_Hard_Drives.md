---
title: "Running Ubuntu on 2 Hard Drives?"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by aweg on 2013-02-19
I was wondering how I can configure Ubuntu for my SSD and my HDD.  I put things that I want to boot faster on my SSD so should I just put Ubuntu on my SSD or do I have to put it on my HDD too??  I'm normally not a noob at computer stuff but I just wanted to be sure to avoid any further problems.

---

### Post by fantab on 2013-02-19
Create a '/' partition on SSD and '/home' on your HDD...

---

### Post by oldfred on 2013-02-20
Welcome to the forums.

fantab suggestion is a good one as many do that and it is easy to setup that way.

My way is more complex. I use data partitions & linking.
But I know hard drives fail, so I always install a full install of Ubuntu in a 25GB / (root) partition including /home and link data from other drives. Then if a drive fails I can still boot my other drive. I do have a working install on every drive.

---

