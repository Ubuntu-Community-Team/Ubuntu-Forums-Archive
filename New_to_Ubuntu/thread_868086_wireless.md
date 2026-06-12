---
title: "wireless"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by sameer.india on 2008-07-23
I upgraded to hardy from gutsy.
While I had gutsy I had kernel 2.6.22-14-generic i which all is fine.
But now I have another kernel too which is 2.6.24-19-generic.
In this Kernel the wireless driver is not good.
As the indicator doesn't show whether wireless is on or off and many times suddenly the signal is lost.

---

### Post by phidia on 2008-07-23
What wireless card do you have? From a terminal lspci -v or lshw -C network should provide that. Once you have the model you can search at the forums here or specifically the [Networking & Wireless Forum]("http://ubuntuforums.org/forumdisplay.php?f=336").

---

### Post by sameer.india on 2008-07-23
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by phidia on 2008-07-23
> **sameer.india said:**
> 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

Take a look at the thread [here]("http://ubuntuforums.org/showthread.php?t=820297&highlight=Intel+Corporation+PRO%2FWireless+3945ABG") and the link to a fix within that thread. Hope that helps.

---

