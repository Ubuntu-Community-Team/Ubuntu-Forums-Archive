---
title: "need help about panel"
date: 2008-10-02
forum: New to Ubuntu
---

### Post by puleo1333774 on 2008-10-02
my taskbar is gone help:(

and the back and forward button to my internet browser are not activating even when going

to the next page

---

### Post by Paqman on 2008-10-02
Relax, everything on your desktop is completely customisable, so you can get it back with a few mouse clicks.

Is it the whole panel that's gone, or just the list of open windows? To get a panel back, right click and select "add new panel", to get the taskbar back, right click on a panel and add a "window list" (IIRC) to it.

---

### Post by PocketDog on 2008-10-02
Just in case you've inadvertently killed your panel - which isn't easy but it's easier than removing it completely(!) - go to terminal and simply enter **gnome-panel**. Hopefully this will bring it back

---

### Post by puleo1333774 on 2008-10-02
> **PocketDog said:**
> Just in case you've inadvertently killed your panel - which isn't easy but it's easier than removing it completely(!) - go to terminal and simply enter **gnome-panel**. Hopefully this will bring it back

by my terminal is with the panel is there a shortcut to go there?

---

### Post by Ryadt on 2008-10-02
> **puleo1333774 said:**
> by my terminal is with the panel is there a shortcut to go there?

Alt+F2, then```
gnome-terminal
```

---

### Post by PocketDog on 2008-10-02
hah! yeah, sorry.

---

### Post by puleo1333774 on 2008-10-02
> **PocketDog said:**
> hah! yeah, sorry.

andrew@andrew-desktop:~$ gnome-panel

(gnome-panel:5914): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(gnome-panel:5914): GLib-CRITICAL **: g_bookmark_file_load_from_data: assertion `length != 0' failed

(gnome-panel:5914): Gtk-WARNING **: Attempting to store changes into `/home/andrew/.recently-used.xbel', but failed: Failed to close file '/home/andrew/.recently-used.xbel.Y8PJIU': fclose() failed: Success

this message appear when i type  gnome-panel in terminal

---

### Post by puleo1333774 on 2008-10-02
when im clicking the green button in right upper corner side of screen 
(the power off option) and when im exiting in terminal, the panel will be gone again

---

### Post by puleo1333774 on 2008-10-02
> **PocketDog said:**
> Just in case you've inadvertently killed your panel - which isn't easy but it's easier than removing it completely(!) - go to terminal and simply enter **gnome-panel**. Hopefully this will bring it back


thank you for the help but still it didn't work

---

### Post by Paqman on 2008-10-02
Have you done anything weird to your /home folder lately? Looks like your settings have got messed up. Do you have another user account you can log into to give you a stable desktop in the meantime?

---

