---
title: "Help switch from Unity to Gnome"
date: 2016-06-25
forum: Recurring Discussions
---

### Post by spayman2 on 2016-06-25
**Hi,**
Why are we no longer able to decorate windows, doesn't that take away one of the major benefits of using a Linux distro rather than a Windows.
For example I can't even change window-controls to the right rather than the left.
Please consider changing back to Gnome or some other DE or at least invest in making Unity more open to customization.

Now I need help switching to gnome, I know how to install and switch to it, but I'm afraid of system instability or GUI errors.
Also will I be able to update ubuntu in the future without issues?
Currently using Ubuntu 16.04

**Thanks**

---

### Post by yetimon_64 on 2016-06-25
> **spayman2 said:**
> **Hi,**
Title says it all, Unity sucks, Why are we no longer able to decorate windows, doesn't that take away one of the major benefits of using a Linux distro rather than a Windows.
For example I can't even change window-controls to the right rather than the left.
Please consider changing back to Gnome or some other DE or at least invest in making Unity more open to customization.

Now I need help switching to gnome, I know how to install and switch to it, but I'm afraid of system instability or GUI errors.
Also will I be able to update ubuntu in the future without issues?
Currently using Ubuntu 16.04

**Thanks**

Rather than expecting the OS to change drastically why don't you just install another DE alongside Unity and use that. Log into the other DE once and the log in screen remembers your choice thereafter.

I have a choice here of Unity, XFCE (an xubuntu or ubuntu studio xfce session) and Gnome 3 etc from the log in screen. You can install ubuntu and then add other DEs that suit your needs. For example to install an xfce session (windows controls on the right etc, see attached screenshot of my browser with window controls on the right in an xubuntu session.)
```
sudo apt-get install xubuntu-desktop
``` OR for a more simple install ...
```
sudo apt-get install xfce4
``` This second code won't draw in so many alternate applications just the plain xfce4 session.

**Edit**: some more info if you choose to add xubuntu or xfce, once installed log out and at the lightdm log in screen click on the cog icon at the side of the log in dialog you will get a drop down selection of sessions there to choose from (dependent on what extra DEs you install). Once you choose a different session the log in screen will always use it until you change it manually again the same way.
[B]
Edit[/B] 2: just noted the title a bit better and noticed gnome is mentioned there, try also ...
```
sudo apt-get install gnome
``` but if I recall correctly, gnome3 also uses window controls on the left. If you want the older style of gnome desktop you may need to try a "mate-desktop" DE install.

---

### Post by Geoffrey_Arndt on 2016-06-25
Or just do a fresh install of Xubuntu, or Kubuntu 16.04.     Kubuntu is already especially customizable.   No need to complain about Unity when there are so many other options available.   I run Unity on 3 of 5 systems, the others are Xubuntu and Mate.

---

### Post by yetimon_64 on 2016-06-25
> **Geoffrey_Arndt said:**
> Or just do a fresh install of Xubuntu, or Kubuntu 16.04.     Kubuntu is already especially customizable....

@ OP, if you are "afraid of instability" etc this is actually a better idea than my previous post.

---

### Post by spayman2 on 2016-06-25
Thank you very much!
Side note though, why I complain is because installing a different DE will result into conflicts with Unity, and some programs will have GUI bugs. also little problems when updating versions later.
I just preferred if Ubuntu interface came out customizable out of the box.
Anyways, I ended up installing Gnome3.
Thanks for correcting my title and thank you for the help.

---

### Post by spayman2 on 2016-06-25
Kubuntu is EXTREMELY unstable on my machine, it kept crashing completely and requiring a hardware reboot at random moments.
Thanks for the suggestion though.

---

### Post by Omar_Jair on 2016-06-25
You can try a fresh install of Ubuntu Gnome (which is slightly better than unity but only by a little bit), I use MATE since it is GNOME 2 based.
You can also convert from Unity to XFCE following the steps here
[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

---

### Post by wildmanne39 on 2016-06-26
Moved to recurring!

---

