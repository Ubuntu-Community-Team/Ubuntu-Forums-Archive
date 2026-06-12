---
title: "[SOLVED] Where are the plasmoids?"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by tarahmarie on 2008-09-08
Here's something I don't understand: where are the widgets? On the KDE site at [http://techbase.kde.org/Projects/Plasma/Plasmoids](http://techbase.kde.org/Projects/Plasma/Plasmoids) , it says that a given widget (like Binary Clock) is located at: /KDE/kdeplasma-addons/applets/binary-clock. I've used the locate command to try to find any directory with binary-clock in it, and there isn't one. Where are these plasmoids/widgets ACTUALLY located?

---

### Post by marsmissionaries on 2008-09-08
> **tarahmarie said:**
> Here's something I don't understand: where are the widgets? On the KDE site at [http://techbase.kde.org/Projects/Plasma/Plasmoids](http://techbase.kde.org/Projects/Plasma/Plasmoids) , it says that a given widget (like Binary Clock) is located at: /KDE/kdeplasma-addons/applets/binary-clock. I've used the locate command to try to find any directory with binary-clock in it, and there isn't one. Where are these plasmoids/widgets ACTUALLY located?

The above information is for SVN.

The above information was found on techbase which is a developer resource. Plasmoids can be found on [http://kde-look.org](http://kde-look.org) or if you know how to use SVN they can be compiled.

---

### Post by tarahmarie on 2008-09-08
> **marsmissionaries said:**
> The above information is for SVN.

The above information was found on techbase which is a developer resource. Plasmoids can be found on [http://kde-look.org](http://kde-look.org) or if you know how to use SVN they can be compiled.

So I tried to download the Debian package for Quick Access (apparently the most common and popular widget on the site); Firefox saw the .deb extension, and gave me the option to install using the package installer.  I tried that, I tried compiling it myself with cmake, and nothing seems to work.  How does one install this (or any) widget?

---

### Post by benerivo on 2008-09-08
Open a terminal and type```
sudo dpkg -i /home/me/Desktop/plasmoid.deb
``` as a shortcut you can drag the icon in to the terminal instead of typing out the full location.

---

### Post by tarahmarie on 2008-09-08
> **benerivo said:**
> Open a terminal and type```
sudo dpkg -i /home/me/Desktop/plasmoid.deb
``` as a shortcut you can drag the icon in to the terminal instead of typing out the full location.

So I did that, and after updating the db, I find that using "locate quicklauncher" gives me this:

tarahmarie@tarahmarie-desktop:~$ sudo dpkg -i /home/tarahmarie/Desktop/plasma-applet-quicklauncher_0.4-1_i386.deb
[sudo] password for tarahmarie:
Selecting previously deselected package plasma-applet-quicklauncher.
(Reading database ... 115196 files and directories currently installed.)
Unpacking plasma-applet-quicklauncher (from .../plasma-applet-quicklauncher_0.4-1_i386.deb) ...
Setting up plasma-applet-quicklauncher (0.4-1) ...
tarahmarie@tarahmarie-desktop:~$ sudo updatedb
tarahmarie@tarahmarie-desktop:~$ locate quicklauncher
/home/tarahmarie/.kde4/share/apps/RecentDocuments/plasma-applet-quicklauncher_0.4-1_i386.deb.desktop
/home/tarahmarie/.local/share/Trash/files/plasma-applet-quicklauncher_0.4-1_i386.deb
/home/tarahmarie/.local/share/Trash/info/plasma-applet-quicklauncher_0.4-1_i386.deb.trashinfo
/home/tarahmarie/Desktop/plasma-applet-quicklauncher_0.4-1_i386.deb
/usr/lib/kde4/lib/kde4/plasma_applet_quicklauncher.so
/usr/lib/kde4/share/kde4/services/plasma-applet-quicklauncher.desktop
/var/lib/dpkg/info/plasma-applet-quicklauncher.conffiles
/var/lib/dpkg/info/plasma-applet-quicklauncher.list

Which one of these is the plasmoid?

---

### Post by benerivo on 2008-09-08
I think ```
/usr/lib/kde4/lib/kde4/plasma_applet_quicklauncher.so
``` is the file you would say the installed plasmoid is. To add it to your desktop, right click on the desktop and choose 'Add Widget'. It should have an entry in the list.

---

### Post by tarahmarie on 2008-09-08
> **benerivo said:**
> I think ```
/usr/lib/kde4/lib/kde4/plasma_applet_quicklauncher.so
``` is the file you would say the installed plasmoid is. To add it to your desktop, right click on the desktop and choose 'Add Widget'. It should have an entry in the list.

Worked like a champ.  Thanks!

---

### Post by tarahmarie on 2008-09-08
> **tarahmarie said:**
> Worked like a champ.  Thanks!

I figured this one out with the .deb package, and it worked fine. It seems that the plasmoids that were in the /usr/lib/kde4/lib/kde4 directory are developmental; I ended up being successful using dpkg -i on the quicklauncher plasmoid (after a reboot, the widget appeared in the Add New Widgets desktop context menu). Right now, I'm trying to install the Timoid plasmoid, and it requires making makefiles with cmake. I've installed gcc and build-essential; I theoretically have everything I need to do it. The problem is that I don't understand the process of using the cmake command. Here are the instructions from the Kde-Look site for the Timoid plasmoid:

- extract
- navigate a konsole to source dir
- create a build dir ("mkdir build")
- change to build dir ("cd build")
- generate makefiles: "cmake ../"
--> on my system (debian) i need to use "cmake -DCMAKE_INSTALL_PREFIX=/usr ../"
- make... ("make")
- become root ("su")
- install ("make install")

Here's the widget site: [http://www.kde-look.org/content/show...?content=85802](http://www.kde-look.org/content/show...?content=85802)

I've downloaded the plasmoid, and extracted it to: /home/tarahmarie/Documents/Software/Timoid.

Inside /Timoid/src, I created /build.

What does it mean by generate makefiles? I've looked at the cmake command, but I haven't been able to google any information that I understand.

---

