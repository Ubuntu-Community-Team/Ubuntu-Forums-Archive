---
title: "Uninstall Icon Pack or Theme"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by GUZZLR on 2013-06-23
If I wish to uninstall an Icon pack or Theme...how do I do it?
Thanks

---

### Post by fantab on 2013-06-24
That would depend on how you've installed it. If you installed the icon pack from the ubuntu repositories or using some ppa then:

sudo dpkg --purge icon-theme-name
sudo apt-get remove --purge icon-theme-name

Or you can use 'Software Center' or 'Synaptic' package managers to do the same.

If you just installed the Icon pack by copying the package folder into usr/share/icons then Deleting the your-icon theme folder from the said path will remove it.

---

### Post by GUZZLR on 2013-06-24
I got it from Noobs Labs, and I believe it is an PPA

---

