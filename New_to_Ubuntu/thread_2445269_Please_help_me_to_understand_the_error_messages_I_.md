---
title: "Please help me to understand the error messages I get at boot &amp; correct the failiures"
date: 2020-06-11
forum: New to Ubuntu
---

### Post by peb-cak on 2020-06-11
Hi, 

I am getting the following errors at boot. Please help me to understand what they are about and point me to how I could correct these failiures:

```
$ journalctl -b -p 3
-- Logs begin at Thu 2020-06-11 14:26:31 CEST, end at Thu 2020-06-11 14:29:13 CEST. --
Jun 11 14:26:32 ubuntu kernel: Initramfs unpacking failed: Decoding failed
Jun 11 14:26:32 ubuntu kernel: psmouse serio1: synaptics: Unable to query device: -5
Jun 11 14:26:48 ubuntu gdm-password][3198]: gkr-pam: unable to locate daemon control file

```

---

### Post by dino99 on 2020-06-11
If you glance at your above comments logged, you find:
- a race comment, which is solved later into the journal (initramfs)
- a long standing error (gkr)
- and something unknown (kernel's hardware id)

... nothing fatal by the way. :p

---

### Post by peb-cak on 2020-06-12
> **dino99 said:**
> 
- a race comment, which is solved later into the journal (initramfs)


Thanks for the reply dino99!
I am afraid I don'y quite get what this means. Does it mean that the issue will be resolved later on? Would you mind elaborating a bit?

> ... nothing fatal by the way. :p

So there is nothing to worry about then?

---

### Post by ActionParsnip on 2020-06-12
Does the system have a make and model?

---

### Post by peb-cak on 2020-06-12
> **ActionParsnip said:**
> Does the system have a make and model?

Here it is:


```
System:    Kernel: 5.4.0-37-generic x86_64 bits: 64 compiler: gcc v: 9.3.0 
           parameters: BOOT_IMAGE=/boot/vmlinuz-5.4.0-37-generic root=UUID=e72211ed-9efb-440a-a643-266a3da1245c ro 
           Desktop: Gnome 3.36.2 info: plank wm: gnome-shell dm: GDM3 3.34.1 Distro: Ubuntu 20.04 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Dell product: XPS 13 9380 v: N/A serial: <filter> Chassis: type: 10 serial: <filter> 
           Mobo: Dell model: 0KTDY6 v: A00 serial: <filter> UEFI: Dell v: 1.10.0 date: 02/04/2020 
CPU:       Topology: Quad Core model: Intel Core i7-8565U bits: 64 type: MT MCP arch: Kaby Lake family: 6 model-id: 8E (142) 
           stepping: B (11) microcode: CA L2 cache: 8192 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 31999 
           Speed: 800 MHz min/max: 400/4600 MHz Core speeds (MHz): 1: 800 2: 800 3: 800 4: 795 5: 800 6: 800 7: 800 8: 800 
Info:      Processes: 282 Uptime: 55m Memory: 7.43 GiB used: 2.12 GiB (28.5%) Init: systemd v: 245 runlevel: 5 Compilers: 
           gcc: 9.3.0 alt: 9 Shell: bash v: 5.0.16 running in: gnome-terminal inxi: 3.0.38 

```

---

