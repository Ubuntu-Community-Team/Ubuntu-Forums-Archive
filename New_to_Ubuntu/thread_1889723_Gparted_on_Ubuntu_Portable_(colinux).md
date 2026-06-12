---
title: "Gparted on Ubuntu Portable (colinux)"
date: 2011-12-01
forum: New to Ubuntu
---

### Post by mraeryceos on 2011-12-01
I can't get Gparted to install.  The error from terminal is:

```
The following packages have unmet dependencies:
  gparted: Depends: libparted0 (>= 2.2-1) but it is not going to be installed
E: Broken packages
```

Okay, fine, be that way, so sudo apt-get install libparted0

```
The following packages have unmet dependencies:
  libparted0: Depends: libparted0debian1 (= 2.2-5ubuntu5) but 2.2-5ubuntu5.2 is to be installed
E: Broken packages
```

No way!  sudo apt-get install libparted0debian1

```
libparted0debian1 is already the newest version.
libparted0debian1 set to manually installed.
```

libparted doesn't like gparted?  get rid of it!

OMG, that was it!  Linux is really wierd.  I think I like the Slax philosophy better.

Ok, why does Gparted not see any of my partitions?  I guess I need to learn how to read the hardware to software diagrams to see exactly how cooperative colinux is.  Anybody have a link for that?

---

### Post by mraeryceos on 2011-12-01
I was hoping to take a look at the partition naming for Linux (SDA this, SDA that...) so I would know those details for installing Grub.

You see, I installed opensuse a while ago, and when I went to try out an unattended 7 install, the mbr got wiped out, and I was never able to restore Grub again.  Next time I will back up the MBR before installing Windows.

Anyway, I happened to notice colinux and it promised to be everything I was hoping for: a way to run Linux without giving up all my Windows tools all at once, and without having to reboot.

I can't get the [solved] tag off this thread.  Though I did solve a little intermediary step that lead to no-where.  I just want to know one thing: [COLOR="Red"]Is it true that Gparted will never have access to the disk partitions when run within cooperative linux?[/COLOR]

---

### Post by Chronon on 2011-12-02
> Is it true that Gparted will never have access to the disk partitions when run within cooperative linux?

I believe that since it runs inside of a loop file system gparted can't access the host file system.

---

### Post by mraeryceos on 2011-12-03
> **Chronon said:**
> I believe that since it runs inside of a loop file system gparted can't access the host file system.
I thought as much, but people are good at finding work-arounds.  I bet it would be easier in the day of DOS and Windows 98, where there was more direct access to hardware.

---

