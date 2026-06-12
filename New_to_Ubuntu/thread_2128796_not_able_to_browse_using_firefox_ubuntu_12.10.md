---
title: "not able to browse using firefox ubuntu 12.10"
date: 2013-03-24
forum: New to Ubuntu
---

### Post by maher0 on 2013-03-24
i faced this a couple of times - i have dual boot windows 8 and Ubuntu - trying to learn as i can to get away from windows  [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]
now i can ping 8.8.8.8 from Ubuntu my wired connection is working i have a good IP, but i can not browse using Firefox
i checked my proxy and nothing is there - i am not using a proxy 
what could be the prob
no i restarted to check the INTERNET on the windows - working fine - i rebooted back to Ubuntu - not working i added a manual dns 8.8.8.8 - Google
not working - i just kept trying and suddenly it worked ! what is going on

---

### Post by pfeiffep on 2013-03-24
From a terminal window (Ctrl-Alt-t) type > ping google.comIf you have internet connectivity within Ubuntu you should see similar results as below - *(Ctrl-c) will end*:> PING google.com (74.125.228.38) 56(84) bytes of data.
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=1 ttl=252 time=13.4 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=2 ttl=252 time=12.2 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=3 ttl=252 time=14.6 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=4 ttl=252 time=11.5 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=5 ttl=252 time=72.7 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=6 ttl=252 time=84.2 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=7 ttl=252 time=11.8 ms
^C64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=8 ttl=252 time=12.8 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=9 ttl=252 time=11.3 ms
64 bytes from iad23s06-in-f6.1e100.net (74.125.228.38): icmp_req=10 ttl=252 time=10.6 ms


If you have Ubuntu internet connectivity then possibly FF has a setting for proxy that requires adjustment (not to use in your case). I use Chromium so I'm not familiar with FF.

Check your network settings (System Settings | Network)

Post back if you haven't solved the connectivity problem with some additional details

---

### Post by gordintoronto on 2013-03-24
When you set up Windows 8, did you enter DNS server numbers provided by your ISP? Do you use DHCP, or a static IP address?

---

### Post by Adi Krishnan on 2013-03-25
Please try to remove the Google DNS entry and try again, it could be possible that the Google DNS is not being configured correctly.

P.S. Using Google DNS can cause performance issues such as slow loading of websites.

---

