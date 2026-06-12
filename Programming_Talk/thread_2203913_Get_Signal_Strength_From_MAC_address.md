---
title: "Get Signal Strength From MAC address"
date: 2014-02-05
forum: Programming Talk
---

### Post by shibby4555 on 2014-02-05
I'm working on a project that requires me to know the signal strength of a mac address. I have no idea how to go about this other than maybe running airodump and recursively regexing it

Any ideas?

---

### Post by steeldriver on 2014-02-05
I'm not sure exactly what you're asking, but if you are running a fairly recent standard Ubuntu desktop system (i.e. with interfaces controlled by network-manager), then the nmcli utility can provide that info

```
nmcli --fields BSSID,SIGNAL dev wifi list
```

or to match and select a specific BSSID (MAC)

```

nmcli --fields BSSID,SIGNAL dev wifi list | awk -v bssid="$mac" '$1 ~ bssid {print}'

```

Depending on your language preference you should be able to obtain the same information via dbus

---

### Post by shibby4555 on 2014-02-05
So close,

Thats pretty much what I was looking for except it only displays router mac addresses, need to be able to pick up clients mac addresses.

---

