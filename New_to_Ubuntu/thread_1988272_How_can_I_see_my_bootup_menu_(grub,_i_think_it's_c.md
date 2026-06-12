---
title: "How can I see my bootup menu (grub, i think it's called) without booting up?"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by hanzj on 2012-05-27
Hello, while logged in, is it possible to see the my bootup list that appears after I start the computer and before I get to the login screen for either linux or windows?

---

### Post by drs305 on 2012-05-27
You can run this to see the menu items:
```
grep "menuentry" /boot/grub/grub.cfg
```

You can look at it with a text editor with:
```
gksu gedit /boot/grub/grub.cfg
```

---

### Post by hanzj on 2012-05-27
thanks, drs305. just what i was looking for.

---

