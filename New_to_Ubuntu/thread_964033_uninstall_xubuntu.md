---
title: "uninstall xubuntu"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by twistadias on 2008-10-30
i installed xubuntu via the iso. Then i installed ubuntu-desktop

Now I only want to keep the ubuntu-desktop and delete xubuntu

When I use this code

```
sudo apt-get remove --purge xubuntu-desktop

```

It says that only 41kB of space will be free. Im pretty sure the actual xubuntu install is a lot larger than this

---

### Post by tompickles on 2008-10-30
try without --purge?

---

### Post by twistadias on 2008-10-30
> **tompickles said:**
> try without --purge?

same thing :(

---

### Post by Pogeymanz on 2008-10-30
I haven't used apt in a while, but what happens when you use Synaptic and check the "remove completely" box for xubuntu-desktop?

If that doesn't work, try using your command on xfce4 and xubuntu-desktop separately.

---

### Post by markharding557 on 2008-10-30
you probably need to remove everything to do with xfce and all the programs bundled with it xubutu-desktop is a metapackage which installs a list of packages determined by ubuntu

---

### Post by kansasnoob on 2008-10-30
Look at this entire section:

> Playing Around
Enable Desktop Effects
KDE/Gnome Comparison
Install Gnome
Install KDE
Install XFCE
Install IceWM
Install XPDE
Pure Gnome
Pure KDE
Pure XFCE
A faster KDE
Replacing Nautilus 

Of this tutorial:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

The reason I don't just point here:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Is because I want you to be sure you have ALL necessary Gnome! Gnome is the Ubuntu desktop!

---

### Post by kansasnoob on 2008-10-30
Actually I see this should work just fine:

```
sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop
```

That's the command to remove Xubuntu from:

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

Wow! It works, I've done it!

It might be wise to run:

```
sudo apt-get -f install
```

after a restart just to resolve any unmet dependencies.

---

### Post by twistadias on 2008-10-31
thanks a lot man

---

