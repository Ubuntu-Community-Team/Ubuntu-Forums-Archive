---
title: "[Archlinux] Getting deluge play nice with trackers"
date: 2007-12-21
forum: Other OS Talk
---

### Post by kpkeerthi on 2007-12-21
[ I'm at work and quite free :) Thanks to Christmas. The proxy here blocks access to Arch forum so I'm posting here. I hope it is OK with you guys. ]

This is my first attempt to use a torrent. After searching around, I decided to try Deluge. 

I'm connected to internet via Router (192.168.1.1). So I'm firewalled. To be nice with the trackers, I decided to forward port 6881 Deluge is listening on to my static-IP'ed host 192.168.1.2. I restarted my router to make sure that the port-forwarding changes take effect.

I launched Deluge and then used [nmap-online]("http://nmap-online.com/") (-p 6881-6881) to check if the port 6881 is visible to the outside world. But it reports that the port is not open. I verified with netstat and it reports that port 6881 is being listened on.

I'm not sure if I should add 'something' to /etc/hosts.allow. This file is empty right now. Should I add my router's IP to this file or the port# 6881 or both? And how? I'm not running iptables/firestarter other than this. 

Any help is much appreciated. Thanks in advance.

---

### Post by OoooMatron on 2007-12-21
Firstly, do the test with the linux firewall disabled to ensure that the port is being forwarded correctly in the first place. There's no point trying to troubleshoot until you take down each barrier one by one.

I would also recommend moving the deluge port to something else (doesnt matter what, keep it high like 62111 for example) as some trackers block the default port ranges. Of course, youll need to forward that port instead.

---

### Post by lvleph on 2007-12-21
> **OoooMatron said:**
> Firstly, do the test with the linux firewall disabled to ensure that the port is being forwarded correctly in the first place. There's no point trying to troubleshoot until you take down each barrier one by one.

I would also recommend moving the deluge port to something else (doesnt matter what, keep it high like 62111 for example) as some trackers block the default port ranges. Of course, youll need to forward that port instead.

Also, some trackers do not allow the use of Deluge as a client. The trackers I use only allow BitTorrent, Azureus, and utorrent.

---

### Post by OoooMatron on 2007-12-21
> **lvleph said:**
> Also, some trackers do not allow the use of Deluge as a client. The trackers I use only allow BitTorrent, Azureus, and utorrent.

That's also a good thought. Though I do use Deluge myself and all the sites I have used work with it (private and non private).

---

