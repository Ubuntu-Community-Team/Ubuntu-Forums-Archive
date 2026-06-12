---
title: "LAN network connected but it doesn't work"
date: 2014-10-07
forum: New to Ubuntu
---

### Post by masood-meidani on 2014-10-07
Hi,
I installed Kubuntu 12.04 on my PC and it is connected via LAN but it doesn't work and I cannot load any page!
What is the problem?

Thanks.

---

### Post by varunendra on 2014-10-08
Welcome to the forums masood-meidani!

Please open a terminal (Ctrl-Alt-T) and post back the outputs of -
```
sudo lshw -C network
nm-tool
route -n
cat /etc/network/interfaces
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

