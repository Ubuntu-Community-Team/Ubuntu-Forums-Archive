---
title: "Transmission 1.22"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by Tom--d on 2008-06-20
Currently, Ubuntu;s repos only have the version 1.06 and I was wondering if there is a repo I can use to update it. 

I've looked on Launchpad and nothing is there (far as I could see)

Could anyone point me in the right directio.


Thanks,
Tom :)

---

### Post by RomeReactor on 2008-06-20
Hi. You can get a .deb package from [GetDeb]("http://www.getdeb.net/app/Transmission"). Which version of Ubuntu do you have?

---

### Post by Nameless_one on 2008-06-20
You might also want to try [compiling from source](http://www.transmissionbt.com/development.php) if you feel an inclination to ;)

---

### Post by Tom--d on 2008-06-21
> **Nameless_one said:**
> You might also want to try [compiling from source](http://www.transmissionbt.com/development.php) if you feel an inclination to ;)

I cant be bothered to install all the devs ;)

And, I have version 1.06

---

### Post by RomeReactor on 2008-06-21
> **Tom--d said:**
> I have version 1.06

That's transmission's version, but we need to know which version of Ubuntu you have--6.06 (Dapper), 7.04 (Feisty), 7.10 (Gutsy), or 8.04 (Hardy).

---

### Post by Christmas on 2008-06-21
I recently made a short tutorial to compile it from source [here](http://vivapinkfloyd.blogspot.com/2008/06/how-to-compile-and-install-transmission.html). Bassically, download the source, uncompress it. Install dependencies:

```
sudo apt-get build-dep transmission
```

Compile it:

```
./configure
make
sudo make install
```

---

### Post by Tom--d on 2008-06-21
Ah, its no biggy. Just wondering why they haven't updated it in the repos as there has been many updates for Transmission. 

And I'm on Hardy. I have it now Installed.

Thanks all :)

---

### Post by jdarias on 2008-06-21
Debuntu repository updates it. [http://www.debuntu.org/](http://www.debuntu.org/)
If you use clutch don't update it. it's not compatible with 1.22

---

