---
title: "upgrade from 12.10 to studio 12.10"
date: 2012-12-25
forum: New to Ubuntu
---

### Post by beelzebufo on 2012-12-25
I think this has probably been covered, but I can't seem to find anything about it.  I just installed ubuntu 12.10 but I actually wanted to install studio 12.10.. I know I could just reinstall using just the ubuntu studio 12.10 iso, but I already did all my tweaking and installations that I do with new installs, and I don't wanna do it again lol.  


thanks in advance

---

### Post by Elfy on 2012-12-25
You could install ubuntustudio-desktop, that will bring in the studio packages.

You could install ubuntustudio-audio, if you were only interested in the audio packages.

Try this from a terminal to see what's available

```
apt-cache search ubuntustudio
```

You'll though have a lot of ubuntu packages kicking around afterwards, studio is based on XFCE not Gnome.

---

