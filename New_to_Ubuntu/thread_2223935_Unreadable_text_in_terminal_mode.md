---
title: "Unreadable text in terminal mode"
date: 2014-05-13
forum: New to Ubuntu
---

### Post by cnra on 2014-05-13
Hi guys

I'm running Lubuntu v13 on a vintage computer without any problems when i'm using the GUI. But if I change the grub to start up in terminal mode, the result is a white screen with distorted and unreadable text. The problem also occure for a short time during normal startpunkt/shut down.

If I use recovery mode and startup in shell, there are no problems, are there any way to get the terminal mode to use the same screen settings as when in recovery mode?

---

### Post by bapoumba on 2014-05-13
I'm not quite clear as to why you would change grub to start in a non-graphical session.
Why not use <ctrl><alt><F1> to get to the first virtual terminal ? <ctrl><alt><F7> will get you back to the graphics session.

---

### Post by cnra on 2014-05-13
As I said, its a vintage computer.. :-)

I hope to increase performance by starting up in terminal mode and use a daemon

---

### Post by bapoumba on 2014-05-14
> **cnra said:**
> As I said, its a vintage computer.. :-)

I hope to increase performance by starting up in terminal mode and use a daemon

OK, I'm sorry but had no time today and wont have time tomorrow. May be someone can help you out :)

---

### Post by ibjsb4 on 2014-05-14
My method is no display manager (dm) installed and use xinit.  In your case you could just disable the dm which is usually lightdm.  Xinit will take you to a tty login screen, then you can use the startx command or create a auto login.

You need to install 'xinit' and create a executable ~/.xinitrc file.

[https://wiki.archlinux.org/index.php/xinitrc](https://wiki.archlinux.org/index.php/xinitrc)

If interested I suggest you further research the key words.
startx
xinit
xinitrc

I have no idea what is causing unreadable text.

---

### Post by cnra on 2014-05-15
Thx - I will give it a try :-) Another guy allso suggestet, that I took a look at the runlevels - another thing to look into :-)

---

