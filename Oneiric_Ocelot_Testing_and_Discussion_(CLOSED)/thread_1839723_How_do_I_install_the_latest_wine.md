---
title: "How do I install the latest wine?"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Melhisedek on 2011-09-06
The one in Ubuntu Software Centre is 1.3.15 while the latest version is up to 1.3.27 by now.

Any ideas?
Thank you for your time!

---

### Post by howefield on 2011-09-06
Instructions here..

[http://www.winehq.org/download/ubuntu](http://www.winehq.org/download/ubuntu)

Basically, add the repository to your sources and update, then install wine1.3

---

### Post by Melhisedek on 2011-09-06
Sorry I didn't mention it in the first post, but I already did it. I'm running 11.10 if that makes any difference. Latest version is still x.x.15

---

### Post by howefield on 2011-09-06
OK, I am using 11.04 and it is a case of using the terminal commands..

```
sudo add-apt-repository ppa:ubuntu-wine/ppa
```

then

```
sudo apt-get update
```

then

```
sudo apt-get install wine1.3
```

But now you mention you are on the development release, I'll move the thread to that forum.

---

### Post by jou770d on 2011-09-06
The Wine repo still doesn't have Oneiric packages.

A, probably-not-so-recommended, workaround would be to modify the PPA list file and make it use the Natty repo instead.
I guess that using repos for a different version might cause some dependencies to break eventually, but as it's only a Wine repo the breakage would only affect Wine packages. Personally, I can live with that, but keep that in mind if you decide to proceed.

To do that, you'll need to modify this file:
```
$ sudo nano /etc/apt/sources.list.d/ubuntu-wine-ppa-oneiric.list
```
like so:
```
deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu natty main
# deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main
# deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu oneiric main

```
You could treat the "deb-src" line the same way as the "deb" one, personally I don't care about it so I've left it commented.

Do an
```
$ sudo apt-get update
```
and you'll have:
```

amarus@zephuros:~$ apt-cache policy wine1.3
wine1.3:
  Installed: 1.3.15-0ubuntu6
  Candidate: 1.3.27-0ubuntu1~ppa1~natty1
  Version table:
     1.3.27-0ubuntu1~ppa1~natty1 0
        500 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ natty/main amd64 Packages
 *** 1.3.15-0ubuntu6 0
        500 http://archive.ubuntu.com/ubuntu/ oneiric/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

### Post by Melhisedek on 2011-09-06
It worked :) 
thanks a lot mate, now to see if it will fix my flashing Team Fortress 2

---

