---
title: "Wired connection always swiches off"
date: 2014-04-26
forum: New to Ubuntu
---

### Post by mervyn2 on 2014-04-26
Fine for 5 minutes after booting but then disconnects.   Only way I have found to reconnect is to reboot.
May also be tied up to fact that I could not load Ubunto 12 with the added drivers and the system does not find the WiFi connection only the cable.   The PC has the minimum memory spec only

---

### Post by varunendra on 2014-04-27
Welcome to the forums mervyn2!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
uname -mr
lsb_release -d
lspci -nnk | grep -iA2 net
free -m
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by squakie on 2014-04-27
Also post back your hardware specs, since you mentioned you have limited memory.  We need to know the cpu, memory, disk if possible.

---

