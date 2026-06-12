---
title: "Reatek wireless woes..."
date: 2008-08-06
forum: New to Ubuntu
---

### Post by pikeman47 on 2008-08-06
Today I went out and bought a laptop for myself (a Gateway T-series) and installed Ubuntu 8.04 right away. Quite unfortunately, the internal wireless card was not automatically detected, and being a laptop, wireless internet is pretty important:). I've done a little searching on these forums but nothing I've found has been able to fix my problem. All I know is it's a internal Realtek wireless card (not sure of the model and not sure how to find that out) and that's about it. Could somebody walk me through the process of getting my wireless to work?
Thanks!

[Edit] Just realized I misspelled Realtek in the thread title. woops

---

### Post by wdaniels on 2008-08-06
Please post the result of this command:

```
lspci | grep Realtek
```

(though I think I can already guess - the 8185)

---

### Post by pikeman47 on 2008-08-06
```
08:00.0 Network controller: Realtek Semiconductor Co., Ltd. Unknown device 8199 (rev 22)
0e:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

---

### Post by wdaniels on 2008-08-06
Interesting, that one should work with the rtl8187 driver I think. Try this first:

```
sudo modprobe rtl8187
```

---

### Post by pikeman47 on 2008-08-06
ok
ran that command and i don't think anything happened

---

### Post by wdaniels on 2008-08-06
I've done some investigating and though the information is quite patchy, it seems to suggest that 8199 equates to 8187SE, for which there only seems to be a patched version of the old r8180 module available at present.

I suggest you try the directions for compiling the patched sources [as given here]("http://wiki.msiwind.net/index.php/Ubuntu_8.04_Hardy_Heron#Option_2:_Compiling_Drivers_for_the_Supplied_Wireless_Card").

---

