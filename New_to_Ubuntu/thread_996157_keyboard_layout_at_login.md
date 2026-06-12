---
title: "keyboard layout at login"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by Razorrr on 2008-11-28
Today I received my us international qwerty keyboard. I changed my settings but when i want to login I still get my azerty layout.

I tried to reconfigure the xserver and i tried to edit the xorg.conf file
but both times it did nothing.

Can anyone help?

kind regards

---

### Post by Elfy on 2008-11-28
I've not need to do this yet - so not sure but from the release notes - > The X.Org configuration file (/etc/X11/xorg.conf) still has InputDevice entries for the mouse and keyboard, but they are ignored now because input-hotplug is used. The keyboard settings now come from /etc/default/console-setup; to change them please use sudo dpkg-reconfigure console-setup. After that, HAL and X need to be restarted (e.g., by rebooting your system).

That file for me does include - 
> 
# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.
XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""


Try the command it gives = 

```
sudo dpkg-reconfigure console-setup
```

---

### Post by Razorrr on 2008-11-28
Thank you very much for the quick reply.
It works fine now.

---

