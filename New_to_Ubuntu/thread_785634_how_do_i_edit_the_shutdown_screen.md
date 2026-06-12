---
title: "how do i edit the shutdown screen?"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by cpu_medic on 2008-05-07
ok heres my problem, when ever i hit the power down button, or my compy's power button, the screen that pops up only gives me 3 things to do. they are : log out    lock screen      switch user

      suspend       hibernate

ok i need to restart my compy all the time so how do i change this screen?

---

### Post by KIAaze on 2008-05-09
I found those two threads:
[http://ubuntuforums.org/archive/index.php/t-181719.html](http://ubuntuforums.org/archive/index.php/t-181719.html)
[https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/44585](https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/44585)

The second one (bug report) seems to be the most interesting one.
Apparently you have to "clean up your /etc/gdm/gdm.conf-custom" file.
> I had switched back to human before I posted those file's, but I also thought that I would clean up the gdm.conf-custom to see if that made a difference. And it did !!! I have my icons back. Thanks for your help,
Kiwinote


I suppose this means replacing it with the default one or one that works.
-The default one is in the [gdm package]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?word=gdm.conf-custom"). (simply reinstall gdm or extract it from the .deb package using dpkg -x)
-[The one on the bug report]("http://launchpadlibrarian.net/3007940/gdm.conf-custom") seems pretty clean.

And here's mine:

---

