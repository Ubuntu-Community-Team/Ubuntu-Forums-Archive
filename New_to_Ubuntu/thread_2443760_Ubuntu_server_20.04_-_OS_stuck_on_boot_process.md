---
title: "Ubuntu server 20.04 - OS stuck on boot process"
date: 2020-05-19
forum: New to Ubuntu
---

### Post by bitexplorer on 2020-05-19
I have installed a fresh install of ubuntu server 20.04. When I boot the server. During the boot process the system gets stuck on the following error. Please let me know if you have thoughts on how to address this issue.

"A start job is running for wait for Network to be Configured (1 min / no limit)"

watchdog: BUG: soft lockup - CPU#0 stuck for 22s! [swapper/0:0]

I did try the following, but it didn't help.

sudo systemctl mask systemd-networkd-wait-online

Additional information: 3 total NICs in the PC, 1 onboard and one PCIe dual NIC. This PC is being setup as a router, so iptable rules were applied.

---

