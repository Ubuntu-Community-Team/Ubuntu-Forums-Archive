---
title: "[SOLVED] Carbon copy of home directory in wine"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by lsutiger on 2008-06-05
I have no idea how this happened, but would like some insight on it. 

I was browsing through my computer in nautilus looking for an icon for a program that I installed (ie4linux). I didn't find the icon in the ie4linux folder. So I decided to browse over to my .wine folder. While I was browsing, I found a carbon copy of my home folder in /home/<user>/.wine/drive_c/windows/profiles/<user>/My Documents.

Now tell me this...is this just a a link to my home folder or is stuff jacked up?
Thanx in advance!

---

### Post by DezSP on 2008-06-05
It's a symbolic link (i.e. shortcut) to your home directory, you can set it up in winecfg (under directories I believe) to point to wherever you want. Oh, and IEs4Linux will probably have put icons in your Applications menu somewhere.

---

### Post by lsutiger on 2008-06-05
Thanx!

---

### Post by Dr Small on 2008-06-05
Yeah. It's simply a link over to your home folder :)

---

