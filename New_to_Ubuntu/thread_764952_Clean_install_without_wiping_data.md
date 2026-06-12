---
title: "Clean install without wiping data?"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by Dan Sarf on 2008-04-24
Hello

As a noobie I have only ever installed Ubuntu on a freshly formatted drive. I want to do a clean install of 8.04 but I also don't want to bother with backing up all my data. Can I do a fresh install without wiping my whole drive?

If so, how?

Thanks!

---

### Post by Periswell on 2008-04-24
installing from cd or update manager?

-josh

---

### Post by aeiah on 2008-04-24
the easiest thing ive found to do is create a new partition, put everything you want saving on it, and then wipe your ubuntu partition and install

---

### Post by Dan Sarf on 2008-04-24
I assumed (perhaps incorrectly) that a fresh install would *have* to come from the CD!

---

### Post by Dan Sarf on 2008-04-24
> **aeiah said:**
> the easiest thing ive found to do is create a new partition, put everything you want saving on it, and then wipe your ubuntu partition and install

My whole hard drive is one partition with everything on it.

---

### Post by philinux on 2008-04-24
You could move home to its own partition.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by toecutter on 2008-04-24
If you can borrow a hard drive to back all your data to, then you can install Ubuntu so you can 'future-proof' installs down the road: create a separate /home partition and keep all your data there. Then you'll be able to wipe the OS and/or do a clean install (and also install other Linux distro's) on the root partition and you're all set :)

edit: the psycocats instructions ^^^^ are the way to go, that is exactly what I did several installs ago, and I'm able to just do fresh installs from the CDs as they come out.

---

### Post by Dan Sarf on 2008-04-24
OK thanks guys, I think I will do that then.

---

### Post by mister_pink on 2008-04-24
Check this out. [https://wiki.ubuntu.com/UbiquityPreserveHome](https://wiki.ubuntu.com/UbiquityPreserveHome)

Ive never tried it myself and I don't actually know of anyone having tried it either! Worth a try though, if it doesn't seem to be working just abort the install. As always, back up anything really vital.

---

