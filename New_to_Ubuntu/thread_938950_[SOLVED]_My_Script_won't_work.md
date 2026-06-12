---
title: "[SOLVED] My Script won't work"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-05
```
m=$GEDIT_CURRENT_DOCUMENT_NAME;n=$m | sed 's/%20/ /'; echo $n
```

I want to assign the variable m as the name of my document which has a space in the name. Gedit wants to put the URL code %20 in for the space and my script should add the file name to m, and then remove the %20 and replace it with a space and then assign n to be the name WITH a space and not %20.

Please help.

---

### Post by detroit/zero on 2008-10-05
Here's an "open with gedit" script i downloaded somewhere that has no problems with filenames.[IMG]http://ubuntuforums.org/images/editor/attach.gif[/IMG]

---

### Post by JohnGalt131 on 2008-10-05
```
m=` echo $GEDIT_CURRENT_DOCUMENT_NAME | sed 's/%20/ /' | sed 's/ /\?/'`
gnome-terminal -x octave --persist $m
```

This Works.

I thought ` was a ' so my code wasn't working...

---

