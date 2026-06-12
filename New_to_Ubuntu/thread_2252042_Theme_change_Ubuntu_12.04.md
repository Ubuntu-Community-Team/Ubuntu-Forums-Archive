---
title: "Theme change Ubuntu 12.04"
date: 2014-11-08
forum: New to Ubuntu
---

### Post by matthew_Epperson on 2014-11-08
Please and Thank you all for the help!:KS:KS:KS:KS:KS:KS

all good

---

### Post by matthew_Epperson on 2014-11-08
I've tried setting the background so much all it does is set it as the screen saver. I can't double right click my desktop. Help? Any suggestions? My quest account works great.....

Sorry

[http://imagebin.ca/v/1gaXNdcFFCPW](http://imagebin.ca/v/1gaXNdcFFCPW)                      Look it wont change and idk what to do

---

### Post by Frogs Hair on 2014-11-09
Edit : a possible solution I posted is not applicable after 12.04 . Is this an upgrade to 14.04 ?

---

### Post by CantankRus on 2014-11-09
> **matthew_Epperson said:**
> I've tried setting the background so much all it does is set it as the screen saver. I can't double right click my desktop. Help? Any suggestions? My quest account works great.....

Sorry

[http://imagebin.ca/v/1gaXNdcFFCPW](http://imagebin.ca/v/1gaXNdcFFCPW)                      Look it wont change and idk what to do
Make sure nautilus is still drawing the desktop.
Terminal...
```
gsettings set org.gnome.desktop.background show-desktop-icons true
```

Try some different themes installable from the [**_[COLOR="#B22222"]noobslab theme ppa[/COLOR]_**]("http://www.noobslab.com/2013/03/mediterranean-themes-for-ubuntu.html"),
then use **unity-tweak-tool** to choose a new theme.

You can browse the ppa once installed from the software center.

---

### Post by matthew_Epperson on 2014-11-09
It's like i'm locked out of everything except internet use, and the ability to actually log in and change my password. IDK , yes  12.04 completly updated

---

### Post by CantankRus on 2014-11-09
> **matthew_Epperson said:**
> It's like i'm locked out of everything except internet use, and the ability to actually log in and change my password. IDK , yes  12.04 completly updated

Is English your first language?

---

### Post by Frogs Hair on 2014-11-09
If you are using 12.04 and have the Gnome Tweak Tool installed select desktop and make sure "Let File Manager Handel The Desktop" is enabled . If it isn't the desktop right-click/context menu won't work.

---

### Post by matthew_Epperson on 2014-11-20
I love you thank you, its slow learning but pretty fun. Still having problems with terminal though.

---

