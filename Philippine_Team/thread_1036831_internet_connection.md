---
title: "internet connection"
date: 2009-01-11
forum: Philippine Team
---

### Post by king leoric on 2009-01-11
Hello guys. As of now nasa korea me. Got a question here

As of now naka dual boot me with XP. At connection ko ay Broadband. If using windows, got a connection right at once at ang settings ay auto (assigned by DHCP) meaning changing ip or ip is assigned automatically. Pag sa ubuntu na, nakakaconnect naman pero endi makaasign ng ip address thus endi ako makaconnect. That was the original setting (roaming mode), what I've done was boot at XP. took IP address, subnet mask and DNS and manually configure my ubuntu. and Yes I was connected.

Now my question is, anu ang pwede kong gawin para maibalik ko sa roaming mode at maka connect siya kasi pag binalik ko roaming mode, mawawala ang connection ko.

By the way, I'm using Hardy (LTS version)

Many thanks po sa inyong lahat ::p

---

### Post by daxumaming on 2009-01-11
possibly a bug with Network Manager. Had that same problem back during my Hardy days, but it did improve with the Intrepid release. You could try using WICD and uninstall Network Manager, that's what I used back in Hardy.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by kiminaiseah on 2009-01-12
@king leoric 

sudo /etc/init.d/networking stop
sudo /etc/init.d/NetworkManager stop

sudo nano /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

sudo /etc/init.d/networking start

sudo update-rd.d -f NetworkManger remove

remedy for wired connection

---

