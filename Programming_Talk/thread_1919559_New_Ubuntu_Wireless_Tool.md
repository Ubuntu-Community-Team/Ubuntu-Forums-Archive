---
title: "New Ubuntu Wireless Tool?"
date: 2012-02-03
forum: Programming Talk
---

### Post by james.kenaley1 on 2012-02-03
I don't want anyone to tell me "How To Do It" but how I would go about making a wireless script to connect to a known network automatically AND if there are more then one "known" network to connect. Connect to the one that has a better signal quality. (I.e. drivers to include what lib's to address etc...)
Thank you,
James

P.s. I apologise if I came off a little rude

---

### Post by emiller12345 on 2012-02-04
What I would do is look at how someone goes about logging into a wireless router from the commandline, then look at a scripting language like Bash to automate it.  
To get started
```
~$ man wpa_supplicant
```
this program is what your Ubuntu computer is most likely currently using if your not using an open wifi router (i.e. using WEP, WPA, or WPA2). wpa_supplicant is used by NetworkManager to handle wifi connections.

---

