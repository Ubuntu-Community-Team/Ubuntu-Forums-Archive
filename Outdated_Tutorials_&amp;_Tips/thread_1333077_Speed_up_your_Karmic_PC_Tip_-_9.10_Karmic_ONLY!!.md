---
title: "Speed up your Karmic PC Tip - 9.10 Karmic ONLY!!"
date: 2009-11-21
forum: Outdated Tutorials &amp; Tips
---

### Post by gordong11 on 2009-11-21
I forget where, but I came across this guide and tried it. Wow it makes a huge difference in speed. Please know what you are doing first, tis why I hate posting these tips, but this one really helped my pc.
[B]
THIS IS FOR 9.10 KARMIC USERS ONLY[/B].

Important tips to make Ubuntu faster
Faster boot time:

Edit /etc/init.d/rc
$ sudo gedit /etc/init.d/rc

And change the line (line 33)
CONCURRENCY=none
to
CONCURRENCY=shell
----


Install preload daemon

Linux's preload daemon... monitors what programs you use most often and caches these programs and dependent libraries in (unused) memory to speed up application start time. If your system has 1GB or more memory then preload will have a positive effect. Install and start the preload process. Run command

$ sudo apt-get install -y preload

It will automatically load at boot.
----


Disable IPv6 in the kernel
It seems to me that the lookup of IP version 6 addresses takes a lot of time. Let's disable it.
$ echo 1 | sudo tee /proc/sys/net/ipv6/conf/all/disable_ipv6

Check its status
$ cat /proc/sys/net/ipv6/conf/all/disable_ipv6
0 = Enabled
1 = Disabled

$ sudo gedit /etc/rc.local
You can put the following blue line to /etc/rc.local (before the "exit 0" line) so it's set at boot up:

echo 1 > /proc/sys/net/ipv6/conf/all/disable_ipv6
----


Disable IPv6 in Firefox
Start Firefox and write about:config in the address (location) bar.

Then look for network.dns.disableIPv6 parameter.
Double click the line and set it to true.  Restart your Firefox.  
 __________________________________________________________________________


I rebooted my system afterwards JIC, but I'm not sure if needed for full effect.

---

