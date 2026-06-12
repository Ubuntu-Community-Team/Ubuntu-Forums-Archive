---
title: "Xfce - 2 questions"
date: 2011-10-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Kronalias on 2011-10-11
Let's not knock Unity, let's move on ...

Question 1

Y'know the xfce desktop thing - the one with a mouse (rat?) in the middle?
[
   it's what you get if you:
   sudo apt-get install xfce4
]

That was working well, but it now keeps reverting to the Ubuntu background - the purply thingy.

Anyone know why?

Question 2

It would be *really* nice if I could boot this PC into xfce.

Right now on booting it ends up in Unity, then I have to log out / log in  and then choose xfce on the way in.

I'm obviously doing something really stupid, but I can't work out what it is - so if anyone would care to help me that would really be appreciated!

Cheers, K

---

### Post by Stephan Volkmann on 2011-10-11
have a look at etc/lightdm/lightdm.conf "user-session=**x**ubuntu"

the little x takes it

---

### Post by LADmaticCA on 2011-10-11
It could be the gnome-settings-daemon loading that's causing your background to change. I was having this problem with my openbox setup. Since you're using xfce you should be able to safely remove it.
```

sudo apt-get remove gnome-settings-daemon
```

---

### Post by Toz on 2011-10-11
> **Kronalias said:**
> Question 2

It would be *really* nice if I could boot this PC into xfce.

Right now on booting it ends up in Unity, then I have to log out / log in  and then choose xfce on the way in.

I'm obviously doing something really stupid, but I can't work out what it is - so if anyone would care to help me that would really be appreciated!

Cheers, K

Try creating a **~/.xinitrc** file in your home directory with the following contents:
```
#!/usr/bin/env bash
exec startxfce4
```
...and make the file executable:
```
chmod +x ~/.xinitrc
```

You might also want to link .xsession to this file so that gdm (if you use it) works correctly:
```
ln -s ~/.xinitrc ~/.xsession
```

Reference link: [https://wiki.ubuntu.com/CustomXSession]("https://wiki.ubuntu.com/CustomXSession")

---

### Post by Kronalias on 2011-10-12
Thanks all! I can now boot automatically into xfce, and the answer is a bit of everything above, but simpler...

From a brand new install of 11.10 I did the following:

Install xfce:
sudo apt-get install xfce4

Reboot, then log out and log back in to xfce

Now edit /etc/lightdm/lightdm.conf and change the line ...
user-session=ubuntu
... to ...
user-session=xfce

Reboot, and you're automatically logged into xfce

---

### Post by Kronalias on 2011-10-12
If anyone bothers to read this then please save yourself a lot of heartache.

If you want xfce then don't put it on top of Ubuntu - there are a lot of idiot interactions that are just waiting to screw you up as you get the full benefit of everything for Ubuntu and everything for xfce all at the same time.

E.g. Thunar v Nautilus. If you don't believe me try running Nautilus on xfce on Ubuntu. Don't do this unless you know how to get out of a tangle.

If you want xfce then then it looks (well, it does to me, anyway) as if the sensible way to go is the daily build for Xubuntu 11.10:
[http://cdimage.ubuntu.com/xubuntu/daily-live/20111010/](http://cdimage.ubuntu.com/xubuntu/daily-live/20111010/)

---

### Post by kansasnoob on 2011-10-12
> **Kronalias said:**
> If anyone bothers to read this then please save yourself a lot of heartache.

If you want xfce then don't put it on top of Ubuntu - there are a lot of idiot interactions that are just waiting to screw you up as you get the full benefit of everything for Ubuntu and everything for xfce all at the same time.

E.g. Thunar v Nautilus. If you don't believe me try running Nautilus on xfce on Ubuntu. Don't do this unless you know how to get out of a tangle.

If you want xfce then then it looks (well, it does to me, anyway) as if the sensible way to go is the daily build for Xubuntu 11.10:
[http://cdimage.ubuntu.com/xubuntu/daily-live/20111010/](http://cdimage.ubuntu.com/xubuntu/daily-live/20111010/)

I've found the same is true with Lubuntu/LXDE now. Just too many things get flaky when installing a different DE on top of Ubuntu with gnome3 in the mix, unity may play a bit into the equation also. To me it's simply not worth the hassle to try and straighten things out :)

If you want Xubuntu just install it, likewise with Lubuntu. If you're not sure build a multi-boot :)

---

