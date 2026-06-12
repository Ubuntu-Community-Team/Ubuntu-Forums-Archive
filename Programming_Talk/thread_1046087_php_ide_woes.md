---
title: "php ide woes"
date: 2009-01-21
forum: Programming Talk
---

### Post by KCormier on 2009-01-21
Hey all.  I run an ubuntu server and most of my developers use ubuntu.  I'm looking for a decent IDE that will allow most of my developers to debug.  Nearly all of my developers will switch to whatever ide I ask so I'd like to know what people are using to develop php applications.  The server is behind a nat with just port 80 forwarded (i can forward more if necessary).  I'm really so lost as i've been fighting with quanta & gubed for a while...and i hacked together xdebug and webgrind, only to realize it doesn't do what i want... nothing seems to work.  Any advice?

-Kevin

---

### Post by sonicb00m on 2009-01-21
Zend Eclipse is pretty hot.

There are also plugins to handle PHP within eclipse.

---

### Post by KCormier on 2009-01-21
Forgot to mention...I'm hoping for something free here.

---

### Post by sonicb00m on 2009-01-21
php plugins with eclipse then (as mentioned above).

---

### Post by KCormier on 2009-01-30
I downloaded and am testing aptana.  The ide is fantastic and free.  It works on a plugin module basis so you have to first install the php plugin (quick and super easy!)  In also has officially supported plugins for ruby and subversion, among other things.  The plugins are developed by the same company and really work well (not like some of the plugins you get for other stuff).

There is a paid version with advanced uploading features (built in ftp, sftp, etc).  Built in web server with debugger and javascript debugger.  Plenty of supported ajax libraries although for now it's missing xajax unfortunately.  The php module went gold less than 2 months old at the time of this writing.  Give it a try and if you like it, it's definitely worth supporting and spending $100.

---

