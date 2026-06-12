---
title: "Need help bad"
date: 2020-12-14
forum: New to Ubuntu
---

### Post by billywyatt2 on 2020-12-14
I downloaded and installed Ubuntu 20.04.1 LTS on my desktop computer.
I later opened a terminal and typed ```
lsb_release -a
``` to confirm my OS
which stated Ubuntu 20.04.1 "focal"

The problem i have is that i suffer from very bad eyesight and have tried and tried to make the mouse/pointer bigger
and have failed miserably at each and every attempt.

I even tried to install Ubuntu tweaks via Synaptic and failed at that as well.

When i open up Ubuntu in the top left-hand corner at the top of the screen just the menu icon and the Firefox icon nothing else.

Would be very grateful for any help and advice

---

### Post by Frogs Hair on 2020-12-14
The cursor size can be changed from settings>universal access > cursor size. Right click on the desktop and select change desktop background to open settings. When settings are open scroll down to universal access. 

If you need gnome-tweaks installed try from the terminal or software center.
```
sudo apt install gnome-tweaks   
```

---

### Post by ActionParsnip on 2020-12-14
[https://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size](https://askubuntu.com/questions/126491/how-do-i-change-the-cursor-and-its-size)

dconf-editor lets you make the pointer bigger, nice and easy

---

### Post by billywyatt2 on 2020-12-15
Hello Frogs Hair

I did exactly as you suggested in your post but all it did was open up the Appearance Preferences window and not the Settings window.
There was no mention what-so-ever of Universal Access.

On my desktop in the top left-hand corner there are two options, Menu and Firefox.
I can click on Menu and scroll down the list until i come to Universal Access.

But Universal Access only gives me three options:

1} Magnus
2) Onboard
3) Screen Reader

So i am still trying to use an almost invisible mouse/pointer.

I did think that by installing GNOME-Tweaks that i would be able to do what i wanted from there.
But unfortunately it was not so.

Anyway, a big thanks for taking the time out to help me.

Regards Billy

---

### Post by billywyatt2 on 2020-12-15
Finally!!

I managed to make the mouse/pointer bigger by doing the following:

I went to System Settings and from there in the new window that appears i typed "Appearance"
in the Filter search box (top left) now click on Appearance -> Customize -> Pointer

now select MATE (black) and that's it.

Hope this helps someone

---

### Post by Frogs Hair on 2020-12-16
> **billywyatt2 said:**
> Hello Frogs Hair

I did exactly as you suggested in your post but all it did was open up the Appearance Preferences window and not the Settings window.
There was no mention what-so-ever of Universal Access.

On my desktop in the top left-hand corner there are two options, Menu and Firefox.
I can click on Menu and scroll down the list until i come to Universal Access.

But Universal Access only gives me three options:

1} Magnus
2) Onboard
3) Screen Reader

So i am still trying to use an almost invisible mouse/pointer.

I did think that by installing GNOME-Tweaks that i would be able to do what i wanted from there.
But unfortunately it was not so.

Anyway, a big thanks for taking the time out to help me.

Regards Billy

Should have ask what Ubuntu desktop you had installed. The settings vary on different Ubuntu Flavors .

---

