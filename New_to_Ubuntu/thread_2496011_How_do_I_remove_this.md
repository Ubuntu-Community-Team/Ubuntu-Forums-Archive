---
title: "How do I remove this?"
date: 2024-03-11
forum: New to Ubuntu
---

### Post by ssalander on 2024-03-11
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293478&stc=1[/IMG]

Somebody has connected their Iphone to my computer. How do I get rid of the damn thing and prevent it from happening again?

---

### Post by ssalander on 2024-03-11
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293479&stc=1[/IMG]

After I changed my macadress this came up.

---

### Post by MAFoElffen on 2024-03-11
Please attach the results of these generated files to a post:
```

sudo netstat --tcp --udp --listening --programs --numeric 2>/dev/null >> connections_log.txt
nmap -sV --allports -T4 10.0.0.0/8 >> device_scan_tcp.txt
nmap -sV --script=broadcast-upnp-info -T4 10.0.0.0/8 >> device_scan_udp.txt

```
Changing the "Network" IP & it's network mask 10.0.0.0/8 (my own) to what yours is... For example if your IP address is 168.172.0.12, then 168.172.0.0/24...

The second one will take a long time to scan. Wait for it. 

The first scan will check anything connected to your device and which application it is connected through. The second and third scans will look for devices in your local network, to check for rogue device access.

Do you have a wireless network?

---

