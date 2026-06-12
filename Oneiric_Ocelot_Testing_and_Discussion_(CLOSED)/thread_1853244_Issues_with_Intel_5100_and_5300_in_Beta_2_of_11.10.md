---
title: "Issues with Intel 5100 and 5300 in Beta 2 of 11.10"
date: 2011-10-01
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by obriente on 2011-10-01
So this is really just a quick PSA for those running Oneiric on a laptop packing Intel's 5100 or 5300 WiFi chips. As you're probably already familiar with, connectivity was highly unstable under 11.04. The solution was to add "options iwlagn 11n_disable50=1 11n_disable=1" to /etc/modprobe.d/iwlagn.conf. Well, bad news. With those options (at least on my ThinkPad x200) Ubuntu didn't even recognize that I had WiFi. I removed them and suddenly I had wireless back. Huzzah!

That excitement didn't last long. WiFi died after about 2 min. After several tests to isolate the problem I discovered that simply connecting to the wireless network with my Ubuntu laptop was actually taking out WiFi on the router completely. That's right: everything was disconnected just because I connected to a laptop running Beta 2 of 11.10. After a little troubleshooting I've discovered that adding "options iwlagn 11n_disable=1" to the iwlagn.conf solved the problem. Obviously this still leaves you without 802.11n connectivity, but at least you'll still have a WiFi network. Just in case anyone else has encountered the same (seriously bizarre) issue, I figured I'd share the solution.

---

### Post by cariboo on 2011-10-01
There is a link to the bug report in [this]("http://ubuntuforums.org/showthread.php?t=1852857&highlight=reset+router") thread.

---

### Post by obriente on 2011-10-01
Ah! beautiful, was just about to file a bug report. Clearly my Google-fu has failed me cause I wasn't able to find anyone experiencing the same issue.

---

