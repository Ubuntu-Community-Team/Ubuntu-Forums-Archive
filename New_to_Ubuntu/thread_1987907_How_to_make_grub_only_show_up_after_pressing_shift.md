---
title: "How to make grub only show up after pressing shift?"
date: 2012-05-26
forum: New to Ubuntu
---

### Post by Chiel92 on 2012-05-26
I once got it working, but an update has overwritten my /etc/default/grub.
I want the grub menu to show up only after I pressed the shift key.
What configuration do I need to put in /etc/default/grub?

Thanks for any help!

---

### Post by drs305 on 2012-05-26
I'll assume you have a multi-boot system.

There are some long-standing bugs concerning the GRUB_HIDDEN_TIMEOUT and GRUB_HIDDEN_TIMEOUT_QUIET settings. Additionally, the keystatus check (SHIFT) isn't incorporated on multi-OS systems for some reason. But don't fear, GRUB 2 will let us modify things to get it back for you.

Open /etc/default/grub and /etc/grub.d/30_os-prober:
```
gksu gedit +29 /etc/grub.d/30_os-prober /etc/default/grub &
```

In 30_os-prober find the following line (Gedit should open on this line) and make the following changes. It allows the addition of the keystatus check on multi-OS systems.
Change:
> 
make_timeout () {
  if [ "x${found_other_os}" = "x" ] ; then
To:
> 
make_timeout () {
**[COLOR="DarkRed"]#[/COLOR]**  if [ "x${found_other_os}" = "x" ] ; then
**[COLOR="DarkRed"]  if [ true ]; then[/COLOR]**

In /etc/default/grub, your first settings should look like the following (with GRUB_DEFAULT set to your wishes):
> GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10

Save both files and run sudo update-grub.

Note: Unless they have fixed this, with this change the GRUB_TIMEOUT setting is actually not important, as the system will boot without displaying the menu unless the SHIFT key is held down.

---

### Post by Chiel92 on 2012-05-27
Thanks, that worked!

---

