---
title: "random thought"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by druid696 on 2011-11-20
is there a way to go from ubuntu-32bit to kubuntu-64 bit in the terminal?

---

### Post by -LynX- on 2011-11-20
no, in order to change to 64 bit, you have to install everything from start again.

---

### Post by 3rdalbum on 2011-11-20
You can't change bit-width without doing a reinstall.

Ubuntu and Kubuntu are the same base, but with a different desktop and a different set of preinstalled programs. If you want to try the KDE desktop, you can install it from the repositories and then choose between KDE and Unity at the login screen.

If you want to try Kubuntu (so, the KDE desktop and all the preinstalled programs) you can install the 'kubuntu-desktop' package.

But going 32-bit to 64-bit requires a reinstall.

---

### Post by dniMretsaM on 2011-11-20
Well you could change to the 32-bit PAE kernel which will allow you to access more than 4GiB of RAM. You can also completely remove GNOME and install KDE from the command line, too (see [here]("http://www.psychocats.net/ubuntu/purekde")). This won't give you a true 64-bit system though, so your best bet is probably to just do a fresh install of Kubuntu 64-bit.

EDIT: Note that if you had 4GiB of RAM when you did the original install the PAE kernel is already installed.

---

