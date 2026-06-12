---
title: "Can't edit 70-wizardpen.conf"
date: 2014-07-02
forum: New to Ubuntu
---

### Post by bluesky541 on 2014-07-02
So I finally found the file 70-wizardpen.conf which is in usr/share/X11/xorg.conf.d
I type in the terminal, typing ```
sudo gedit usr/share/X11/xorg.conf.d/70-wizardpen.conf
``` then gedit opens, I edit the file, but when I click the save button it says "Could not find file usr/share/X11/xorg.conf.d/70-wizardpen.conf" but the file IS there, I checked it myself. I typed the exact location where the file is.
And in the terminal, after clicking the save button, this appears:```
(gedit:3322): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

(gedit:3322): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

```
What am I doing wrong?This time, I checked if all the locations are on my computer, and if the file already exists, they are all there....
Please help...

---

### Post by sandyd on 2014-07-02
You missed a slash in front of /usr
```

sudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

Also, using sudo with graphical apps sometimes messes up the permissions of files in your home directory.

If you want, you can use gksu instead of sudo 

**Install gksu**```
sudo apt-get install gksu
```

**Use gksu instead of sudo**
```

gksu gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```

---

### Post by bluesky541 on 2014-07-02
Thank youu~!!!! It now saves(stupid me for missing the slash ^^;)

---

