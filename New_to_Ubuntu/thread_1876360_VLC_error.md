---
title: "VLC error"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by editheraven on 2011-11-06
Some .mp4 files fails to run

```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x90e8914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1321048475)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:22317): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[mp3 @ 0xb680c360]Header missing
[mp3 @ 0xb680b1d0]Estimating duration from bitrate, this may be inaccurate
Warning: call to rand()
TagLib: MP4: Invalid atom size
[mp3 @ 0x95f33c0]Header missing
[mp3 @ 0x95f2220]Estimating duration from bitrate, this may be inaccurate
TagLib: MP4: Invalid atom size
```

Vlc version
```

VLC media player 1.1.9 The Luggage (revision exported)
VLC version 1.1.9 The Luggage (exported)
Compiled by buildd on vernadsky.buildd (Jul 21 2011 11:32:22)
Compiler: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.
```

Ubuntu natty.

---

### Post by Script Warlock on 2011-11-06
> **editheraven said:**
> Some .mp4 files fails to run

```
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x90e8914] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Warning: call to srand(1321048475)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:22317): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Blocked: call to setlocale(6, "")
[mp3 @ 0xb680c360]Header missing
[mp3 @ 0xb680b1d0]Estimating duration from bitrate, this may be inaccurate
Warning: call to rand()
TagLib: MP4: Invalid atom size
[mp3 @ 0x95f33c0]Header missing
[mp3 @ 0x95f2220]Estimating duration from bitrate, this may be inaccurate
TagLib: MP4: Invalid atom size
```

Vlc version
```

VLC media player 1.1.9 The Luggage (revision exported)
VLC version 1.1.9 The Luggage (exported)
Compiled by buildd on vernadsky.buildd (Jul 21 2011 11:32:22)
Compiler: gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu4) 
This program comes with NO WARRANTY, to the extent permitted by law.
You may redistribute it under the terms of the GNU General Public License;
see the file named COPYING for details.
Written by the VideoLAN team; see the AUTHORS file.
```

Ubuntu natty.

does the file plays on some machines or movie player?

---

### Post by editheraven on 2011-11-06
No. Not even mkvmerge gui or pitivi or gnome player. I thaught that is a problem with my codecs. I could play the file some time ago.

---

