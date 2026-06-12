---
title: "CPU Temperature Clarification"
date: 2012-05-05
forum: New to Ubuntu
---

### Post by deepaknet on 2012-05-05
The following is the output regarding my CPU Temperature. Is it normal? The fan still doesn't appear to be chipping in.


lavanyadeepak@lavanyadeepak:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +51.0°C  (crit = +105.0°C)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +51.5°C  (high = +70.0°C)
                       (crit = +115.0°C, hyst = +115.0°C)

radeon-pci-0008
Adapter: PCI adapter
temp1:        +51.0°C

---

### Post by Paqman on 2012-05-06
Depends on what kind of chip you've got, and whether it's a laptop or a desktop. It's a little warm, but not too bad.

---

### Post by deepaknet on 2012-05-06
Toshiba Satellite C655 Laptop AMD processor

---

### Post by Paqman on 2012-05-06
No worries there then, the AMD chips are traditionally a bit hotter than Intel ones, and laptops run hotter than desktops.

---

