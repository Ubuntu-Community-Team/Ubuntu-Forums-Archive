---
title: "How to prompt information from user during postinst?"
date: 2009-06-01
forum: Packaging and Compiling Programs
---

### Post by iiska on 2009-06-01
How to prompt user for information from postinst script? The prompt should use GUI or ncurses dialog if any of those are available and fallback to commandline like Ubuntu packages do it.

I'm sure that there is some general method for this, but can't find any clues from other source packages. (For example xorg-server package contains this functionality when creating config.)


Edit: The keyword was debconf, and found out this tutorial: [http://www.fifi.org/doc/debconf-doc/tutorial.html](http://www.fifi.org/doc/debconf-doc/tutorial.html) which probably solves this for me.

---

