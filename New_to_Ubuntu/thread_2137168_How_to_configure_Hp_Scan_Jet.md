---
title: "How to configure Hp Scan Jet"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by padasalgi on 2013-04-19
Will some one please guide me how I can configure and use my HP Scan Jet 3770 in ubuntu 12.10
Thanks

---

### Post by tgalati4 on 2013-04-19
Install hplip and run hp-toolbox.  Open a terminal:

```
sudo apt-get install hplip
hp-toolbox
```

Ignore the above.  The ScanJet is not supported by hplip.  Become familiar with SANE instead:  [http://www.sane-project.org](http://www.sane-project.org)

Ignore that.  Your printer is not supported according to:  [http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=scanjet&bus=any&v=&p=](http://www.sane-project.org/cgi-bin/driver.pl?manu=hp&model=scanjet&bus=any&v=&p=)

You really didn't want to scan.

---

