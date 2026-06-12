---
title: "QR code reader"
date: 2014-03-13
forum: New to Ubuntu
---

### Post by 393 on 2014-03-13
I have an offline computer running linux 12.04 and I was hoping someone could point me in the direction of a downloadable qr reader/writer that I could place on a usb stick and import it the computer.

And is it possible for the qr reader to read the code via a scan as opposed to my coputer or phone taking a picture?

Anyone have any ideas?

---

### Post by Impavidus on 2014-03-13
The **zbar-tools** package can read qr codes, in addition to other dot/bar codes, both using a webcam and from images. Do you have synaptic on that offline computer? It can create download scripts for packages to be installed or upgraded, so that you can download the packages on another computer and transfer them by usb stick.

---

### Post by 393 on 2014-03-13
Which is the most stable version?


[LIST]
[*][Debian 6.0 "Squeeze" (testing)]("http://packages.debian.org/source/squeeze/zbar")
[*][Fedora 10]("http://rpmfind.net/linux/rpm2html/search.php?query=zbar&system=fedora_10") (at [rpmfind.net]("http://rpmfind.net"))
[*][Fedora 11]("http://rpmfind.net/linux/rpm2html/search.php?query=zbar&system=fedora_11") (at [rpmfind.net]("http://rpmfind.net"))
[*][Gentoo ebuild]("http://bugs.gentoo.org/show_bug.cgi?id=288002")
[/LIST]

---

### Post by 393 on 2014-03-13
Never mind.  I got it.  Thank you much.

---

