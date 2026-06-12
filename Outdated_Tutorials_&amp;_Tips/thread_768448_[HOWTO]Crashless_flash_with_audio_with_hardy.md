---
title: "[HOWTO]Crashless flash with audio with hardy"
date: 2008-04-26
forum: Outdated Tutorials &amp; Tips
---

### Post by artir on 2008-04-26
From [Conn's post]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888/comments/39") in launchpad:

1.Install this
[URL="http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb"]
http://launchpadlibrarian.net/13470096/nspluginwrapper_0.9.91.5-2ubuntu2_i386.deb[/URL]

1.5 Install libflashsupport
sudo apt-get install libflashsupport

2.Run

sudo apt-get remove --purge flashplugin-nonfree
sudo apt-get install flashplugin-nonfree

Restart firefox et voilá!

---

### Post by blacksm1th on 2008-04-26
Yes this is working solution. Thank you.

---

### Post by salvador_luna on 2008-05-01
Thank you!

---

### Post by fly3rman on 2008-05-01
it worked, didnt had sound before.
thx.

---

### Post by woutervanwijk on 2008-06-06
Imho this should have been fixed before the release. A webbrowsing experience without flash-sound is a bad start for a newby.

---

