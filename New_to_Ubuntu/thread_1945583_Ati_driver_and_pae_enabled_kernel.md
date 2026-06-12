---
title: "Ati driver and pae enabled kernel"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by editheraven on 2012-03-23
I updated my kernel to a pae enabeld one. After restart, ati kernek module wouldn't work (i noticed it when compiz wasn't loaded) so i downloaded the ati driver from their site (as usual) But the installer said i could not remove the old files and "DKMS part of installation failed. Please refer to /usr/share/ati/fglrx-install.log for details".   GLXinfo gives me   "name of display: :0.0  X Error of failed request: BadRequest (invalid request code or no such operation)  Major opcode of failed request: 139 (ATIFGLEXTENSION)  Minor opcode of failed request: 66 ()  Serial number of failed request: 13  Current serial number in output stream: 13"   wich doesn't seems to be right.

---

### Post by editheraven on 2012-03-23
x

---

### Post by editheraven on 2012-03-24
Bump!  I managed to run compiz with ati driver from ubuntu ppa. But now compiz-decorator can't start. Whenever i enable decorations in compiz manacger, gnome-panel keeps restarting.  "compiz-decorator Starting unity-window-decorator /usr/bin/unity-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager. "  But i disabled the plugin.

---

### Post by NikTh on 2012-03-24
Hello , 
did you try to remove ati driver and install it again ? 
Remove the driver ```
sudo apt-get purge fglrx
```and try this 
```
apt-add-repository [B]ppa:ubuntu-x-swat/x-updates 
[/B]sudo apt-get update 
sudo apt-get install fglrx
```this PPA has the latest driver for Ati (amd) . 
I think that the manual install it is a little bit tricky, so try this ppa to see how it's going.

---

