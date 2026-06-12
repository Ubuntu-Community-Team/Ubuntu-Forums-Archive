---
title: "unable to boot ubuntu on new XMG NEO 17 laptop"
date: 2021-08-17
forum: New to Ubuntu
---

### Post by exolve on 2021-08-17
I just bought a new laptop with the name mentioned in the title. 
CPU = intel core i7-11800H
Graphics card = NVIDIA RTX 3070

I recently decided to switch from windows to linux and decided to use Ubuntu as my operating system for this laptop and booted it via the USB but everytime I try the booting process stops midway and the only way out is force quitting via the power button.
[ 0.573521] pci 0000:00:07.0: DPC: RP PIO log size 0 is invalid
[ 0.996644] r8169 0000:2e:00.0: unknown chip XID 641
[ 1.024474] genirq: Setting trigger mode 8 for irq 163 failed (intel_gpio_irq_type+0x0/0x130 [pinctrl_intel])
[ 1.026442] gpiochip0: (INT34C6:00): gpiochip_lock_as_irq: cannot get GPIO direction
[ 1.026507] gpiochip0: (INT34C6:00): unable to loct HW IRQ 44 for IRQ
[ 1.026563] genirq: Failed to request resources for UNIW0001:00 (irq 163) on irqchip INT34C6:00
[ 2.729109] usbhid 3-11:1.0: couldn’t find an input interrupt endpoint

I am not sure what to do next. Could someone advise me on what the problem here is and if there is a way to fix it?

---

### Post by tea for one on 2021-08-17
Which version of Ubuntu did you try?

How did you create your USB?

---

### Post by ActionParsnip on 2021-08-17
If you are using a USB 3 port, use USB 2

---

### Post by exolve on 2021-08-17
i am using 20.4.2.0 LTS and created bootable flash drive (USB) via rufus.

---

### Post by tea for one on 2021-08-17
New hardware generally requires a later kernel.

It looks like you have 11th Generation Intel processor launched April - June 2021

I would try Ubuntu 21.04, failing that possibly the version in development [http://cdimage.ubuntu.com/daily-live/current/HEADER.html](http://cdimage.ubuntu.com/daily-live/current/HEADER.html)

---

### Post by exolve on 2021-08-17
I see, thank you very much for the information.

---

