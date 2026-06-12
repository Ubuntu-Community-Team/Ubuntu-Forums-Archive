---
title: "Browsing speed increase?"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by rbcl15 on 2008-05-04
I managed to connect to the internet useing wvdial. How may I speed up the web browsing? Is there any regular advice that may help? Thanks.

Oh and what regular plugins mof good quality might get me to at least a standard level?

---

### Post by bobplano on 2008-05-04
you could try blacklisting ipv6. most of the time this isn't needed, so it slows down internet browsing I think.

```
gksudo gedit /etc/modprobe.d/blacklist
```

then add the line "blacklist ipv6" without the quotes in there somewhere, and you should see some improvement

---

### Post by h4mx0r on 2008-05-04
Tweak firefox to your specifications:
[http://www.tweakfactor.com/articles/tweaks/firefoxtweak/1.html](http://www.tweakfactor.com/articles/tweaks/firefoxtweak/1.html)

Use opendns for faster queries:
[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

Use a local dns cache for less queries for address information:
[http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/](http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/)


For firefox under edit > preferences > content uncheck the following enable javascript, enable java, load images automatically. Then find a font that is less visually appealing and has faster rendering speed.

You can also use swiftweasel which is an optimized firefox build for different architectures.

adblock plus extension to cut down on wasted cycles and loading of ads.

Possibly try something like this (experimental):
You can also load up only a browser and no desktop to make sure your full system is dedicated to uber surfing speed. ctrl alt f2 then login and do sudo /etc/init.d/gdm stop create a file in your home directory called .xinitrc that says exec firefox and has a few blank lines after it (use nano to write it) then do startx --notcp that should pull up firefox in its own graphical session or you can do swiftweasel which ever you use. To get back to normal just log out and switch to terminal then do sudo /etc/init.d/gdm start.

There are also window scaling values for how your network stack handles data you can put custom values in /etc/sysctl.conf try to find what you need for your connection rate. Without as much data throttling things should run smoother.

---

### Post by nowshining on 2008-05-04
also see my site in blocking ADs, Trackers, etc.. (re-check in about a month as i'll be updating it here pretty soon)

also in firefox

about:config in the addr/url bar

find network.dns.disableipv6 and set it to true and re-start firefox. :)

---

### Post by sailor2001 on 2008-05-04
or you could go with a real light-weight browser 'KAZEHAKASE

---

### Post by h4mx0r on 2008-05-05
I had an awful time trying kazehakase before. Why does it have several lines for empty gui space? It has little plugin support for extra features that could possibly save bandwidth. If your going to recommend it can you post some help guides or how-tos for configuring it?

---

### Post by cartisdm on 2008-05-05
Are you just inquiring out of curiosity or are you experiencing a slow connection?

---

