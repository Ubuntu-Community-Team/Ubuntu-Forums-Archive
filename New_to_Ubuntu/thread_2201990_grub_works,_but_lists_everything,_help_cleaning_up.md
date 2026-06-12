---
title: "grub works, but lists everything, help cleaning up"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by crip720 on 2014-01-26
I recently installed Linux Lite in my multi-boot setup.  Unfornutary it installed Grub with every listing/kernal it could find.  Now I have a grub with a couple pages of listings that I have touble reading/finding what I would like to boot to.  I would like get it back to the way it was, but I am unsure which way would be the best.  I tried sudo update-grub with another Ubuntu, but it did not seem to help.  I do not know if boot-repair would do it, or if I have to reinstall grub.  I would not like to have to uninstall all these listings one at a time.  Any ideas would be appeciecated.  Thanks  Colin.

---

### Post by Dave_L on 2014-01-26
What version of grub do you have?

```
$ grub-mkconfig -v
```

---

### Post by QIII on 2014-01-26
Hello!

Don't know if Linux Lite, even with its roots in Debian and Ubuntu, works quite the same -- but you may be able to remove those old kernels (and thus remove them from GRUB) with

```
sudo apt-get autoremove
```

There are similar commands for other OSes.  Fedora, for instance is

```
package-cleanup --old-kernels
```



Let us know if that works.

---

### Post by crip720 on 2014-01-26
2.00-19ubuntu2.1, this is from Ubuntu 13.10 64b.  Not sure which one Linux Lite 12.04 64b uses, but I can reinstall grub, if that is easier.  Just want grub back to listing OS1, OS2 etc, without having 10 to 15 listings for every OS.

---

### Post by crip720 on 2014-01-26
Do I need to add any thing to autoremove, my CLI is mainly copy&paste?

---

### Post by QIII on 2014-01-26
That is all that is needed.

---

### Post by crip720 on 2014-01-26
Linux lite is using verson  1.99-21ubuntu3.14 grub.  autoremove and update-grub in 13.10 and Linux Lite has not worked.

---

### Post by deadflowr on 2014-01-26
Linux Lite seems to be a debian-based distro.
Here's one way of removing old kernels.
[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)
nice informative breakdown.

Adding, it's just one of many ways to clean out the old kernels.
I use synaptic to find and clean out kernels as well.

---

### Post by Dennis N on 2014-01-27
> **crip720 said:**
> Linux lite is using verson  1.99-21ubuntu3.14 grub.  autoremove and update-grub in 13.10 and Linux Lite has not worked.

In your kind of setup, with multiple OSes, you can remove the clutter from other OSes:

1) Create a maintanance-free custom menu - a guide can be found at: [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

2) After the custom menu is known to be working, disable the OS prober in the controlling OS and update grub, which will leave you with just the custom menu and the entries for the controlling OS only (which can be further reduced by deleting old kernels).

[906]

---

### Post by crip720 on 2014-01-27
Thank you for your help.  The custommenus for grub were more than I was looking for, and a bit above my alibility.  I think I have solved this by using Parted Magic and a program called Grub Doctor.  Grub seems to be back to normal now, with just the plain listings for the OSs.  I will mark this as solved.  Thank you.  Colin.

---

### Post by Dennis N on 2014-01-28
> The custommenus for grub were more than I was looking for, and a bit above my alibility.

Understandable. At least be sure you are using Grub version 2.00 to control the booting, since it will use submenus to hide from view the older kernel entries of the various OSes on your system.

---

### Post by Dave_L on 2014-01-28
> **Dennis N said:**
> Understandable. At least be sure you are using Grub version 2.00 to control the booting, since it will use submenus to hide from view the older kernel entries of the various OSes on your system.

And the "2.00" is not meant to be taken literally. Grub 2 is actually Grub 1.98 or later (I think). The submenu feature mentioned was added around 1.99, as I recall.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by crip720 on 2014-01-28
Hi, just want to clarify that the mess with grub[?], was that it was listing long lines and I think a lot of them were not kernals or recovery options.  A lot of them had os prober in them.  Thanks for your help.  Colin.

---

