---
title: "Mono on PPC Linux"
date: 2009-10-03
forum: Programming Talk
---

### Post by WitchCraft on 2009-10-03
I've  a question:

I wanted to port a mono program to my Synology Linux server.
The Synology Linux Server has a PPC processor:

```

DiskStation> uname -a
Linux DiskStation 2.6.24 #942 Fri Sep 4 07:09:08 CST 2009 ppc GNU/Linux


DiskStation> cat /proc/cpuinfo
processor	: 0
cpu		: 82xx
revision	: 1.4 (pvr 8081 1014)
bogomips	: 176.12
chipset		: 8245
vendor		: Synology Inc.
machine		: MPC824X
DiskStation> 

```


I first tested with a HelloWorld program, but it always segfaults on the Synology server. It runs ok on my x86 Linux, and I've also tried to compile the program on a PPC Linux. It worked fine, but when I put it on the Synology server, it segfaulted...

There is the appropriate version of mono installed.

Anybody knows what I am doing wrong?

---

### Post by directhex on 2009-10-03
> **WitchCraft said:**
> I've  a question:

I wanted to port a mono program to my Synology Linux server.
The Synology Linux Server has a PPC processor:

```

DiskStation> uname -a
Linux DiskStation 2.6.24 #942 Fri Sep 4 07:09:08 CST 2009 ppc GNU/Linux


DiskStation> cat /proc/cpuinfo
processor	: 0
cpu		: 82xx
revision	: 1.4 (pvr 8081 1014)
bogomips	: 176.12
chipset		: 8245
vendor		: Synology Inc.
machine		: MPC824X
DiskStation> 

```


I first tested with a HelloWorld program, but it always segfaults on the Synology server. It runs ok on my x86 Linux, and I've also tried to compile the program on a PPC Linux. It worked fine, but when I put it on the Synology server, it segfaulted...

There is the appropriate version of mono installed.

Anybody knows what I am doing wrong?

There may be some oddities on this particular PPC chip - I imagine it's not a well-tested configuration. Specific info on the version used, and on the crash info, would help

---

### Post by WitchCraft on 2009-10-11
> **directhex said:**
> There may be some oddities on this particular PPC chip - I imagine it's not a well-tested configuration. Specific info on the version used, and on the crash info, would help

How can I get additional crash info besides segmentation fault?

---

### Post by directhex on 2009-10-11
> **WitchCraft said:**
> How can I get additional crash info besides segmentation fault?

Adding a --debug to the mono command, or running it in gdb and getting a backtrace. Or just file a bug & people will tell you what they need

---

### Post by WitchCraft on 2009-11-13
> **directhex said:**
> Adding a --debug to the mono command, or running it in gdb and getting a backtrace. Or just file a bug & people will tell you what they need

gdb doesn't recognize the file format ;-)

But the adding the --debug to the mono command let me realize i should try:
```

mono ./monotest.exe

```

instead of just
```

./monotest.exe

```

Why does it run on Ubuntu without adding mono in front?
How can I make it run without adding mono in front of the *.exe?
That would be interesting for wine, too.

---

### Post by directhex on 2009-11-13
> **WitchCraft said:**
> Why does it run on Ubuntu without adding mono in front?
How can I make it run without adding mono in front of the *.exe?
That would be interesting for wine, too.

The "binfmt-support" package enables this, including for wine (with autodetecting between mono/wine apps)

---

### Post by WitchCraft on 2009-11-14
> **directhex said:**
> The "binfmt-support" package enables this, including for wine (with autodetecting between mono/wine apps)

Thanks.

---

