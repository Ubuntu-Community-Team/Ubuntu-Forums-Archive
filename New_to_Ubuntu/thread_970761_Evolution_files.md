---
title: "Evolution files"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by shawfield on 2008-11-04
Hi
I want to copy my old evolution files that are on a different partition, to my new partition.

I tried looking for /home/user/.evolution but even if I tell the file browser to show hidden files, the .evolution folder is not there.

Help ?

thanks

---

### Post by gandaran on 2008-11-04
maybe it's not there then, open terminal and type *locate .evolution* this will tell you where it is

---

### Post by Coreigh on 2008-11-04
I agree, it will probably be easier to find it using the terminal.

If locate doesn't turn up anything you may need to update the locate data
Make sure the old partition is mounted and type:
```
sudo updatedb
```

You can also try:
```

cd /<path to old home folder>
ls -al ./.ev*

```

This changes to the old home folder then does a directory listing, showing hidden files and folders starting with .ev

---

