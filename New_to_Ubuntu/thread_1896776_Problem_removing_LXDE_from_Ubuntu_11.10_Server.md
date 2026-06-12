---
title: "Problem removing LXDE from Ubuntu 11.10 Server"
date: 2011-12-17
forum: New to Ubuntu
---

### Post by kapsklok on 2011-12-17
Hello, I have the Ubuntu 11.10 Server edition installed on my PC and installed Fluxbox. Then I decided to try out LXDE, and installed it along with Fluxbox, but don't like lxde as much
I have tried uninstalling LXDE using
```

apt-get remove lxde
apt-get autoremove

```
as I found searching the internet. However, this did not work, as when I startx without an .xinitrc, LXDE runs without a cursor or icons.
Any help in completely removing LXDE would be appriciated.

---

### Post by mikewhatever on 2011-12-17
Here is the list of packages lxde pulls in, so:

```
sudo apt-get purge arj galculator giblib1 gpicview leafpad libfm-data libfm-gtk-data libfm-gtk1 \
libfm1 libimlib2 libjpeg-progs libmenu-cache1 libobrender27 libobt0 librpm2 \
librpmbuild2 librpmio2 librpmsign0 libxmmsclient-glib1 libxmmsclient6 \
lxappearance lxde lxde-common lxde-core lxde-icon-theme lxinput lxmenu-data \
lxmusic lxpanel lxrandr lxsession lxsession-edit lxshortcut lxterminal menu \
menu-xdg obconf openbox openbox-themes p7zip-full pcmanfm rpm rpm-common \
rpm2cpio scrot xarchiver xmms2-core xmms2-plugin-alsa xmms2-plugin-id3v2 \
xmms2-plugin-mad xmms2-plugin-vorbis xscreensaver xscreensaver-data
```

---

### Post by kapsklok on 2011-12-17
Thank you very much, it worked, but I'm not sure why I didn't think of this

---

