---
title: "Whats the difference between Ubuntu KDE Commands and GNOME Commands ?!"
date: 2012-05-12
forum: New to Ubuntu
---

### Post by IRhQ on 2012-05-12
Hi , How r u friends ?!
Can any one Change these KDE commands to GNOME Commands ?!

1
fix-splash

2
rm /root/.kde/cache-root/icon-cache.kcache

3
rm /root/.kde/cache-root/plasma_theme_Volatile.kcache

4
rm /root/.kde/cache-bt/icon-cache.kcache

5
rm /root/.kde/cache-bt/plasma_theme_Volatile.kcache

6
rm -rf /tmp/vmware-root

---

### Post by coffeecat on 2012-05-12
@IRhQ, some of those commands suggest that you have been running the KDE GUI desktop while logged in as root. Is this correct? Since this is a very unwise thing to do, I think we need to clarify this point before blindly translating commands for you.

---

### Post by jtarin on 2012-05-12
The "rm" command can be found by typing "man rm" (without quotes) in a terminal. The fix-splash seems to be a command for a certain application.
Maybe you would explain why you would like to do this? As coffeecat says "you have been running the KDE GUI desktop while logged in as root".
The "why" of this is important before you start using the "rm" command.

---

