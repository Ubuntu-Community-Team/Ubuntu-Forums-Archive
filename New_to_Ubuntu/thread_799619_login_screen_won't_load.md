---
title: "login screen won't load"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by jacklsw2008 on 2008-05-19
out of sudden, the login screen can't load whn i start ubuntu and it stays in command line interface. how do i change it back to gui? i think i had messed up smth in ubuntu hardy heron.

---

### Post by jacklsw2008 on 2008-05-19
it shows smth like this:

starting up ...
loading, please wait ...
kinit: name_to_dev_t (.......)
kinit: trying to resume from /dev/disk/........
kinit: no resume image, doing normal boot...

Ubuntu 8.04 jack-laptop tty1

jack-laptop login:

*that's it. my ubuntu no more gui.

---

### Post by philinux on 2008-05-19
When it drops you out to the command prompt try this.

Save your actual xorg.conf and redo xorg configuration, from terminal:
cd /etc/X11

sudo cp xorg.conf xorg.conf.bak

sudo dpkg-reconfigure xserver-xorg

sudo reboot

---

### Post by prshah on 2008-05-19
> **jacklsw2008 said:**
> 
jack-laptop login:
*that's it. my ubuntu no more gui.

Login, then try the below command; post errors if any.
```
startx
```

---

### Post by Bodsda on 2008-05-19
If all else fails, try rebooting, when grub selection loads choose the recovery option (second line usually) then choose the 'fix x' option.

---

### Post by jacklsw2008 on 2008-05-19
i can now go into gui with startx command. now how do i set back gnome display manager as default?

---

### Post by prshah on 2008-05-19
> **jacklsw2008 said:**
> i can now go into gui with startx command. now how do i set back gnome display manager as default?

give the command ```
sudo /etc/init.d/gdm start
```

That will startup the gnome desktop manager. You (usually) shouldn't have to do anything else to make it permanent.

---

