---
title: "wlan 54g w450"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by nukeworker on 2008-10-09
Hello

  I'm somewhat new at ubuntu so please bare with me. I do want to get away from windows though. I have a hp pavilion ze4800. Everything works but the wireless card. The card name is HP WLAN 54G W450. I think it's a broadcom 802  card though.

I have another laptop (acer) that the wireless works fine on. I just can't get this one to work. I downloaded cutter for the acer and it worked.  It does not seem to be working on this one. 

I will need detailed instructions if anyone can help me. 

Thanks 

Nukeworker:confused:

---

### Post by punong_bisyonaryo on 2008-10-10
Ok, so for the forum community to be able to help, you'll probably need to provide some more info. In this case, could you paste here the output of lspci (that command lists the pci devices in your computer).
After typing "lspci" in terminal, you'll get a lot of devices. We are particularly interested in your ethernet controller.

As an example, mine looks like this:
```
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

Paste your ethernet controller here and we'll figure out where to go from there.

---

### Post by punong_bisyonaryo on 2008-10-10
By the way, just in case, you can open terminal by clicking on Applications > Accessories then click on the "Terminal" menu item. The Windows command prompt looks like terminal.

---

