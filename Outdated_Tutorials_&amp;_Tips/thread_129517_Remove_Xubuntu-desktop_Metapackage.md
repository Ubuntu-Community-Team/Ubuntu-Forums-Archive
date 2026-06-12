---
title: "Remove Xubuntu-desktop Metapackage"
date: 2006-02-13
forum: Outdated Tutorials &amp; Tips
---

### Post by aysiu on 2006-02-13
If you installed Xubuntu-Desktop over Gnome, and you want to get rid of Xubuntu, doing this won't help: ```
sudo apt-get remove xubuntu-desktop
``` Xubuntu-Desktop is just a metapackage. Installing it will install all its dependencies (the entire XFCE desktop and more). Removing it, however, won't remove all its dependencies.

To uninstall Xubuntu from on top of Gnome, go to Applications > Accessories > Terminal and copy and paste (shift-insert) this command: ```
sudo apt-get remove abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0 libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-desktop
``` For Dapper, go [here](http://www.psychocats.net/ubuntu/puregnome).

---

### Post by Josef K. on 2006-02-15
and if you want to remove xubuntu-desktop from your kubuntu installation use this command 
```

sudo apt-get remove xubuntu-* xfce4-* ubuntu-docs abiword esound sox firefox gqview gaim-data libxfcegui* libgnomecanvas*-common libvte-common libxfce4util* libgnomeprint* libgnomecups* libcompfaceg* libglib2.0-data libdbh* launchpad-integration libmyspell* libstartup-notification* xchat-common xscreensaver shared-mime-info dbus-1-utils
sudo apt-get install libesd0
sudo apt-get autoclean

```
and of course you still need to remove the thousand of directories that gtk proggies seeds around your home directory :KS

---

### Post by RaptorRaider on 2006-02-15
Nevermind... was posting too fast again.
I guess the goal of this is simply to save space on your HDD.

---

### Post by aysiu on 2006-02-15
[QUOTE=Josef K.]and if you want to remove xubuntu-desktop from your kubuntu installation use this command 
```

sudo apt-get remove xubuntu-* xfce4-* ubuntu-docs abiword esound sox firefox gqview gaim-data libxfcegui* libgnomecanvas*-common libvte-common libxfce4util* libgnomeprint* libgnomecups* libcompfaceg* libglib2.0-data libdbh* launchpad-integration libmyspell* libstartup-notification* xchat-common xscreensaver shared-mime-info dbus-1-utils
sudo apt-get install libesd0
sudo apt-get autoclean

```
and of course you still need to remove the thousand of directories that gtk proggies seeds around your home directory :KS[/QUOTE] I actually wrote a separate HowTo about removing it from Kubuntu--it's right [here](http://www.ubuntuforums.org/showthread.php?t=129079)

---

### Post by gulp35 on 2006-05-22
I'm running Dapper right now and this still doesn't seem to remove all the xfce stuff... I get alot of "*some program* is not installed, so not removed" 

how can xubuntu be removed completely on dapper?

---

### Post by aysiu on 2006-05-22
I wrote those specifically for Breezy. I'm not surprised at all that it doesn't work for Dapper. I'll see if I can pop together one that works for Dapper...

Okay, this is based off a clean Ubuntu Dapper **Beta** installation, so it'll work for Dapper Beta, but I don't know if it'll work 100% for a more up-to-date version of Dapper: ```
sudo apt-get remove abiword abiword-common abiword-plugins anthy gnumeric-common gnumeric-gtk gqview gtk2-engines-xfce libaiksaurus-1.2-0c2a libaiksaurus-1.2-data libaiksaurusgtk-1.2-0c2a libanthy0 libchewing-data libchewing2 libenchant1c2a libexo-0.3-0 libgdome2-0 libgdome2-cpp-smart0c2a libgoffice-1-common libgoffice-gtk-1-2 libgsf-gnome-1-113 libgtkmathview0c2a libjpeg-progs libmodplug0c2 libots0 libpcre3 libt1-5 libtag1c2a libtagc0 libthunar-vfs-1 libwpd-stream8c2a libxcomposite1 libxfce4mcs-client3 libxfce4mcs-manager3 libxfce4util4 libxfcegui4-4 libxine-main1 libxvmc1 mousepad mozilla-thunderbird orage scim-anthy scim-chewing scim-hangul scim-pinyin tango-icon-theme-common thunar thunar-media-tags-plugin ttf-gentium xarchiver xfburn xfce4-appfinder xfce4-battery-plugin xfce4-clipman-plugin xfce4-cpugraph-plugin xfce4-fsguard-plugin xfce4-icon-theme xfce4-mailwatch-plugin xfce4-mcs-manager xfce4-mcs-plugins xfce4-mixer xfce4-mixer-alsa xfce4-mount-plugin xfce4-netload-plugin xfce4-panel xfce4-quicklauncher-plugin xfce4-screenshooter-plugin xfce4-session xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-utils xfce4-verve-plugin xfce4-weather-plugin xfce4-xkb-plugin xfdesktop4 xfmedia xfprint4 xfwm4 xfwm4-themes xscreensaver xubuntu-artwork-usplash xubuntu-default-settings xubuntu-desktop xubuntu-docs
```

---

### Post by gulp35 on 2006-05-22
thank you!!! It works!!! there should be something like this integrated into apt-get... 
if you try to apt-get remove (--meta*suggested tag*) (meta package) it uninstalls all the dependencies that aren't being used by any other packages.

---

### Post by aysiu on 2006-05-22
[QUOTE=gulp35]there should be something like this integrated into apt-get... 
if you try to apt-get remove (--meta*suggested tag*) (meta package) it uninstalls all the dependencies that aren't being used by any other packages.[/QUOTE] Actually, there is something like that, but it's built into aptitude, not apt-get.

To take advantage of it, you must update and install with aptitude and then remove the package with aptitude also.

```
sudo aptitude update
sudo aptitude install xubuntu-desktop
``` and later ```
sudo aptitude remove xubuntu-desktop
```

---

### Post by gulp35 on 2006-05-22
Then why doesn't everyone use aptitude?

Is it because of the extra character that you have to type? (people aren't that lazy *are they??*)

---

### Post by aysiu on 2006-05-22
[QUOTE=gulp35]Then why doesn't everyone use aptitude?

Is it because of the extra character that you have to type? (people aren't that lazy *are they??*)[/QUOTE] I think it's a combination of a bunch of things:

1. Some people just don't know about aptitude.
2. Most of the documentation uses apt-get, so people are just used to it and recommend it out of habit.
3. Fear of the unknown. If apt-get "works" for people, they want to try something new that may screw up their system.

---

### Post by subru77 on 2008-07-02
Can you give me the list for Hardy ?

Thanks in advance ..

---

### Post by aysiu on 2008-07-02
Here:
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by sisco311 on 2008-07-02
> **subru77 said:**
> Can you give me the list for Hardy ?

Thanks in advance ..
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by subru77 on 2008-07-02
Thanks, I will try this .. Appreciate the quick help.

EDIT: It worked... thanks you all :)

---

### Post by Martin Marshalek on 2009-01-12
Will this work with any metapackage (i.e. opengeu-desktop)?

---

### Post by Rohan on 2010-03-15
> **aysiu said:**
> I think it's a combination of a bunch of things:

1. Some people just don't know about aptitude.
2. Most of the documentation uses apt-get, so people are just used to it and recommend it out of habit.
3. Fear of the unknown. If apt-get "works" for people, they want to try something new that may screw up their system.

Also I've been in a situation where I've installed something from source and lost a dependency because I removed it inadvertendly through aptitude

---

### Post by cbbnewbie on 2010-06-27
**hello im in ubuntu 10.04 and tried xubuntu desktop but now want to get rid of it i tried**

sudo apt-get remove abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0 libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-desktop

**but didn't work i got this error**


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cdrdao is not installed, so not removed
Package gqview is not installed, so not removed
E: Couldn't find package graveman
charlie@bsw:~$ 

**thanks ^_^**

---

### Post by sisco311 on 2010-06-27
> **cbbnewbie said:**
> **hello im in ubuntu 10.04 and tried xubuntu desktop but now want to get rid of it i tried**

sudo apt-get remove abiword abiword-common cdrdao gqview graveman gtk2-engines-xfce ivman libdbh1.0-1 libenchant1c2 libexo0.3-0 libgpgme11 libid3tag0 libmad0 libmodplug0c2 liboggflac3 libsensors3 libxcomposite1 libxfce4mcs-client-2 libxfce4mcs-manager-2 libxfce4util-1 libxfcegui4-3 libxine1c2 mousepad rox-filer sox sylpheed sylpheed-i18n vorbis-tools xfcalendar xfce4 xfce4-appfinder xfce4-artwork xfce4-battery-plugin xfce4-clipman-plugin xfce4-datetime-plugin xfce4-diskperf-plugin xfce4-fsguard-plugin xfce4-genmon-plugin xfce4-goodies xfce4-icon-theme xfce4-iconbox xfce4-mcs-manager xfce4-mcs-plugins xfce4-minicmd-plugin xfce4-mixer xfce4-netload-plugin xfce4-notes-plugin xfce4-panel xfce4-panel-menu-plugin xfce4-sensors-plugin xfce4-session xfce4-showdesktop-plugin xfce4-systemload-plugin xfce4-systray xfce4-taskbar-plugin xfce4-taskmanager xfce4-terminal xfce4-toys xfce4-trigger-launcher xfce4-utils xfce4-wavelan-plugin xfce4-weather-plugin xfce4-windowlist-plugin xfce4-xkb-plugin xfdesktop4 xffm4 xfmedia xfprint4 xfwm4 xfwm4-themes xubuntu-artwork-usplash xubuntu-desktop

**but didn't work i got this error**


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cdrdao is not installed, so not removed
Package gqview is not installed, so not removed
E: Couldn't find package graveman
charlie@bsw:~$ 

**thanks ^_^**
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by -humanaut- on 2010-06-27
sudo aptitude remove xubuntu-desktop && sudo aptitude install ubuntu-desktop

---

### Post by cbbnewbie on 2010-06-27
thanks sisco311 that worked!

---

