---
title: "Error while starting Ubuntu 12.10,"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by mayank2013 on 2013-03-15
Hi I am new to ubuntu 12.10

After installing ubuntu i installed Power tools since my battery was draining out fast
But, now everytime I boot, I get this error on startup where screen is black... and it says

Speed_dispatcher disabled.
saned disabled
Enabling Laptop mode

SG_IO bad missing sense data.....
etc....

And this doesnt allow me to log into ubuntu which i believe loaded well in background...

Any advice from someone who has faced this issue... I have to restart numerous times before it loads correctly

Thanks,
Mayank

---

### Post by matt_symes on 2013-03-15
Hi

> SG_IO bad missing sense data

This sounds like a hard drive issue. Maybe hdparm is running on your system now to power down the hard drive.

Can you post the output of (when you can get it to boot)

```
sudo grep -r hdparm /etc
```

Kind regards

---

