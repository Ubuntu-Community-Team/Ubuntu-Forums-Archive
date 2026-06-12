---
title: "Firefox Human FTP Icons"
date: 2007-08-15
forum: Outdated Tutorials &amp; Tips
---

### Post by alecjw on 2007-08-15
This howto explains how you can change your firefox FTP icons from:
[[img=http://img393.imageshack.us/img393/8908/oldiconsyt4.th.jpg]](http://img393.imageshack.us/my.php?image=oldiconsyt4.jpg)
to
[[img=http://img393.imageshack.us/img393/7554/newiconr3.th.jpg]](http://img393.imageshack.us/my.php?image=newiconr3.jpg)
(Human icons)
It just takes two simple steps.

1) Download the attached new-ftp-icons.tar.bz2 to your home folder.
2) Open a terminal and type:
```
sudo tar xjvf new-ftp-icons.tar.bz2 -C /usr/share/firefox/res/
```
And you're done! Now go to [ftp://ftp.gnu.org/]("ftp://ftp.gnu.org/") to test it!

If you want the old icons back, you can either do the same as above, but with old-ftp-icons.tar.bz2, or do the command:
```
sudo aptitude reinstall firefox
```
or if you're an apt-get fan,
```
sudo apt-get reinstall firefox
```

---

