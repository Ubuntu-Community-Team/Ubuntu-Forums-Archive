---
title: "problem with opening https pages"
date: 2008-06-20
forum: New to Ubuntu
---

### Post by seyed-mehdi on 2008-06-20
hi everyone

I've got problem with opening https pages. This probelm has been appear since I install Hardy. I use Firefox either Konqueror but none of them can open those https pages, such az [https://addons.mozilla.org/](https://addons.mozilla.org/)

I'm not behind proxy and those https can be opened without any problem in Windows. Even in Live CD, the problem remains.

does anyone can help ?

---

### Post by the_doc on 2008-06-20
What's happening exactly?

---

### Post by seyed-mehdi on 2008-06-20
> **the_doc said:**
> What's happening exactly?


I can ping those https site's but when I want to open https site by Firefox or anyother browser after a minute or more it say's:

Network Timeout
The server at addons.mozilla.org is taking too long to respond.

that site is said just for example. the problem is with all of https pages.

---

### Post by Austin_KW on 2008-06-20
It may be tcp fragmentation; Try reducing the mtu eg for eth0, enter in a terminal and retry https
```

sudo ifconfig eth0 mtu 1400
```

---

### Post by seyed-mehdi on 2008-06-20
> **Austin_KW said:**
> It may be tcp fragmentation; Try reducing the mtu eg for eth0, enter in a terminal and retry https
```

sudo ifconfig eth0 mtu 1400
```

Already I had do that before, but nothing changes.

---

### Post by Austin_KW on 2008-06-20
Try flushing the iptables

 sudo iptables -F

---

### Post by the_doc on 2008-06-20
And it definately is all browsers and not just FF?

---

### Post by seyed-mehdi on 2008-06-20
> **Austin_KW said:**
> Try flushing the iptables

 sudo iptables -F

done, but no changes.

> And it definately is all browsers and not just FF? 
yeah surely I tested other browser, neither can open https.

Maybe it would be useful to say that those https can be opened by using webproxies.

but I notice something just now. I decide to make a bug report, as I open [http://bugs.launchpad.net](http://bugs.launchpad.net) it redirected to [https://bugs.launchapd.net](https://bugs.launchapd.net) and the page DID opened !

---

### Post by the_doc on 2008-06-20
I've found suggested fixes for that kind of beahviour in FF exclusively, bit that's not on the table if it's an 'all browser' issue.

---

### Post by seyed-mehdi on 2008-06-20
> **the_doc said:**
> I've found suggested fixes for that kind of beahviour in FF exclusively, bit that's not on the table if it's an 'all browser' issue.

sorry, I didnt got what you mean.

---

### Post by the_doc on 2008-06-20
After searching the web I found people with a similar issue and they included suggested fixes, however, in these cases the problem was with FF exclusively not all browsers as per you problem.

---

### Post by philinux on 2008-06-20
In firefox address bar type 

```
about:config
```

In the filter search type 

ipv6

double click that line to change it from false to true.

Close and restart FF see if that helps. If not change it back.

---

### Post by seyed-mehdi on 2008-06-20
> **philinux said:**
> In firefox address bar type 

```
about:config
```

In the filter search type 

ipv6

double click that line to change it from false to true.

Close and restart FF see if that helps. If not change it back.

I've search the web before making new post. I had disabled IPv6, reinstall FF, reconfigure FF and reconfigure openssl already and due to not finding any solution for the problem I make a new post.

I used w3m for testing if it can browse https, but the answer is clear that can't browsed.

---

### Post by seyed-mehdi on 2008-06-20
> **the_doc said:**
> After searching the web I found people with a similar issue and they included suggested fixes, however, in these cases the problem was with FF exclusively not all browsers as per you problem.

yeah I've problem with any browser I have.

---

### Post by Austin_KW on 2008-06-20
You initial post was a little unclear;
Can you browse to https using the live CD?

---

### Post by seyed-mehdi on 2008-06-20
> **Austin_KW said:**
> You initial post was a little unclear;
Can you browse to https using the live CD?

No, I can't

---

