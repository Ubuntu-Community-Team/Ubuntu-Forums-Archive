---
title: "USB Modem in KDE Fedora"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Ginoxy on 2008-05-29
Good day all, i was trying to reach or find how to enable my USB modem (E220) in Ubuntu but i could not find i was able to enable it very easy and simple through KDE desktop in Fedora but unfortunately in ubuntu it is hard so any idea how to enable it ? 

Thanks in advance

---

### Post by rraj.be on 2008-05-31
Plug in the usb modem.

Just open the terminal and type
 
```
wvdialconf
```

it will search for usb modems that have been pluged in.

then it will save its settings in /etc/wvdial.conf.

just try whether your modem is detected and then you can just edit the seetings in /etc/wvdial.conf file according to your details.

or just  post a message if there any further problem

---

