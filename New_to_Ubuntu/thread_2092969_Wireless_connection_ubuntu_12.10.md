---
title: "Wireless connection ubuntu 12.10"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by shani1991 on 2012-12-09
Hi
I cant set up a wireless connection in my Ubuntu.
in windows I connect to a LAN network wireless ,then I connect to internet with a broadband connection.
Now I can connect LAN networks but how to set up a connection??

---

### Post by gandaran on 2012-12-09
most likely you need to install a driver first if the wireless card chipset is not supported with open source software.
lets see the hardware info, run in terminal this code and post the output
```
sudo lshw -C network
```

---

### Post by shani1991 on 2012-12-11
[IMG]http://img4up.com/up2/61803457895443644208.png[/IMG]

---

### Post by gandaran on 2012-12-11
hi
do you see any networks in the panel network icon? if you see one you just click it then network manager should ask you for the password, that's how easy it is to connect wireless on Ubuntu.
apparently the only issue on Ubuntu 12.10 with the Atheros wireless AR9285 chipset is a very slow internet
check these, one of them should provide a fix for you
 [http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10](http://askubuntu.com/questions/205704/cannot-get-atheros-ar9285-to-work-on-12-10)
[http://askubuntu.com/questions/206529/atheros-ar9285-wireless-extremely-slow](http://askubuntu.com/questions/206529/atheros-ar9285-wireless-extremely-slow)
[http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card/40692#40692](http://askubuntu.com/questions/37409/why-is-my-internet-so-slow-with-an-atheros-wireless-card/40692#40692)
[http://linuxplained.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/](http://linuxplained.com/how-to-fix-atheros-ar9285-ar9287-wireless-problems-in-ubuntu-1104/)

---

