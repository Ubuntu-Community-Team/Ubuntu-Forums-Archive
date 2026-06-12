---
title: "udevadm info attributes"
date: 2020-09-29
forum: New to Ubuntu
---

### Post by jcdenton1995 on 2020-09-29
Hi all!

I've been looking to make a udev rule that will allow me to just plug in my usb memory stick and have the system take a snapshot for me, but I'm not sure which of the device attributes to use as the match keys as there aren't many and I'm not sure weather the ones that are there are likely to be truly unique?```
KERNEL=="sda1"
    SUBSYSTEM=="block"
    DRIVER==""
    ATTR{start}=="2048"
    ATTR{stat}=="   35879    22656   487586    32029     1717   105456  1213168   121414        0    36388   126056        0        0        0        0"
    ATTR{inflight}=="       0        0"
    ATTR{discard_alignment}=="0"
    ATTR{ro}=="0"
    ATTR{alignment_offset}=="0"
    ATTR{size}=="120174592"
    ATTR{partition}=="1"

```

Can anyone more informed advise?

Thanks!

---

