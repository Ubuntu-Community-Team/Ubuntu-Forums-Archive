---
title: "[SOLVED] Real to MP3 and more"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by mbadawi23 on 2008-08-01
Hello all,
      Is there is a way on ubuntu 8.04 to convert .rm files to .mp3? and also I'm shopping for an mp3 player; would any one suggests a device and/or a linux program that achieves convenient syncing.

---

### Post by dca on 2008-08-01
As far as MP3 players go it's a tough call.  You can get an iPod to work w/ Rhythmbox, Banshee, GTKpod, and many others.  The thing that separates an iPod from other conventional MP3 players is the fact the iPod has its own file system per 'se and database.  It has to be formatted before use with iTunes but I believe GTKpod can perform this functionality.
 
iPod's still get recognized in GNU/Linux as block devices like external HDD(s), thumbdrives, etc but because of the weird directory locations it like music stored is a little weird.
 
Other (older) conventional MP3 players are basically formatted the same as a USB thumb-drive block device so it's just a matter of copying your files over in a recognized file format and file name...

---

### Post by diafanos on 2008-08-01
> **mbadawi23 said:**
> Hello all,
      Is there is a way on ubuntu 8.04 to convert .rm files to .mp3?

Yeah.
You can use **ffmpeg** (it's in repos, just type: **sudo apt-get install ffmpeg**)
and it supports many, many audio and video formats....(including .rm and .mp3)

---

### Post by vambo on 2008-08-01
You can use mplayer to write the rm stream to a .wav. Once you have that you can use your favourite tool to convert to mp3.

---

### Post by LowSky on 2008-08-01
iRiver makes some very nice Portable players that can play many formats. Also iPods can have there software changed out with [ipod linux]("http://ipodlinuxinstl.sourceforge.net/") that can play even more formats

heres a list of players off [Newegg.com]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=2100080023&bop=And&Order=REVIEWS"), read the reviews it helps when choosing

---

### Post by knightcoder on 2008-08-01
Check this out: This is Samsung's newest MP3 player. Its a touch screen and kicks a**

[http://www.engadget.com/2007/08/14/samsungs-yepp-yp-p2-touchscreen-dap-with-bluetooth/](http://www.engadget.com/2007/08/14/samsungs-yepp-yp-p2-touchscreen-dap-with-bluetooth/)

---

### Post by forger on 2008-08-01
I think you can use **[soundconverter]("apt://soundconverter")** to convert .rm to .mp3 (and more) :)

---

