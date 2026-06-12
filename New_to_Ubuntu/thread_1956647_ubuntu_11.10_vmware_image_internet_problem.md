---
title: "ubuntu 11.10 vmware image internet problem"
date: 2012-04-11
forum: New to Ubuntu
---

### Post by pamuluri on 2012-04-11
Hi all,
 
I am very happy to drop first message in this great forum!.
 
i am facing issue to access internet in ubuntu 11.10 vm image (32bit), let me give details:
 
1.Base OS: Windows 2008 server , IP:10.200.61.127
2.I have downloaded the ubuntu-11.10-desktop-i386.iso file.
3.using vmware player i have created ubuntu image with 1GM ram and 30gm hd.
4.Vmplayer settings for this vm image: Network Adapter->NAT (radio buttion) enabled.
4.System Setting -> Network proxy -> 
method:manual 
http proxy: pdc-proxy.wipro.com (same as base machine)
5.Edit connections ( Network connections)
wired (tab) -> add new connection with details:
for IPV4 settings: address(x.x.x.x) , netmask (x.x.x.x) , gateway (x.x.x.x) , 
DNS servers(x.x.x.x) searchdomains (x.x.x.x) 
all details are same as base machine.
 
6. Mrozilla Firefox settings.
Edit->preferences ->Network ->settings
(radio buttion) manual proxy configuration is enabled.
HTTP proxydc-proxy.wipro.com port:8080 (same as base machine.)
 
7.output of $ifconfig
etho
inet addr:192.168.59.130->which differet form baseMachine ip(IP:10.200.61.127)
Bcase: 192.168.59.255
mask: 255.255.0
lo
inet addr: 127.0.0.1 Mask: 255.0.0.0
inet6 add: : :1/128 scope: host
 
still i am not able to access the internet.
i am struggling with this problem since 3 days. Your help is highly appreciated.
 
thanks
chandra.

---

