---
title: "Can RPi5 Ubuntu desktop 24.4 LTS run PCIe 3 for NVMe?"
date: 2024-11-18
forum: New to Ubuntu
---

### Post by ken-91283 on 2024-11-18
At default, **PCIe version 2** for NVMe, our newly brought Raspberry Pi 5 is running **Ubuntu desktop 24.4 LTS**?

Tried but **failed to switch to PCIe version 3**.

Many thanks

---

### Post by grahammechanical on 2024-11-18
What makes you think that it is the operating system that is blocking PCIe version 3.

The official Raspberry Pi 5 data sheet does not claim that the Pi 5 is PCIe 3 capable.

> for the first time the platform exposes a single-lane PCI Express 2.0 interface, providing support for high-bandwidth peripherals.

> PCIe 2.0 x1 interface for fast peripherals (requires separate M.2 HAT or other adapter)

[https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf](https://datasheets.raspberrypi.com/rpi5/raspberry-pi-5-product-brief.pdf)

And then there is this:

> The connection is certified for Gen 2.0 speeds (5 GT/sec), but you can  force it to Gen 3.0 (10 GT/sec) if you add the following lines to your ... 

and this

> Warning The Raspberry Pi 5 is not certified for Gen 3.0 speeds, and connections to PCIe devices at these speeds may be unstable.

[https://docs.sunfounder.com/projects/pironman-u1/en/latest/hardware/nvme_pip.html](https://docs.sunfounder.com/projects/pironman-u1/en/latest/hardware/nvme_pip.html)

Surely, the block is in the hardware and not the operating system.

Regards

---

