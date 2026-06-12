---
title: "How to Install HP Scanjet G2410"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Nhatz on 2008-07-26
Guys... anybody know how to install HP Scanjet G2410 in Ubuntu 8.04?

---

### Post by eightmillion on 2008-07-26
Have you tried HP Linux Printing and Imaging? It's available by running "sudo apt-get install hplip-gui". Then you can find it in System>Preferences.

---

### Post by Nhatz on 2008-07-26
Yup! tried it but no luck... it says No HP Device Found.. but when i typed *lsusb* it gives..

Bus 001 Device 022: ID 03f0:0a01 Hewlett-Packard

---

### Post by vikram_sdlp on 2010-07-03
How to Install HP Scanjet G2410

---

### Post by steveneddy on 2010-07-03
Firt of all - uninstall the hplip from the repos that you just installed.

Now go to HP's website and install the newer version available there for the best results.

Here's the link:

[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

This is direct to HP, so it should work better, just follow the direction it gives you for installation.

Looks like HP isn't supporting a single function scanner for Linux at this time. Maybe you need to purchase one of HP's all in one printer/scanner/fax/copier units that are actually supported with HPLIP.

Looks like sane might do the trick on your scanner:

[http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD](http://www.sane-project.org/sane-mfgs.html#Z-HEWLETT-PACKARD)

I believe installing **xsane** should get you where you need to go.

```
sudo apt-get install xsane
```

Good luck - post back your results.

---

