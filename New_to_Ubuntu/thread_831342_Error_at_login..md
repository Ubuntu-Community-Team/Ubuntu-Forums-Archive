---
title: "Error at login."
date: 2008-06-16
forum: New to Ubuntu
---

### Post by motopsyco on 2008-06-16
Hi all,

I'm setting up my first Ubuntu server and I'm learning a bunch in the process. However, I have encountered a problem.

I installed Xubuntu over Ubuntu Server, both latest releases, I now get a error at login from(?) gdm:

~/.xsessions - errors file

Setting IM through im-switch for local=en_US.

Starting IM through /etc/X11/init/xinput.d/all_ALL linked to /mkdtemp: private socket dir: Permission denied

I'm not sure what I'm looking at here, it looks like a temp file needs to be written and its being denied. Or, both left and right hands are trying to do the same thing. That is, two startup routines trying to do the same thing.

If it matters somehow, I have the system on a hardware RAID 5. I'm running LVM with dedicated LVs for VAR, USR, HOME, and TMP.

Any insights and help would be welcome. After being away from the command line for thirty years, its been a bit of the learning curve for me.

Cheers!

---

### Post by motopsyco on 2008-06-18
The solution to my problem was simple. We changed the permissions for the /tmp directory and the login completed.

Cheers!

---

