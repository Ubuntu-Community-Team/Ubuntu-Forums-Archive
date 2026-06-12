---
title: "Help with My Geforce 6200 - and Dual Screens"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by Laticpot on 2008-10-05
Hi all,

This is my first post and I am a real newbie.

I have a Geforce 6200 in my computer and 2 monitors.

I have just created a dual boot system with this at the heart and 2 monitors running off of the one card.

Unfortunatly they will both run in Windows, but only one works in Ubuntu.

Could anyone help me.

I have this driver installed I think - NVidia binary X.Org driver ('new' driver)

Thanks in advance

Tim Rourke

---

### Post by fooman on 2008-10-05
you can configure dual monitors in nvidia-settings.  you need to be root to make the changes, so run the following in a terminal:

```
gksudo nvidia-settings
```

you should be able to configure the other monitor under the "x sever display configuration" section.  click apply after the changes,  then "save to x configuration file" to make it stick.

logout and back in again (alt-ctrl-backspace) to see if it worked.

hope that helps

---

