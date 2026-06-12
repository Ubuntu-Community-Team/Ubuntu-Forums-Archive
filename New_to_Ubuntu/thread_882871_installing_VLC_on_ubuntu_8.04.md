---
title: "installing VLC on ubuntu 8.04"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by waterrr on 2008-08-07
I followed the instructions on the VLC website and tried to install it through synoptic package manager but the VLC package could not be found...what can I do to install VLC?

---

### Post by Aetherius on 2008-08-07
open gnome-terminal and type:

```
sudo apt-get install vlc
```

enter your password when prompted.

if it says no package found please ensure repositories are enabled in synaptic.

---

### Post by drs305 on 2008-08-07
VLC is in the multiverse repository. Synaptic > Settings > Repositories > Ubuntu software. Make sure Multiverse is checked, then hit the 'Reload' button.  If vlc still doesn't show up, you might want to try the main server (selected from the same tab). VLC is in the repositories.

---

### Post by waterrr on 2008-08-07
okay thanks, bc on the website it said to check universe not multiverse - ill give it a shot

---

### Post by prabhakaran1989 on 2008-08-07
just search in add/remove programs or in the Synaptic package manager ..VLC u can find the files needed,there u select>apply
it will download all necessary files!!

---

