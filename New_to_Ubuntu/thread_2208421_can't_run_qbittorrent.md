---
title: "can't run qbittorrent"
date: 2014-02-28
forum: New to Ubuntu
---

### Post by hugh4 on 2014-02-28
Hi,
I have a problem with my usb hard disk disappearing/unmounting every now and then (posted in mythbuntu section).  It crashed tonight and now the program qbittorrents won't run. I've tried removing it in unbuntu software center and reinstalling it.... No go. Tried the terminal apt-get etc and installed but again won't run from the applications menu.
Also have mythbuntu 12.04 and installed the ubuntu desktop and now I get a keyboard displayed when I reboot. How can I disable this?
Cheers,
Hugh

---

### Post by hugh4 on 2014-02-28
The problem was with locales and affected more than qbit.
Fixed by running:
sudo dpkg-reconfigure locales

---

### Post by oldos2er on 2014-02-28
Tried running it from a terminal (Ctrl-Alt-t)? ```
qbittorrent
``` Copy and paste any output here.

---

