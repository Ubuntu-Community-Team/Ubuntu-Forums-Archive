---
title: "basic help in ubuntu init level"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by ubhi on 2008-10-30
hi all, i want to boot up my ubuntu system from terminal means from command line with network support as well, after that if i wish to go onto graphic mode then i can go with startx option or something else...

can anyone suggest me the proper way..??

---

### Post by billgoldberg on 2008-10-30
> **ubhi said:**
> hi all, i want to boot up my ubuntu system from terminal means from command line with network support as well, after that if i wish to go onto graphic mode then i can go with startx option or something else...

can anyone suggest me the proper way..??

Just disable the gdm and you should start in a cli.

Startx would then boot up gnome.


--

Bum ( search for it in the repos) can do this if you don't know how to do it cli style.

---

### Post by The Cog on 2008-10-30
The easiest way is to delete or rename either /etc/rc2.d/S30gdm or the file it links to, which is /etc/init.d/gdm. My inclination would be to rename the link like this:
sudo mv /etc/rc2.d/S30gdm /etc/rc2.d/X-S30gdm

---

### Post by ubhi on 2008-10-30
gr8, thanks for both of you, i tried the second method its working fine, & i just started ubuntuforms now, & i get the answers now i am happy..

---

