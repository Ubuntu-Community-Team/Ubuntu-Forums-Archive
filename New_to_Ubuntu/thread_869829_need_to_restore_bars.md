---
title: "need to restore bars"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by mnimmo1986 on 2008-07-25
i have just installed a login screen and when restarted i now only have a picture in the desktop no bars or anything have look at restoring them on google but it asks to use the terminal (alt + f2) however this does not work the only things that i can open are help and firefox (via f1) and the desktop settings

how do i get the bars back at the top and bottom of the screen?

thanks in advance

Mike,

---

### Post by mattismyname on 2008-07-26
To get to the terminal (text console) you actually need to do <ctrl>+<alt>+F2

---

### Post by RealPSL on 2008-07-27
Not necessarily. When you are going to login you can select options > session > failsafe terminal and get a terminal. Once you have the terminal you can restore the original ubuntu gnome interface by renaming the following files in your home directory.

 ```

$ mv .gconf .gconf.bak
$ mv .gconfd .gconfd.bak
$ mv .gnome2 .gnome2.bak
$ mv .gnome2_private .gnome2_private.bak
$ mv .gnome .gnome.bak
$ mv .themes .themes.bak

```

This will restore the original ubuntu desktop configuration if you are okay with that. This is also useful after upgrading and wanting to try the default interface.

---

