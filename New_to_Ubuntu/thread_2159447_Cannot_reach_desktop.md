---
title: "Cannot reach desktop"
date: 2013-07-03
forum: New to Ubuntu
---

### Post by lemonwire on 2013-07-03
Hello, I am completely new to linux and have succesfully (I think) installed Ubuntu 13.04 on a seperate partition on my laptop (I usually run windows 8). When I boot I am asked to choose my OS, and when I choose Ubuntu I am brought to
 grub>
I've tried all sorts of commands (boot, startx) but nothing seems to get me to the desktop. Please help :)
*I should mention that when I try "boot" an error tells me that I need to start a "kernel" first

---

### Post by TheFu on 2013-07-03
grub gets loaded before Linux, so you aren't into Linux at this point. It is a boot loader. Something about your install got screwed up.
There are Win8 dual-boot instructions here somewhere. If you have UEFI, I think there are extra steps necessary.
Google:
* ubuntu uefi
* ubuntu boot repair
for more help. The links that point back to the Ubuntu.com or some other ubuntu* domain are what you want.

While others will probably disagree, I think new-to-linux users should stay with LTS releases. That would be 12.04 in your case. Non-LTS releases are simply not as polished and do not have enough support time (in years). E.i. patches end in about 1 yr, while the LTS releases get patched for 5 years. Big difference.

---

### Post by sandyd on 2013-07-03
Hi, are you currently running with UEFI enabled or disabled?

try running [Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair") on a livecd, and see if it allows you to boot.

---

