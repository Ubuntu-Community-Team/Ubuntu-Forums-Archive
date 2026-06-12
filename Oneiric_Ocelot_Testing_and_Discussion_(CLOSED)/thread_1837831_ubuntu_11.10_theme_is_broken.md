---
title: "ubuntu 11.10 theme is broken"
date: 2011-09-02
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by opengl_cpp on 2011-09-02
I'm using ubuntu 11.10 right now, yesterday I updated my system and after rebooting I realized that gnome-shell was installed automatically, and ubuntu desktop was removed, so installed ubuntu desktop again then I faced with a broken Gtk+3 theme, I tried to re-install humanity icon and ambiance themes but again I see the same crappy theme. 

what do I have to do to fix this problem?

---

### Post by lucazade on 2011-09-02
> **opengl_cpp said:**
> I'm using ubuntu 11.10 right now, yesterday I updated my system and after rebooting I realized that gnome-shell was installed automatically, and ubuntu desktop was removed, so installed ubuntu desktop again then I faced with a broken Gtk+3 theme, I tried to re-install humanity icon and ambiance themes but again I see the same crappy theme. 

what do I have to do to fix this problem?

is gtk3-engines-unico installed?
check also if ambiance theme is selected in the appearance/background applet.

---

### Post by opengl_cpp on 2011-09-02
It's already installed and ambiance is set by default. :(

---

### Post by lucazade on 2011-09-02
> **opengl_cpp said:**
> It's already installed and ambiance is set by default. :(

by broken do you mean a win95 grey style? correct?
just a trial.. try to see if gnome-settings-daemon is running:
```
ps -ax | grep gnome-settings-daemon
```

if output is empty try to launch it manually with:
```
gnome-settings-daemon &
```

---

### Post by opengl_cpp on 2011-09-02
yes it looks like win 95. I checked gnome-settings-deamon, it's running
I attached this image, now you can see what happened to my desktop :(
[http://postimage.org/image/1mgbxf7r8/](http://postimage.org/image/1mgbxf7r8/)

---

### Post by opengl_cpp on 2011-09-02
by the way, I stopped gnome-settings-deamon and ran it again and got following error messages:


GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): Gtk-WARNING **: gtk_window_set_wmclass: shouldn't set wmclass after window is realized!


(gnome-settings-daemon:17237): GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): power-plugin-WARNING **: not connected

(gnome-settings-daemon:17237): GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): power-plugin-WARNING **: Failed to get brightness: GDBus.Error:org.freedesktop.DBus.Error.UnknownMethod: Method "GetBrightness" with signature "" on interface "org.freedesktop.UPower.KbdBacklight" doesn't exist


(gnome-settings-daemon:17237): GnomeDesktop-WARNING **: could not get output property for LVDS-1, rc: 15

(gnome-settings-daemon:17237): color-plugin-WARNING **: failed to create device: Failed to CreateDevice: GDBus.Error:org.freedesktop.ColorManager.Failed: could not check org.freedesktop.color-manager.create-device for auth: GDBus.Error:org.freedesktop.PolicyKit1.Error.NotAuthorized: Only trusted callers (e.g. uid 0) can use CheckAuthorization() for subjects belonging to other identities

---

### Post by lucazade on 2011-09-02
checked the warnings and are present also in my installation so seem harmless.

you could check .xsession-errors to see if anything went wrong in session startup routine
or start gnome-session --debug to figure out something but it is probably not an easy road. no other ideas..

---

### Post by opengl_cpp on 2011-09-03
Fortunately I found how to fix my problem, I did these things:
1. went to my home directory and deleted contents of these folders: 
   .cache .compiz-1 .config .dbus .gconf .local (I wasn't sure which folder contains the default theme, so I had to delete contents of all these folders)

2. went to system settings->Appearance and chose my theme(ambiance)

that's all :)
:guitar:   :lolflag:

---

### Post by snadrus on 2011-09-24
Same for me. You don't want to upgrade with a weird theme. It fixed when I just deleted:
.cache .compiz-1 .dbus .gconf

...which is better since google chrome & some other apps use the other folders.

---

