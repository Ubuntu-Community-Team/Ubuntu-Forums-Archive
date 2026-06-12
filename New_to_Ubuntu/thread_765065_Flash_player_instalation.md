---
title: "Flash player instalation"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by jus71n742 on 2008-04-24
ok my girl friend has Ubuntu now and I am trying to get her flash player plug ins to work ....apparently I have the install files on her machine but I can't figure out how to run the install file. or any ideas on how to get it through a terminal would be more beneficial in my mind.

---

### Post by Ub1476 on 2008-04-24
To install flash, simply search for it in the package-manager (add/remove or Synaptic). I suggest you install "ubuntu-restricted-extras" though, because this package has flash, java, codecs and a few extra fonts like the ms-tff fonts, which is needed to display some webpages correctly.

---

### Post by mikewhatever on 2008-04-24
<sudo apt-get install flashplugin-nonfree> should get Adobe flash installed.

---

### Post by swoll1980 on 2008-04-24
easiest way is to open synaptics package manager (system > adminastration > synaptics
click the search button in the search box enter ubuntu restricted extras this will give you all the things you need for audio and video

---

### Post by chameleonkid on 2008-04-24
I believe it can also be installed "automatically" by just by going to a website that has flash in it and installing it "through" the browser. But don't quote me on that.

---

### Post by aysiu on 2008-04-24
If you're still using Ubuntu 7.10 (and not 8.04), the safest way to install it is manually:
[http://www.psychocats.net/ubuntu/flashmanual](http://www.psychocats.net/ubuntu/flashmanual)

---

### Post by jus71n742 on 2008-04-24
> **chameleonkid said:**
> I believe it can also be installed "automatically" by just by going to a website that has flash in it and installing it "through" the browser. But don't quote me on that.

that is what I tried...it just gave me the installer...nothing else would be done.

---

### Post by billgoldberg on 2008-04-24
> **jus71n742 said:**
> that is what I tried...it just gave me the installer...nothing else would be done.

Restricted extra's will install it for you.

Did it work?

---

### Post by jus71n742 on 2008-12-15
Yes ...the command ```
sudo apt-get install flashplugin-nonfree
``` did the job quite well.

I have learned that command line is the best way to do virtually everything with anything lol.

---

