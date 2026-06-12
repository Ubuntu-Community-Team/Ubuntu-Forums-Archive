---
title: "Second monitor not detected after update from 14.04 to 16.04"
date: 2016-08-22
forum: New to Ubuntu
---

### Post by gramdel2 on 2016-08-22
After upgrading from 14 to 16 the second monitor is not detected. They both work individually regardless of which display port input i plug them in. But when i connect second monitor, one of them goes black and is not detected as connected anymore. 

```
lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller (rev 06)
```

```
sudo lshw -c video   *-display               
       description: VGA compatible controller
       product: Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 06
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:29 memory:f7800000-f7bfffff memory:e0000000-efffffff ioport:f000(size=64)
```

```
sudo xrandr -qScreen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP1 disconnected (normal left inverted right x axis y axis)
DP2 disconnected (normal left inverted right x axis y axis)
HDMI1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 531mm x 299mm
   1920x1080     60.00*+  50.00    59.94    59.99  
   1920x1080i    60.00    50.00    59.94  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1366x768      59.79  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.08    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
HDMI2 disconnected (normal left inverted right x axis y axis)
VGA1 disconnected (normal left inverted right x axis y axis)
VIRTUAL1 disconnected (normal left inverted right x axis y axis)
```

---

### Post by gramdel2 on 2016-09-06
bump

---

