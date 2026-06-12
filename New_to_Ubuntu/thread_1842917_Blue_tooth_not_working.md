---
title: "Blue tooth not working"
date: 2011-09-12
forum: New to Ubuntu
---

### Post by chitragurung on 2011-09-12
I have been using Dell Inspiron Mini with ubuntu 10.04. I noticed that bluetooth is not working. When I click on bluetooth button on panel  it does not response. I try to install and reinstall from package manager but no success. When I click on bluetooth button it gives error message Bluetooth Bhuz daemon is not connected etc.

---

### Post by LowSky on 2011-09-12
```
sudo service bluetooth restart
```

---

### Post by gandaran on 2011-09-12
> **chitragurung said:**
> I have been using Dell Inspiron Mini with ubuntu 10.04. I noticed that bluetooth is not working. When I click on bluetooth button on panel  it does not response. I try to install and reinstall from package manager but no success. When I click on bluetooth button it gives error message Bluetooth Bhuz daemon is not connected etc.
the wireless switch is on?

---

### Post by chitragurung on 2011-09-16
hello,

I did both but no result. Where is the wireless switch ?

---

### Post by gandaran on 2011-09-16
> **chitragurung said:**
> hello,

I did both but no result. Where is the wireless switch ?
check your laptop specifications.

also check in BIOS that bluetooth in enabled.

---

### Post by Lisiano on 2011-09-16
Don't know but maybe this might work?```
sudo rfkill unblock bluetooth
```

---

