---
title: "[SOLVED] packages"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by k33bz on 2008-06-14
when you install packages from the synaptic manager, or even with apt-get, where do the deb packages go?

---

### Post by ukripper on 2008-06-14
> **k33bz said:**
> when you install packages from the synaptic manager, or even with apt-get, where do the deb packages go?

to /var/cache/apt/archives/
and partial ones to /var/cache/apt/archives/partial/

---

### Post by ChameleonDave on 2008-06-14
> **k33bz said:**
> when you install packages from the synaptic manager, or even with apt-get, where do the deb packages go?

/var/cache/apt/archives/partial as they are downloading, and then to /var/cache/apt/archives/ when they are finished.

Depending on what you set in your Synaptic preferences, they may be deleted.

---

### Post by k33bz on 2008-06-14
ok, thanks to both of you.

---

### Post by ukripper on 2008-06-14
you can also get rid of them using :
```
sudo apt-get clean
```
to clean all debs from there.

and for only partial ones use:
```
sudo apt-get autoclean
```

---

### Post by k33bz on 2008-06-14
how about any libraries that my be needed, tryin to forge packages over from my laptop to my desktop, if that is possiable.

---

### Post by ukripper on 2008-06-14
> **k33bz said:**
> how about any libraries that my be needed, tryin to forge packages over from my laptop to my desktop, if that is possiable.

To the same location, but if they are dependent on another package's library then it won't be downloaded as they already exists on your system.

---

### Post by ChameleonDave on 2008-06-14
> **ukripper said:**
> 
and for only partial ones use:
```
sudo apt-get autoclean
```

That will delete all archived packages no longer available in the repos.

---

### Post by ukripper on 2008-06-14
> **ChameleonDave said:**
> That will delete all archived packages no longer available in the repos.

From man pages:
>     Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.


---

### Post by k33bz on 2008-06-14
> **ukripper said:**
> To the same location, but if they are dependent on another package's library then it won't be downloaded as they already exists on your system.

o ok, kuz my synaptic manager says i have over 1100 packages installed, and yet those folders only have bout 450 packages in them

---

### Post by ChameleonDave on 2008-06-14
> **k33bz said:**
> o ok, kuz my synaptic manager says i have over 1100 packages installed, and yet those folders only have bout 450 packages in them

As I said, if you have ever run "autoclean", or if your preferences in Synaptic are set to delete old packages, then you will not have archives of old packages that are no longer available.  Furthermore, you can only have archives of packages that you have downloaded to install.  There will be no archives of packages that come preinstalled with Ubuntu.  Those are on the Live CD instead.

---

