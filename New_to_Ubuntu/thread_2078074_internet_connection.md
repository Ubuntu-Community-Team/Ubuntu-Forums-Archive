---
title: "internet connection"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by sheptel on 2012-10-30
Hi, I've installed ubuntu 12:04 and use mobile broadand.  On installation it was easy to connect the net. When I restart however the drop down menu in the connection icon, Does Not include an option for connecting. If I try to open firefox then try the icon again, Sometimes the connection option is there. Sometimes I have to try a few times before it appears. Sometimes its still not there so I go and add the connection all over again, and then the option appears.

There must be an easier way. Please dont reply in Geek.

---

### Post by varunendra on 2012-10-30
Hi sheptel, Welcome to the forums !

Please open a terminal (Ctrl+Alt+T), then enter or copy-paste the following commands and post their outputs here (do this after plugging-in your usb modem/mobile, then waiting 6-8 sec.):
```
lsusb
lsmod
dmesg | tail -20
```

While posting the outputs, click on **#** at the top of the edit-box (in which you write new posts) to auto-generate [ code] and [ /code] tags. Then copy-paste the outputs in-between those tags. This preserves the formatting, thus keeps the post clean and more readable.

You may also like to follow this thread : [http://ubuntuforums.org/showthread.php?t=2074129](http://ubuntuforums.org/showthread.php?t=2074129)

---

### Post by fat yak on 2012-10-30
sheptel, my 12.04 keeps my connections in 
/etc/NetworkManager/system-connections
might be worth a check to see if your mobile broadband connection is saved there. Each connection has a file with details ie name and type of connection, security etc.

---

