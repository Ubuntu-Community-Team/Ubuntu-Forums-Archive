---
title: "Dual-Boot Sync [8.10 + Vista]"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by shoot2kill on 2008-11-11
i was just wondering if it is possible for apps that are used in both my 8.10 and vista partitions to use the same configs & settings..

e.g.
Firefox: im pretty sure that all of the bookmarks and even history are file based, and not registry based, could both 8.10 firefox and vista firefox read from the same files. this way, when i add a bookmark in vista, it will be there when i boot to ubuntu..

Azureus (Vuze): this one may be a bit more tricky. i am wanting it so that if i download a torrent and start downloading it in one OS, when i boot to the other OS it carries on downloading the same file. again, im sure all of the settings and state of the torrents are stored in files, and both installations can access one another's file-systems.

there are other apps that i cant think of now, but does anyone know if this is possible ??

---

### Post by quirks on 2008-11-11
I know of Firefox that it stores all of your personal data in a "profile", which you can find in ~/.mozilla/firefox. In theory, you could remove the profile directory and replace it by a symbolic link pointing to the same profile you use in Windows. BUT: I highly recommend not doing so! Almost every application saves data differently under different OSes and you might end up with a corrupted profile. Not to mention, the versions of Firefox should match on Windows and Linux. Otherwise, the newer version might update the profile and the older version might not be able to read it anymore.

If you still want to give it a shot, do it with a test profile, where there is nothing to lose. But such a scenario is certainly not supported and will probably fail one day. You have been warned - twice.

---

### Post by chrisod on 2008-11-11
The Foxmarks extension for Firefox will sync your bookmarks across different installs of Firefox.

---

