---
title: "Cannot Connect to Wireless Internet"
date: 2012-05-07
forum: New to Ubuntu
---

### Post by StoneCampbell4Life on 2012-05-07
For some reason my laptop will not automatically connect to the Internet, so I have to do so manually. The problem is that the Network Manager application is the only way I know of that will allow me to be able to connect manually to the Internet, and the NM was uninstalled. In ordert to install it, however, you have to be connected to the Internet. I have no clue what to do!

---

### Post by Sonsum on 2012-05-07
Is a wired internet connection available to you to go and install NM?

I once ran into a similar problem with a Debian install (Network Manager doesn't come by default) and found it easier to find an Ethernet port for internet rather than manually set up the WiFi.

---

### Post by StoneCampbell4Life on 2012-05-07
I have acess to wired connection and I tried to use it, but when I plugged in the cable, it still didn't connect me to the Internet.

---

### Post by Sonsum on 2012-05-07
Try this page: [http://www.zachburlingame.com/2011/07/howto-enable-wired-networking-on-boot-in-ubuntu-linux-without-networkmanager/]("http://www.zachburlingame.com/2011/07/howto-enable-wired-networking-on-boot-in-ubuntu-linux-without-networkmanager/")

Of course, you can skip straight to "Enable Wired Interface".
I would recommend DHCP unless you have a special setup (it's just easier)

---

### Post by StoneCampbell4Life on 2012-05-09
Thanks! I had someone update my server and it's all good now.

---

