---
title: "lubuntu to ubuntu"
date: 2012-06-07
forum: New to Ubuntu
---

### Post by sengpoi on 2012-06-07
Now here's the problem,
I had windows xp sp3 installed on my laptop and wanted to install fresh copy of ubuntu 12.04.

I have both Ubuntu 12.04 and Lubuntu 12.04 burned into cd but Ubuntu 12.04 requires the CPU to have the pae feature and my acer travelmate doesn't support it, therefore i need to install Lubuntu first since it doesn't require pae by default and i can manually install ubuntu using lubuntu.

And I've installed Lubuntu 12.04, and tried to install ubuntu via lubuntu by using > sudo apt-get install ubuntu-desktop on the terminal.

I thought i would get a fresh new ubuntu by using this method, but all i had was ubuntu on the previously installed lubuntu.

I even tried using wubi.exe (using wine), but the maximum partition distribution i can get is the free space of the current hard disk, not the whole space i would get from a fresh copy of an os.

I've been figuring this thing out since yesterday, can some ubuntu guru help me, please :cry:? I'm starting on ubuntu over windows xp on my old laptop since it's getting slower and slower, and i prefer the unity (of ubuntu)over the LXDE (of lubuntu).

---

### Post by Paqman on 2012-06-07
> **sengpoi said:**
> 
I thought i would get a fresh new ubuntu by using this method, but all i had was ubuntu on the previously installed lubuntu.


You can uninstall all the Lubuntu components with this command:
```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg docbook-xml elementary-icon-theme esound-common galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0 libabiword-2.9 libass4 libaudclient2 libaudcore1 libaudiofile1 libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libencode-locale-perl libept1.4.12 libesd0 libexo-1-0 libexo-common libexo-helpers libfaad2 libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4 libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmcrypt4 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libnss3-1d libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libpostproc52 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsidplay2 libsocket6-perl libswscale2 libtar0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libts-0.0-0 libuniconf4.6 liburi-perl libva1 libvdpau1 libvpx1 libvte-common libvte9 libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1 libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-headers-generic lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sgml-data sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter

```

---

### Post by snowpine on 2012-06-07
Unity, LXDE, KDE, Xfce, etc. are simply desktop environments or "skins." Ubuntu is still Ubuntu no matter which desktop environment you're using; giving them different names is simply a marketing tactic. You can have both LXDE and Unity installed and switch back and forth between them depending on your mood that day. If you want to completely uninstall LXDE then see Paqman's post above.

---

### Post by sengpoi on 2012-06-07
```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg docbook-xml elementary-icon-theme esound-common galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0 libabiword-2.9 libass4 libaudclient2 libaudcore1 libaudiofile1 libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libencode-locale-perl libept1.4.12 libesd0 libexo-1-0 libexo-common libexo-helpers libfaad2 libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4 libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmcrypt4 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libnss3-1d libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libpostproc52 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsidplay2 libsocket6-perl libswscale2 libtar0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libts-0.0-0 libuniconf4.6 liburi-perl libva1 libvdpau1 libvpx1 libvte-common libvte9 libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1 libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-headers-generic lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sgml-data sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter

```
does this uninstall the packages one by one? and when i reboot, will i be greeted with ubuntu or lubuntu page ? thx:lolflag:

---

### Post by snowpine on 2012-06-07
> **sengpoi said:**
> ```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg docbook-xml elementary-icon-theme esound-common galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-status-provider-pidgin leafpad libaacs0 libabiword-2.9 libass4 libaudclient2 libaudcore1 libaudiofile1 libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libdvdnav4 libdvdread4 libenca0 libencode-locale-perl libept1.4.12 libesd0 libexo-1-0 libexo-common libexo-helpers libfaad2 libfile-listing-perl libfluidsynth1 libfm-data libfm-gtk-data libfm-gtk1 libfm1 libfont-afm-perl libgdome2-0 libgdome2-cpp-smart0c2a libgif4 libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgringotts2 libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libhtml-form-perl libhtml-format-perl libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libhttp-cookies-perl libhttp-daemon-perl libhttp-date-perl libhttp-message-perl libhttp-negotiate-perl libid3tag0 libimlib2 libio-socket-inet6-perl libio-socket-ssl-perl libjavascriptcoregtk-1.0-0 libjpeg-progs libjpeg-turbo-progs liblaunchpad-integration1 liblink-grammar4 libloudmouth1-0 liblwp-mediatypes-perl liblwp-protocol-https-perl libmailtools-perl libmcrypt4 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libnet-dbus-perl libnet-http-perl libnet-ssleay-perl libnss3-1d libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libpostproc52 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsidplay2 libsocket6-perl libswscale2 libtar0 libtidy-0.99-0 libtie-ixhash-perl libtimedate-perl libts-0.0-0 libuniconf4.6 liburi-perl libva1 libvdpau1 libvpx1 libvte-common libvte9 libwebcam0 libwebkitgtk-1.0-0 libwebkitgtk-1.0-common libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libwww-perl libwww-robotrules-perl libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util4 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxss1 libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic linux-headers-generic lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-04 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes osmo pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sgml-data sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf ttf-lyx uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter

```
does this uninstall the packages one by one? and when i reboot, will i be greeted with ubuntu or lubuntu page ? thx:lolflag:

The page that greets you when you reboot is just artwork. Probably there is a way to change it, but it doesn't really matter. ;) The desktop environment is not selected until the login screen.

---

### Post by sengpoi on 2012-06-07
Oh, thanks very much !:p

and i've been wondering about how my lubuntu can't boot properly.
when i reboot the laptop, it will always stuck before the lubuntu logo comes up, i had to turn off the power and starting again,which will let me choose to whether generic mode or recovery mode.when i chooses generic mode, it starts up normally and it happens again when i reboot the laptop.

does this have anything to with bad installation or hardware problems ?

sorry if it's hard to understand me,cause english is not mother tongue.

---

### Post by snowpine on 2012-06-07
Your English is fine. :)

Do I understand: You can boot OK, but your system freezes on reboot? 

I do not know the answer; you can start a new thread for that topic and someone will help you. :)

---

### Post by sengpoi on 2012-06-07
> 
Do I understand: You can boot OK, but your system freezes on reboot? 

I mean it freezes after the boot options and doesn't even show the greeting page(is that what it's called ? o.0),and the whole screen is black without any sign of booting to the os.

---

### Post by Paqman on 2012-06-07
> **sengpoi said:**
> I mean it freezes after the boot options and doesn't even show the greeting page(is that what it's called ? o.0),and the whole screen is black without any sign of booting to the os.

Does this happen every time you try to boot?

---

### Post by sengpoi on 2012-06-07
yes, the only time I can boot properly is by shutting down forcefully by plugging off and start again,and reaching the recovery mode (kinda like start windows normally in windows ?).Only then i can reach the greeting page. Maybe it's a lubuntu bug, since i uninstalled the whole lubuntu package using your code, this problem doesn't arouses anymore. Ubuntu boots up nicely without any glitch.

---

### Post by Paqman on 2012-06-07
> **sengpoi said:**
> since i uninstalled the whole lubuntu package using your code, this problem doesn't arouses anymore. Ubuntu boots up nicely without any glitch.

Ah, right. Problem fixed then. I'm not sure if it was a bug as such, or just something misconfigured on your system, but either way I'm glad it's sorted.

---

### Post by sengpoi on 2012-06-07
yeah, maybe i made a mistake while installing it. Thank you very much for the command.:)

Oh and 1 more thing, if i reinstall lubuntu from the start and uses the command u gave right off, will that give me Ubuntu as well ?

---

### Post by Paqman on 2012-06-08
> **sengpoi said:**
> 
Oh and 1 more thing, if i reinstall lubuntu from the start and uses the command u gave right off, will that give me Ubuntu as well ?

Yes, although there would be easier ways to install. You could use the [minimal image]("https://help.ubuntu.com/community/Installation/MinimalCD") and then install ubuntu-desktop.

---

### Post by sengpoi on 2012-06-08
> **Paqman said:**
> Yes, although there would be easier ways to install. You could use the [minimal image]("https://help.ubuntu.com/community/Installation/MinimalCD") and then install ubuntu-desktop.

What does the PowerPC do ?
How is it different from the usual version ? The only difference i can see is the size.

---

### Post by Paqman on 2012-06-08
> **sengpoi said:**
> What does the PowerPC do ?
How is it different from the usual version ? The only difference i can see is the size.

Don't worry about that. It's a computer architecture used on old Apple Macs and some servers and embedded devices. Unless you've got a really old Mac you don't have a PowerPC machine. You probably want the 32-bit x86 download.

---

### Post by sengpoi on 2012-06-08
> **Paqman said:**
> Don't worry about that. It's a computer architecture used on old Apple Macs and some servers and embedded devices. Unless you've got a really old Mac you don't have a PowerPC machine. You probably want the 32-bit x86 download.

Okay, thanks so much for the help. Gonna try it out when i have the free time. =)

---

