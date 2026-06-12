---
title: "How does Vuze (Azureus) decide which program to use to open a file type?"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by janmartin on 2008-09-17
Hi,

I am running Vuze, (ex. Azureus) 3.1.1.0 on Ubuntu 8.04.

Recently I changed the program to open .mpg files from mplayer to smplayer using a rightclick in the nautilus filemanger. Works fine.

However Vuze does still use mplayer. 
Also there is no way to change this behavior in the Options tab.

Any ideas?

Thanks,
Jan

---

### Post by aeiah on 2008-09-17
perhaps mplayer is set as default media player for all video types, whereas all you did was tell nautilus to open mpg files with mplayer when you double click them. vuze perhaps relies on the global settings rather than nautilus settings. try changing the video file defaults in gconf-editor or perhaps somewhere in the preferences menu (i forget if its there, but it'll be in gconf)

---

### Post by detroit/zero on 2008-10-17
The Preferred Applications app in System>Preferences is a joke. Config editor doesn't give you too many options, either. In terminal, run the following command:```
 gksudo gedit /etc/gnome/defaults.list
```Look for the file extensions you want to change the behavior for and change "totem.desktop" or "mplayer.desktop" to "vlc.desktop", or the player of your choice.

---

### Post by talon314 on 2008-10-25
I tried changing application/x-matroska in /etc/gnome/defaults.list (to vlc.desktop, mplayer.desktop, etc.) and vuze still launches mkv files with (in my case) totem-xine. Anyone have any other ideas?

(Adding application/x-extension-mkv=mplayer.desktop doesn't help either)

---

### Post by quaternion on 2009-03-01
Bump... I have the same problem as well.

---

### Post by alroger on 2010-01-21
> **quaternion said:**
> Bump... I have the same problem as well.

Wow, still no help.
Same problem here.
Vuze was opening some program... I uninstalled it... then started opening SubDownloader... uninstalled it... now it's opening Miro!
And long before that I uninstalled Totem and whatever the default media player for Ubuntu 8.10, 9.04 and 9.10... 
it simply picks the worst options! maybe it's picking from reverse order.
Anyway, went into the file properties of Nautilus and removed all options for openening an AVI file, leaving only VLC for playing.... no help, it picks Miro for some reason!
Miro doesn't even exist in my defaults.list.
I did try to uninstall and install VLC again, so it would register itself again as the mediaplayer... same thing.

BUMP!

---

### Post by alroger on 2010-03-24
Same thing here... very frustrating... and I think it also changes due to some of the updates... last time it was opening using Miro, now it's back to Totem again.
If we just found out where Vuze and others like it are looking at for this configuration...

---

