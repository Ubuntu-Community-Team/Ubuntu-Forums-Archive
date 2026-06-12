---
title: "hal missing?"
date: 2009-07-05
forum: Programming Talk
---

### Post by WitchCraft on 2009-07-05
Question: I wanted to compile gnome-network manager applet

It's a ./configure, make, make install process.
Of course it's missing dependencies, and so far I managed to get almost all the dependencies.

However, now it's complaining about hal not found, though hal is installed, obviously...


> 
checking for HAL... configure: error: Package requirements (hal >= 0.5.0) were not met:

No package 'hal' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables HAL_CFLAGS
and HAL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

What's the matter?

---

### Post by PmDematagoda on 2009-07-05
> **WitchCraft said:**
> Question: I wanted to compile gnome-network manager applet

It's a ./configure, make, make install process.
Of course it's missing dependencies, and so far I managed to get almost all the dependencies.

However, now it's complaining about hal not found, though hal is installed, obviously...


What's the matter?

Did you install the development files for HAL? That's probably what you need.

---

### Post by WitchCraft on 2009-07-05
never mind...

```

[apt-get install libiw-dev]("http://packages.debian.org/sid/libiw-dev")
apt-get install libhal-dev
apt-get install libdbus-1-dev
apt-get install libnl-dev
apt-get install ppp-dev
 apt-get install libpolkit-gnome-dev

```

---

### Post by WitchCraft on 2009-07-05
I've now successfully compiled and installed it, even completely restarted, but the applet is still missing from the gnome panel.

It disappeared one month ago (update), and never came back.

In the meantime I'm using knetworkmanager, but that's really annoying...

Anybody knows what the problem is?

---

### Post by PmDematagoda on 2009-07-06
Tried running with:-
```
nm-applet
```
?

The applet isn't really an applet that can just be added to the panel, it's part of the notification area and hence is just a normal program.

---

### Post by WitchCraft on 2009-07-07
> **PmDematagoda said:**
> Tried running with:-
```
nm-applet
```
?

The applet isn't really an applet that can just be added to the panel, it's part of the notification area and hence is just a normal program.

all:~# nm-applet
bash: nm-applet: command not found
all:~#


Edit: ah, apt-file search nm-applet revealed the problem:
```

apt-get install network-manager-gnome

```

How the hell on earth did it get uninstalled ? ...
Anyway, problem solved.

---

