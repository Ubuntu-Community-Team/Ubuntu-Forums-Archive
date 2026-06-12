---
title: "Howto change dependencies"
date: 2005-12-30
forum: Outdated Tutorials &amp; Tips
---

### Post by bean1975 on 2005-12-30
While installing monkey audio .deb files from [http://www.rarewares.org](http://www.rarewares.org) I found that they failed a minor dependency libstdc++6 (>= 4.0.2) was needed while I had 4.0.1-4ubuntu9, so I decided that I'll try whether it works -- the difference seemed minor. Warning: this may be dangerous to your system. You may end up with a system that is unrepairable. You are off all tracks and on your own if you try this. LIkely apt will awake Godzilla to eat you :rolleyes: .

With that said, dependency information is stored in a file called control. Follow the following simple steps;

[LIST=1]
[*]dpkg-deb -x foo.deb tmpdir
[*]dpkg-deb --control foo.deb tmpdir/DEBIAN
[*]nano tmpdir/DEBIAN/control 
[*]dpkg -b tmpdir hacked.deb
[/LIST]

and there you are, your shiny new .deb file. And yes, monkey audio works :)

---

### Post by MillDaKill on 2010-05-25
Thanks for this guide.  I had to rebuild some deb files for my printer.

---

### Post by posburn on 2010-11-28
HOLY CRAP! You are my hero :)

I had a problem with a package that needed libc6-i686. With the upgrade to Maverick, this package no longer exists per se (it's now just libc6).

Followed your guide and voila - problem solved. God I love Linux.

Thanks much (if you're still around from '05)!

---

### Post by ki4jgt on 2011-04-28
Thanks for THIS!! Boxee needed a dependency which was changed :-)

---

