---
title: "[SOLVED] cp command help"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by ARhere on 2008-08-31
I am trying to duplicate a filesystem from a USB disk drive to a USB thumb drive.  For clarity, "/media/disk-1" is the USB disk drive and "/media/disk" is a USB thumb (*solid state*) drive.

I am typing...```
sudo cp -prv /media/disk-1 /media/disk
``` but this creates /media/disk/disk-1/ and then starts copying all the data into it.

What am I doing wrong?

**ALSO...**

Can I request a new category be created under "Main Support Categories" titled "Linux Command Line" for help with general Linux command line use.

-AR

---

### Post by Bachstelze on 2008-08-31
Do this instead :

```
sudo cp -prv /media/disk-1/* /media/disk
```


Requests about the forums should be made in the Forum Feedback & Help section.

---

### Post by ARhere on 2008-08-31
> **HymnToLife said:**
> Do this instead :

```
sudo cp -prv /media/disk-1/* /media/disk
```

Thank you, that worked.  By the way, was my difficulties due to something different with Ubuntu vs. other distro's?  As I understand the cp command, typing "**sudo cp -prv /media/foo /media/faa**" should duplicate "foo" and rename it "faa" under /media/.

> Requests about the forums should be made in the Forum Feedback & Help section.

Will do.

-AR

---

### Post by Bachstelze on 2008-08-31
> **ARhere said:**
> Thank you, that worked.  By the way, was my difficulties due to something different with Ubuntu vs. other distro's?  As I understand the cp command, typing "**sudo cp -prv /media/foo /media/faa**" should duplicate "foo" and rename it "faa" under /media/.

You don't understand the [FONT="Courier New"]cp[/FONT] command well ;)

If the second argument of [FONT="Courier New"]cp[/FONT] is a directory, the source file will be copied *into* it, it will not replace it.

---

### Post by ARhere on 2008-09-01
Ah, got it.  So my understanding was just with files.

Thanks,
-AR

---

