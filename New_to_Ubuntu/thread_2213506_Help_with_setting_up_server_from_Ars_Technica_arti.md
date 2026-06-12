---
title: "Help with setting up server from Ars Technica article"
date: 2014-03-27
forum: New to Ubuntu
---

### Post by ben_b2 on 2014-03-27
Hello. I've been following the steps from the article below:
[http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/](http://arstechnica.com/gadgets/2012/11/how-to-set-up-a-safe-and-secure-web-server/)

Everything has been going fine with the following configuration: (I had to turn on virtualization in my BIOS though)
-Windows 7 with VirtualBox
-Ubuntu Server 12.04

I've installed Nginx, and running the version command etc. all works fine. However, when I try to connect to my server from a different computer on the same network with the ip address I found from ifconfig and eth0, I am unable to connect to the server.
Suggestions? Thank you.

---

### Post by mastablasta on 2014-03-27
ubutnu is virtual box guest os? if so you need bridged network adapter set in virtual box setting. then you should be able to access it from LAN.

if you are still having problmes seting it all up in vbox perhaps look at some preinstalled options with premade virtual mashcines such as bitnami stack or turnkey linux.

---

