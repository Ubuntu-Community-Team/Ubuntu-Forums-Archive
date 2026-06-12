---
title: "No wired connection with 13.10"
date: 2013-10-22
forum: New to Ubuntu
---

### Post by w0lf19 on 2013-10-22
So today I installed 13.10 on my spare box after clearing out Vista and reformatting the drive. Install went fine. 

However, I cannot connect to the internet. I have a wired connection. It was working fine in windows. I connect through a router.

Any suggestions?

---

### Post by varunendra on 2013-10-24
Have you checked that the Ethernet interface is active or not? Does the Network Manager show it as connected?

Please open a terminal (Ctrl-Alt-T), and post back the output of following commands -
```
lspci -nnk | grep -A2 0200
nm-tool
cat /etc/network/interfaces
cat /etc/NetworkManager/NetworkManager.conf
cat /var/lib/NetworkManager/NetworkManager.state
```

While posting the outputs, please use the '**Code**' box. It preserves its formatting and makes your post cleaner, compact and more readable. Follow the "Using Code Tags" link in my signature to see how.

---

