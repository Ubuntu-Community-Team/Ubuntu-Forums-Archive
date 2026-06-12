---
title: "Updates ... tips on recovery  from an errant update"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by cwmoser on 2008-10-16
Yesterday my Ubuntu Linux received a major update - and my VMWare software stopped working and the configuration utility for VMWare could not find the linux header files.

In addition, whether by coinsequence or not, my nVidia drivers would no longer work and I could not get the GUI desktop.  I had to copy a preserved copy of /et/X11/xorg.conf, get into low resolution desktop, reinstall the nVidia drivers, and copy back by original xorg.conf file.

These updates have the potential to be dangerous -- a really bad one could wipe out the Ubuntu Linux community or at least could weed out a lot of users.

So, my question is, what are some good advice on recovery from an errant update?

Carl

---

### Post by brettg on 2008-10-16
Well, in the short term you can boot from the kernel that worked before the upgrade (select in grub menu). That gives you time to fix the primary problem

---

### Post by bumanie on 2008-10-16
If something like that happens, I usually comment out the offending kernel (if it is the recent kernel update you describe as a 'major update') and boot with one I know works - I believe this will be available in intrepid as a default choice ie one can choose to boot from the last known good kernel if something doesn't work following a kernel update.

---

### Post by hyper_ch on 2008-10-16
you haven't compiled vmware modules yet for the new kernel. run:
```

sudo vmwaresetup.pl

```
that should trigger the tool

---

### Post by cwmoser on 2008-10-16
> **bumanie said:**
> If something like that happens, I usually comment out the offending kernel (if it is the recent kernel update you describe as a 'major update') and boot with one I know works - I believe this will be available in intrepid as a default choice ie one can choose to boot from the last known good kernel if something doesn't work following a kernel update.

If I remember correctly, I tried the second kernel in the boot menu -- still did not work.  That would not have helped if the issue was like mine where it was the nVidia drivers - or would it???

Carl

---

