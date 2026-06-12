---
title: "Howto: Speed up gnome on older computers"
date: 2006-07-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Johnsie on 2006-07-12
There's a few ways to speed up your gnome desktop:

> sudo gconf-editor /apps/nautilus/preferences

When that comes up.. uncheck the show_desktop box

That stops nautilus from managing the icons on your desktop. If you really need your icons you can install another lighter desktop manager like xfdesktop4  to show them by doining the following:

> sudo apt-get install xfdesktop4 


Another way I've heard that might speed things up a little is:
(in terminal)

> sudo gedit /etc/sysctl.conf


and add the line:
Quote:
> vm.swappiness=10

If these methods work you should see some improvement after reboot.

---

### Post by harisund on 2006-08-14
Awesome. Thanks for this post.
 
I have been looking for something like this. Do you know of any more ideas to make Gnome faster? 

There is also an option for making metacity faster by asking it to use lesser resources.

---

### Post by parktownprawn on 2006-08-14
To make moving widows around less demanding on your computers resources try:

```
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true
```

this will make windows appear as wire-frames when you move them

---

### Post by MyBigToe on 2006-08-14
thanks!

---

### Post by regeya on 2006-09-20
> **parktownprawn said:**
> To make moving widows around less demanding on your computers resources try:

```
gconftool-2 --type bool --set /apps/metacity/general/reduced_resources true
```

this will make windows appear as wire-frames when you move them

Awesome.  Hadn't seen that before.  Another option is to use Openbox, which can be used as a drop-in replacement.  Not that it can use Metacity themes or anything like that; it can act as a windowmanager for GNOME and nearly everything works right, though.  Search on the forums for Openbox; there's a nice HOWTO around somewhere on setting up OB to integrate more seamlessly into GNOME.

---

