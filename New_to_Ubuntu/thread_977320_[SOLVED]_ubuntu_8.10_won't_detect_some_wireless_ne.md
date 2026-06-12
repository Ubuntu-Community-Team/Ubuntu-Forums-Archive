---
title: "[SOLVED] ubuntu 8.10 won't detect some wireless networks"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by lemik_7 on 2008-11-10
Hello,

I've recently updated to Intrepid, and since then ubuntu only detects open wifi networks. I've tried it with an open wifi network and works fine but does not detect my wireless network with WEP protection...

Anyone has had the same issue?

Thanks in advance

---

### Post by lemik_7 on 2008-11-10
i have just solved it... it was not a wep issue... the network i was trying to connect to was on channel 12 and ubuntu by default is configured to look for networks in U.S. authorized channels (that excludes channels 12, 13 used in Eupore and 13,14 used in Japan)

the solution was to edit the file in etc/modprobe.d/options and add the following line for Europe:

options cfg80211 ieee80211_regdom=EU

or this for Japan:

options cfg80211 ieee80211_regdom=JP

Here's where i've found the answer: [http://www.ubuntu.com/getubuntu/releasenotes/810](http://www.ubuntu.com/getubuntu/releasenotes/810)

Hope this helps someone...

---

### Post by Noirtheater on 2009-04-08
It has definitely helped me! I've spent the last two hours trying to figure this out without any good results until I found your post, so thank you very much! :)

---

