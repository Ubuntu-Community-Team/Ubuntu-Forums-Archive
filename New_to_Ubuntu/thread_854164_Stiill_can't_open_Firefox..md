---
title: "Stiill can't open Firefox."
date: 2008-07-09
forum: New to Ubuntu
---

### Post by Whatrymes on 2008-07-09
This problem really has me stuck, no answers?

Media Connectivity wizard freezes. . . 

--------------------------------------------------------------------------------

Just installed 8.04.1 and tried to install "media player connectivity." The wizard begins to set up then freezes. I can't do anything 'cept hold power button and shut down computer. Now whenever I try to open "Firefox" the wizard opens again and then freezes again and, well, you know. ???

Thank you,
Ed

---

### Post by Tatty on 2008-07-09
Im not really sure whats gone wrong here, but the first thing i would try to get firefox working again (especially since this is a new install so i assume you dont have any bookmarks) is to try removing the mozilla folder in your /home directory.

Well, for caution's sake lets just rename it so you can restore it if nessesary.

try closing firefox then running:

```
mv ~/.mozilla ~/.mozilla.my.backup
```

then try opening firefox again.  Hopefully it should recreate a fresh user directory for you.

---

