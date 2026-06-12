---
title: "Build Package From Source"
date: 2012-02-24
forum: Programming Talk
---

### Post by ryanrio95 on 2012-02-24
Hi.

If i want for example build gnome-control-center from scratch.
How can i do this?
If i extract the source tar.gz in an directory.
Could i build from that directory to an deb file?

Please help me.

Regards, Ryan.

---

### Post by agillator on 2012-02-24
This link should get you going. It tells you how to install the things you need and then how to compile a program.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by ryanrio95 on 2012-02-24
Thanks, but i have a problem.
There is no makefile in the gnome-control-center source.
And there are two tar.gz files. The ubuntu one with DEBIAN package files and patches and the original source.

Regards

---

### Post by agillator on 2012-02-24
Are you trying to compile the source code specific to Ubuntu, or the generic source code? I don't know what the differences are, if any. However, the first step in compilation is to configure it, i.e. run ./configure in the source code directory. That should create the makefile for you, I believe. The instructions for the generic source, which can be found here among other places: [http://linux.softpedia.com/get/Desktop-Environment/Gnome/Gnome-Control-Center-28148.shtml](http://linux.softpedia.com/get/Desktop-Environment/Gnome/Gnome-Control-Center-28148.shtml), say to run configure then make then make install like most packages. I haven't seen the instructions for the version specific to Ubuntu. So what happens if you extract your package, move to the source directory and run ./configure, then make, then (if make runs, of course) sudo make install? Does make not run?

---

### Post by ryanrio95 on 2012-02-24
i already ran the ./configure command
but after that,  the make command said that there is no makefile
i will try further tommorow

regards

---

### Post by pbrane on 2012-02-24
> **ryanrio95 said:**
> i already ran the ./configure command
but after that,  the make command said that there is no makefile
i will try further tommorow

regards

You should look closely at the output from the ./configure command. It probably failed, which is why you have no make file.

---

### Post by MadCow108 on 2012-02-25
```
sudo apt-get build-dep gnome-control-center
apt-get source gnome-control-center --compile
```

---

### Post by ryanrio95 on 2012-02-26
with ./configure
i got this error:

configure: error: Package requirements (gtk+-3.0 >= 3.1.19
 glib-2.0 >= 2.29.14
 gthread-2.0
 gio-2.0
 gio-unix-2.0
 gsettings-desktop-schemas >= 3.0.2
 libnotify >= 0.7.3 gconf-2.0) were not met:

No package 'gsettings-desktop-schemas' found
No package 'libnotify' found
No package 'gconf-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBGNOME_CONTROL_CENTER_CFLAGS
and LIBGNOME_CONTROL_CENTER_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

---

### Post by Barrucadu on 2012-02-26
Try installing gsettings-desktop-schemas, libnotify, and gconf-2.0.

---

### Post by ryanrio95 on 2012-02-26
I can't find the package libnotify.

Regards.

---

### Post by agillator on 2012-02-26
Now you are running into the reason many do NOT try to compile from source but use the distribution packages. Each of the packages listed in the error message from your ./configure run needs to be installed. For the libnotify you couldn't find, do a google search for 'ubuntu libnotify' and follow the links to the version of ubuntu you are using and you will find the source file, which, of course, needs to be compiled. I have no idea how many packages it requires that you naturally don't have installed because you otherwise don't need them. But, it is a vicious cycle. EVENTUALLY you can get everything you need, but sometimes it is a real pain and not worth the effort or the time. 

You can, however, do a sudo apt-get install libnotify-bin, or you can use the synaptic package manager to install libnotify-bin and probably libnotify-dev if there is one. Synaptic is often the easiest. 

At this point I will ask if you really think building gnome-control-center from scratch is really necessary or worth the effort? If it is, forge on. If not . . . . Perhaps there is an easier way to get where you want to go?

---

### Post by MG&amp;TL on 2012-02-27
```
michael@laptop-testing:~$ apt-cache search libnotify
firefox-gnome-support - Safe and easy web browser from Mozilla - GNOME support
libnotify-bin - sends desktop notifications to a notification daemon (Utilities)
libnotify-dev - sends desktop notifications to a notification daemon (Development files)
libnotify-doc - sends desktop notifications to a notification daemon (Documentation)
libnotify4 - sends desktop notifications to a notification daemon
pidgin-libnotify - display notification bubbles in pidgin
python-notify - Python bindings for libnotify
thunderbird-gnome-support - Email, RSS and newsgroup client - GNOME support
evolution-indicator - GNOME panel indicator applet for Evolution
awn-applet-awn-notification-daemon - Libnotify notification daemon implementation for Awn
clementine - modern music player and library organizer
libdesktop-notify-perl - Perl module which communicates with the Desktop Notifications framework
libgtk2-notify-perl - Perl interface to libnotify
libnotify-cil-dev - CLI library for desktop notifications
libnotify0.4-cil - CLI library for desktop notifications
mango-lassi - Share mouse and pointer with other computers
seamonkey-gnome-support - Seamonkey client - GNOME support
vlc-plugin-notify - LibNotify plugin for VLC
michael@laptop-testing:~$ 


```you want the libnotify-dev package.


If you have good reason for compiling from source, please do so. :) Otherwise, use ubuntu packages.

---

