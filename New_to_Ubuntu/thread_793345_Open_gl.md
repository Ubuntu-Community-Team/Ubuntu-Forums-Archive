---
title: "Open gl?"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Kaneda187 on 2008-05-13
can anyone tell me how to set mplayer or movie player to open gl?

---

### Post by SunnyRabbiera on 2008-05-13
well I am not sure on movie player but do you have mplayer gui installed?

---

### Post by Kaneda187 on 2008-05-13
gui?

---

### Post by SunnyRabbiera on 2008-05-13
graphic user interface, in your menus do you have mplayer listed as an option?

---

### Post by Tomatz on 2008-05-13
To my knowledge you can only do this on vlc.

In a terminal:

```
sudo apt-get install vlc
```

Then open **preferences** (vlc) then check the **advanced box** and go to **output modules**.


Why you want to do this anyway???

---

### Post by SunnyRabbiera on 2008-05-13
> **Tomatz said:**
> To my knowledge you can only do this on vlc.
No I have done it in others, in Xine, in kaffeine, and in mplayer/smplayer.

---

### Post by Kaneda187 on 2008-05-13
yeah i have mplayer listed in my menu....

---

### Post by SunnyRabbiera on 2008-05-13
> **Kaneda187 said:**
> yeah i have mplayer listed in my menu....

then you have mplayer gui.
open it up and right click any of its windows (the control panel or the window will do and select "preferences"
then go to the "video" tab
now there is a choice here, between two main opengl's, play with each one and see what works, and remember to restart mplayer each try.

---

### Post by eldepeche on 2008-05-13
try adding the line 
```
vo=gl
```
to the file 
```
~/.mplayer/config
```

---

