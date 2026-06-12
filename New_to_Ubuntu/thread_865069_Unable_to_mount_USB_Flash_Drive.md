---
title: "Unable to mount USB Flash Drive"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by mu:te on 2008-07-20
So here´s there deal. I'm trying to copy some files from my comp. to my USB fd. The problem is, that Ubuntu is unable to locate my FD. When I plug it in, nothing happened.

---

### Post by pi.boy.travis on 2008-07-20
Click on places, computer.  Is there an icon for the drive there?  You may have automounting of external drives turned off.

---

### Post by Rodd_Roddy on 2008-07-20
what type of Flash Drive is it .. I find Kingston works find for me just make sure it Linux compatible

---

### Post by mu:te on 2008-07-20
> **pi.boy.travis said:**
> Click on places, computer.  Is there an icon for the drive there?  You may have automounting of external drives turned off.

No of course the icon is int there, I would have noticed. :/

---

### Post by mu:te on 2008-07-20
> **Rodd_Roddy said:**
> what type of Flash Drive is it .. I find Kingston works find for me just make sure it Linux compatible

OCZ Rally 8GB

---

### Post by asmoore82 on 2008-07-20
Open a Terminal "Applications -> Accessories -> Terminal"

Then, unplug and reconnect your Flash Drive,
Then, run this command and post the last few lines if it doesn't make sense to you...
```
dmesg
```

---

