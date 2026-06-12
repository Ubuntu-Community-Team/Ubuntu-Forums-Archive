---
title: "network connection!"
date: 2012-09-30
forum: New to Ubuntu
---

### Post by jordan35080 on 2012-09-30
I just downloaded ubuntu onto my brothers computer and he cant connect to the network! i have wireless and i can connect but on his the connections dont show up. none of them it just says "device not ready" whats that?

---

### Post by kleinempfaenger on 2012-09-30
Hi, 

maybe you just have to activate network?

Or maybe it has to do with your brothers wireless card and the drivers. There are some additional firmware drivers available in Synaptic (for example Broadcom).

In some cases you have to install Windows drivers with Ndiswrapper (from Software Center or Synaptic). Tried that once, but it didnt work for me.



Greetings, kl

---

### Post by ranger1021994 on 2012-09-30
try installing wpa supplicant and ndis wrapper

---

### Post by daslinkard on 2012-09-30
What's the output of the following terminal command?
```

lspci
```

---

### Post by 2F4U on 2012-10-01
> **jordan35080 said:**
> I just downloaded ubuntu onto my brothers computer and he cant connect to the network! i have wireless and i can connect but on his the connections dont show up. none of them it just says "device not ready" whats that?

If you have the chance, connect this machine to a wired network connection and see if that works. If it works and Ubuntu is able to find appropriate drivers for the hardware, it will suggest to install them automatically. If not, as suggested in other posts, you should give more information about the hardware.

---

