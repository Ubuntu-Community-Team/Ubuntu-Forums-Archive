---
title: "Cannot burn data DVD/CD or BRDVD"
date: 2014-07-29
forum: New to Ubuntu
---

### Post by CJ_Hudson on 2014-07-29
Hi,
I am posting here because despite my bean rating I have been out of the loop wrt Ubuntu for a few years. So please bear with me.
I recently tried burning a data BRDVD (about 5.2 Gb of data) however I got the error log (see attached.)
I think it might be my hardware.
Please help anyone?

[ATTACH]255149[/ATTACH]

(I pasted the log file contents into Open Office Writer since the original log wouldn't upload)

Thanks in advance.

---

### Post by kira-yamato-2008 on 2014-07-29
I have two basic suggestions: First make sure you run a Lens Cleaner, and make sure it's one with Nylon brushes. Do not clean the lens directly with Paper towels, q-tips or similar. Second get K3b from the Ubuntu Software Center. In my experience it's the most stable and fastest writing tool for discs(CD/DVD.)

A slightly more advanced step is to check the manufacturer's website and make sure your burner's drivers and firmware are up-to-date.

---

### Post by UltimateCat on 2014-07-30
Do you have permission to burn in the cdrom group?

Type "[B]groups" in the terminal and it will show what groups you have permission to-

If you don't see cdrom open the terminal as root and run:
```
usermod -G cdrom (name of user)

```

Close the terminal, log out and log back in--
[/B]

---

### Post by CJ_Hudson on 2014-08-23
> groups

gives:

> chris adm cdrom sudo dip plugdev lpadmin sambashare

---

