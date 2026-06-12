---
title: "'meld' insane dependencies?"
date: 2007-04-22
forum: Programming Talk
---

### Post by jjalocha on 2007-04-22
Meld is a visual diff and merge tool. There's an Ubuntu package available.

But I don't understand why 'aptitude' wants to install so many (multimedia!!!) packages, even if my system is up-to-date. 

```

$ sudo aptitude install meld
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following NEW packages will be automatically installed:
  esound-clients esound-common gnome-media gnome-media-common gstreamer0.10-alsa 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x libaudiofile0 
  libavc1394-0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcaca0 
  libcdio6 libcucul0 libdv4 libesd-alsa0 libgda2-3 libgda2-bin libgda2-common libgdl-1-0 
  libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-desktop-2 libgnome-media0 
  libgnome2-0 libgnome2-common libgnomeui-0 libgnomeui-common libgtksourceview-common 
  libgtksourceview1.0-0 libiec61883-0 libmetacity0 libnautilus-burn4 liboil0.3 
  libpanel-applet2-0 libraw1394-8 libshout3 libtotem-plparser1 libvisual-0.4-0 
  libvisual-0.4-plugins libvorbisenc2 metacity-common oss-compat python-gnome2 
  python-gnome2-desktop python-gnome2-extras python-gnomecanvas 
The following NEW packages will be installed:
  esound-clients esound-common gnome-media gnome-media-common gstreamer0.10-alsa 
  gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-x libaudiofile0 
  libavc1394-0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcaca0 
  libcdio6 libcucul0 libdv4 libesd-alsa0 libgda2-3 libgda2-bin libgda2-common libgdl-1-0 
  libgdl-1-common libgksu1.2-1 libgksuui1.0-1 libgnome-desktop-2 libgnome-media0 
  libgnome2-0 libgnome2-common libgnomeui-0 libgnomeui-common libgtksourceview-common 
  libgtksourceview1.0-0 libiec61883-0 libmetacity0 libnautilus-burn4 liboil0.3 
  libpanel-applet2-0 libraw1394-8 libshout3 libtotem-plparser1 libvisual-0.4-0 
  libvisual-0.4-plugins libvorbisenc2 meld metacity-common oss-compat python-gnome2 
  python-gnome2-desktop python-gnome2-extras python-gnomecanvas 
0 packages upgraded, 52 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.4MB of archives. After unpacking 58.8MB will be used.
Do you want to continue? [Y/n/?] n
Abort.

```

---

### Post by engla on 2007-04-22
You don't use Ubuntu/gnome right? That package depends on python-gnome2 which in turn depends on lots of things in gnome etc.. hence the large collection of packages of all types. So to use this package, you basically have to install lots of "gnome backend" things.

---

### Post by jjalocha on 2007-04-22
Thanks, engla, you're right, I'm using Xubuntu. I'll dig into this. I think I'll contact the developers about it, too.

---

