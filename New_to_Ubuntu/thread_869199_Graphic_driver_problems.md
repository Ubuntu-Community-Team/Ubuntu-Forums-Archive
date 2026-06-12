---
title: "Graphic driver problems"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by Techpenguin on 2008-07-24
I'm having a problem with the default nvidia geforce graphics driver. whenever I attempt to enable it and then reboot like I'm supposed to, it always says not in use and if I try to enable desktop effects they don't work. any ideas why this is happening?
P.S. I just upgraded to hardy heron 8.04. also if you know of an alternative driver could you please tell me?

---

### Post by phidia on 2008-07-24
What specific nvidia card model are you using? There are reports of problems with the 8800 GTS and higher models. If you have a 8 or 9 series card you should search the [multimedia & video]("http://ubuntuforums.org/forumdisplay.php?f=334") section using your card #.

---

### Post by Techpenguin on 2008-07-24
thanks, i'll do that i'm using an 8600

---

### Post by Techpenguin on 2008-07-24
ok now I attempted to install envy, then rebooted like it said. when I rebooted, ubuntu said I was running in low graphics mode(somehow my resolutin got changed) and I reconfigured my screen, but it didn't work. now I'm stuck in 800x600 resolution and I can't change it. please help?

---

### Post by phidia on 2008-07-24
What driver is listed in /etc/X11/xorg.conf? If it's not "nvidia" edit your xorg.conf to get that driver listed.

I don't know why the 8 & 9 series cards are troublesome and there are reports to back that up. 
Anyway if editing xorg.conf doesn't work you may need to manually install the latest nvidia driver from [the nvidia site]("http://www.nvidia.com/Download/index.aspx?lang=en-us").

Also check out [this thread]("http://ubuntuforums.org/showthread.php?t=864202&highlight=nvidia+8600+gt") to at least read about an edit you might need to make.

---

