---
title: "Xfire plugin Pidgin"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Socca on 2008-08-09
Hey!

I love xfire and I want to be able to talk to people through xfire while i am working on my laptop. Now that I have ubuntu, I have heard it's hard to use xfire itself. But I found this Xfire plugin for the Pidgin messenger and I would really like to have it installed. I have seen other similar threads on this forum about the plugin but not really on how to install it since I am new to Ubuntu.

I downloaded the newest file gaim-xfire-0.6.1~20071109.tar.bz2 from [http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/) 

How would I get around to installing this?

Thanks

Socca

---

### Post by Socca on 2008-08-09
Anybody with some help?

---

### Post by SZ07 on 2008-08-09
I have never played around with xfire but it looks like the file you have downloaded is not the latest.

Go here: [http://gfire.info/downloads/](http://gfire.info/downloads/)

Click on the DEB button (it will download a .deb package)

One the package is downloaded, just double click it and then press install package and you should be set.

---

### Post by SlalomMan on 2008-08-10
Whenever I do a fresh install of ubuntu, I use this release:

[http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb](http://gfire.sourceforge.net/snapshots/gaim-xfire_0.6.1~20071109-pidgin-2.2-gutsy1_i386.deb)

Even though it says its for hardy, it works. I can vouch for it; the only thing that i have found not to work is in-game support (but you probably won't be playing too many games on linux anyways)

The snapshots page that I got this from is here:
[http://gfire.sourceforge.net/snapshots/](http://gfire.sourceforge.net/snapshots/)

EDIT: I misread your post; when you have options of different formats to download, you should probably download the .deb file; .tar.bz2 files have to be uncompressed and might not work.

If you want to still use the file you downloaded, you should extract it, and then from a terminal run:

"./configure"

"make"

"make install"

If any of these commands don't go through, read the error messages, you might have to run them as sudo + command.

---

### Post by Socca on 2008-08-10
Ah! Deb files are much easier to install :D Thx. Now it all works. But SZ07, gfire.info site is down.

Thanks guys!

---

### Post by FiskFisk33 on 2009-01-20
I know this thread is getting old but it is what comes up on google
so i just thought i should add this:

[http://gfire.site40.net/](http://gfire.site40.net/)

[http://gfire.site40.net/?page_id=24/](http://gfire.site40.net/?page_id=24/)

;)

---

