---
title: "Installing GIMP for a new instalation"
date: 2020-11-13
forum: New to Ubuntu
---

### Post by gmseed on 2020-11-13
Just installed a brand new version of Ubuntu Desktop 20.04LTS.

I then immediately went to install GIMP via the Ubuntu Software installer on the left hand tool bar.

I did a search for GIMP and clicked install and got the following message in a popup:

"Sorry, something went wrong: Error opening directory ""/usr/share/appdata": No such file or directory"

Great eh.

This is crazy. I performed the installation a 2nd time and ignored the popup and let it do its thing. I then see that GIMP was in fact installed, irrespective of the popup warning/error message.

---

### Post by Impavidus on 2020-11-13
Weird. There appears to be nothing gimp-related in /usr/share/appdata on my Xubuntu 20.04 box, which has gimp installed by default. Did you install the deb version or is there a snap version too?

If gimp is correctly installed, I wouldn't worry too much.

---

### Post by ActionParsnip on 2020-11-13
What is the output of:
```

sudo apt update
sudo apt install gimp

```
Thanks

---

### Post by gmseed on 2020-11-13
Apparently in posting this original thread and simply stating facts issued by trying to install GIMP, complaint(s) were lodged. Hard to believe but I received a personal message from someone called coffee...whatever stating that complaints had been received on all 3 posts I made today, one of which was this one. What kind of forum is this when one or more persons make complaints about factual warning/error norifications when trying to install GIMP on a fresh straight out of the box Ubuntu installation?

In fact, the warning/error message popups whenever an attempt is made to install a new piece of software using the provided installer, so not GIMP specific.

---

### Post by CelticWarrior on 2020-11-13
So that's a symptom of an issue that seem to be system specific, same for Chrome, that millions have installed simply by double-clicking the downloaded .deb file and then the "install" button. Perhaps check that before going on full rant mode.

---

### Post by T6&amp;sfpER35% on 2020-11-13
[https://itsfoss.com/things-to-do-after-installing-ubuntu-20-04/](https://itsfoss.com/things-to-do-after-installing-ubuntu-20-04/)

---

### Post by T6&amp;sfpER35% on 2020-11-13
can sort of understand where OP is coming from ,expecting everything to work out of the box after a fresh installation.
however ,one got to update /upgrade packages and stuff first.
getting some basic linux knowledge would help here
linux is not windows after all ...and thank God

---

### Post by DuckHook on 2020-11-14
The OP has left the building so thread has been closed to prevent our volunteers from wasting any more time on this issue.

Thanks everyone!

---

