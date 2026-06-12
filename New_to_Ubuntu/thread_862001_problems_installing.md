---
title: "problems installing"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by edwin2105z on 2008-07-17
installed compiz fusion and i get the effects but in the synaptic package manager i'm getting an error, that i'm guessing a folder didnt get installed:

E: /var/cache/apt/archives/compiz-fusion-bcop_0.6.0-1_all.deb: trying to overwrite `/usr/bin/bcop', which is also in package compiz-bcop

so i went to the terminal and tryed to install it from there but did not let me gave me this:


edwin2105z@edwin2105z-desktop:~$ sudo apt-get install compiz-fusion-bcop
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
edwin2105z@edwin2105z-desktop:~$ 

can someone help me to install this last folder?

---

### Post by iaculallad on 2008-07-17
Try to close all opened Synaptics window and terminate all running apt process on your terminal.

```
ps aux | grep apt
kill -9 process_id_from_ps
```

Then redo your install.

---

### Post by lizzard on 2008-07-17
Close Synaptic, then type in terminal:
```
sudo apt-get remove compiz-bcop 
``` and after that install compiz-fusion-bcop with```
sudo apt-get install compiz-fusion-bcop
```

---

