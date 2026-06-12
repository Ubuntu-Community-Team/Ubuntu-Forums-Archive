---
title: "gsettings"
date: 2012-08-29
forum: Programming Talk
---

### Post by mikemike1232 on 2012-08-29
Hello!
i need to set hotkey using terminal or by changing some files, i know that it possible by gnome-contro-center keyboard, but i need it in terminal, i read that it's possible with gsettings
```
 gsettings get org.gnome.settings-daemon.plugins.media-keys custom-keybindings 
``` and then using gsettings set, but i don't have custom-keybindings key in this scheme, how i can solve this problem ( Ubuntu 12.04) thank you.

---

### Post by Vaphell on 2012-08-29
it appears custom keybindings still use older gconf
when i run gconf-editor and go to /desktop/gnome/keybindings i see custom0 with action, binding and name keys.

i think you need to use gconftool-2 to manipulate gconf settings from terminal

---

### Post by mikemike1232 on 2012-08-30
but why there is no custom keysettings in gsettigs, in Fedora it's easy to do usings gsettings

---

### Post by Vaphell on 2012-08-30
apparently fedora moved further in gnome3 adoption than ubuntu

---

