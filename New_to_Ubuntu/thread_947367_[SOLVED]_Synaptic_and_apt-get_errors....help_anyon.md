---
title: "[SOLVED] Synaptic and apt-get errors....help anyone?"
date: 2008-10-14
forum: New to Ubuntu
---

### Post by Bobb11 on 2008-10-14
E: Problem parsing dependency Depends
E: Error occurred while processing btnx (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.


Any suggestions how to fix this?
Thanks.

---

### Post by drs305 on 2008-10-14
Open sources.list and correct the typo:  harty >> hardy

```

sudo cp /etc/apt/sources.list /etc/sources.list.14102008
gksudo gedit /etc/apt/sources.list

```

Once you have changed all instances of "harty" to "hardy", reload synaptic or run "sudo apt-get update".

If this does not solve it, rename the offending list:
```

sudo mv /var/lib/apt/lists/repoubuntusoftware.info_dists_harty_all_binary-i386_Packages /var/lib/apt/lists/repoubuntusoftware.info_dists_hardy_all_binary-i386_Packages

```

---

### Post by Bobb11 on 2008-10-14
Thank you, that did the trick. Consider this problem Solved.
But I really have no clue how that "typo" occurred. Everything had been working just great, until I went on vacation for a week and came back, turned on the PC, and there was the error (when I attempted to click on the UPDATE ICON up at the top). Oh well....gremlins do sneak up on us occasionally for no apparent reason.
Again, thanks for your quick response and help.

---

### Post by drs305 on 2008-10-14
> **Bobb11 said:**
> Thank you, that did the trick. Consider this problem Solved.
But I really have no clue how that "typo" occurred. 

It wasn't you. There have been several threads - either people are copying a posted typo from a thread or a web page somewhere has a bad reference.

Btw, did you just have to correct the sources.list or did you have to rename the lists file?

---

### Post by qpa_z_wonsem on 2008-10-14
> **drs305 said:**
> 
Btw, did you just have to correct the sources.list or did you have to rename the lists file?

Thanks!
It worked for me, but only correcting the source list. When I've changed the lists file, error occured again.
Now, I have hardy in source list and harty in list file.

---

