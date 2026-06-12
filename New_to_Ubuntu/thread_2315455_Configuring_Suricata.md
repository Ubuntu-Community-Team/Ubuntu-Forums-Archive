---
title: "Configuring Suricata"
date: 2016-02-29
forum: New to Ubuntu
---

### Post by marc68 on 2016-02-29
Hello i am in doubt. I am an new user of Lubuntu and see that mine network interface no longer eth0 is named but enp63s0. Must i now replace eth0 with enp63s0 in every configuration. For example suricata expect eth0 as nic interface but mine nic interface is enp63s0 should i use the last.

---

### Post by Bucky Ball on 2016-02-29
Welcome. The change is normal. I don't know why they've done it, but eth0 and wlan0 are now obsure and somewhat, at least to most of us, meaningless alpha/numeric strings.

Change the entry in Suricata to whatever eth0 is now called and see what happens. Should work.

---

### Post by grahammechanical on 2016-02-29
This has come about because Ubuntu is built on Debian and when Debian started using systemd as an init system Ubuntu also did likewise

enp63s0 -- en = _e_ther_n_et. p = pci. bus 63. = something to do with the pci bus. s = slot. 0 = first slot.

> Two character prefixes based on the type of interface:
 *   en -- ethernet
 *   sl -- serial line IP (slip)
 *   wl -- wlan
 *   ww -- wwan

[https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20](https://cgit.freedesktop.org/systemd/systemd/tree/src/udev/udev-builtin-net_id.c#n20)

Regards.

---

