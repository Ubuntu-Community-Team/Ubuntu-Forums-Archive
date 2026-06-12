---
title: "Slow Browsers"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by kneewax on 2008-05-15
I have been blaming Firefox for being very slow in Ubuntu - and indeed many concur that version 2 was slow.  I have been using Hardy since its release and the only disappointment I had was that FF3b5 was still as slow. Well I finally got around to playing with some other browsers - including Epiphany, Swiftfox and Midori and I find them all slow to load web pages.  I wonder is there something else (like DNS settings) that I could be missing that are causing my web speed issues?  TB also renders html/linked emails slowly....

any help appreciated.

---

### Post by drs305 on 2008-05-15
Some people, including me, have found that disabling ipv6 speeds up initial loading of web pages. The first step (and easiest) would be to 'about:config' in firefox, then type 'ipv6' in the filter. You will see 'network.dns.disableIPv6' and change it to true. 

I don't know if that by itself will improve your situation. There are other modifications to /etc/modprobe.d files that may also be necessary. You can search this site for those instructions.

Here is a link to a recent thread:
[http://ubuntuforums.org/showthread.php?t=777320](http://ubuntuforums.org/showthread.php?t=777320)

---

### Post by nicedude on 2008-05-15
Also you might try running some ping tests to say Google.com and see what your results are. If you know what your ms ( milli second ) response was on this internet connection with older operating system versions or windows then you can see if yours is slower now. I find that here in the USA with cable or dsl modems that ping ms response is usually 25ms - 100ms  -  If your pings are much more than 100ms and you have high speed connection then I would investigate the situation furthur.

---

### Post by kneewax on 2008-05-15
Yeah - my IPv6 setting was already set to true - I guess I must have tried that in FF2 in Gusty and the setting was kept at upgrade. 

My laptop currently pings google at between 126 131 ms - this seems quite high to me.

64 bytes from google.com (64.233.167.99): icmp_seq=1 ttl=246 time=126 ms
64 bytes from google.com (64.233.167.99): icmp_seq=2 ttl=246 time=130 ms
64 bytes from google.com (64.233.167.99): icmp_seq=3 ttl=246 time=125 ms
64 bytes from google.com (64.233.167.99): icmp_seq=4 ttl=246 time=137 ms
64 bytes from google.com (64.233.167.99): icmp_seq=5 ttl=246 time=135 ms

Having said that, my Wife's VistaHP machine pings at a shocking 138-148 ms. 

I would expect it to be the connection or something at the router end EXCEPT that Firefox is much quicker on the Vista box - despite these results....

---

### Post by kk0sse54 on 2008-05-15
You could try Opera

---

### Post by kneewax on 2008-05-15
Since all the other browser I've tried have same problem I doubt Opera will make any difference (it never did in Gusty).  Also Firefox is expandable and customisable in a way opera isn't and never has been, also I don't like the Opera interface or the business model they use.  So thanks btu NO thanks.

---

### Post by enyckma on 2008-05-15
you can use the latest beta version of opera!

[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/) for 64bit version

&

[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/i386/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/i386/) for 32 bit

---

### Post by kneewax on 2008-05-15
> **enyckma said:**
> you can use the latest beta version of opera!

[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/x86_64/) for 64bit version

&

[ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/i386/](ftp://ftp.opera.com/pub/opera/linux/950b2/final/en/i386/) for 32 bit

Really, I don't like Opera and I don't want to use it AND it won't be any quicker -  because if you read my first post all the browsers I have tried are suffering the same speed issues.

---

