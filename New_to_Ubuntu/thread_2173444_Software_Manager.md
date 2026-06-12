---
title: "Software Manager"
date: 2013-09-09
forum: New to Ubuntu
---

### Post by spillage2 on 2013-09-09
Hi,

I am using ubuntu 10 but when ever I start up the software manager it just hangs on loading.


Any help would be appreciated.

Thaks,

Spill.

---

### Post by carl4926 on 2013-09-09
could it be 10.04 is dead, end of life?!

---

### Post by Jonathan Precise on 2013-09-09
> **spillage2 said:**
> Hi,

I am using ubuntu 10 but when ever I start up the software manager it just hangs on loading.


Any help would be appreciated.

Thaks,

Spill.

Ubuntu 10.04 LTS and Ubuntu 10.10 are now _**EOL**_s (reached their _**E**_nd _**O**_f _**L**_ife). Please upgrade to a newer version. If you can't, please provide a reason why, as there are alternatives.

---

### Post by whitesmith on 2013-09-09
> **carl4926 said:**
> could it be 10.04 is dead, end of life?!
Unless you were being facetious, EOL  means end of support, not death of software in the distro. As another member said, updating to something more recent is in order. You **did** put /home on its own separate partition, didn't you? Otherwise you'll have an opportunity to do so when you update. That way, future updates will be smoother.

---

### Post by alphacrucis2 on 2013-09-09
> **whitesmith said:**
> Unless you were being facetious, EOL  means end of support, not death of software in the distro. As another member said, updating to something more recent is in order. You **did** put /home on its own separate partition, didn't you? Otherwise you'll have an opportunity to do so when you update. That way, future updates will be smoother.


You can update directly from 10.04 to 12.04 (lts to lts). Doesn't really matter if /home is on a separate partition or not. The main thing is that /home is backed up in case the upgrade breaks.

1. Backup your data .

2. sudo do-release-upgrade

This will take some time as there will be a lot of packages involved. Be prepared for a shock. The UI for 12.04 (unity)  is very different to gnome 2 used in 10.04.

---

### Post by deadflowr on 2013-09-09
End of Life and End of support are synonymous terms in this case.
The repos for old releases get pulled out and place in the archives [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)
The path way to them is not the same as what would be in your sources.list.
Hence the hanging, and troubles.

As stated before, upgrading is the best alternative.
If Ubuntu, in it's current form bothers you, try one of the other flavors such as
[Lubuntu]("http://lubuntu.net/")
[Xubuntu]("http://xubuntu.org/")
[Kubuntu]("http://www.kubuntu.org/")
[Ubuntu Gnome]("http://ubuntugnome.org/")
as well as a few others.

---

