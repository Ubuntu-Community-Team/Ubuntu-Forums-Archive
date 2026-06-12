---
title: "how to force log in and desktop switch upon reboot"
date: 2013-08-27
forum: New to Ubuntu
---

### Post by micahpage on 2013-08-27
I have a laptop with ubuntu 12.04 on it, with numerous desktops. The main one i use on it is gnome 3, which works fine. The computer was slow lately so i tried uses a lighter desktop. So i switched over to xfce to see how it would run in there. But when the desktop loaded xfce, xfcxe freezes. However when using Cntrl + Alt + F2 and logging in to reboot. However on reboot it now auto logs into the desktop xfce which is apparently messed up. The GUI isnt working at all. The only thing i can access is Cntrl + Alt + F2 on the computer.

I cant figure out how to force the computer to stop auto log in and auto log into xfce. I want to switch it back to gnome 3 desktop.

How can i do this via command?

EDIT:
I also seem to not be able to log in as root

---

### Post by micahpage on 2013-08-27
i resolved the problem by installing a new desktop to the laptop 
kde-workspace
which it set that as default, and allowed me to login, allowing me to change it back to gnome 3/ gnome-session
But now i get the KDE log in screen each time logging in. Not a biggie,

But how would i resolve this via terminal without installing a new desktop?

---

### Post by GwL3eNC on 2013-08-27
Normaly ubuntu use the lightdm display manager (unity greeter). It's config file is in /etc/lightdm/lightdm.conf.
One option is

user-session=ubuntu

which starts ubuntu on login. I use kubuntu and

user-session=kde

starts this mode. Hope it brings you further.

[https://wiki.ubuntu.com/LightDM](https://wiki.ubuntu.com/LightDM)

---

### Post by micahpage on 2013-08-28
ah yeah ok.
I see an auto login in value in there

thank you

---

