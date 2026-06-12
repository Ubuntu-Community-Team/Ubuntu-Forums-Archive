---
title: "snap version of cups"
date: 2023-05-30
forum: New to Ubuntu
---

### Post by tuesdaybarrett on 2023-05-30
Just read in omg ubuntu news that there is a new snap version of cups. Will this this compatible with ubuntu 23.04 to use a HP Printer. Tried to install Hplip and it is not supported in Ubuntu 23.04 with missing dependencies.

---

### Post by ian-weisser on 2023-05-30
The hplip-printer-app snap, made by the OpenPrinting developers, has been in the snap store for 2 years, and should work with Ubuntu 23.04.

---

### Post by TenPlus1 on 2023-05-31
This worries me, instead of updating cups libraries as .deb files users will be dowloading the entire and humungous snap each time.  For home users this isn't a great idea.

---

### Post by Dennis N on 2023-05-31
> **tuesdaybarrett said:**
> Just read in omg ubuntu news that there is a new snap version of cups. Will this this compatible with ubuntu 23.04 to use a HP Printer. **Tried to install Hplip and it is not supported in Ubuntu 23.04 with missing dependencies.**


The snap cups is planned for 23.10. In 23.04, it is .deb

hplip is available in 23.04 as a .deb package:

```
dmn@Tyana:~$ apt policy hplip
hplip:
  Installed: 3.22.10+dfsg0-1
  Candidate: 3.22.10+dfsg0-1
  Version table:
 *** 3.22.10+dfsg0-1 500
        500 http://us.archive.ubuntu.com/ubuntu lunar/main amd64 Packages
        100 /var/lib/dpkg/status

```

How did you try to install it?

---

### Post by ian-weisser on 2023-05-31
> **TenPlus1 said:**
> ... dowloading the entire and humungous snap each time...

Let's move this discussion to real numbers:
The download size is 57MB.
Less than 1/4 the size of the Firefox snap (edge/262MB), half the size of the Thunderbird snap (edge/111MB).

---

### Post by tuesdaybarrett on 2023-05-31
I used these commands 
```
sudo apt-get install hplip-gui 
hp-setup
```
I'm out of ink. the lights are flashing on printer. If i buy new ink cartridges will it them work?Thx for help

---

