---
title: "No more sound?"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by chris062689 on 2008-08-03
I recently installed Ubuntu 8.04.1 32bit and it's working great.
Sound worked, but I then I looked a bit later, and now in my volume control it's showed as muted, when I double click on it; it says it can't find an audio device.

I think I updated software, installed WINE, and Virtualbox...
Can anyone help me fix this problem?

---

### Post by Locutus_of_Borg on 2008-08-03
ensure you are in the audio group
run alsaconf as root
run alsamixer as root
modprobe whatever drivers are needed

if this still doesnt work, show us your lspci and dmesg

---

### Post by CloudFX on 2008-08-04
Try going to System > Preferences > Sound, and under the Devices tab, try the different options from the drop down boxes.  This fixed sound problems for me.

---

### Post by chris062689 on 2008-08-04
I did a reinstall (because I wanted to switch to 64bit anyway)

---

