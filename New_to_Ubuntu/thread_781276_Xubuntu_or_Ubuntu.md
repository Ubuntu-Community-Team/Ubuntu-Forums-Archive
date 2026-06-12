---
title: "Xubuntu or Ubuntu?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by Darksci on 2008-05-04
So I just found out Xbuntu offers a faster GUI than the regular distr of Ubuntu. Is there any advantages of using Xubuntu?

I am a new user to Ubuntu, but I used Red Hat at uni
I want to use the advanced desktop effects like beryl and compiz
I have a Dell Laptop with an ATI card

:confused:

---

### Post by Paqman on 2008-05-04
> **Darksci said:**
> 
I want to use the advanced desktop effects like beryl and compiz


Then Xubuntu isn't really for you. Xubuntu does have a compositor like Compiz, but the most you'll get out of it effects-wise is some dropshadows behind your windows and transperancy.

If you want to try out Xubuntu: [click here to install xubuntu-desktop](apt:xubuntu-desktop). Log out > Options > Select Session > XFCE and log in as normal.

If you don't like it, paste this into a terminal to completely remove it:
```

sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop

```

---

### Post by ugm6hr on 2008-05-04
> **Darksci said:**
> So I just found out Xbuntu offers a faster GUI than the regular distr of Ubuntu. Is there any advantages of using Xubuntu

Xubuntu (XFCE) does support Compiz-Fusion.

I haven't used XFCE on a high-end computer with Compiz, but I suspect that the extra speed will be minimal, if any.

XFCE's speed boost is most obvious when running on low-end hardware, with unnecessary functions turned off.

The main advantage is personal preference / choice.

I think XFCE does some things better than Gnome (especially thunar as file manager), but Gnome is overall a more polished Desktop Environment.

---

