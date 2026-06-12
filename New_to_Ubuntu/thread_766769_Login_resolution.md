---
title: "Login resolution"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by SpinningAround on 2008-04-25
I update from ubuntu 7.10 to ubuntu 8.04 and most seem to work quite fine so far, but there is one thing and that is the resolution of the login screen. The resolution seem to low since the screen wont show the entire view of the login screen, I don't think that there is a problem with the general resolution since both the desktop and the nvidia logo (show up first) are fine. Is it possible to change the resolution on the login screen?


Not same computer as in sign.

---

### Post by milosz.galazka on 2008-04-25
One example how to change first/login X resolution is to edit /etc/X11/xorg.conf

Just look at screen section:
```
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024"
    EndSubSection
EndSection
```
and modify it as you wish but first make a backup :)

---

### Post by dokdoom on 2008-04-25
Is it just the login screen that is having the resolution issue?

---

### Post by milosz.galazka on 2008-04-25
> **dokdoom said:**
> Is it just the login screen that is having the resolution issue?

I use nvidia driver, I changed X configuration file to keep always same resolution.

---

### Post by SnakeHips on 2008-04-25
> **SpinningAround said:**
> I update from ubuntu 7.10 to ubuntu 8.04 and most seem to work quite fine so far, but there is one thing and that is the resolution of the login screen. The resolution seem to low since the screen wont show the entire view of the login screen, I don't think that there is a problem with the general resolution since both the desktop and the nvidia logo (show up first) are fine. Is it possible to change the resolution on the login screen?


Not same computer as in sign.

You might like to try adding the following.....from terminal

but first take a backup

```
cd /boot/grub
sudo cp menu.lst menu.bak

```

then

```
sudo gedit /boot/grub/menu.lst
```

I'm thinking you may need to add the following entry in red (scroll across)


```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1823ba20-6cdc-4476-ad39-763e28593824 ro quiet splash [COLOR="Red"]vga=791[/COLOR]
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
```

---

