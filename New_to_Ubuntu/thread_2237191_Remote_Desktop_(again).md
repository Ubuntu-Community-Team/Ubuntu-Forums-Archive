---
title: "Remote Desktop (again)"
date: 2014-07-31
forum: New to Ubuntu
---

### Post by oldfart101 on 2014-07-31
Sorry, posted in a 'solved' thread.
Can't get Remote Desktop to work...
I tried 'a load' of solutions proposed on the internet - still no connection from vnc (Windows) to Ubuntu 14.04
there seems to be an issue I can't find a solution to:
 	```
 	:~$ vino-preferences
error: XDG_RUNTIME_DIR not set in the environment.

(vino-preferences:29061): Gtk-WARNING **: cannot open display:
```
and
```
sudo gsettings set org.gnome.Vino require-encryption false
(process:6880): dconf-WARNING **: failed to commit changes to dconf: Cannot autolaunch D-Bus without X11 $DISPLAY
```

---

### Post by steeldriver on 2014-07-31
From where exactly are you trying to run vino-preferences / gsettings? Are you trying to do that over SSH?

---

### Post by oldfart101 on 2014-07-31
yes -- oops -- maybe I should run that locally??

---

### Post by oldfart101 on 2014-07-31
OK
ran this locally - without any errors:-
sudo gsettings set org.gnome.Vino require-encryption false

but

vino-preferences

(vino-preferences:7850): Gtk-CRITICAL **: gtk_entry_set_text: assertion 'text != NULL' failed

---

### Post by steeldriver on 2014-07-31
Yes they should work if you run them locally (i.e. on the actual desktop of the machine that you want to remote into).

If you have to do it over SSH, then you need to find a way to identify that desktop session - for gsettings (which is a CLI utility) it *should* be sufficient to specify the DISPLAY environment variable for the remote display e.g.

```

DISPLAY=:0 gsettings set org.gnome.Vino require-encryption false

```

(note that sudo should not be required - assuming that you are ssh'd in as the same user who owns the desktop session, you are trying to set properties for a session that you own). 

If you need to run vino-preferences that will be a bit harder, since it needs a remote X session to display on - in the absence of a VNC remote session you'd need to run SSH with X forwarding and have an X server running on the Windows box. 

If setting the DISPLAY variable doesn't work for gsettings, there are ways to extract the actual DBUS_SESSION_BUS_ADDRESS but it's a bit more complicated.

---

### Post by oldfart101 on 2014-07-31
tadaah!
Thanks very much - that worked

---

### Post by steeldriver on 2014-07-31
you're welcome - btw I don't know why vino-preferences is giving you that error, if you need further help debugging that then please post back

---

