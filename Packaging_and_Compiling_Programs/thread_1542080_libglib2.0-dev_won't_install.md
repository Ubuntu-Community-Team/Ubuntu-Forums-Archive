---
title: "libglib2.0-dev won't install"
date: 2010-07-30
forum: Packaging and Compiling Programs
---

### Post by BillRebey on 2010-07-30
I'm using Ubuntu 9.10 on an ARM processor, and I'm trying to install the dbus  libraries.  

Specifically, the glib interface library messes up.  When I run:  

```
sudo apt-get install libdbus-glib-1-dev
```

I get:

```
The following packages have unmet dependencies:
  libdbus-glib-1-dev: Depends: libglib2.0-dev but it is not going to be installed
```

So naturally I attempt to install libglib2.0-dev, as suggested by  the error above:
```
sudo apt-get install libglib2.0-dev

```
and I get 
```
The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.22.2-0ubuntu1) but 2.22.3-0ubuntu1 is to be installed

```
Now what??   Anybody know how to fix this?

---

### Post by mc4man on 2010-07-30
Open up your software sources (System - Admin. ) and under the updates tab make sure the first two are checked (security and updates
Then click close and 'reload'
Or if both were checked then run
 ```
sudo apt-get update
```

---

### Post by BillRebey on 2010-07-30
I'm not running GNOME, so there's nothing to click.

sources.list contains a single entry, which is how the device was shipped:
```
deb http://ubuntu.src.cn/ubuntu-ports/ karmic main  universe restricted multiverse
```

The platform is a SmartQ-V7 ARM11-based tablet PC. The sources.list referenced above is what it came with.

I've done an apt-get update and apt-get upgrade, but to no avail.

---

### Post by mc4man on 2010-07-30
Sorry - read right over the "ARM", don't really know.

You're issue seems to be it shipped with the updated version but the -dev is only available from 'Updates' which isn't part of your sources.

(you can d. ck. what version of libglib is installed - should say 2.22.3-0ubuntu1, you'll need that exact same version for the dev.

You should try to find out if the security and update are available in a suitable repo or if not maybe see if you can acquire the proper versions and packages from launchpad, though using repo's is highly preferred.

Here's the full lp page on the dev
[https://launchpad.net/ubuntu/karmic/+package/libglib2.0-dev](https://launchpad.net/ubuntu/karmic/+package/libglib2.0-dev)

---

