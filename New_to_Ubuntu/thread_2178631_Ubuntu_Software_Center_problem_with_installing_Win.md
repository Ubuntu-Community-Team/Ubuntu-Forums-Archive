---
title: "Ubuntu Software Center problem with installing Wine"
date: 2013-10-04
forum: New to Ubuntu
---

### Post by vlada92 on 2013-10-04
So i wanted to install wine via USC. and this error happens...

[ATTACH=CONFIG]246740[/ATTACH]

---

### Post by whitesmith on 2013-10-04
You can download a .deb from WineHQ.com and try installing that. Regards.

---

### Post by ian-weisser on 2013-10-05
Go into Software Sources. Disable ALL PPAs and third party repositories. All of them.

Next, open a terminal. Enter the following commands. Paste the entire output of the terminal session here.
```
sudo apt-get update
sudo apt-get upgrade
```

---

