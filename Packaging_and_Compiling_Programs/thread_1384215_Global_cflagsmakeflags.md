---
title: "Global cflags/makeflags"
date: 2010-01-18
forum: Packaging and Compiling Programs
---

### Post by wmd on 2010-01-18
Hello,

I just wanted to know where to set global cflags/makeflags, so that they're used for kernel and other compiles? ~/.bashrc or ~/.profile (which would be user-specific, where to set system-wide)? Also, what's the difference between MAKEOPTS and MAKEFLAGS (where I would set -j X)?

TIA  ;)

---

### Post by SevenMachines on 2010-01-20
Hopefully useful but its been a while :)

where you put the variables depends on what you want to do, /etc/profile is a system wide initialisation script run at user login, ~/.profile is a per user script run at login. you could probably use these if you don't exect to change the flags often, or do a lot of compiling from the tty
.bashrc is a non login script run every time you start an interactive shell, such as starting a shell from the desktop menu. you should probably use this if you think you'll often need to change flag settings during a session or expect to do you compiling from a gui shell
you should probably have a look at the bash manpage as it gives a better explanation than i can manage about the different scripts and when they are called

As for the diference between MAKEOPTS and MAKEFLAGS, i'm really not entirely sure. I would tend towards using MAKEFLAGS myself, but only because i'm used to seeing MAKEFLAGS generally whereas rightly or wrongly i associate MAKEOPTS  with gentoo

a slightly vague and unsure explanation but hopefully it'll help :)

---

### Post by wmd on 2010-01-22
Maybe it was vague and unsure, but sure it was helpful.  :)

I packed everything into ~/.profile which as far as exports go worked a treat. Problem is, Kernel compiles mostly ignores what I write in there anyway. I wanted to weed out unneeded parts of the kernel, which worked fine. But cflags seem to be ignored, ICC don't seem to work either for this. It's not complaining anywhere but the resulting kernel isn't performing any different at all. :(

---

