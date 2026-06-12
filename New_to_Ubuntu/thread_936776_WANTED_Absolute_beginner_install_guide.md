---
title: "*WANTED* Absolute beginner install guide"
date: 2008-10-03
forum: New to Ubuntu
---

### Post by spa21788 on 2008-10-03
HELP!

I'm new enough to ubuntu and LInux in general and I was hoping to get compiz desktop effects working, but I don't know how to install it from the terminal, or anything from the terminal for that matter!

Can someone give me a rough list of commands?:confused::confused::confused:

---

### Post by billgoldberg on 2008-10-03
> **spa21788 said:**
> HELP!

I'm new enough to ubuntu and LInux in general and I was hoping to get compiz desktop effects working, but I don't know how to install it from the terminal, or anything from the terminal for that matter!

Can someone give me a rough list of commands?:confused::confused::confused:

Check out my customizing ubuntu guide.

The link is in my signature.

--

Also, you can install most things from either "applications -> Add/Remove" or "System -> Administrations -> Synaptic package manager".

---

### Post by spa21788 on 2008-10-03
*bookmarked* Thanks!

[EDIT]

Ah I encountered the same problem as before, it doesn't appear on the tab, it says it's installed, but I can't find it in the menu...

---

### Post by Ryadt on 2008-10-03
> **spa21788 said:**
> *bookmarked* Thanks!

[EDIT]

Ah I encountered the same problem as before, it doesn't appear on the tab, it says it's installed, but I can't find it in the menu...
Can you give some more information.

---

### Post by spa21788 on 2008-10-03
Step by step. I clicked applications-> Add/remove. Searched 'compiz'. Ticked box, apply changes-> 'yes'. Message box prompts that compiz was installed and I clicked close. System-> preferences and there is no compiz

---

### Post by pi.boy.travis on 2008-10-03
You can use the command:

sudo apt-get install (package name)

. . . to install any package in the repositories.

sudo apt-get remove (package name)

 . . .to uninstall any package

sudo apt-get autoremove

. . . to remove unneeded dependencies.

EDIT

OOPS, forgot to explain.

sudo

. . . gives you administrative privileges

apt-get

. . . is the package manager

---

### Post by Ryadt on 2008-10-03
System > Preferences > Advanced Desktop Effect Settings.

---

### Post by spa21788 on 2008-10-03
spa21788@spa21788-laptop:~/Desktop/compiz-0.6.2$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libsdl-ttf2.0-0 libfreebob0 menu libxml++2.6c2a libwxbase2.6-0
  libphysfs-1.0-0 python-twisted-bin libmodplug0c2 tuxtype-data python-editobj
  libjack0 libmp4v2-0 libgtk2-ruby1.8 libiso9660-5 libfftw3-3 libode0debian1
  libxosd2 libportaudio2 libwxgtk2.6-0 libgconf2-ruby1.8 libboost-thread1.34.1
  libglc0 libmatroska0 libcal3d12 libglib2-ruby1.8 python-twisted-core
  libsdl-gfx1.2-4 libdvdnav4 ttf-sil-doulos libcairo-ruby1.8
  python-zopeinterface libatk1-ruby1.8 libpango1-ruby1.8 liblua5.1-0 libtar
  ttf-sil-andika libitext-java libgdk-pixbuf2-ruby1.8 libadns1 libvcdinfo0
  libebml0 python-pyogg libmpcdec3 libsdl-pango1 libboost-filesystem1.34.1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
spa21788@spa21788-laptop:~/Desktop/compiz-0.6.2$ 


Still no joy... any suggestions?

---

### Post by philinux on 2008-10-03
sudo apt-get install compizconfig-settings-manager

copy and paste the above into the terminal

---

### Post by oldos2er on 2008-10-03
System, Preferences, Appearance, Visual Effects.

---

### Post by eternalnewbee on 2008-10-03
you should first check if your hardware can handle compiz; so do list your system specs. See below
_______________________________________

Ubuntu 8.04 Gnome 2.22.2 2.6.24-19-generic
AMD Athlon(tm) XP 899.219 MHz 256 KB
GeForce 7300 GT

---

