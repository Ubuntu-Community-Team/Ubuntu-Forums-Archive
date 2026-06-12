---
title: "Installing Theme Engines"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by joshdudeha on 2008-05-18
I really want to install some new theme engines.
Like Aurora and stuff.
But when I type ./configure in the terminal.
It outputs a load of stuff, until it gets to:
  ```
checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora

```

And I get this with every single engine I try to compile.
I thought ubuntu came with GTK+ on installation?
Can someone walk me through installing it please?

Thank you

---------
Josh

---

### Post by cb951303 on 2008-05-18
you need gtk dev packages ;) check synaptic

---

### Post by joshdudeha on 2008-05-18
Ahh, I will try that
Thanks

---

### Post by joshdudeha on 2008-05-18
Wait, where can I find it.
It doesn't have anything "gtk-dev-engines"

?

Thanks again

---

### Post by joshdudeha on 2008-05-18
/Bump =/

---

### Post by joshdudeha on 2008-05-18
Hey can someone please help
im going mad with all these clashing packages im trying

thanks
im off xx

---

### Post by cb951303 on 2008-05-18
sudo apt-get install libgtk2.0-dev

---

### Post by speedemonV12 on 2008-05-19
hey, i have done this, and i am still having problems installing aurora1.4

I install the dev package, then i run ./configure, and that works
then i run make, and that works, 
then i run make install, and that does not work.. it get a permission error, 
so just for the heck of it i ran sudo make install, and it said that it installed fine.. 
i check to see if it installed.. but nope.. didnt work... anything i can do ? I really want this engine!!!

---

### Post by chamberlain2006 on 2008-05-19
You need root permissions.  Do this instead
```
sudo make install
```

---

### Post by SunnyRabbiera on 2008-05-19
I think there is a debian installer for the aurora theme if I remember right, let me find it...

Edit:
yeh you can get the debian installer here:
[look]("http://software.opensuse.org/search?q=gtk2-engines-aurora&baseproject=ALL&p=1")

any of the .deb packages will probably do.

---

### Post by joshdudeha on 2008-05-21
Thank you everyone so much.
Have got it working now

:]
I love this place

---

