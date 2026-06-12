---
title: "HowTo: VMware Server 1.0.1 on Ubuntu Server 6.10"
date: 2006-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Incroyable HULK on 2006-11-08
I hope this ain't against this forum rules to post an external link to my blog... if so, I apologize :oops: 

I've made an HowTo about Ubuntu and VMware Server that you can read here: 
[http://itgeek.squarespace.com/journal/2006/11/7/howto-vmware-server-101-on-ubuntu-server-610.html]("http://itgeek.squarespace.com/journal/2006/11/7/howto-vmware-server-101-on-ubuntu-server-610.html")

I wrote this guide as a reminder and a documentation for my work but also to share the knowledge. I hope this can help. 

Comments and improvements are welcome!

---

### Post by domino on 2006-11-10
I use Ubuntu 6.10 server appliance and i also have it stored on an NTFS external drive with NTFS-3G driver loaded on Ubuntu 6.10 desktop. I share my 6.10 server with windows host and this is where the no bridged networking problem begins. This is the solution. Run command in ubuntu guest OS:

```
sudo nano /etc/iftab
```

comment out eth0, Ctrl+x to save, press y, then Enter. Reboot vmware session and bridged networking should now work in both windows host and linux host using the same ubuntu 6.10 server vmware image.

---

