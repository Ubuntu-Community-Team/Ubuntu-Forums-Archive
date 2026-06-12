---
title: "Can't Find Firefox-Bin?!?!?"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by redmask on 2013-06-23
I can't seem to find firefox-bin, I tryed "ps -e", "locate firefox-bin" "whereis firefox-bin" and a few other options but I cannot find it.

I am ubuntu 12.04 TLS.

---

### Post by deadflowr on 2013-06-23
Don't know what firefox-bin is, but the firefox should be /usr/bin/firefox.

If that's what you mean.

You could also just use locate firefox, and search the results.

---

### Post by Irihapeti on 2013-06-23
*Thread moved to **Absolute Beginners Section**.*

---

### Post by monkeybrain2012 on 2013-06-23
You get firefox-bin in the downloaded folder if you get Firefox from Mozilla. But the executable for the Ubuntu installed version is /usr/bin/firefox as deadflower said.

---

### Post by deadflowr on 2013-06-23
No wonder I never heard of it.
Why would one need to download it from mozilla when you get a perfectly good, well maintained version by default, and updated consistently?

---

### Post by Impavidus on 2013-06-24
> **monkeybrain2012 said:**
> You get firefox-bin in the downloaded folder if you get Firefox from Mozilla. But the executable for the Ubuntu installed version is /usr/bin/firefox as deadflower said.

If fact, /usr/bin/firefox is a symlink to /usr/lib/firefox/firefox.sh, which is a shell script that starts /usr/lib/firefox/firefox. IIRC, that last one used to be called firefox-bin.

---

