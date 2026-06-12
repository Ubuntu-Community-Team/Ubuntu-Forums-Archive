---
title: "gcc not included"
date: 2012-05-09
forum: Programming Talk
---

### Post by alif rizki on 2012-05-09
I have installed kubuntu 12.04 from its live cd, but it is strange, the gcc is not included.. How to install it without internet connection? (cannot connect to internet since my dial up modem still doesn't work)

---

### Post by stchman on 2012-05-09
> **alif rizki said:**
> I have installed kubuntu 12.04 from its live cd, but it is strange, the gcc is not included.. How to install it without internet connection? (cannot connect to internet since my dial up modem still doesn't work)

You will need to install build-essential and all its dependencies.

---

### Post by alif rizki on 2012-05-09
How should i do to install build-essential and all its dependencies?

---

### Post by markbl on 2012-05-09
> **alif rizki said:**
> How should i do to install build-essential and all its dependencies?

apt-get install build-essential

or search for it in ubuntu software center and install it from there.

---

### Post by codemaniac on 2012-05-09
> **alif rizki said:**
> I have installed kubuntu 12.04 from its live cd, but it is strange, the gcc is not included.. How to install it without internet connection? (cannot connect to internet since my dial up modem still doesn't work)

As you have mentioned your internet is not working , you can download the build-essential deb packages from a other machine with working internet and then install them in your system .
Here is the package link for build-essential .

[http://packages.ubuntu.com/search?keywords=build-essential](http://packages.ubuntu.com/search?keywords=build-essential)

Else you might consider a source install .

---

### Post by 3Miro on 2012-05-09
build-essential is a meta package, it doesn't install anything by itself, it only pulls other packages.

Working offline is tricky, try this tutorial:

[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

---

### Post by Bachstelze on 2012-05-09
Last I checked, build-essential was on the CD.

---

