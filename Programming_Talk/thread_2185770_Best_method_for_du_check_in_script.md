---
title: "Best method for du check in script"
date: 2013-11-04
forum: Programming Talk
---

### Post by drmrgd on 2013-11-04
Working on a backup / mirror utility for one of my data servers and wondering the best way to check the disk size of the mirror device.  Currently, I'm running:

```

du -s BM --exclude='lost*' <drive>

```

But, this takes a lot longer than using df (I guess the data for df gets cached periodically while du checks on the fly?).  I also notice that the results of df and du do not always agree, although the difference is pretty small and probably insignificant.  Would it be good practice to use the output from df, extracting the column with the data I need (either 'Used' or 'Available' - haven't quite decided) in my script, or would it be better to use the output from du instead?

---

