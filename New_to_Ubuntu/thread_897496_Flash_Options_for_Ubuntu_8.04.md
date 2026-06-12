---
title: "Flash Options for Ubuntu 8.04"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by padrejeff on 2008-08-22
Completed my dual boot install (32 bit) with no real problems (IBM T41).

Printer, wireless all work perfectly.

Flash?

It seem as though there are many options for flash. I need the easiest as I am terribly afraid of trashing something.

If I try to open a YouTube video, I am prompted to download Adobe Flash. If I so click, I am given options for Linux x86:

tar.gz
.rpm
YUM

Which of these should I choose, or is there some other option that you feel is better and that I can do without messing uip anything else??? (realy timid newbee here)

Thanks all............

---

### Post by silverglade00 on 2008-08-22
```

sudo aptitude install ubuntu-restricted drivers
```

That will get you pretty much all of the codecs, plugins, etc that you will need on the Internet.

In Linux, it is always better to install a program from the repositories for your distribution because they have been specifically tailored and packaged to it. In this case, the Flash player has been rolled into a package (along with some other plugins like Java) that is made for Ubuntu. If you are unsure of the name of a program in the repos, you can either open Synaptic and do a search for it, or use:
```
apt-cache search whatever-you-are-looking-for
```

There are times where you need to install a program from a website because it is not available in the repos, or you need a later version, or whatever. The best thing to do would be to ask on here if anyone else has been able to get it to work from that website. Maybe they have some pointers that will save you some trouble.

---

### Post by philinux on 2008-08-22
Install the flashplugin-nonfree from synaptic or

sudo apt-get install flashplugin-nonfree

Or
sudo apt-get install ubuntu-restricted-extras

to get all the other stuff like java.

---

