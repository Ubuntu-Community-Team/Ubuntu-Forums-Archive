---
title: "sluggish since upgrading"
date: 2012-04-10
forum: New to Ubuntu
---

### Post by ub newb on 2012-04-10
My machine has been intermittently sluggish since upgrading to Lucid 10.04 several months back.  Even though the computer sounds like it's processing at very high speed it runs slowly, sometimes coming to a complete halt when I am online.

I was delighted with the performance of Hardy and didn't have this trouble with it. I would appreciate it if you could tell me what my  next step should be to try to fix this.

using htop, the top CPU file consistently is a file with /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm followed by a variable letter/number named database and then -nolisten tcp  

Today I noticed for the first time that root is running it. Is this something I just never noticed before? Usually that file is run by whatever user's desktop I'm on at the time.

---

### Post by snowpine on 2012-04-10
What can you tell us about your hardware? Which desktop environment (Gnome, KDE, etc) are you running?

---

### Post by ub newb on 2012-04-10
dell optiplex Gx240 and I'm running Gnome
Intel(R) Pentium(R) 4 CPU 1.60GHz

---

### Post by snowpine on 2012-04-10
> **ub newb said:**
> dell optiplex Gx240

Google tells me this is 1.8ghz Pentium 4 with 512mb RAM. This is on the low end for Ubuntu, in my opinion.

> **ub newb said:**
> I'm running Gnome

Give Xfce (Xubuntu) or LXDE (Lubuntu) a try, two "lightweight" desktops.

You might also try a fresh install rather than an upgrade. This will give you the ext4 filesystem (among other improvements) which might speed up any task involving disk access.

A hardware upgrade would be my recommendation, see the current hardware requirements here: [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by ub newb on 2012-04-10
Thanks for your suggestions.

---

