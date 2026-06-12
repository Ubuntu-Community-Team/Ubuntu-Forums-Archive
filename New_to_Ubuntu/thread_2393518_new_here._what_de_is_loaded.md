---
title: "new here. what de is loaded"
date: 2018-06-04
forum: New to Ubuntu
---

### Post by bodhin2 on 2018-06-04
looking at bionic beaver and wondering gnome is the de.  so - what about all of the other versions of de?  is there an enlightnement version?  also is gnome the default one that installs?

---

### Post by Frogs Hair on 2018-06-04
Gnome is the default for Ubuntu on the 18.04 release . There are other Ubuntu flavors with different DE's including [Budgie ]("https://ubuntubudgie.org/blog/2018/04/26/18-04-lts-ubuntu-budgie-released"), [Mate  ]("https://ubuntu-mate.org/blog/ubuntu-mate-bionic-final-release/"), [Xubuntu]("https://xubuntu.org") , [Lubuntu ]("https://lubuntu.net")and [Kubuntu ]("https://kubuntu.org/news/kubuntu-18-04-has-been-released/").   An Enlightenment flavor is not available.

---

### Post by bodhin2 on 2018-06-04
thank you for the quick reply!  Most appreciative.

---

### Post by poorguy on 2018-06-04
Best advice I have to offer is to post systems specs of the computer you are planing to use.

Based on the system specs the forum members here will be able to suggest which Ubuntu distro and DE will work best for your particular computer and hardware it uses.

---

### Post by bodhin2 on 2018-06-04
thanks will have to do it soon.

---

### Post by oldrocker99 on 2018-06-05
I would definitely recommend installing MATE.
```
 sudo apt install mate-desktop-environment
```

I think you'll like it; it's lightweight and very configurable. Easy to use, too, and it doesn't have the enormous icons of Unity and GNOME, which I greatly dislike. You can always uninstall it this way: ```
sudo apt remove mate-desktop-environment
```

You do have to log out, select MATE, and log back in. Give it a shot. It is the same interface I fell in love with when I started using Ubuntu 8.04 lo these many years ago. Once the MATE project started, I found myself back in what, IMHO, is the best desktop environment ever designed, based on the GNOME2.3 interface and very much improved, and I've never been happier. You might, if you're a beginner, just get Ubuntu MATE and install it, if you try it out and like it. It has an original and completely unique Welcome window, which allows installation of a curated list of great free programs.

You might gather that I love UM. [https://www.ubuntu-mate.org](https://www.ubuntu-mate.org)

---

### Post by deadflowr on 2018-06-05
You can post specs with
either
```
inxi -Fz
```
or
```
sudo lshw -sanitize
```
lshw would be installed, however I'm never sure if inxi is installed or no.
But just in case, to install inxi run
```
sudo apt install inxi
```

inxi has a ton of options -F being the most generic (Full). and the z tries to filter out some user info.
lshw's -sanitize option also filters out private information, or at least tries to.
Both will output fairly usefull system information.

run 
```
inxi -h
or 
man inxi
```
to see more inxi options and
```
lshw -h
or
man lshw
```
for more lshw options.

---

### Post by bodhin2 on 2018-06-05
thanks for all of the info

---

