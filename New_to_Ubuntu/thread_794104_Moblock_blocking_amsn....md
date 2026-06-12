---
title: "Moblock blocking amsn..."
date: 2008-05-14
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-14
How do you create exceptions in moblock? so it doesn't block amsn

Thanks in advance:)

---

### Post by 505 on 2008-05-14
Open the file /etc/moblock/moblock.conf and whitelist the ports MSN should use. Look for the line "WHITE_TCP_OUT=" and add the ports for MSN.

---

