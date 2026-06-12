---
title: "how to install firefox dom inspector?"
date: 2006-09-01
forum: Programming Talk
---

### Post by jimmyp on 2006-09-01
I am running dapper and can't figure out how to install the firefox dom inspector.

The generic answer is to reinstall firefox and choose to install the inspector but I'm trying to stick with software from the repositories.  So if I install firefox with apt, it doesn't ask whether I want the inspector or not.

From the repository doesn't work:
sudo apt-get install firefox-dom-inspector

The following packages have unmet dependencies:
  firefox-dom-inspector: Depends: firefox (= 1.5.dfsg+1.5.0.3-0ubuntu3) but 1.5.dfsg+1.5.0.5-0ubuntu6.06.1 is to be installed
E: Broken packages

Next, I hear you can install it by installing adt.xpi, but at 1.5.0.5, there is no more adt.xpi in the directory:
[http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/xpi](http://ftp-mozilla.netscape.com/pub/mozilla.org/firefox/releases/1.5.0.5/linux-i686/xpi)

There is one for 1.5.0.4, but when I try to install that, I get an error.

How do I install it?

Thanks.

---

### Post by mkalbere on 2006-09-04
.. here:
[http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffirefox%2Ffirefox-dom-inspector_1.5.dfsg%2B1.5.0.5-0ubuntu6.06.1_i386.deb&md5sum=500f92b789dc30a7cce74e58c339bbdd&arch=i386&type=security](http://packages.ubuntulinux.org/cgi-bin/download.pl?arch=i386&file=pool%2Funiverse%2Ff%2Ffirefox%2Ffirefox-dom-inspector_1.5.dfsg%2B1.5.0.5-0ubuntu6.06.1_i386.deb&md5sum=500f92b789dc30a7cce74e58c339bbdd&arch=i386&type=security)

---

### Post by hardyheronnewb on 2008-06-22
i clicked on above link and it gives an error. i would also like DOM inspector for Hardy Heron tho. thanks.

---

