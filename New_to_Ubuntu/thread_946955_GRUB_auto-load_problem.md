---
title: "GRUB auto-load problem"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by OriginalAdric on 2008-10-13
So I decided to take the plunge and install Ubuntu on my desktop system. Everything works great except for one minor issue: the GRUB bootloader automatically loads Ubuntu without providing me a choice of OS. If I save an incorrect partition parameter in the menu.lst configuration file, GRUB returns an error, then provides me options, but with correct partition parameters, it chooses for me and continues to load. I have used that to test my options to chainload the Windows bootloader from a secondary drive, so I know the load configurations are correct. I just can't figure out how to prevent GRUB from automatically loading Ubuntu.

---

### Post by Unanimated on 2008-10-13
Either press ESC when GRUB finishes loading, edit menu.lst and remove the # before hiddenmenu so it looks like this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu
```

Or, you can download startup-manager from the repos and change the default boot option.

---

### Post by anewguy on 2008-10-13
What are your "default" and "timeout" parameters set to in menu.lst?  They are normally very near the top of the file.

Dave :)

---

### Post by OriginalAdric on 2008-10-13
Hooray! It was the hidden menu and timeout options that needed to be tweaked. Thanks for your help.

---

