---
title: "Help me with Firefox not using DNS"
date: 2009-06-22
forum: Ohio Team - US
---

### Post by zerhacke on 2009-06-22
I have a strange problem.  Firefox will not use DNS.  I can get to Google by IP but not by domain name.  I can't get to ANYTHING by domain name.

Opera has the same problem and so does seamonkey.

However, Konqueror will browse just fine.

Can any of you help me get DNS back on Firefox??

---

### Post by Derath on 2009-06-23
Sounds like 2 possibilities to me, first you set a proxy or something under firefox and all, or second there's a dns config issue. Do a "cat /etc/resolv.conf" to see what servers you're using for dns. I can't remember what I did to fix that, but I used eth0 at college and it forced the college's dns and search settings to keep populating into resolv.conf, and that messed a lot of things up for me.

You could also try using OpenDNS for your dns server settings in NetworkManager ([http://www.opendns.com](http://www.opendns.com), dns server addys: 208.67.222.222 and 208.67.220.220)

---

### Post by zerhacke on 2009-06-23
openDNS did not solve the problem, and I have no proxies set up in firefox.

I would think that if it were a DNS problem that Konqueror would not be able to get pages either.

---

### Post by Derath on 2009-06-23
Well, I'm out of ideas

---

### Post by Panhead Bill on 2009-06-23
I'm haveing a similar issue.  I tried to set up a static address for Mythtv, but when I did, Firefox then failed to "find" any of my saved searches.  I was able to connect to my router (192.168.0.1).

---

