---
title: "Apt-get online problem Dapper Drake"
date: 2006-03-09
forum: Repositories &amp; Backports
---

### Post by mwaddoups on 2006-03-09
I am confined to the console while trying to get the fglrx driver to work and I need access to the internet using apt-get. I have used ndiswrapper to enable my wireless adapter, and the internet connection is definitely working - I can ping the router and [www.google.com](www.google.com). I have also enabled all the repositories. However, when I try and use apt-get to get something from the repositories, it fails to work - it only uses the packages on the cd. If I reboot the machine I have to configure the internet again - it does not configure automatically on boot. Any ideas?

---

### Post by cilynx on 2006-03-09
You need to setup your online repositories to be ahead of the CDROM...mostly, get rid of the CDROM from the list

You can edit /etc/apt/sources.list by hand if you're comfortable with that, else

System->Administration->Software Properties

Is the graphical repository manager

Good Luck

---

### Post by mwaddoups on 2006-03-09
Thanks for the suggestion! I'm gonna try that right now and I'll let you know if it worked (hopefully from my linux box)!

---

