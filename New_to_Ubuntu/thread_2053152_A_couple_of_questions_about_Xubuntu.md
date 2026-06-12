---
title: "A couple of questions about Xubuntu"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-09-04
I've just (luckily) been able to resurrect my old laptop and upgrade to 12.04. I do however have a couple of questions ... It's a Fujitsu Amilo 2727.

(1) Funny. Previously I was having problems with a dark screen ... now the screen seems incredibly bright for my poor eyes. The function keys which are marked to deal with this don't seem to work in Xubuntu. Is there any other way I can make things a little less eye watering?

(2) I don't seem to be able to (like I can on Windows for example) find an easy way to see how much space I have on flash drives or even my hard disk. Can someone tell me how to do this please?

Many thanks in advance.

---

### Post by doktorOblivion on 2012-09-04
Not sure how to help on #1, but for #2 consider installing gparted, it should be able to give you and idea of the disk configuration for all of your drives.

---

### Post by black veils on 2012-09-04
try changing the backlight in settings manager >> power manager >> ac and on battery, on the monitor tabs. then use the function keys to blindly set it to darkest setting (press many times), then blindly turn the brightness up by pressing once up. reboot and see if there is a change.

as for "easy" way to see free space left on drives, i dont know what that means for you. but in thunar file manager, it says at the status bar on the bottom (or you can right-click within the opened drive, and go to properties).

---

### Post by pqwoerituytrueiwoq on 2012-09-04
go into your keyboard setting and look at the shortcut tabs yuo can make the keys work
you just have to google up a few commands

---

### Post by Merrattic on 2012-09-04
CLI:
```
xrandr --output "YourScreenName" --brightness "A number between 0 & 255"
```
this is in software only so may want to try **xbacklight**

---

### Post by hamstermoon on 2012-09-05
> **black veils said:**
> try changing the backlight in settings manager >> power manager >> ac and on battery, on the monitor tabs. then use the function keys to blindly set it to darkest setting (press many times), then blindly turn the brightness up by pressing once up. reboot and see if there is a change.

as for "easy" way to see free space left on drives, i dont know what that means for you. but in thunar file manager, it says at the status bar on the bottom (or you can right-click within the opened drive, and go to properties).

Thankyou. Both of those seem to work ... and a friend suggested I install Disk Utility, which I have also done. Everything seems to be working nicely now.

---

