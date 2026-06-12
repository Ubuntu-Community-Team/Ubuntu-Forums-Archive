---
title: "HowTo: Uninstall the Xubuntu-Desktop Metapackage"
date: 2006-02-12
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2006-02-12
**Warning**: This is for Kubuntu only.

If you installed Xubuntu in Kubuntu using the command ```
sudo apt-get install xubuntu-desktop
``` and you want to remove Xubuntu, the command ```
sudo apt-get remove xubuntu-desktop
``` will do essentially **nothing**.

Xubuntu-desktop is only a *metapackage*--it points to a bunch of other packages for installation and upgrade only. Removing the metapackage does not remove the packages it depends on.

To remove Xubuntu, copy and paste this command into a terminal: ```
sudo apt-get remove abiword abiword-common cdrdao dbus-1-utils esound foomatic-db-hpijs gaim gaim-data gqview graveman gtk2-engines-xfce hpijs hplip-base hplip-data hplip-ppds libcompfaceg1 libdbh1.0-1 libenchant1c2 libesd-alsa0 libexo0.3-0 libglib2.0-data libgnomecups1.0-1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgtkspell0 libvte-common libvte4 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 mousepad rox-filer sylpheed sylpheed-i18n synaptic ubuntu-docs xchat xchat-common xfcalendar xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes xscreensaver xscreensaver-data xubuntu-artwork-usplash xubuntu-desktop
```

---

