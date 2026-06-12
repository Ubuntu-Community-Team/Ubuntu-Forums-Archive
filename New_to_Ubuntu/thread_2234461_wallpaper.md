---
title: "wallpaper"
date: 2014-07-14
forum: New to Ubuntu
---

### Post by trav9595 on 2014-07-14
when I set a picture as desktop background it never takes.....why not??

---

### Post by yancek on 2014-07-14
The link below has a brief explanation.  In Xubuntu as in some of the other Ubuntus, you change from the System Settings, Appearance.  Is this an actual install to a hard drive or a Live CD on a flash/CD/DVD?  That's expected behavior on a Live CD, read-only filesystem so if you have an actual install, you need to post specifics on what you have done so someone can tell you how to correct it.

[http://www.dedoimedo.com/computers/xubuntu-pimp.html](http://www.dedoimedo.com/computers/xubuntu-pimp.html)

---

### Post by Impavidus on 2014-07-15
In Xubuntu 14.04, that would be Settings &#8594; Desktop &#8594; Background. Of course the image has to be available and a valid image file (jpeg is OK, as is png I think) and to make it work the next time you log in it has be stored on a partition that is mounted at a fixed location at the moment of login.

Alternatively, using the more complicated way it is possible to set the background using xfconf (channel xfce4-desktop, property /backdrop/screen0/monitorLVDS1/workspace0/last-image, set to the path to the image) or, even more complicated, from the command line, which allows you to set it from scripts.

---

