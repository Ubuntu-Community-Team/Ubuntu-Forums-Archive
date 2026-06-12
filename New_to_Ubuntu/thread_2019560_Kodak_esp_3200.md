---
title: "Kodak esp 3200"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by degarb on 2012-07-07
I have tried the sane method, [http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/](http://sourceforge.net/projects/cupsdriverkodak/files/Scanning%20-%20sane%20backend/)

no luck getting scanner working.

---

### Post by paulnewall on 2012-07-07
Suggestions:
Try and install from the latest sane git version, instructions here:
[https://help.ubuntu.com/community/CompileSaneFromSource](https://help.ubuntu.com/community/CompileSaneFromSource)
Try and use the how-to here:
[https://sourceforge.net/projects/cupsdriverkodak/forums/forum/2125778/topic/5396909](https://sourceforge.net/projects/cupsdriverkodak/forums/forum/2125778/topic/5396909)
Or start on the investigation process by telling us:
Are you using usb?
can you detect the scanner using sane-find-scanner?
After installing, what do you get from sudo scanimage -L  ?

---

