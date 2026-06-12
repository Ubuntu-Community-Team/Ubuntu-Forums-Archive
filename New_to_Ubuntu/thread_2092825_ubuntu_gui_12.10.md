---
title: "ubuntu gui 12.10"
date: 2012-12-08
forum: New to Ubuntu
---

### Post by loloko29 on 2012-12-08
hi guys, i am new to this ubuntu OS. i just want to try it for additional knowledge on computers. 
my problem is that, GUI is crashing. i can't really explain it. its like the desktop is changing its color and the icons doesn't really appear. 
i tried 12.10 when i thought that its working quite well, i clicked on the dash home, and boom, it hanged. gui crashed and needed to restart. after that, i can't really use it.

second time, i installed 12.04.. all i get is black screen and a little of its desktop background.

what seems to be the problem?
i only have on-board video card, maybe that's it?
also, when i booted the 12.04 "out of range" prompted in the monitor.
pls help. i really want to try ubuntu.. thanks.

---

### Post by debodas on 2012-12-08
First up, well done on wanting to try Ubuntu - once you get it working you'll find its great!

Try typing 'unity --reset' into the terminal. If that doesn't work type this into the terminal (first one, run that, then the second one, run that, then the third one and run that).
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
sudo apt-get install unity

This will reinstall unity. 
If neither of these work, could easily be a graphics problem, but try this first.

---

### Post by johnycsf on 2012-12-08
I experienced problems with colors on my machine as well but after I updated the system everything worked fine. 
Also check if you have the proper drivers installed for your video card. It may need  proprietary driver from the manufacturer.
The out of range problem during the boot. To fix that boot on to ubuntu and go to software center and search for "Session and Startup" download and install 
Open it and change the resolution!

Hope it helps!

---

### Post by loloko29 on 2012-12-09
thank you for the tips, but that is where my problem is occurring, that "terminal"
where can i find it? i found one on google, but i cannot access that because when i click "dash home" it crashes then all i can see is random colors.
if pressing the "windows button" in the keyboard is another way, or i think it is, it does not work too.
i will try to install it again and do what both of you have said, does ubuntu require a video card? my on-board is updated, also i've seen settings that makes the display driver in the "propriety" thing. but it does not change anything in the GUI.
also i want to ask, what version fits a 64bit pc? maybe it has something to do with that. thank you!

---

### Post by debodas on 2012-12-09
Crl + Alt + t will open the terminal without opening dash.

edit - Once you've opened the terminal by using the Crl + Alt + t shortcut, type ```
sudo apt-get install xfce4
``` into the terminal and hit enter. Once that has finished running, type ```
sudo apt-get install xfce4-goodies
``` into the terminal and hit enter. Then, once this has finished running, shut down and bott up again.

 At the login screen, in the top right corner of the login box there should be a circle with the ubuntu symbol (like the dash symbol). Click on that, and select xfce, then click ok and enter your password and login. This will boot you into xfce (which you installed just before via the terminal). Xfce should be stable, so you can go about fixing unity from there without the worry of it crashing.

If you ever want to uninstall Xfce, type ```
sudo apt-get remove abiword abiword-common abiword-plugin-grammar abiword-plugin-mathview ace-of-penguins audacious audacious-plugins audacious-plugins-data blueman catfish chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg elementary-icon-theme fonts-lyx galculator gdebi gdebi-core gecko-mediaplayer giblib1 gnome-desktop-data gnome-icon-theme-full gnome-mplayer gnome-system-tools gnome-time-admin gnumeric gnumeric-common gnumeric-doc gpicview gtk2-engines-pixbuf guvcview hardinfo indicator-application-gtk2 leafpad libaacs0 libabiword-2.9 libass4 libaudclient2 libaudcore1 libavcodec53 libavformat53 libavutil51 libbinio1ldbl libbluray1 libbs2b0 libcddb2 libcolamd2.7.1 libcompfaceg1 libcue1 libdca0 libdirectfb-1.2-9 libenca0 libept1.4.12 libexo-1-0 libexo-common libexo-helpers libfaad2 libfluidsynth1 libfm-data libfm-gtk-bin libfm-gtk-data libfm-gtk3 libfm3 libgdome2-0 libgdome2-cpp-smart0c2a libglade2-0 libgmlib0 libgmtk0 libgmtk0-data libgoffice-0.8-8 libgoffice-0.8-8-common libgsf-1-114 libgsf-1-common libgsm1 libgtkmathview0c2a libgtkspell0 libguess1 libid3tag0 libimlib2 libindicate-gtk3 libjpeg-progs libjpeg-turbo-progs liblink-grammar4 libloudmouth1-0 libmenu-cache1 libmms0 libmodplug1 libmowgli2 libmp3lame0 libmpg123-0 libmusicbrainz3-6 libnet-dbus-perl libobrender27 libobt0 libonig2 liboobs-1-5 libopts25 libots0 libpisock9 libpostproc52 librarian0 libresid-builder0c2a libschroedinger-1.0-0 libsdl1.2debian libsidplay2 libswscale2 libtidy-0.99-0 libtie-ixhash-perl libts-0.0-0 libuniconf4.6 libva1 libvdpau1 libvpx1 libvte-common libvte9 libwebcam0 libwv-1.2-4 libwvstreams4.6-base libwvstreams4.6-extras libxfce4ui-1-0 libxfce4util-bin libxfce4util-common libxfce4util6 libxfconf-0-2 libxml-parser-perl libxml-twig-perl libxml-xpath-perl libxvidcore4 lightdm-gtk-greeter link-grammar-dictionaries-en lm-sensors lp-solve lubuntu-artwork lubuntu-artwork-12-10 lubuntu-core lubuntu-default-settings lubuntu-desktop lubuntu-icon-theme lubuntu-lxpanel-icons lubuntu-software-center lxappearance lxappearance-obconf lxinput lxkeymap lxlauncher lxmenu-data lxpanel lxpanel-indicator-applet-plugin lxrandr lxsession lxsession-data lxsession-edit lxshortcut lxtask lxterminal mplayer2 mtpaint ntp obconf openbox openbox-themes pcmanfm pidgin pidgin-data pidgin-libnotify pidgin-microblog plymouth-theme-lubuntu-logo plymouth-theme-lubuntu-text python-pysqlite2 python-support python-xklavier rarian-compat scrot sylpheed sylpheed-doc sylpheed-i18n sylpheed-plugins synaptic system-tools-backends transmission tsconf uvcdynctrl uvcdynctrl-data wvdial xfburn xfce-keyboard-shortcuts xfce4-notifyd xfce4-power-manager xfce4-power-manager-data xfconf xfonts-100dpi xpad xscreensaver xscreensaver-data && sudo apt-get install ubuntu-desktop && sudo /usr/lib/lightdm/lightdm-set-defaults -g unity-greeter
```into the terminal and hit enter, then follow the prompts.

Note - none of this will fix unity, but installing xfce gives you a stable platform on which to do so.

---

