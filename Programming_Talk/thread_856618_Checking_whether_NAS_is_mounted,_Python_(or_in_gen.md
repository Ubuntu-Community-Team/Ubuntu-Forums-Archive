---
title: "Checking whether NAS is mounted, Python (or in general)"
date: 2008-07-11
forum: Programming Talk
---

### Post by EricDB on 2008-07-11
I'm writing a little script to backup some files periodically and automatically to my NAS, whenever my laptop connects to my home network.  My plan is to run it every five minutes or so from cron, and have it check to see whether the NAS is mounted, and if so, do the backup (provided it hasn't been done today already).

So, I'm using os.path.exists to check.  The probem is, it returns True if the NAS is mounted, but if not, it just blocks (seemingly) forever.  Is there a better way to check?  

Incidentally, what usually happens is that the NAS is mounted when I'm at home, then I suspend, resume somewhere else, and although the icon is still on my desktop, obviously I have no access.

---

### Post by ghostdog74 on 2008-07-11
how your script looks like?

---

### Post by EricDB on 2008-07-12
> **ghostdog74 said:**
> how your script looks like?

I don't have a script yet.  I'm testing my method in the Python interpreter.  If I am connected to my home network, I get this (immediately):

```
>>> os.path.exists('/mnt/my_nas')
True
```

But if I'm not at home, it hangs forever instead of returning 'False' as I would like.

---

