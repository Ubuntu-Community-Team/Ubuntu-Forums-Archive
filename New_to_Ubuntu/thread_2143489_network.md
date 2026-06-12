---
title: "network"
date: 2013-05-09
forum: New to Ubuntu
---

### Post by gkanengoni on 2013-05-09
i have installed ubuntu 10.04.1 on a lenovo ThinkCentre M92p and after installation its like there are no network drivers since its saying no network devices.i want it to run on a wired network and i do not know what to do

---

### Post by Cheesemill on 2013-05-09
Try installing a version of Ubuntu that is still supported such as 12.04 or 13.04 as these have drivers for newer networking hardware built in.

10.04 has now reached end-of-life and so won't be receiving bug fixes or security updates any more.

---

### Post by grahammechanical on 2013-05-09
No network devices found can also mean that the network adapters are switched off. This could happen with laptops as a power saving action. run this command

```
rfkill list
```

and see if there is a hardware block or a software block.

Regards.

---

