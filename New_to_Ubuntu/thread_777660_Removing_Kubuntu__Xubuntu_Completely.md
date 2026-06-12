---
title: "Removing Kubuntu / Xubuntu Completely"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by CoeusTitan on 2008-05-01
How in the blazes do I remove the Kubuntu and Xubuntu desktops ENTIRELY, meaning not just the 45kb desktop file? 

I want to remove all files relating to Xfce and KDE.

I just want my Ubuntu / Gnome back.

Thanks!

---

### Post by .nedberg on 2008-05-01
sudo apt-get autoremove kubuntu-desktop
sudo apt-get autoremove xubuntu-desktop

---

### Post by Oldsoldier2003 on 2008-05-01
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

unless you used aptitude to install the desktops there will probably be some trash left behind. this tutorial shows how to clean it all up

---

### Post by CoeusTitan on 2008-05-01
Thanks oldsoldier, that website helped a lot. Saved me the trouble of having to hunt down every program and package that was installed with KDE or Xfce...bah

---

