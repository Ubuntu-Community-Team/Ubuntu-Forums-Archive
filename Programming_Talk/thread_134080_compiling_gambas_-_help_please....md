---
title: "compiling gambas - help please..."
date: 2006-02-21
forum: Programming Talk
---

### Post by gregwa on 2006-02-21
Hi.  Hopefully I am posting in the correct place.  If not, please forgive me.

I'm currently running dapper and want to upgrade the version of gambas to the latest "stable" version.  Unfortunately, this requires me to compile it from source.  The gambas webpage says the following...

> Remember that you must install the following development packages : X11, QT3, KDE3, PostgreSQL, MySQL. The way to do that depends on your distribution.

Now, please understand that I'm a noob to the deep down goodies that linux provides (windows guy for years and years...I worked with Windows 2.0 ) so I don't really know what the development packages are that are being refered to.

Could someone point me to the proper packages that I should get?

Thanks in advance,

Gregwa

---

### Post by hod139 on 2006-02-21
[quote=gregwa]
Remember that you must install the following development packages : X11, QT3, KDE3, PostgreSQL, MySQL. The way to do that depends on your distribution.
Gregwa[/quote]

My guess is 
```

sudo apt-get install  libx11-dev libqt3-headers kdebase-dev postgresql-dev libmysqlclient14-dev

```

Again, these are just guesses and may be wrong.  If something is still missing, just look for packages with a -dev suffix.

---

### Post by gregwa on 2006-02-22
Thanks! :D

I'll give it a shot.

Thanks for responding!

---

