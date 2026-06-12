---
title: "[SOLVED] how to remove"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by ibbill on 2008-08-03
I have Hardy Heron and xubuntu installed on the same partition. This is how I installed xubuntu [HERE]("http://www.howtogeek.com/howto/ubuntu/install-xfce-xubuntu-on-ubuntu-linux/")

Is there a way to remove xubuntu with out causing any problems with the Hardy Heron install.

Thanks Bill

---

### Post by tamoneya on 2008-08-03
just remove its partition.  Use gparted.  Alt-F2:```
gksudo gparted
```

EDIT: sorry i missed that they were on the same partition.  ignore this.

---

### Post by jamesrfla on 2008-08-03
Just run this command in the terminal ```
sudo apt-get install ubuntu-desktop
```

---

### Post by jamesrfla on 2008-08-03
> **tamoneya said:**
> just remove its partition.  Use gparted.  Alt-F2:```
gksudo gparted
```

He didn't install kubuntu just the desktop environment.

---

### Post by Paqman on 2008-08-03
All you installed with those instructions was the desktop environment. Both the standard Ubuntu environment (Gnome) and the Xubuntu environment (XFCE) use the same basic system. So it's completely ok to remove XFCE if you have Gnome.

This command will remove all traces of XFCE from your system:
```

sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop

```

---

### Post by ibuclaw on 2008-08-03
> **Paqman said:**
> All you installed with those instructions was the desktop environment. Both the standard Ubuntu environment (Gnome) and the Xubuntu environment (XFCE) use the same basic system. So it's completely ok to remove XFCE if you have Gnome.

This command will remove all traces of XFCE from your system:
```

sudo apt-get remove a2ps abiword abiword-common abiword-plugins gnumeric-common gnumeric-gtk gtk2-engines-xfce imagemagick libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libglib2.0-data libgoffice-0-6 libgoffice-0-6-common libgsf-gnome-1-114 libgtkmathview0c2a liblink-grammar4 libots0 libt1-5 libtagc0 libthunar-vfs-1-2 libwpd-stream8c2a libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 link-grammar-dictionaries-en mousepad mozilla-thunderbird orage psutils python-exo ristretto tango-icon-theme tango-icon-theme-common thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-thumbnailers thunar-volman thunderbird vim-runtime xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-dict-plugin xfce4-fsguard-plugin xfce4-governor-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mcs-plugins-extra xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-places-plugin xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-smartbookmark-plugin xfce4-systemload-plugin xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfdesktop4-data xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs && sudo apt-get install ubuntu-desktop

```

Then run:
```
sudo aptitude purge $(dpkg -l | awk '{if ($1 == "rc") print $2}')
```
To purge all left over residual config files.

Regards
Iain

---

### Post by ibbill on 2008-08-04
Thank you all it worked perfectly. Wow that was fun.

Thanks all again for your quick replies. Going to mark this solved after I ask one more question.

How do you know if your running Gnome 

Bill

---

### Post by ibuclaw on 2008-08-04
Gnome has some fundamental differences from Xfce...

But, I guess the major one would be checking that the following menu link exists:
**System -> About Gnome**

else, you could always try grepping the current running processes.
```
ps -el | grep xfce
```
The above should give no output. Whereas:
```
ps -el | grep gnome
```
in the terminal will.

Also, in the login screen, you can select your "Session", you can check that gnome is the default there.

Regards
Iain

---

