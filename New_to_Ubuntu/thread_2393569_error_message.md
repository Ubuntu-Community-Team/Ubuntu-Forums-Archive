---
title: "error message"
date: 2018-06-05
forum: New to Ubuntu
---

### Post by rburkartjo on 2018-06-05
running 16.04
Setting up falkon (3.0.1-0ubuntu0.1) ...
update-alternatives: error: alternative path /usr/bin/falkon doesn't exist
dpkg: error processing package falkon (--configure):
 installed falkon package post-installation script subprocess returned error exit status 2
Processing triggers for hicolor-icon-theme (0.17-2) ...
Errors were encountered while processing:
 falkon
E: Sub-process /usr/bin/dpkg returned an error code (1)

any idea how to fix/tks

---

### Post by #&amp;thj^% on 2018-06-05
Please see this: [https://www.omgubuntu.co.uk/2017/08/falkon-web-browser-snap-app](https://www.omgubuntu.co.uk/2017/08/falkon-web-browser-snap-app)
It will need this package "kde-frameworks-5" installed if not already using a KDE session.
And for what it's worth "‘Falkon’ is the new name of cross-platform Qt web-browser QupZilla."

---

### Post by rburkartjo on 2018-06-05
1fallen tks. still getting the error messages after doing as your link said. least i know what it is/

---

### Post by #&amp;thj^% on 2018-06-05
Sorry I just won't install it>>>due to the added bloat for my system "kde-frameworks-5"** adds another 200Mb of unwanted software** for my install. :(
Besides I have seen all kinds of negative posts for "Falkon" at least for Non KDE Sessions....Might be best to wait till it gets a bit more love.
Sorry i was not very helpful here.
Welp I compiled from source here and got it installed>>>But nothing to see here as far as my taste's go. (Just my opinion ;))
So far it has crashed 2 times inside of 1 minute of use, i believe "qt5-webengine-5" needs to help out here upstream.

---

### Post by roguescholar2 on 2018-06-25
To anyone else still wrestling with this issue I'd recommend simply installing the Falkon-tesing PPA which doesn't seem to be suffering the same build issues as the bionic repo version.

```
[COLOR=#333333]sudo add-apt-repository ppa:tsimonq2/falkon
```

[/COLOR][https://launchpad.net/~tsimonq2/+archive/ubuntu/falkon](https://launchpad.net/~tsimonq2/+archive/ubuntu/falkon)

---

### Post by rburkartjo on 2018-06-26
tks rog will give that a try. havent upgraded to 3.01 still running falkon 3.099 with no problems

---

