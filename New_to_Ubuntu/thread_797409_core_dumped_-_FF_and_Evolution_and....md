---
title: "core dumped - FF and Evolution and..."
date: 2008-05-17
forum: New to Ubuntu
---

### Post by beanco on 2008-05-17
.... CPU over heated...

I cannot launch FF or Evolution. When I booted up I got the CPU overheated message.  I suppose that is simple enough to fix... just replace the fan, right?

what about the core dump?

I cannot check this site because epiphany crashes when I hit search.

---

### Post by beanco on 2008-05-17
tried it again as root, i mean launching from the commmand line and got this

```
root@rob-desktop:/home/rob# firefox

(firefox-bin:6554): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:6554): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(firefox-bin:6554): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
Segmentation fault (core dumped)
root@rob-desktop:/home/rob# evolution

(evolution-2.10:6623): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(evolution-2.10:6623): Gdk-WARNING **: locale not supported by C library

(evolution-2.10:6623): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
CalDAV Eplugin starting up ...
Segmentation fault (core dumped)

```

---

### Post by beanco on 2008-05-17
been 3 hours sinc eI first p[osted but no ideas yet. folks. need a working browser ASAP.

thanks

robi

---

