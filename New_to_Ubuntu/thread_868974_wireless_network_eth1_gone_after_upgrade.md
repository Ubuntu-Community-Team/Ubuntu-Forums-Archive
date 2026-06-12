---
title: "wireless network eth1 gone after upgrade"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by spearo on 2008-07-24
hi there. i recently upgraded to 8.04, which im beginning to feel might not of been the best move. i have a dell inspiron 1501 and with all the previous versions the wireless worked fine.

now after this upgrade, my laptop no longer acknowledges that it even has wireless capabilities. I type in ifconfig and it only shows the eth0 and the lo. eth1 has disappeared.

If anyone can help or want any more info please message back. Any help would be greatly appreciated!

Kind Regards

Liam

---

### Post by Seisen on 2008-07-24
What is the name of your wireless card?

```
lspci
```

---

### Post by spearo on 2008-07-24
got it working1 just needed to enable the wireless card in the hardware drivers.

thanks anyways

liam

---

### Post by marshall.robert on 2008-07-24
something i found is that since my upgrade to 8.04 from 7.10 my desktops wifi card went from eth1 to wlan0, but i didnt upgrade via the internet, i did a fresh install

---

