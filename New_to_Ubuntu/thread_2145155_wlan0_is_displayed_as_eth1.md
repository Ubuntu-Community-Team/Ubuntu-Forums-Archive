---
title: "wlan0 is displayed as eth1"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by asmolinski on 2013-05-14
Does anyone know why my wireless card is seeing it as eth1 instead of what it should be wlan0? It's not an issue i'm just really curious. I have a lenovo g560 running ubuntu 13.04

---

### Post by bkratz on 2013-05-14
> **asmolinski said:**
> Does anyone know why my wireless card is seeing it as eth1 instead of what it should be wlan0? It's not an issue i'm just really curious. I have a lenovo g560 running ubuntu 13.04



Ubuntu does not always generate a wlan0, different software such as the STA driver create eth1.  Don't worry about it, it is normal.

---

### Post by asmolinski on 2013-05-14
I'm not worried, I was just curious. I started using Ubuntu at 11.04. starting at 11.10 or 12.04 it changed to eth1. It was just more out of curiosity.

---

### Post by bkratz on 2013-05-14
What type of card or driver are you using?

If you drop to the terminal and type


lspci -n | grep 0280


it will let us know what card you have (by the way that is LSPCI in lowercase not 1)

---

### Post by asmolinski on 2013-05-14
```
andrew@andrew-Lenovo-G560:~$ lspci -n | grep 0280
05:00.0 0280: 14e4:4727 (rev 01)



```

---

### Post by bkratz on 2013-05-14
You are using a Broadcom card, and probably the sta driver which does create eth1 rather than wlan0. If you drop to the terminal and type in

lsmod


(LSMOD in lowercase) . You should see wl as one of the listed modules ( that is the STA driver!)

---

### Post by asmolinski on 2013-05-14
I found the wl module, interesting though. It says it is used by 0.

---

