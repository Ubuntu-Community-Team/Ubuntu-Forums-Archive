---
title: "Drivers for HD 4250"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by Suicidemoon on 2013-03-14
I am using 12.10 and i can NOT get any drivers for my HD 4250 (laptop) onboard to go in! I have tried a hundred different ways with google and they either show just a blank desktop, or like am sitting at now after installing this [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

My system just says Ubuntu and goes to a blank black screen. Trying to take out the ppa with the ROOT thingy will not work as he does not know the command.

Anyone Please help? Linux is way harder than windows but so so so much better if i can get my drivers installed!

Thanks!

---

### Post by mastablasta on 2013-03-14
try 12.04 LTS rather than downgrading the x server. see if that works better and install should be easier.

---

### Post by rrich1974 on 2013-03-14
hd 4xxx does not work on 12.10....install 12.04

---

### Post by 3rdalbum on 2013-03-14
> **rrich1974 said:**
> hd 4xxx does not work on 12.10....install 12.04

Not quite true; what you mean is the official AMD/ATI driver that works on 12.10 doesn't support the HD4000 series. In order to use the older version of the driver that still supports the card, you need to be using 12.04.

So yes, if you want the best 3D performance you need to be using the AMD/ATI Catalyst driver on 12.04. The card works on 12.10, but only with the open-source driver that won't give you very good 3D performance.

---

### Post by mad2-814 on 2013-03-14
> **Suicidemoon said:**
> I am using 12.10 and i can NOT get any drivers for my HD 4250 (laptop) onboard to go in! I have tried a hundred different ways with google and they either show just a blank desktop, or like am sitting at now after installing this [https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx)

My system just says Ubuntu and goes to a blank black screen. Trying to take out the ppa with the ROOT thingy will not work as he does not know the command.

Anyone Please help? Linux is way harder than windows but so so so much better if i can get my drivers installed!

Thanks!

What laptop do you have? If it has switchable graphics, you must select dedicated only in you bios.  I have a thinpad w500 with a card comparable to a 3650 and the ppa you listed worked without a problem after turning off mu switchable graphics.  Also, if it doesnt seem to be taking the driver, try booting into the recovery mode and run this command as root.

```
aticonfig --initial
```

---

