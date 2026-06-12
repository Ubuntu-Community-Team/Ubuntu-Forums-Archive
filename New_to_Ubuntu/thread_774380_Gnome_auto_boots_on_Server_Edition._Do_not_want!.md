---
title: "Gnome auto boots on Server Edition. Do not want!"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-04-29
Hi,

I have just installed the Server Edition on a box, and then installed Webmin followed by Gnome.

Now when I switch the box on, it automatically fires up Gnome (the login screen).

I'm wanting to have the box normally boot to the terminal logon screen as normal. 

Many thanks for any help!

---

### Post by billgoldberg on 2008-04-29
Hide the gdm, then ubuntu should start without a gui.

startx should then start gnome if you want to.

I forgot the exact location, but I'm sure someone else will give it.

---

### Post by Monicker on 2008-04-29
This thread may help:

[http://ubuntuforums.org/showpost.php?&p=1483050&postcount=3]("http://ubuntuforums.org/showpost.php?&p=1483050&postcount=3")

---

### Post by shearn89 on 2008-04-29
^ that looks like the thing. Not sure about the rc2.d directory, but something similar should be there. I would have suggested uninstalling gdm, but i'm not sure you can do that and keep gnome.

---

