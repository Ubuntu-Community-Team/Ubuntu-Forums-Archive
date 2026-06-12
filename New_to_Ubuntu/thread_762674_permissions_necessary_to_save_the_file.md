---
title: "permissions necessary to save the file"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by jduplant on 2008-04-22
I am new to ubuntu and I cant get my desktop res to change so I am trying to edit xorg.conf but I get an error that says 

Could not save the file /etc/X11/xorg.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.

---

### Post by Ub1476 on 2008-04-22
```
gksudo gedit /etc/X11/xorg.conf
```

You are sure you aren't missing drivers for your graphic card/controller?

You can change resolution (those available) in System>Preferences>Screen res.

**If you edit xorg.conf** and do something wrong (higher value than the VGA can handle at that moment for instance), you wont be able to start a GUI after restarting, so **make sure you know what you are doing.**

---

### Post by Joeb454 on 2008-04-22
Open up a terminal from Applications>Accessories (I know you might not want to, but it's the easiest way :))

type the following ```
gksudo gedit /etc/X11/xorg.conf
``` it will allow you to edit (and save) the xorg.conf file :)

---

### Post by jduplant on 2008-04-22
That worked thanks for the help

I have a voodoo 5 in my pc and the video driver was already installed but would not allow me to change res

---

