---
title: "[SOLVED] Screen Resolution Ibex"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by neverett on 2008-09-22
I changed my screen resolution in Ibex to something that is too high for my monitor.  So I can see the login screen but when I login, I see nothing but black screen.  Please HELP me fix my resolution back to my old resolution!!!  Thanks in advance!

---

### Post by Tatty on 2008-09-22
Development releases usually have their own forums on here, it is usually best to direct questions reguarding that version there

[http://ubuntuforums.org/forumdisplay.php?f=346](http://ubuntuforums.org/forumdisplay.php?f=346)

Try booting into recovery mode then backup your xorg.conf (just in case) and run:

```
xfix
```

I have never used xfix myself, but i believe that is the best tool to use for such probs since hardy.

---

### Post by Ryadt on 2008-09-22
Try ```
sudo dpkg-reconfigure xserver-xorg
```

---

