---
title: "[SOLVED] Updating OpenOffice"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by adobrakic on 2008-11-24
I have absolutely NO idea how to do this. I've downloaded the .deb from the OO website, but it comes with like 40 .debs.

I've tried installing all of them one-by-one (is that stupid?), but it comes down to one dependency error: ooobasis3.0-en-US, which I appear to have.. but I get that same error when trying to install that file, so I guess it isn't the correct one.
:lolflag:

---

### Post by Skripka on 2008-11-24
Don't torture yourself.

Simple and easy does the trick:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by adobrakic on 2008-11-24
Wow, next time I'm just going to swallow my pride and ask beforehand.
Thanks a lot

---

### Post by AnimalMagic on 2008-11-25
Now tell us the easy way in 8.04 :-)

---

### Post by frankleeee on 2008-11-25
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) hardy main

Put these in the 3rd party in software sources or put them in the apt source list. This is a direct down load from launchpad and will install directly through update manager.

---

