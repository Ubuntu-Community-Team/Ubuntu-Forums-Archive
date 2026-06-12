---
title: "Ubuntu =&gt; Lubuntu =&gt; Ubuntu"
date: 2013-08-28
forum: New to Ubuntu
---

### Post by czgirb on 2013-08-28
Today I found:
According to this URL [https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu) , in order to make current used Ubuntu (12.04) to become Lubuntu, I required for using the following command:
```

sudo apt-get update sudo apt-get install lubuntu-desktop

```

My question is ... after give it a try, if it is not suitable to me ... **how can I remove/delete it**, without having any effect/affect to my current Ubuntu?
Please help ...

**PS: Sorry for my English**

---

### Post by SweetAurora on 2013-08-28
First, run the command, but don't hit "y" Now in the apt-get summary section where it tells you everything that will be installed, copy the output text line by line and paste them to a text file making sure each pasted line is directly after the last. That way we remove the word wrap the terminal created. Use Gedit, Vi, whatever you like to paste the text in, then save it to the pc. 

Now go ahead and install. Now if you don't like Lubuntu, just log out and log back into Unity, and then open the text file. In a terminal, just type "sudo apt-get remove --purge" hit space and copypaste the text there. and hit enter. :)

---

### Post by alphacrucis2 on 2013-08-28
> **czgirb said:**
> Today I found:
According to this URL [https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu](https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu) , in order to make current used Ubuntu (12.04) to become Lubuntu, I required for using the following command:
```

sudo apt-get update sudo apt-get install lubuntu-desktop

```

My question is ... after give it a try, if it is not suitable to me ... **how can I remove/delete it**, without having any effect/affect to my current Ubuntu?
Please help ...

**PS: Sorry for my English**

You shouldn't need to remove it. You should be able to choose which session you want to log in to. On my previous install I had, normal ubuntu (unity), gnome shell, kde and cairo dock available to choose from the login screen. I would expect it would be the same with lxde.

---

### Post by ptn107 on 2013-08-28
I'm not sure about 12.04 (precise), but a default lubuntu-desktop install in 13.04 (raring) brings in:
```

abiword
abiword-common
ace-of-penguins
audacious
audacious-plugins:amd64
audacious-plugins-data
blueman
chromium-browser
chromium-codecs-ffmpeg
cups-driver-gutenprint
elementary-icon-theme
ffmpegthumbnailer
galculator
gdebi
gdebi-core
gecko-mediaplayer
giblib1:amd64
gksu
gnome-icon-theme-full
gnome-mplayer
gnome-system-tools
gnome-time-admin
gnumeric
gnumeric-common
gpicview
gtk2-engines:amd64
gtk2-engines-pixbuf:amd64
guvcview
hardinfo
indicator-application-gtk2
leafpad
libabiword-2.9:amd64
libass4:amd64
libaudclient2:amd64
libaudcore1:amd64
libavcodec53:amd64
libavformat53:amd64
libavutil51:amd64
libbinio1ldbl
libbluray1:amd64
libbs2b0
libcddb2
libcompfaceg1
libcue1
libdca0
libdirectfb-1.2-9:amd64
libdiscid0:amd64
libdvdnav4:amd64
libdvdread4
libenca0
libencode-locale-perl
libept1.4.12
libexo-1-0:amd64
libexo-common
libexo-helpers
libfaad2:amd64
libffmpegthumbnailer4
libfile-listing-perl
libfluidsynth1:amd64
libfm-data
libfm-gtk-bin
libfm-gtk-data
libfm-gtk3
libfm3
libgda-5.0-4
libgda-5.0-common
libgif4:amd64
libgksu2-0
libglade2-0:amd64
libgmlib1:amd64
libgmtk1:amd64
libgmtk1-data
libgoffice-0.10-10
libgoffice-0.10-10-common
libgsf-1-114
libgsf-1-common
libgsm1:amd64
libgtkspell0
libguess1:amd64
libhtml-parser-perl
libhtml-tagset-perl
libhtml-tree-perl
libhttp-cookies-perl
libhttp-date-perl
libhttp-message-perl
libhttp-negotiate-perl
libid3tag0
libimlib2
libio-socket-ssl-perl
libjs-jquery
libloudmouth1-0
liblwp-mediatypes-perl
liblwp-protocol-https-perl
libmenu-cache2
libmms0:amd64
libmodplug1
libmowgli2:amd64
libmp3lame0:amd64
libmpg123-0:amd64
libmusicbrainz3-6
libnet-dbus-perl
libnet-http-perl
libnet-ssleay-perl
libnss3-1d:amd64
libobrender27
libobt0
libonig2
liboobs-1-5
libopts25
libots0
libpisock9
libpostproc52:amd64
libresid-builder0c2a
libschroedinger-1.0-0:amd64
libsdl1.2debian:amd64
libsidplay2
libswscale2:amd64
libtidy-0.99-0
libts-0.0-0:amd64
libuniconf4.6
libva1:amd64
libvdpau1:amd64
libvte-common
libvte9
libwv-1.2-4:amd64
libwvstreams4.6-base
libwvstreams4.6-extras
libwww-perl
libwww-robotrules-perl
libxfce4ui-1-0
libxfce4util-common
libxfce4util6
libxfconf-0-2
libxml-parser-perl
libxml-twig-perl
libxss1:amd64
libxvidcore4:amd64
lightdm-gtk-greeter
lubuntu-artwork
lubuntu-artwork-13-04
lubuntu-core
lubuntu-default-session
lubuntu-default-settings
lubuntu-desktop
lubuntu-icon-theme
lubuntu-lxpanel-icons
lubuntu-software-center
lxappearance
lxappearance-obconf
lxinput
lxkeymap
lxlauncher
lxmenu-data
lxpanel
lxpanel-indicator-applet-plugin
lxrandr
lxsession
lxsession-data
lxsession-edit
lxshortcut
lxtask
lxterminal
mplayer2
mtpaint
ntp
obconf
openbox
pcmanfm
pidgin
pidgin-data
pidgin-microblog
plymouth-theme-lubuntu-logo
plymouth-theme-lubuntu-text
python-pysqlite2
python-support
python-xklavier
scrot
sylpheed
sylpheed-doc
sylpheed-i18n
sylpheed-plugins
synaptic
system-tools-backends
transmission
tsconf
wvdial
xfburn
xfce-keyboard-shortcuts
xfce4-notifyd
xfce4-power-manager
xfce4-power-manager-data
xfconf
xpad
xscreensaver
xscreensaver-data

```

I will post shortly the 12.04 Lubuntu list.  It should be similar to the 13.04 assortment.

---

### Post by ptn107 on 2013-08-28
Here's what Lubuntu 12.04 has that Ubuntu 12.04 doesn't:
```

abiword
abiword-common
ace-of-penguins
audacious
audacious-plugins
audacious-plugins-data
blueman
chromium-browser
chromium-codecs-ffmpeg
cups-driver-gutenprint
elementary-icon-theme
esound-common
galculator
gdebi
gdebi-core
gecko-mediaplayer
giblib1
gnome-icon-theme-full
gnome-mplayer
gnome-system-tools
gnome-time-admin
gnumeric
gnumeric-common
gpicview
gtk2-engines-pixbuf
guvcview
hardinfo
leafpad
libabiword-2.9
libass4
libaudclient2
libaudcore1
libaudiofile1
libavcodec53
libavformat53
libavutil51
libbinio1ldbl
libbluray1
libbs2b0
libcddb2
libcompfaceg1
libcue1
libdca0
libdirectfb-1.2-9
libdvdnav4
libdvdread4
libenca0
libencode-locale-perl
libept1.4.12
libesd0
libexo-1-0
libexo-common
libexo-helpers
libfaad2
libfile-listing-perl
libfluidsynth1
libfm-data
libfm-gtk-data
libfm-gtk1
libfm1
libgif4
libgl1-mesa-dri
libgl1-mesa-glx
libglade2-0
libglapi-mesa
libgmlib0
libgmtk0
libgmtk0-data
libgoffice-0.8-8
libgoffice-0.8-8-common
libgringotts2
libgsf-1-114
libgsf-1-common
libgsm1
libgtkspell0
libguess1
libhtml-parser-perl
libhtml-tagset-perl
libhtml-tree-perl
libhttp-cookies-perl
libhttp-date-perl
libhttp-message-perl
libhttp-negotiate-perl
libid3tag0
libimlib2
libio-socket-ssl-perl
libjavascriptcoregtk-1.0-0
liblaunchpad-integration1
libllvm3.0
libloudmouth1-0
liblwp-mediatypes-perl
liblwp-protocol-https-perl
libmcrypt4
libmenu-cache1
libmms0
libmodplug1
libmowgli2
libmp3lame0
libmpg123-0
libnet-dbus-perl
libnet-http-perl
libnet-ssleay-perl
libnss3-1d
libobrender27
libobt0
libonig2
liboobs-1-5
libopts25
libots0
libpisock9
libpostproc52
libresid-builder0c2a
libschroedinger-1.0-0
libsidplay2
libswscale2
libtar0
libtidy-0.99-0
libtimedate-perl
libts-0.0-0
libuniconf4.6
liburi-perl
libutouch-evemu1
libutouch-frame1
libutouch-geis1
libutouch-grail1
libva1
libvdpau1
libvpx1
libvte-common
libvte9
libwebkitgtk-1.0-0
libwebkitgtk-1.0-common
libwv-1.2-4
libwvstreams4.6-base
libwvstreams4.6-extras
libwww-perl
libwww-robotrules-perl
libxatracker1
libxfce4ui-1-0
libxfce4util-common
libxfce4util4
libxfconf-0-2
libxml-parser-perl
libxml-twig-perl
libxss1
libxvidcore4
lightdm-gtk-greeter
lubuntu-artwork
lubuntu-artwork-12-04
lubuntu-core
lubuntu-default-settings
lubuntu-desktop
lubuntu-icon-theme
lubuntu-software-center
lxappearance
lxappearance-obconf
lxinput
lxkeymap
lxlauncher
lxmenu-data
lxpanel
lxpanel-indicator-applet-plugin
lxrandr
lxsession
lxsession-edit
lxshortcut
lxtask
lxterminal
mplayer2
mtpaint
notification-daemon
ntp
obconf
openbox
osmo
pcmanfm
pidgin
pidgin-data
pidgin-microblog
plymouth-theme-lubuntu-logo
plymouth-theme-lubuntu-text
python-pysqlite2
python-support
python-xklavier
scrot
sylpheed
sylpheed-doc
sylpheed-i18n
sylpheed-plugins
synaptic
system-tools-backends
transmission
tsconf
wvdial
xfburn
xfce-keyboard-shortcuts
xfce4-power-manager
xfce4-power-manager-data
xfconf
xpad
xscreensaver
xscreensaver-data

```

So just save it to a text file like lubuntu-packages.txt and after you reinstall ubuntu-desktop do:
```
cat lubuntu-packages.txt | xargs sudo apt-get -y purge
```
and all the Lubuntu stuff will be removed.

---

### Post by czgirb on 2013-08-29
Wow! If that so ... I choose to run **LiveCD** first.
If it's OK, I will shift to Lubuntu when the **LTS** come out
Thank you everybody

---

### Post by Crusty Old Fart on 2013-08-29
I know that you've already marked this thread as [SOLVED] but there's a better, more reliable, less error prone, and more complete way to take Lubuntu desktop for a test drive, and completely remove it when you're done. Using the method presented below, your computer does most of the work for you, and it will put itself back to the same state it was in before you installed Lubuntu desktop.

**Before** you install Lubuntu desktop, make a list of the package selection states of every package on your computer and save it to your home directory in a file named: **[COLOR=blue]state_before_Lubuntu[/COLOR]**:
```

dpkg --get-selections >**[COLOR=blue]state_before_Lubuntu[/COLOR]**

```
Now you can install Lubuntu desktop and take it for a test drive.

When you're ready to remove it, and put your system back to the way it was before you installed it, you need to set the selection state on the requested packages using the file you created above. You do this with the following two commands:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <**[COLOR=blue]state_before_Lubuntu[/COLOR]**

```
Now that the selection states are set, you can perform the installation with the following command:
```

sudo apt-get dselect-upgrade

```
At this point, all of the changes made, since Lubuntu desktop was installed, have been deinstalled. However, the configuration files have remained. The easiest way to remove them is to set their states to "purge" instead of "deinstall". So, you need to make a new list of the package selection states of every package on your computer and save it to your home directory in a file named: **[COLOR=green]state_after_Lubuntu_deinstall[/COLOR]**:
```

dpkg --get-selections >**[COLOR=green]state_after_Lubuntu_deinstall[/COLOR]**

```
Now, to change all the "deinstall" states to "purge" you run the following command, which performs the edit and saves the result in a file named: **[COLOR=red]state_before_Lubuntu_purge[/COLOR]**
```

cat **[COLOR=green]state_after_Lubuntu_deinstall[/COLOR]** | sed s/deinstall$/purge/ > **[COLOR=red]state_before_Lubuntu_purge[/COLOR]**

```
You now have a file that you can use to set the selection state on the requested packages, as follows:
```

sudo dpkg --clear-selections
sudo dpkg --set-selections <**[COLOR=red]state_before_Lubuntu_purge[/COLOR]**

```
And then perform the installation:
```

sudo apt-get dselect-upgrade

```

Finally, after making so many changes, a little bit of housekeeping might help the computer boot without hurling its lunch:
```

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get clean
sudo apt-get autoremove
sudo dpkg --configure -a
sudo update-initramfs -k all -u
sudo update-grub

```

That's it, all done.

A few final comments:
Earlier this week, I took Xubuntu desktop for a test drive for two days and when I was finished, I put my system right back to the way it was before the ride. I used the exact method described above. It was fast, easy and it worked perfectly. I liked the test drive enough that I'm putting together plans to install Xubuntu as my main Linux OS.

---

