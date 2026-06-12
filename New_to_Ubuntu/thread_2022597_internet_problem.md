---
title: "internet problem"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by randhir4605 on 2012-07-11
I hv ubuntu 11.04. Proxy is installed in my college.
after installation ubuntu internet worked fine without setting
up any proxy address. 
I closed the terminal while installing mysql.
after that internet is not working even setting up proxy in mozilla and system wide proxy.

while in windows 7 internet works fine with proxy address.

so please help me out what should I hv to do.

---

### Post by papibe on 2012-07-11
Hi randhir4605. Welcome to the forums!

Open a terminal and try this:
```
sudo service network-manager restart
```
Tell us how it goes.
Regards.

---

