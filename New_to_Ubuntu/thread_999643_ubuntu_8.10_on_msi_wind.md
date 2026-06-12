---
title: "ubuntu 8.10 on msi wind"
date: 2008-12-02
forum: New to Ubuntu
---

### Post by lynx shadow on 2008-12-02
i just got an msi wind. i got it loaded with ubuntu 8.10 using wubi (cuz i don't have a cd drive), and win xp sp3 (which i loaded before my cd drive conked out).

the wind has realtek's 801.11b/g Mini Card wireless adapter. it works fine on xp, finding my router and connecting to the net just fine.

but when i run ubuntu, there's no wireless connection. which i found a bit strange cuz when i bought the wind, it was loaded with suse linux and the wireless worked just fine!

a friend has advised me that realtek has no linux drivers and has advised me to buy a dell broadcom adapter.

is this my best alternative? is there really no realtek wireless driver out there for ubuntu? or should i just load suse? i'm fairly new to linux so i'm open to any and all advice.

thanks

---

### Post by CholericKoala on 2008-12-02
There are many, many guides on this forum for how to get wireless to work on Ubuntu.  Depending on your card, there will be a different guide.  Typing lspci -nn in terminal will show you all your devices.  Of course you want the wireless one, so put the name of it in the search and look up the guide for your adapter.

Linux does not natively have drivers written for most wireless adapters, but there are wrappers for it to make them work surprisingly well.  Good luck!

---

### Post by lynx shadow on 2008-12-02
i'll do what you suggest. thanks.

---

