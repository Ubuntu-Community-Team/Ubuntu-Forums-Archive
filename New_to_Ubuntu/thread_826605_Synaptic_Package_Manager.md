---
title: "Synaptic Package Manager"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Mitchlb on 2008-06-12
Synaptic Package Manager isn't working. It hasn't been working since I installed Gutsy Gibbon on my rig. I've been getting around it by using *Gasp, God Forbid* Tarballs! I know... It sucks. It opens, but when I search for things, it always comes up with 0 results... My biggest problem however, is when I try to install, it says something along the lines of "Please insert the Ubuntu install disc ie1010080182312 or something rather"... I haven't had the disc since I installed it. Threw it away. It was just an iso I burned and I didn't think I'd need it. Is there a way to fix it?

---

### Post by ad_267 on 2008-06-12
You could try going to Settings - Repositories and ticking all of the repositories, closing that then clicking reload and see if that helps.

If it's not working maybe see if you get any errors from the command line. Try entering:

```
sudo apt-get update
sudo apt-get install any_package_you_want
```

---

### Post by wormser on 2008-06-12
Try going to System> Administration> Software Sources and uncheck CDrom.

---

### Post by Mitchlb on 2008-06-12
Thats the problem! When I uncheck it and click revert, it does nothing. It just re-checks itself.

---

### Post by Mitchlb on 2008-06-12
Settings - repositories is the same place... That's what I did b4.

---

### Post by Mitchlb on 2008-06-12
It says this in the section that I'm trying to uncheck:

Cdrom with Ubuntu version 7.10 'Gutsy Gibbon'
Officially Supported
Restricted Copyright

---

### Post by hyper_ch on 2008-06-12
```

gksudo gedit /etc/apt/sources.list

```

and comment the cdrom entry by adding a # at the beginning for the line, then save it and then run:
```

sudo apt-get update

```

---

### Post by ad_267 on 2008-06-12
Of course if you click revert it re ticks itself. Revert means to return to the original setting. You need to click "close" and then click "reload." Don't click revert.

---

### Post by _sphinx_ on 2008-06-12
You don't have to hit revert. Just click close after unchecking. revert means return to original settings.

---

### Post by Mitchlb on 2008-06-12
Wow... That was stupid... I had no idea what was meant by 'revert'... Revert means to change... but it also means 'to return to a former habit'.... So wow... Thanks though!

---

