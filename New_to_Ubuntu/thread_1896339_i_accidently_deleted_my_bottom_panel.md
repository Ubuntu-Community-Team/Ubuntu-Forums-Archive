---
title: "i accidently deleted my bottom panel"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by ilikelinuxitisthebest on 2011-12-16
Hey guys. i think i just made the biggest noob move of my life right now. i was changing panel settings and i accidently deleted my bottom panel cause i thought it was a junk one that i added. how do i get the default one back?

---

### Post by N00b-un-2 on 2011-12-16
there's no good way to get the default panel back once you delete it.  However, with that being said, you should be able to boot into a live CD and open up a thunar window which will open up in the Live CD's user account 'ubuntu' home directory. Hit ctrl+h to view hidden files.
then browse to /home/ubuntu/.config/xfce4/xfconf/xfce-perchannel-xml

Leave that window open.

then open a second thunar window, mount your computer's hard drive and browse to the same location in YOUR user's home directory on your computer's hard drive.  then copy the file 

xfce4-panel.xml

from the live CD's home over the one in your home.  Then reboot your computer.  You should have the default panels back.  I hope that helps.

---

### Post by ilikelinuxitisthebest on 2011-12-16
Thank you for your response. But i decided to just use docky instead. it was a good response though and it probably would have worked.

---

### Post by N00b-un-2 on 2011-12-16
excellent choice

---

