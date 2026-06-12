---
title: "Graphic card / Monitor configuration"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Kill-Screen on 2008-10-05
Hi there

Totally noob here.

I have a Lg l226wtq-sf with a nvidia GeForce 6150 LE.
I can't configure it right, at any cost.

Please help me not change to XP again...
Thanks

---

### Post by shifty_powers on 2008-10-05
whats wrong with the configruation for a start?

---

### Post by Kill-Screen on 2008-10-05
I can't get a resolution bigger then 800x600.

---

### Post by Kill-Screen on 2008-10-05
Pretty please?

---

### Post by erickghint on 2008-10-05
are you using the restricted drivers, or the open drivers?

---

### Post by Kill-Screen on 2008-10-05
I used the open one, and then i get an "out of range" screen.

I tryed to configure it by the comand prompt, but i can't find the monitor model in the list. After i change it to a regular plug and play monitor with the resolution of my monitor, it reseted to the previous configuration at the start.

I'm at level zero again.

---

### Post by shifty_powers on 2008-10-05
have you tried reconfiguring xconf with

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

in a terminal?

---

### Post by Kill-Screen on 2008-10-05
how too exacly?

---

### Post by shifty_powers on 2008-10-05
sorry, go Applications menu -> Accessories -> Terminal

cut and paste the command and press enter.

it will ask you for your password, and then follow the instructions...

---

### Post by Kill-Screen on 2008-10-05
i just get this mensage:

xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20091006002916

---

### Post by Kill-Screen on 2008-10-05
I could find this:
[http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html](http://ubuntulinuxtipstricks.blogspot.com/2008/04/faq-hardy-upgrade.html)

"The new Xorg is supposed to be all nice and hotplugable, but dpkg-reconfigure xserver-xorg is no more. /etc/X11/xorg.conf is also now very barebones. This is for the hotplugability. The correct way to configure this new version of X is with the xfix command. Changing resolution is done on the fly with xrandr."

What should i do?

---

