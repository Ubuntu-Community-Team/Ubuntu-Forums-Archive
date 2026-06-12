---
title: "Problems with VLC"
date: 2011-09-22
forum: New to Ubuntu
---

### Post by chinmay152 on 2011-09-22
When i try to start vlc, it does not  start... i went to the terminal and typed in vlc and got the following message:

VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Blocked: call to setlocale(6, "")
Warning: call to srand(1316288432)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:11157): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[0xb4b12454] xml xml error: XML parser error (line 1) : Document is empty

[0x886389c] skins2 interface error: no skins found : exiting

Please help!

---

### Post by wolfen69 on 2011-09-22
It seems it might be related to X somehow.
Try
```
sudo apt-get remove --purge vdpau-video
```
then reboot. You can always put it back if it didn't work.

---

### Post by chinmay152 on 2011-09-23
Not working :( :(

---

