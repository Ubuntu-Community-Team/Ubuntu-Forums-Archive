---
title: "Update Issues"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by petdog on 2008-06-30
Hey guys,
I got this small issue, my update works up until i say update, then all of a sudden the entire thing hangs and hangs. Anyone know a solution.

Thanks! :confused:

---

### Post by Inxsible on 2008-06-30
I had the same issue with update-manager in xubuntu.

You may want to try and install the packages manually in a terminal.

See what the update manager lists and then do a ```
sudo apt-get update *package1 package2 ....*
```

---

### Post by petdog on 2008-06-30
That is going to take for forever, i got 99 updates!! Yes i would love to sit and do it but i can not, is their no way i can try uninstall and reinstall the update manager?

---

### Post by Inxsible on 2008-06-30
> **petdog said:**
> That is going to take for forever, i got 99 updates!! Yes i would love to sit and do it but i can not, is their no way i can try uninstall and reinstall the update manager?you probably will not have to list all 99 because most will be dependent libraries on the main packages...just list the main packages and it should probably cover all.

You can always start update-manager again to see if you missed any.

---

### Post by petdog on 2008-06-30
K will try that, will get back to u on progress in 5 mins! thanks man!

---

### Post by Inxsible on 2008-06-30
> **petdog said:**
> K will try that, will get back to u on progress in 5 mins! thanks man!Happy to help !

good luck !

---

### Post by avtolle on 2008-06-30
Try```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by phoenix_abhi on 2008-06-30
> **avtolle said:**
> Try```
sudo aptitude update && sudo aptitude safe-upgrade
```

Thanx for this. Let me check up with this, otherwise always a load of updates are available. Who have the time to check up the description. Actually what the safe upgrade do ?

---

### Post by avtolle on 2008-06-30
As I understand it, it only upgrades those packages where the upgrade is "safe", i.e., dependencies resolved, etc., and won't break the system. I've noticed when using these commands certain packages are "held back" until new versions of dependencies are available, then the held back packages are installed, together with the dependencies. I believe that's how the update manager is supposed to work as well.

EDIT: see man aptitude for further information.

---

### Post by petdog on 2008-06-30
Hey thanks man, this seems okay, i would really like to get my Ubuntu working, i mean this should not really happen all to often should it? Is there anywhere i can bring it up to maybe get someone to fix it? Next version?

---

### Post by Inxsible on 2008-06-30
> **petdog said:**
> Hey thanks man, this seems okay, i would really like to get my Ubuntu working, i mean this should not really happen all to often should it? Is there anywhere i can bring it up to maybe get someone to fix it? Next version?
If you are lucky..you won't see the problem again. But even if you do, atleast you know the solution :D

---

