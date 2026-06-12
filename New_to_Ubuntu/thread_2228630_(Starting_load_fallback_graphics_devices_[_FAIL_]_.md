---
title: "(Starting load fallback graphics devices [ FAIL ] black screen with orange underscore"
date: 2014-06-08
forum: New to Ubuntu
---

### Post by nigel-huang312 on 2014-06-08
I updated my NVIDIA drivers to 331.79 and restart and then this happens. It all happens in a second. First it loads normally saying everything is [ok] and then the last one says Starting Load Fallback Graphics Driver [FAIL]. Then it becomes a black screen. The login terminal comes for a split second and then disapeers. Leaving a orange flashing underscore.

---

### Post by oldfred on 2014-06-10
When you say updated, did you install from repository?

Installing new nVidia drivers requires a purge of any older driver and settings installed from a different source or else you get conflicts.

 Lists installed version, in/with your kernel:
dkms status
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
# [ using the correct names] for each driver, before running:
sudo apt-get purge nvidia*
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

---

