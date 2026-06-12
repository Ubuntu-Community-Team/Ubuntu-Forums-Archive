---
title: "need permissions"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by diabeetus on 2008-07-17
i need to be able to read/write in /etc. how can i do that, or how do i log into root so i can access these. i just installed ubuntu about an hour ago, and haven't installed or changed anything whatsoever

---

### Post by Stunts on 2008-07-17
Just use sudo and type your password before the command:

sudo 'command'

---

### Post by PinkFloyd102489 on 2008-07-17
Whatever you do, DO NOT CHANGE THE PERMISSIONS ON THE FOLDER. It's a potential security issue if you do.


Awesome username, btw.

---

### Post by Vivaldi Gloria on 2008-07-17
> **diabeetus said:**
> i need to be able to read/write in /etc. how can i do that, or how do i log into root so i can access these. i just installed ubuntu about an hour ago, and haven't installed or changed anything whatsoever

Another way: Press Alt+F2 and start

```
gksudo nautilus
```

to get a nautilus window with root rights.

---

### Post by phidia on 2008-07-17
I don't know what you're editing but obviously be careful. To get administrative privledges just use "sudo".

---

### Post by diabeetus on 2008-07-17
update: i'm going to cut the middle man, because whenever i try to put in a new xorg.conf, it just utterly ***** up my display. i had to make a new virtual machine of ubuntu twice or so, and this current one doesn't have a bright future either.

does anyone know how to add the 1440x900 resolution option **other** than doing that xorg.conf or whatever the name is thing? i've tried so many times and i'm not getting anything out of it.

---

### Post by bodhi.zazen on 2008-07-17
LOL, depends on what virtualization software you are using. Install the "tools" reboot

Then go to System -> preferences -> screen resolution.

If you break X

Boot to recovery mode, select xfix from the menu -> reboot

---

### Post by aysiu on 2008-07-17
You should back up any system file before you edit it: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
gksudo gedit /etc/X11/xorg.conf
``` or ```
sudo nano -B /etc/X11/xorg.conf
```

---

