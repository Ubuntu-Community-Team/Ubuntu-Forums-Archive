---
title: "Python downloading from a torrent"
date: 2009-10-11
forum: Programming Talk
---

### Post by normankev on 2009-10-11
I am writing a python program, but am wondering, how would i download from a torrent using python? I have read up on deluge-torrent's libtorrent python implementation but really do not understand how to use it.

Any help appreciated
Kevin

---

### Post by Can+~ on 2009-10-11
I did [FONT="Courier New"]apt-cache show python-libtorrent[/FONT]

And found a link to the webpage of the developers (rasterbar)
[http://www.rasterbar.com/products/libtorrent/python_binding.html](http://www.rasterbar.com/products/libtorrent/python_binding.html)

---

### Post by bobince on 2009-10-11
You can also just grab BitTorrent Mainline [sources](http://www.bittorrent.com/btusers/download/directory-list/archive) (eg. BitTorrent-5.2.2.tar.gz), as the original BitTorrent client was written in Python.

It's not the most pleasant of codebases, but at least it's pure Python so you don't have to go around compiling dependencies. Look at bittorent-console.py to get an idea of how to import and use BitTorrent from another script/module.

---

