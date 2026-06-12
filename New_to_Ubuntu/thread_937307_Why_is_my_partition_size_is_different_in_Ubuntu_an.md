---
title: "Why is my partition size is different in Ubuntu and Gparted?"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by klemperal on 2008-10-03
Well, I'm reinstalling Ubuntu 8.04.1 after having resized some things.  I used gparted to keep an even 100 gigs of my xp partition, and for the moment the rest is free space.  However, when I look at the size of the xp filesystem on the live CD is says that my XP partition is really 107.4 gigs.  So, Gparted is saying one thing and Ubuntu is saying something else--which one is correct?

---

### Post by klemperal on 2008-10-03
bump

---

### Post by medic2000 on 2008-10-03
I have the same issue dunno the explanation though.

---

### Post by jmszr on 2008-10-03
I think this might explain it: [URL="http://en.wikipedia.org/wiki/Binary_prefix" It's a matter of 1024*1024*1024 = 1073741924. Hence your output of 107.4. It's the difference beteeen GB and GiB. Makes my head hurt.

---

### Post by klemperal on 2008-10-03
yeah...I don't get it.  XP says the partition is 99.9 gigs, gparted says it's 100.00, and linux says the partition is 107.4.

---

### Post by jmszr on 2008-10-03
They are all measuring the same space-Linux is just using a different unit of measurement.

---

