---
title: "Text boot?"
date: 2012-07-28
forum: New to Ubuntu
---

### Post by Kimizor on 2012-07-28
Hi. I'm trying to get a boot text instead of the pretty yet boring Kubuntu splash screen. I tried to fix this a few weeks ago in some file I can't remember the name of by changing &quot;quiet splash&quot; to &quot;splash&quot;. I couldn't make a backup because &quot;the file was read only for me&quot;. So...  1. Does anyone know the location of the file I'm talking about?  2. How do I make it read/write?  I am genuinely sorry for my newbish. I hope this makes sense. I'm using 12.04 installed with wubi if that's helpful.     Thanks,    Kimi

---

### Post by Zorael on 2012-07-29
Open up **/etc/default/grub** in a text editor with root permissions. You can do this by hitting Alt+F2 to pop up a run box, and then entering '**kdesudo kate /etc/default/grub**'.

Find the **GRUB_CMDLINE_LINUX_DEFAULT** line as below, remove [COLOR="Red"]**splash**[/COLOR], then save and exit.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR="Red"]splash[/COLOR]"**
GRUB_CMDLINE_LINUX=""

***[...]***
```
If you also remove **quiet** your boot will be very very verbose, but perhaps that's what you want?

At any rate, after saving your changes, open up a terminal and run the following command;
```
$ sudo update-grub
```
Then you should be all set.

---

### Post by gerrygprs on 2012-08-30
> **Zorael said:**
> Open up **/etc/default/grub** in a text editor with root permissions. You can do this by hitting Alt+F2 to pop up a run box, and then entering '**kdesudo kate /etc/default/grub**'.

Find the **GRUB_CMDLINE_LINUX_DEFAULT** line as below, remove [COLOR="Red"]**splash**[/COLOR], then save and exit.
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
**GRUB_CMDLINE_LINUX_DEFAULT="quiet [COLOR="Red"]splash[/COLOR]"**
GRUB_CMDLINE_LINUX=""

***[...]***
```
If you also remove **quiet** your boot will be very very verbose, but perhaps that's what you want?

At any rate, after saving your changes, open up a terminal and run the following command;
```
$ sudo update-grub
```
Then you should be all set.


Thank you. Worked on a HP 630 laptop running Ubuntu 12.04 with all updates

---

