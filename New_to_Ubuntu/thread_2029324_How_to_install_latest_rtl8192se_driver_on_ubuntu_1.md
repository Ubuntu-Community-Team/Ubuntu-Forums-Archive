---
title: "How to install latest rtl8192se driver on ubuntu 12.04"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by florida73 on 2012-07-19
I have a dual boot with windows7 and ubuntu 12.04.  The rtl8192se wireless driver on windows works great but the signal on ubuntu is not as good.  Would like to update to the latest realtek driver but blacklisting the generic driver and attempting to install the new driver has not been successful.  Any suggestions would be appreciated.  :smile:

---

### Post by m420n on 2012-07-19
Maybe your card is not operating at its max power level due to local regulations. 

These are different for every country and the driver seems to ignore the settings (and any changes).  

Have a look at this:

[http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/](http://ttys1.wordpress.com/2012/04/12/fixing-regulatory-domain-crda-of-realtec-wireless-device-drivers/)

Should give you full signal strength :) at least you should be able to set power manually
with: 

```
iwconfig
```

---

### Post by z3nhakr on 2012-07-19
the driver supplied with ubuntu should be the latest STABLE version. if you update to a newer one you will most likely have frequent crashes and it could break your installation.

---

