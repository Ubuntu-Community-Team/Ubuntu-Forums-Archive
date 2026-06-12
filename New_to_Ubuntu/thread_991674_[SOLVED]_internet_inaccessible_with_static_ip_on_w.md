---
title: "[SOLVED] internet inaccessible with static ip on wifi"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by akkad on 2008-11-24
whenever i connect to my wireless gateway with a static ip i get connected successfully and i appear on the network but the internet become inaccessible, using dhcp has no problem at all, am using ubuntu 8.10.

---

### Post by chuckyp on 2008-11-24
This si a known bug with using a static ip and 8.10. It hasn't been fixed yet. It was in the release notes. I've found to use a static ip I have to remove network-manager completely from startup and sessions. Then you can use /etc/network/interfaces

---

### Post by akkad on 2008-11-24
> **chuckyp said:**
> This si a known bug with using a static ip and 8.10. It hasn't been fixed yet. It was in the release notes. I've found to use a static ip I have to remove network-manager completely from startup and sessions. Then you can use /etc/network/interfaces

do you have the bug log? am looking to follow up.

---

### Post by akkad on 2009-01-01
i found a solution over the net where i lost the link :(, any way the solution is to create a new connection (not editing the exist connection, leave it as is) in gnome network manager and then set it as static IP, this works with me.

---

