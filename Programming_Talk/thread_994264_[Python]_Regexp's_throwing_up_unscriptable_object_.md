---
title: "[Python] Regexp's throwing up unscriptable object error..."
date: 2008-11-26
forum: Programming Talk
---

### Post by fiddler616 on 2008-11-26
Hello,
I've been fiddling around with website scraping, and have made a successful script for a site.
Now I'm trying to make a second one for a different site (kayak.com, as it happens to be) and am baffled:
Here's the relevant bit
[PHP]
kayak_open = u.urlopen("http://www.kayak.com/k/ident/apisession?token=7Ws2oRDNd1G2oQVLgb4sJA")  
kayak = kayak_open.read() 
re_raw = re.compile('<sid>\w*\w</sid>') 
kayak_results = re_raw.findall(kayak) 
re_kayak_clean = re.compile('[^<sid>]\w*\w[^</sid>]') 
temp = re_kayak_clean[0] 
filtered = re_kayak_clean.search(temp) 
opened_kayak = filtered.group()[/PHP]
and the error:> 
Traceback (most recent call last):
  File "kayaka.py", line 10, in <module>
    temp = re_kayak_clean[0]
TypeError: '_sre.SRE_Pattern' object is unsubscriptable

Thank you very much.

---

### Post by geirha on 2008-11-26
> **fiddler616 said:**
> [PHP]
re_kayak_clean = re.compile('[^<sid>]\w*\w[^</sid>]') 
temp = re_kayak_clean[0] 
[/PHP]

re_kayak_clean is a compiled regex, it's not a sequence, so calling [0] on it doesn't make any sense. I'm guessing you intended to get the first line of the web-page or something instead?

---

### Post by fiddler616 on 2008-11-26
> **geirha said:**
> re_kayak_clean is a compiled regex, it's not a sequence, so calling [0] on it doesn't make any sense. I'm guessing you intended to get the first line of the web-page or something instead?
Thanks--you made me realize I'm missing a findall in there (I tried to fix it now but it's too late and my programming brain already fell asleep.)
I'll [SOLVE] this one it wakes up.

---

