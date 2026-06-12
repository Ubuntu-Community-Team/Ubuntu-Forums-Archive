---
title: "installtaion of ubuntu 13.10 alongside windows 7 - what am I doing wrong?"
date: 2014-02-16
forum: New to Ubuntu
---

### Post by pazitp on 2014-02-16
Hi,

I have two separate hard drives, one has windows 7 and the other one had ubuntu 13.10. Until today, when I started the computer, windows was the default and if I wanted to load ubuntu I had to press F12 during the starting process and choose to boot from the second drive.
Today I tried to load ubuntu in this way, but after pressing F12, instead of giving me the boot menu, it showed a message saying "TFTP....", then waited for a few seconds, then said "PXE-E32: TFTP open timeout" and loaded windows. Because the last time I used ubuntu I installed and uninstalled xubuntu, I thought I must have done something wrong during the uninstall of xubuntu and deleted some important file for booting. 
If it matters, I googled "how to uninstall xubuntu" and used this command:
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview alacarte bison blueman brltty-x11 catfish espeak exo-utils flex fonts-droid fonts-lyx gigolo gmusicbrowser gnome-system-tools gnome-time-admin gstreamer0.10-gnomevfs gthumb gthumb-data gtk2-engines-pixbuf indicator-application-gtk2 indicator-sound-gtk2 leafpad libabiword-3.0 libbison-dev libdigest-crc-perl libexo-1-0 libexo-common libexo-helpers libfl-dev libgarcon-1-0 libgarcon-common libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgnomevfs2-0 libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgstreamer-perl libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a libgtkspell0 libido-0.1-0 libindicate-gtk3 libintl-perl libjpeg-progs libjpeg-turbo-progs libkeybinder0 liblink-grammar4 libloudmouth1-0 libnet-dbus-perl liboobs-1-5 libotr2 libots0 librarian0 libsexy2 libtagc0 libthunarx-2-0 libtidy-0.99-0 libtie-ixhash-perl libtumbler-1-0 libunique-1.0-0 libvte-common libvte9 libwv-1.2-4 libxfce4ui-1-0 libxfce4ui-utils libxfce4util-bin libxfce4util-common libxfce4util6 libxfcegui4-4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl lightdm-gtk-greeter link-grammar-dictionaries-en m4 orage parole pastebinit pavucontrol pidgin pidgin-data pidgin-libnotify pidgin-microblog pidgin-otr plymouth-theme-xubuntu-logo plymouth-theme-xubuntu-text python-configobj rarian-compat ristretto screensaver-default-images scrollkeeper shimmer-themes system-tools-backends tcl8.5 thunar thunar-archive-plugin thunar-data thunar-media-tags-plugin thunar-volman tumbler tumbler-common xbrlapi xchat xchat-common xfburn xfce-keyboard-shortcuts xfce4-appfinder xfce4-cpugraph-plugin xfce4-dict xfce4-indicator-plugin xfce4-mailwatch-plugin xfce4-netload-plugin xfce4-notes xfce4-notes-plugin xfce4-notifyd xfce4-panel xfce4-places-plugin xfce4-power-manager xfce4-power-manager-data xfce4-quicklauncher-plugin xfce4-screenshooter xfce4-session xfce4-settings xfce4-systemload-plugin xfce4-taskmanager xfce4-terminal xfce4-verve-plugin xfce4-volumed xfce4-weather-plugin xfce4-xkb-plugin xfconf xfdesktop4 xfdesktop4-data xfwm4 xscreensaver xscreensaver-data xscreensaver-gl xubuntu-artwork xubuntu-default-settings xubuntu-desktop xubuntu-docs xubuntu-icon-theme xubuntu-wallpapers && sudo apt-get install ubuntu-desktop
It seemed to go fine and I continued to use ubuntu after uninstalling xubuntu.

Anyway, since I didn't have anything important on ubuntu, I just inserted the cd and reinstalled ubuntu. Installation seemed fine but didn't help the boot problem, there is still the TFTP timeout message and windows comes up. 
For the ubuntu installation, when it offered to install ubuntu alongside windows I chose "something else" and chose the second drive. I made a primary partition with 50GB, ext4, for the operating system, and another partition with 20GB for swap files. 

What did I do wrong? Why is it not working?

Thanks...

---

### Post by jdeca57 on 2014-02-16
PXE-E32: and TFTP is used to boot from the network. Did you make changes to bios or boot order?

---

### Post by pazitp on 2014-02-16
I didn't make any changes to the bios or boot order. 
But the problem got resolved, I reinstalled ubuntu without partitioning the hard drive. 
Now when I boot the computer, ubuntu is the default, and if I press F9 I can choose to boot windows. F12 still doesn't work though, but I don't need it now.

---

