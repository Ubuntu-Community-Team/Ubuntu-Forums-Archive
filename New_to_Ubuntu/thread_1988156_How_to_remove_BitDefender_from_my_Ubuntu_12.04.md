---
title: "How to remove BitDefender from my Ubuntu 12.04"
date: 2012-05-27
forum: New to Ubuntu
---

### Post by iamzahid on 2012-05-27
I have earlier installed BitDefender.
Unfortunately it is not working though the icon is there in my Launcher. I want to go with different AV rather than BitDefender as I do not want to give effort much with it. Look forward the solution to remove this from my PC.

---

### Post by wilee-nilee on 2012-05-27
> **iamzahid said:**
> I have earlier installed BitDefender by following the instruction [URL="http://*********************.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/"]this site.
[/URL]Unfortunately it is not working though the icon is there in my Launcher. I want to go with different AV rather than BitDefender as I do not want to give effort much with it. Look forward the solution to remove this from my PC.


 try

```
sudo apt-get purge bitdefender-scanner bitdefender-scanner-gui
```

---

