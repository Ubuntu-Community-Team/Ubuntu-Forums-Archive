---
title: "wireless bug"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by b-do on 2008-05-13
when i upgraded kubuntu my wireless driver was lost
my wireless device is :intel PRO/Wireless 3945abg 
please help!:confused:

---

### Post by hermes0710 on 2008-05-13
Can you post the output of :
```
dmesg
```

---

### Post by mapes12 on 2008-05-13
This post may be helpful:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

If that doesn't help then type:

```
sudo lshw
```

go down to the section

```
*-network
```

post the output back here

---

### Post by b-do on 2008-05-13
dmesg file

---

### Post by b-do on 2008-05-13
*-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:07:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1c:bf:be:2e:81
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

---

### Post by hermes0710 on 2008-05-13
Have you installed the linux backport/restricted modules?

---

### Post by b-do on 2008-05-13
yup
and every time i enable it from restricted drivers
it display ipw3945 in the component area
and not in use in the status area

---

### Post by hermes0710 on 2008-05-13
> **b-do said:**
> yup
and every time i enable it from restricted drivers
it display ipw3945 in the component area
and not in use in the status area

That is not good... What is the output of lsmod?

---

### Post by b-do on 2008-05-13
here is the output

---

### Post by b-do on 2008-05-13
anyone respond please, I'm getting crazy over here

---

