---
title: "restoring graphics"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by smile-its-smiley on 2008-04-29
ive just tried getting the correct graphics drivers installed all seemed will but now every thing seems really slugish how can i revert back?

---

### Post by shearn89 on 2008-04-29
try the System->Administration/Preferences-> Hardware menu.

---

### Post by Michael.Godawski on 2008-04-29
what is your graphic card? What version of Ubuntu are you using?

---

### Post by smile-its-smiley on 2008-04-29
im using hardy its an ati graphics card not sure on the model number ill see if i can find out will post back when i do

---

### Post by smile-its-smiley on 2008-04-29
ok its an ATI Radeon® X1200

---

### Post by Michael.Godawski on 2008-04-29
So hoe did you try to install the ati drivers? by the Restricted Driver Manager? by envy ? by hand?

You can try to reconfigure the xserver with this terminal command:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by smile-its-smiley on 2008-04-29
i entered a code in terminal, but  i've just changed a setting in appearance >visual affects and changed it to normal and things seem ok, so should i leave it as it is?

---

### Post by shearn89 on 2008-04-29
If its working, yes. If you try something in future, backup your /etc/X11/xorg.conf first, and call it something like xorg.working.

---

### Post by smile-its-smiley on 2008-04-29
how would i go bout backing this up?

---

