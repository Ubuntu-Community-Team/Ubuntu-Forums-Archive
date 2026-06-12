---
title: "How to connect to WIfi (Ubuntu 12.10)"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by arden2 on 2014-01-20
Good day, I have Ubuntu 12.10 installed in my laptop. I want to install my wifi card so i can download some application for linux. can somebody help me?

---

### Post by squakie on 2014-01-20
First, you should have a little network manager icon on the top bar.  If you click on that, does it show networking enabled and wireless networking enabled?  If so, do any networks show as available?  If so, pick the one you want to connect to.  Remember any "protected" network is going to require a passwork/passkey.

If wireless is not enabled, try enabling it, then see if any networks appear.

If wireless won't enable, then post back the output of these commands:

- if your wireless adapter is internal, it is most probably (but not always) a PCI device:

lspci | grep wireless (or perhaps Wireless - I don't have an internal adapter so I can't say)

- if it's a USB device:

lsusb

- for all:

ifconfig

iwconfig

Post the outputs back here from all of those and we can go from there.

---

### Post by carl4926 on 2014-01-20
Can we please the the result of
```
lspci -nnk | grep -iA2 net
```

---

