---
title: "Backup error"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by peterson43 on 2013-05-07
I use Deja Dup to back up my hard drive daily. Lately, I've been getting error messages after the backup is complete that part of the backup didn't work because a folder apparently doesn't exist. In particular, the error message I get is
```
Backup location ‘/tmp/duplicity-__F0SD-tempdir/mktemp-Hi7yon-4’ does not exist.
```
How can I stop getting this error message? 

I think I could probably avoid it by just adding /tmp to the list of folders for Deja Dup to ignore, but there are a lot of subfolders within Deja Dup as well (although none of them seem terribly important). There should be a more elegant solution it seems.

---

### Post by TheJackal12 on 2013-05-07
Personally, I would exclude /tmp from any sort of backup. It isn't necessary and only takes up more space. You can even mount your /tmp as a tmpfs in RAM, which is cleared each reboot.

---

