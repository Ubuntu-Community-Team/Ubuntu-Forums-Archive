---
title: "Grub Question?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by fabfred on 2008-05-04
Yesterday, I installed Ubuntu Studio on my system successfully so that I can play around in some of my free time. 

My kids use this computer under Windows, unfortunately, so that it is important for the system to default to Windows not Linux.  I understand that Grub is now my boot menu, however I can't seem to find the files where it keeps this info.

Any help would be appreciated.

[COLOR="Blue"]Long Live Rock! [/COLOR] :guitar:

---

### Post by PeterJS on 2008-05-04
Grub stores it's configuration in /boot/grub/menu.lst. /boot/grub/menu.lst being a system file is owned by root, so to edit it you will need to do so with elevated privilages. The run dialog can be opened with alt+f2, you'll want to run:
```

gksudo gedit /boot/grub/menu.lst

```
which is **g**raphical **s**uper **u**ser **do** g(nome) edit /boot/grub/menu.lst.

And the option you're looking for is right up at the top, the default option selects which entry is booted by default. When counting the boot entries they can be found down at the bottom of the configuration file. You might also want to look at the timeout and hiddenmenu options.

---

### Post by northern lights on 2008-05-04
The grub menu is stored in "/boot/grub/menu.lst"

To edit, you have to be root. Run ```
gksu gedit /boot/grub/menu.lst
```

Under the divider (reads "END DEBIAN AUTOMATED KERNEL LIST" or similar), locate and cut the text

```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
``` and paste it on top of the Ubuntu entries, but below the default options (in which you can also set the default OS to be booted).

---

