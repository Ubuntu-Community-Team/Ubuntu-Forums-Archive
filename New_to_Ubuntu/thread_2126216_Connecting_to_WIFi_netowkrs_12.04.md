---
title: "Connecting to WIFi netowkrs 12.04"
date: 2013-03-16
forum: New to Ubuntu
---

### Post by 12roby21 on 2013-03-16
I ubuntu dual booted on a HP laptop reloaded with win 8. Everything is working fine but a have a problem. My internet connection is fine with an ethernet cable but without it ubuntu doesnt find any networks to connect to. Im thinking Ubuntu doesnt recognize my Network interface card but im not sure. any suggestions? I used ubuntu back in hardy heron but am just coming back to it, so any help appreciated.
Thanks!

---

### Post by carl4926 on 2013-03-16
Let us see

```
[COLOR=#000000][FONT=Droid Sans]lspci -nnk | grep -iA2 net[/FONT][/COLOR]
```

---

### Post by 12roby21 on 2013-03-16
Is this what you wanted?


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:1858]
    Kernel driver in use: r8169
--
02:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0036] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:18e3]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device [10ec:5229] (rev 01)

---

### Post by wildmanne39 on 2013-03-16
Hi, this link should get you going.
[http://ubuntuforums.org/showthread.php?t=2103062](http://ubuntuforums.org/showthread.php?t=2103062)
Thanks

---

