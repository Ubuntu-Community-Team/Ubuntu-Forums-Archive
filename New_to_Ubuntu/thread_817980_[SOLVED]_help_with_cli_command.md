---
title: "[SOLVED] help with cli command"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-06-04
is this right:

sudo apt-get install -y k3b k9copy compizconfig-settings-manager epiphany-browser epiphany-extensions ubuntu-restricted-extras vlc libdvdcss2 skype googleearth libdvdcss2 acroread non-free-codecs wine p7zip-full mplayer gnome-mplayer gnome-alsamixer ktorrent firestarter emerald virtualbox-ose nicotine sun-java6-jre && remove open-java


I'm adjusting once of the commands on my blog for hardy, but I can't test it anymore.

Is 

&& remove open-java 

correct?

---

### Post by hyper_ch on 2008-06-04
no, the && remove open-java is not correct ;)

I'd say it should be
```

&& sudo apt-get remove -y open-java

```

---

### Post by sdennie on 2008-06-04
remove openjava will do nothing.  A great way to try out advice before you give it would be to install virtualization software and just try it there.  I use VirtualBox and it works great for that purpose (being able to roll a VM back to its original state is incredibly valuable).

---

### Post by billgoldberg on 2008-06-04
Ok, I wasn't sure if I had to put sudo apt-get in there again.

---

### Post by billgoldberg on 2008-06-04
> **vor said:**
> remove openjava will do nothing.  A great way to try out advice before you give it would be to install virtualization software and just try it there.  I use VirtualBox and it works great for that purpose (being able to roll a VM back to its original state is incredibly valuable).

I tested the command for gutsy, but for since sun-java6 isn't in "ubuntu-restricted-extras" any more I had to put it in there again and remove open-java.


(I also put in bin and plugin for java, to lazy to update the command in the OP).

---

### Post by billgoldberg on 2008-06-04
This is the final command, it presume it's ok:

```
sudo apt-get install -y k9copy compizconfig-settings-manager epiphany-browser epiphany-extensions ubuntu-restricted-extras vlc libdvdcss2 skype googleearth libdvdcss2 acroread non-free-codecs wine p7zip-full mplayer gnome-mplayer azureus firestarter emerald virtualbox-ose nicotine sun-java6-jre sun-java6-bin sun-java6-plugin && sudo apt-get remove -y open-java

```

---

