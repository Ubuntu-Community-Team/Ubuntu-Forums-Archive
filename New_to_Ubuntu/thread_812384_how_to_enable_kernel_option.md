---
title: "how to enable kernel option?"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by aswantaraukta@gmail.com on 2008-05-29
Hello, i want to monitoring soekris net 4801. The requirement are enabling some of kernel option like :
    *I2C support (CONFIG_I2C)
    *National Semiconductor PC87360 family (CONFIG_SENSORS_PC87360)
and need to pass at least init=1 to the pc87360 driver. How can i enable this kernel option? Please any help.
Thanks.


Regards,


Komang

---

### Post by quelx on 2008-05-29
Those options are already set in the kernel

```
.
# CONFIG_HZ_300 is not set
**CONFIG_I2C=m**
CONFIG_I2C_ALGOBIT=m
.
.
CONFIG_SENSORS_MAX6875=m
**CONFIG_SENSORS_PC87360=m**
CONFIG_SENSORS_PC87427=m
.
```

so you need to ```
sudo rmmod pc87360
``` then ```
sudo modprobe pc87360 init=1
```

---

