---
title: "DSDT Help"
date: 2006-04-20
forum: Programming Talk
---

### Post by trent dillman on 2006-04-20
Is there anyone here familiar with DSDT? I have a HP zd7389cl, and I would like to have it run at its best. Unfortunately, I have become aware of a problem: buggy DSDT. I've followed the following: [http://forums.gentoo.org/viewtopic.php?t=122145](http://forums.gentoo.org/viewtopic.php?t=122145)

I'm to the point of recompiling and receiving errors, but I am not a programmer, so I have no clue how to fix them. Apparently, the site that hosts the specifications ([www.acpi.info](www.acpi.info)) is down, so I'm not sure where to even start. I found a site that had a list of error codes (the link escapes me right now), but the errors I receive were not documented there.

I know this buggy DSDT is causing problems with my laptop. I have errors regarding my IDE interface in dmesg, and the errors from my DSDT are in the portion of the code that reference IDE.

I have not yet subscribed to the acpi-devel mailing list, and I plan on doing so. I figured I might ask here, as I find the Ubuntu community to be incredibly friendly and extremely helpful.

Thanks in advance to anyone who can help!

---

### Post by skirkpatrick on 2006-04-20
I don't know if it will help with your specific problem but a while ago, I had to rebuild my son's DSDT for battery monitoring.  Here's the original thread: [http://www.ubuntuforums.org/showthread.php?t=60484&page=2](http://www.ubuntuforums.org/showthread.php?t=60484&page=2) .  I suggest you start on about post #18.  It may help, it may not.

---

### Post by trent dillman on 2006-04-21
Well, here's some output:

```
root@ubuntu:~# iasl -tc dsdt.dsl

Intel ACPI Component Architecture
ASL Optimizing Compiler version 20051216 [Jan  9 2006]
Copyright (C) 2000 - 2005 Intel Corporation
Supports ACPI Specification Revision 3.0

dsdt.dsl    95:             Release (PSMX)
Warning  2097 -                         ^ Statement is unreachable

dsdt.dsl  4656:                     Method (SMSL, 0, NotSerialized)
Warning  2085 -                                ^ Not all control paths return a value (SMSL)

dsdt.dsl  6013:                 Field (IDE1, DWordAcc, NoLock, Preserve)
Error    1025 -                           ^ Access width is greater than region size

dsdt.dsl  6015:                     MAP,    8,
Error    1026 -                       ^ Access width of Field Unit extends beyond region limit

dsdt.dsl  6017:                     PCS,    8
Error    1026 -                       ^ Access width of Field Unit extends beyond region limit

dsdt.dsl  6910:             Name (_HID, "*pnp0c14")
*pnp0c14
dsdt.dsl  6912:             Name (_WDG, Buffer (0x14)
Warning  2096 -                      ^ Unknown reserved name (_WDG)

ASL Input:  dsdt.dsl - 7446 lines, 302774 bytes, 3437 keywords
Compilation complete. 4 Errors, 3 Warnings, 0 Remarks, 700 Optimizations
```

I'm glad to see someone around here knows a bit about this!

---

### Post by trent dillman on 2006-04-21
Whew. After an exaustive google search, I finally got rid of every error and warning!

Now, I don't know if I 'fixed' it as much as I just got the compiler to stop complaining, because I haven't used the new DSDT yet. Off to try that now.

I'm hoping I don't b0rk my Dapper install :/

---

### Post by trent dillman on 2006-04-21
Well, so far no problems!

I went through dmesg with a fine tooth comb, and no ACPI errors!

---

### Post by skirkpatrick on 2006-04-21
Congratulations!  It took me a while to get mine working but that was a while ago :)

---

