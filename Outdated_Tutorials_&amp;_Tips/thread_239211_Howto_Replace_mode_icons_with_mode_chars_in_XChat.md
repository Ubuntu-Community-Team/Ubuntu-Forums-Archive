---
title: "Howto: Replace mode icons with mode chars in XChat"
date: 2006-08-18
forum: Outdated Tutorials &amp; Tips
---

### Post by crackseller on 2006-08-18
[[IMG]http://img219.imageshack.us/img219/8782/xchatsg5.th.png[/IMG]](http://img219.imageshack.us/my.php?image=xchatsg5.png)

This patch will change your [XChat]("www.xchat.org") user list. It will remove the user mode icons (these green, blue, ..., yellow ones representing the modes i.e. op, hop, ..., voice). Then it will add the user mode character representing the mode to the user's nick name (see screenshot above). It supports the user mode characters '~', '&', '@', '%' and '+'. I don't know if there are more, if so, please let me know. Also, let me know if you experience any bugs after the patch that might correspond with the changed user list.

Dependencies:

- patch
- XChat 2.6.6 Source (official, [www.xchat.org](www.xchat.org))

Usage:

1. Extract the source
2. Move/Copy userlistgui.c.patch to xchat-2.6.6/src/fe-gtk/
3. Change directory to xchat-2.6.6/src/fe-gtk/
4. Apply the patch:
```
patch -p0 userlistgui.c < userlistgui.c.patch
```
5. (optional if you've done that before)
```
./configure
```
6. build
```
make
```
7. install
```
sudo make install
```

Have fun and let me know if you like it! :)

---

### Post by h1web on 2006-08-19
nice hack.

---

### Post by xen on 2006-08-20
Cheers love!

---

### Post by luumanh on 2007-05-21
:)

---

### Post by XTREEM|RAGE on 2007-05-23
nice 1, need to remember this 1 ;D

---

