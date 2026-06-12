---
title: "What file does network manager modify?"
date: 2014-01-08
forum: New to Ubuntu
---

### Post by bortable on 2014-01-08
I was trying to set a static ip on my laptop on wlan0 via the terminal. I followed a lot of tutorials found by googling but none of them worked. I broke down and used the Ubuntu network settings to set a static ip and it worked. I am curious to know as to what file does the gui modify? 

```
/etc/network/interfaces
```?

---

### Post by Iowan on 2014-01-08
Look in */etc/NetworkManager/system-connections*. There are files for the different interfaces. You'll probably need **sudo** to view them.

... and you'll need to either escape (with backslash) the spaces in the names, or surround the names with single or double quotes.

---

### Post by bortable on 2014-01-08
Thanks! So is setting a static ip on a wireless adaptor different than setting it on the eth0 adaptor?

---

