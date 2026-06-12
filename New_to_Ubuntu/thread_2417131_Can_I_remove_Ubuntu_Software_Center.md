---
title: "Can I remove Ubuntu Software Center?"
date: 2019-04-21
forum: New to Ubuntu
---

### Post by robertzaku1 on 2019-04-21
It is not useful to me. Whether I'm offline It doesn't work.
I tried sudo apt-get remove software-center.

---

### Post by freemedia2018 on 2019-04-21
> **robertzaku1 said:**
> I tried sudo apt-get remove software-center.  That's the way to remove it. What happened?  ```
sudo apt-get --purge remove software-center
```

---

### Post by westie457 on 2019-04-21
Try this instead. ```
sudo apt remove --purge gnome-software
```

---

### Post by Holger_Gehrke on 2019-04-21
Just because the program is called 'Software Center' in the menu (or Activities or whatever) does not mean that's the name of the program (or the package). Search the .desktop files in /usr/share/applications for 'Software' ('grep "Software" /sur/share/applications/*.desktop'). When you've found the right .desktop-file, check the line starting with 'Exec=' for the actual name of the program. Use 'which' to find the actual location of the executable then use 'dpkg -S' with that to find the package name.
Example:
```

$ grep "Software" /usr/share/applications/*.desktop
/usr/share/applications/activity-log-manager.desktop
/usr/share/applications/debian-uxterm.desktop
/usr/share/applications/debian-xterm.desktop
/usr/share/applications/defaults.list
/usr/share/applications/gnome-software-local-file.desktop
/usr/share/applications/libreoffice-base.desktop
/usr/share/applications/libreoffice-calc.desktop
/usr/share/applications/libreoffice-draw.desktop
/usr/share/applications/libreoffice-impress.desktop
/usr/share/applications/libreoffice-math.desktop
/usr/share/applications/libreoffice-startcenter.desktop
/usr/share/applications/libreoffice-writer.desktop
/usr/share/applications/mimeinfo.cache
/usr/share/applications/mypaint.desktop
/usr/share/applications/org.gnome.Software.desktop
/usr/share/applications/org.gnome.Software.Editor.desktop
/usr/share/applications/software-properties-gtk.desktop
/usr/share/applications/update-manager.desktop

$ cat /usr/share/applications/org.gnome.Software.desktop
[Desktop Entry]
Name=Software
Comment=Add, remove or update software on this computer
# Translators: Do NOT translate or transliterate this text (this is an icon file name)!
Icon=org.gnome.Software
**Exec=gnome-software %U**
Terminal=false
Type=Application
Categories=GNOME;GTK;System;PackageManager;
# Translators: Search terms to find this application. Do NOT translate or localize the semicolons! The list MUST also end with a semicolon!
Keywords=Updates;Upgrade;Sources;Repositories;Preferences;Install;Uninstall;Program;Software;App;Store;
StartupNotify=true
MimeType=x-scheme-handler/appstream;x-scheme-handler/apt;x-scheme-handler/snap;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=gnome-software
X-GNOME-Bugzilla-Component=gnome-software
X-GNOME-UsesNotifications=true
DBusActivatable=true
X-Ubuntu-Gettext-Domain=gnome-software

$ which gnome-software
/usr/bin/gnome-software

$ dpkg -S /usr/bin/gnome-software
gnome-software: /usr/bin/gnome-software

```
So on my system (XUbuntu 18.04), the menu-entry "Software" points to gnome-software from the package of the same name and that's the name I'd have to put in a 'sudo apt remove'-command.
For all it's faults the Software Center is the only tools which tries to produce a unified view of multiple ways (.deb-packages, snaps, flatpacks, limba) to install software. I'd think very hard on whether or not freeing up a few Megabytes of space is worth losing this tool (even though I rarely use it).

Holger

---

### Post by Rubi1200 on 2019-04-21
+1 to what Holger said.

Moreover, removing packages like this could lead to other issues, unmet dependencies or who knows what when running some other package.

If you do not use it, you can remove from view on the dock by right-clicking and remove.

If you really want to be in more control then take a look at the minimal install for Ubuntu:
[https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option](https://www.omgubuntu.co.uk/2018/02/ubuntu-18-04-minimal-install-option)

---

### Post by oldrocker99 on 2019-04-22
It really isn't hard to use Synaptic, and it lists EVERY package.```
sudo apt install synaptic
```

---

### Post by Rubi1200 on 2019-04-23
> **oldrocker99 said:**
> It really isn't hard to use Synaptic, and it lists EVERY package.```
sudo apt install synaptic
```

+1

Synaptic is what I grew up on, so to speak.

---

### Post by oldrocker99 on 2019-04-23
It was the only GUI software manager back when I started with Hardy Heron back in '08. With good old GNOME 2.3. That's why I use Ubuntu MATE exclusively. Here's a way to make synaptic even better, with a filter, which acts like grep, and it is **VERY** useful:

[http://ubuntuhandbook.org/index.php/2019/01/enable-quick-filter-search-box-synaptic-package-manager/](http://ubuntuhandbook.org/index.php/2019/01/enable-quick-filter-search-box-synaptic-package-manager/)

---

### Post by Rubi1200 on 2019-04-23
> **oldrocker99 said:**
> It was the only GUI software manager back when I started with Hardy Heron back in '08. With good old GNOME 2.3. That's why I use Ubuntu MATE exclusively. Here's a way to make synaptic even better, with a filter, which acts like grep, and it is **VERY** useful:

[http://ubuntuhandbook.org/index.php/2019/01/enable-quick-filter-search-box-synaptic-package-manager/](http://ubuntuhandbook.org/index.php/2019/01/enable-quick-filter-search-box-synaptic-package-manager/)

Thanks, I like the look of that!

I started out with Dapper Drake and still have fond memories of installing and using it.

---

