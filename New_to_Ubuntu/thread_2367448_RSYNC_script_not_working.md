---
title: "RSYNC script not working"
date: 2017-07-30
forum: New to Ubuntu
---

### Post by ricardo35 on 2017-07-30
Hello everyone,

I have two external disks which need to be mirrored. For this I run the next script:
```
rsync –av ––delete /mnt/C24E64964E64854F/ /mnt/1A1CD1301CD107A1/
```

Whatever I do, I get:

```
rsync: link_stat "/home/ricardo/Bureaublad/–av" failed: No such file or directory (2)rsync: link_stat "/home/ricardo/Bureaublad/––delete" failed: No such file or directory (2)
skipping directory .
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1183) [sender=3.1.1]

```

What am I doing wrong?

---

### Post by SeijiSensei on 2017-07-30
If the two disks are identical you could use dd instead:

```
dd if=/dev/sda of=/dev/sdb
```

ddrescue is an excellent tool for these kinds of tasks.  It's in the repositories as "gddrescue".

I can't see why you're getting those results from rsync.  Why it's looking for "-av" is beyond me.

---

