---
title: "GNOME Shell"
date: 2011-05-04
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Merk42 on 2011-05-04
**BACK YET AGAIN BY REQUEST**

[b]This thread is for testing support and technical discussion.
Opinions should go to the [Community Cafe thread]("http://ubuntuforums.org/showthread.php?t=1457428") or ideally [the GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")[/b].

With a lot of people dissatisfied with Unity this thread is showing the other new UI, GNOME Shell

**What is GNOME Shell?**
GNOME Shell, for those of you that do not know, is a user interface change to GNOME. With it, brings Mutter a combination of Metacity and Clutter, managing the windows. Say goodbye to compiz as it won't be compatible.

GNOME Shell was released as **one part of GNOME 3** in April of 2011 it [is not the default UI in 11.04+]("http://www.youtube.com/watch?v=YUAzicy_01o#t=17m40s"), that's [Unity](http://unity.ubuntu.com/), though GNOME Shell should still be an optional package going forward.

**What does it look like?**
Here is GNOME Shell. 
[IMG]http://www.markecurtis.com/etc/gnomeshell/gnomeshell.png[/IMG]

The active application near "Activities" has a menu upon clicking. Clicking on the date or username provide a calendar and menu respectively
[IMG]http://www.markecurtis.com/etc/gnomeshell/menus.png[/IMG]

Currently some applications are open but hidden. Where are they?
This is the Activities overview, where you run and manage "Activities"
[IMG]http://www.markecurtis.com/etc/gnomeshell/overview.png[/IMG]

More applications can be run either by searching for the name in "Type to search...", or in this case, clicking the word applications
[IMG]http://www.markecurtis.com/etc/gnomeshell/moreapplications.png[/IMG]

One extra blank workspace is create by default. If an application is put onto that blank workspace, one more blank workspace will be created. The thumbnails on the right, viewable upon hover, let you switch among them. New applications can be opening onto specific workspaces by dragging the launcher to the workspace thumbnail on the right.
[IMG]http://www.markecurtis.com/etc/gnomeshell/add.png[/IMG]

Oh look, an instant message! Unlike the passive notify-OSD, clicking on this will bring up the window
[IMG]http://www.markecurtis.com/etc/gnomeshell/messages.png[/IMG]

If no action is taken, it resides in the lower right, viewable upon hover.
[IMG]http://www.markecurtis.com/etc/gnomeshell/messageexpand.png[/IMG]


**OMG GNOME SHELL IS AWFUL AND I HATE UNITY! I'm moving to xfce/Windows/an abacus**
Calm down. Look at the [GNOME 3 Myths]("http://live.gnome.org/GNOME3Myths")
> **MYTH: GNOME won't support the current panel and window manager anymore and I don't want to use GNOME Shell**

**TRUTH: The GNOME 2.x panel and Metacity (the window manager) will still be available.**
Downstream distributions such as Fedora, openSUSE and Ubuntu will have the option to include them in their distribution. You will be able to install them just as now you can install sawfish, compiz, etc inside your GNOME session. (There are no plans to support GNOME panel applets in GNOME Shell, TBA. This mailing list post has some information.) 


**How do I Learn More?**
[LIST]
[*]GNOME 3's website, [gnome3.org]("http://gnome3.org/").  It shows various parts of GNOME Shell, with videos!
[*]For something smaller, look at [this brief synopsis]("http://gnomejournal.org/article/85/easy-breezy-beautiful-gnome-shell") on GNOME Shell.
[*]Look at the [GNOME Shell cheat sheet]("http://live.gnome.org/GnomeShell/CheatSheet") for features.
[/LIST]

**How do I Try it?**

There are three ways to try GNOME Shell
[LIST]
[*]Build from source (recommended, as it provides the most recent version, though may occasionally break)
[*]Install the gnome-shell package (easy but out of date)
[*]**For Natty Narwhal Only** Use the [Ricotz PPA]("http://ubuntu-tweak.com/source/gnome-shell-testing/") (slightly harder, but more up to date)
[/LIST]
**As of Virtualbox 4.0 GNOME Shell will run in a virtual machine, but very slowly and glitchy, to the point of unusable**

Building from source is a bit more complicated than the GNOME instructions say. So fire up a terminal
```

sudo apt-get install curl libtiff4-dev libgstreamer0.10-dev libcroco3-dev xserver-xephyr xulrunner-dev python-dev mesa-utils mesa-common-dev libreadline5-dev libgl1-mesa-dev libwnck-dev librsvg2-dev libgnome-desktop-dev libgnome-menu-dev libffi-dev libgtk2.0-dev libgconf2-dev libdbus-glib-1-dev gtk-doc-tools gnome-common git-core flex bison automake build-essential icon-naming-utils libpulse-dev libcanberra-dev autopoint libjasper-dev libvorbis-dev libpam-dev libxklavier-dev libgnome-keyring-dev libupower-glib-dev libgtop2-dev libcups2-dev evolution-data-server-dev libsqlite3-dev libproxy-dev libdb-dev libproxy-dev
```
```
curl -O http://git.gnome.org/browse/gnome-shell/plain/tools/build/gnome-shell-build-setup.sh
```
```
/bin/bash gnome-shell-build-setup.sh
```
Get jhbuild (not a command line entry)
[LIST]
[*]For Lucid, Maverick, Natty via repository, package name "jhbuild".
[*][From Jaunty]("http://packages.ubuntu.com/en/jaunty/jhbuild")
[*][From Debian]("http://packages.debian.org/unstable/devel/jhbuild")
[/LIST]
```
jhbuild build
```


**IF YOU HAVE TROUBLE BUILDING**
**Hey it keeps "hanging up unexpectedly"**
Quit building and run
```
 pushd ~/gnome-shell/source/ && git clone git://git.gnome.org/gtk+ gtk3 && popd
``` then re run jhbuild build

**I'm getting a lot of "undefined reference" errors**
try ```
rm ~/gnome-shell/install/*.la && sudo rm -rf /usr/lib*/*.la
```
Then jhbuild build
If it still doesn't work, delete the ~/gnome-shell folder and try again

**I'm getting an error regarding libcanberra-gtk-module.so: undefined symbol: gtk_quit_add**
It's a known bug, just delete the file libcanberra-gtk-module.so


**Yay! It's finally done building! Now what?**
To run
[LIST=1]
[*]cd ~/gnome-shell/source/gnome-shell/src
[*]./gnome-shell --replace
[/LIST]

To quit GNOME Shell and return to the panels
[list=1[*]Go to the terminal
[*]hit CTRL-C[/list]

To update (check the [commit log]("http://git.gnome.org/browse/gnome-shell") for anything new)
[LIST]
[*]jhbuild build (rebuilds updated files)
[*]jhbuild build -f -a -c (builds all gnome shell files)
[/LIST]

To remove (if you want to do a clean install, or just remove it because you don't like it)
[LIST]
[*]Delete the folder gnome-shell in your home directory (assumes build from source)
[/LIST]

If you want to make it your default, put "gnome-shell --replace" in your Startup Items

**Love it? Hate it? Have a suggestion? Make your voice heard in the [GNOME Shell mailing list]("http://mail.gnome.org/mailman/listinfo/gnome-shell-list")**

---

