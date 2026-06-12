---
title: "Cannot find a file I installed"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by snake1086 on 2011-11-01
I'm fairly new to all Linux but have been working my way through things and figuring things out, mainly with the help of reading other posts on this site.  Two nights ago I upgraded my Ubuntu to 11.1 from 11.04.  It is running alongside Windows 7 ultimate using Wubi.

I used Wine to install Starcraft 2 and then began downloading the patches.  About 75% of the way through all of the patches, the patch installer told me I didn't have enough room to download the rest of the patches and stopped.  So i closed everything with most of the patches installed, and then used wubi-resize_1.4b.sh to resize and move my ubuntu to a new virtual disk and changed the root.disk files around to the new one.  That worked fine.  When I tried to find SC2 I couldn't and wine wouldn't load anything that it used to.  I had to uninstall and reinstall wine and unmount and remount my DVD just to get the SC2 installer back up.  Now it is saying i don't have enough room to reinstall SC2, and its mainly because the other copy of SC2 must be somewhere on this virtual disk, but I have no idea where it would be hiding.

Any thoughts on how I can access the SC2 I already installed and finish downloading the patches??

Thank you for all your help in advance!
:confused:

---

### Post by Vaphell on 2011-11-01
look into hidden .wine directory inside your home (ctrl+h to unhide), usually drives (like C:, D:) are merely subfolders of it.

---

### Post by snake1086 on 2011-11-01
Thank you!  Now I foun d it, but when I go to run the .exe with Wine it says "The blizzard launcher needs to be in the same folder as the game." 

Oh jeez.. I may have to re-install the game...

---

