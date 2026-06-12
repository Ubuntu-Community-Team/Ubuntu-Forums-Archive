---
title: "laptop heating"
date: 2013-04-23
forum: New to Ubuntu
---

### Post by abhich on 2013-04-23
i installed Xubuntu 12.04 and its working perfectly. But the thing is, the temp stays ~65c . Is it normal ?

---

### Post by QIII on 2013-04-23
Hello!

Can you give us some information about your hardware?

Have you had Windows installed previously?  What were your temps?

Thanks.

---

### Post by pqwoerituytrueiwoq on 2013-04-23
for a laptop 65C is probably not too much to worry about, for a desktop that is too high, unless it is under heavy load

---

### Post by abhich on 2013-04-23
i have an hp pavillion dv7 , i5 processor and radeon 5 series graphics card .

---

### Post by pqwoerituytrueiwoq on 2013-04-23
that sounds reasonable, you bay get better temps using the latest driver from amd for the gpu
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get udpate
```
you can install the driver, there is additional drivers under settings, if not it in inside software sources

---

### Post by dandroid13 on 2013-04-23
Check this out too: [http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html](http://www.webupd8.org/2013/04/improve-power-usage-battery-life-in.html)
I'm using it here and my temps reduced 6º~7ºC while idling, from 45º to aroud 37º~38º.

---

### Post by zrdc28 on 2013-04-23
I installed "jupiter" on my laptop and it cut the temp down about 10 degrees with no noticable depression in use.

[http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10](http://ubuntuguide.net/install-jupiter-applet-in-ubuntu-12-04-12-10)

---

### Post by dandroid13 on 2013-04-23
Jupiter has been retired, I don't know if webupd8 will keep its ppa with new builds. For example, it's not available for Raring anymore.

---

### Post by abhich on 2013-04-23
i have already installed an additional driver FGLRX.

---

### Post by abhich on 2013-04-23
someone please help

---

### Post by Petro Dawg on 2013-04-23
[http://ubuntuforums.org/showthread.php?t=2041341](http://ubuntuforums.org/showthread.php?t=2041341)

65 deg isn't terrible

if you are really desperate, do what I did...

[URL="http://ubuntuforums.org/showthread.php?t=2045798&page=6&p=12430993#post12430993"]http://ubuntuforums.org/showthread.php?t=2045798&page=6&p=12430993#post12430993
[/URL]
or you can just get a cooling pad (recommended)

---

### Post by cocoakekeyu on 2013-04-23
Suggest you close the Graphics.

---

### Post by dandroid13 on 2013-04-23
Had cooling pad before, made little to no difference, heat ended screwing everything, now it won't even turn on... :(

---

