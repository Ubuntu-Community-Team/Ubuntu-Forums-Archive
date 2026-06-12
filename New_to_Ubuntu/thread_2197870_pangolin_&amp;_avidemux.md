---
title: "pangolin &amp; avidemux"
date: 2014-01-05
forum: New to Ubuntu
---

### Post by czgirb on 2014-01-05
currently, i'm using a pangolin and have avidemux installed.
yesterday, when i check the avidemux version it still 2.5.x version.
i always do an **system update** whenever it was prompt, and **sudo apt-get update & sudo apt-get upgrade** once in a week.
why? is that any wrong with my system?

**PS:**

from **[http://ubuntuhandbook.org/index.php/2013/10/install-avidemux26-ubuntu-1310-linux-mint/](http://ubuntuhandbook.org/index.php/2013/10/install-avidemux26-ubuntu-1310-linux-mint/)** i see there is 2.6.x version
from **[http://ubuntuhandbook.org/index.php/2013/09/avidemux-2-6-5-released-install-upgrade-in-ubuntu-13-04-12-04/](http://ubuntuhandbook.org/index.php/2013/09/avidemux-2-6-5-released-install-upgrade-in-ubuntu-13-04-12-04/)** i see there is 2.6.5 version
is the upgrade proceed the H.264 better?

if i choose to add:
> 
wget [http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb](http://archive.getdeb.net/install_deb/getdeb-repository_0.1-1~getdeb1_all.deb)
sudo dpkg -i getdeb-repository_0.1-1~getdeb1_all.deb

am i required to delete the old one?

---

### Post by claracc on 2014-01-06
The current release of avidemux in ubuntu 12.04 is 2.5.4 and you don't receive any other advanced release of the software package, only security updates, because the stability is preferred instead the newest.

If you want the newest avidemus, try to install it adding ppas repositories which have the newest avidemux, it is esaier and safer. You will have to add the sepository to your sources.list first and then install, there are specific instructions for it.

For example I have found this repository: [https://launchpad.net/~rebuntu16/+archive/avidemux+unofficial](https://launchpad.net/~rebuntu16/+archive/avidemux+unofficial)

---

