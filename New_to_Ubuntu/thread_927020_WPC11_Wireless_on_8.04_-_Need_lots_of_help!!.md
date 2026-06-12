---
title: "WPC11 Wireless on 8.04 - Need lots of help!!"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by GatorsUF on 2008-09-22
I followed a few tutorials and I can't begin to tell you exactly what all I did.  In essence I believe I...

- installed ndiswrapper and I have the "Windows Wireless Driver" program installed.  

- I then downloaded the drivers for my Linksys WPC11 and used the Windows Wireless Driver" to install the .INF file.  I says "unable to see if hardware is present"

- I also tried the driver from the Realtek 8180 because I read that is the one I should use, it gives me the same error.

I do not have any clue where to go from here.  I thought maybe my pci card slot wasn't recognized, because it doesn't make any noises when I put the card it.

---

### Post by willca on 2008-09-23
can ya do this and see whats the card being recognized as..

lspci | grep -i ethernet

---

