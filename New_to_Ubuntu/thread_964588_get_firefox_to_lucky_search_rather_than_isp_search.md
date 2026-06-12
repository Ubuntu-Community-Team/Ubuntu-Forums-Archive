---
title: "get firefox to lucky search rather than isp search"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by Razerblader on 2008-10-31
If I type in something like "google" into my browser, it'll take me to [http://www11.charter.net/search?qo=google&rn=AQC4vdPJNxI2-H5&rg=]("http://www11.charter.net/search?qo=google&rn=AQC4vdPJNxI2-H5&rg=") when I ran Vista or any other windows OS, I would be directly taken to google.com How do I fix this, I want direct access.

---

### Post by wardrich on 2008-10-31
What search engine do you have selected?

---

### Post by lifestream on 2008-10-31
Some ISPs are nice enoguh to have the option to turn it off. You might ask them.

Otherwise, use OpenDNS servers: 208.67.222.222 and 208.67.220.220 instead of your ISP DNS.

I know how to set that up in Wicd (easy as pie) but not Network Manager.
So let me know if you decide to go that route.

---

### Post by Razerblader on 2008-10-31
just a standard install, the only times it redirects me to my ISP's search page is when I type in one word queries, anything at 2 words or above it'll use google. I can set it to take me to google, but I have to enable cookies, and I don't want to do that, I guess I'll go with the OpenDNS thing.

---

### Post by LookTJ on 2008-10-31
> **Razerblader said:**
> just a standard install, the only times it redirects me to my ISP's search page is when I type in one word queries, anything at 2 words or above it'll use google. I can set it to take me to google, but I have to enable cookies, and I don't want to do that, I guess I'll go with the OpenDNS thing.
If it's one word searches, it may be the case your ISP's DNS searching for a domain for that one word, and uses their search engine. 
OpenDNS is the same way, but a little bit more options provided you creating an OpenDNS account, like typo corrections, phish protection etc.

:)

---

### Post by lifestream on 2008-11-03
You can turn off that "friendly" search page when you Use opendns. I opendns and never got those annoying pages :3

---

