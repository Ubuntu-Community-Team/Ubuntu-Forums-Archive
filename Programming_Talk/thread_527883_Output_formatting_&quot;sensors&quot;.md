---
title: "Output formatting: &quot;sensors&quot;"
date: 2007-08-17
forum: Programming Talk
---

### Post by ShareBuntu on 2007-08-17
Hi there,

I'm trying to format the output of sensors for conky. Unfortunately, neither acpi nor i2c works. Here's my current output:

```
k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:
             +20°C
Core1 Temp:
             +28°C
```

I'm still somewhat of a Linux newbie but I've managed to cut it down to the following using sensors | grep ° | cut -c15-16 :

```
22
29

```

I've now got two lines of temperatures. Is there a way to merge those two lines into one? Say, 22 29, and perhaps add a string to the output? E.g. "22 °C and 29 °C".

Any help would be greatly appreciated. Thanks.

---

### Post by ShareBuntu on 2007-08-17
Well, got it working using: sensors | grep ° | cut -c15-16 | sed -n '1,1p' for core 1 and sensors | grep ° | cut -c15-16 | sed -n '2,2p' for core 2. There's probably a better way of doing it but it works. I'm still open to suggestions though. :)

---

