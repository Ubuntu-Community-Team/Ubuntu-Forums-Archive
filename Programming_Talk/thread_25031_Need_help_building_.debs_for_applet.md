---
title: "Need help building .debs for applet"
date: 2005-04-09
forum: Programming Talk
---

### Post by bsoft on 2005-04-09
I've written a wireless configuration applet ([http://gtkwifi.sf.net](http://gtkwifi.sf.net)) and would like to get it deb-packaged to make it easier to install. It's written in Python, and it provides a GTK/GNOME interface to configure wireless network connections: displaying a list of available networks, storing WEP keys, etc.

Currently, the applet uses a Python-based install script. I've read some HOWTOs on Debian packaging, but they seem to be Debian-specific and compiled-language-specific. I don't have a makefile, and I'm intending to distribute for Ubuntu.

If anyone could help out, it would be greatly appreciated. I'd love to see my app become a part of the stock Ubuntu distro - I believe that it could be a boon for usability.

---

### Post by az on 2005-04-09
Google for the debian new maintainers guide.

Look on the wiki for the MOTU (masters of the universe) and how to contribute.

Also, there is a nice page about making packages without debhelper (by hand) from debian women.  You can google for that.  It is a good read.

---

