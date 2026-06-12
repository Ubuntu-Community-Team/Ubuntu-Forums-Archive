---
title: "backdoor into read/write without networking?"
date: 2017-12-17
forum: New to Ubuntu
---

### Post by iamviking214 on 2017-12-17
ok, im having an issue with a ubuntu server ive set up. Its installed on an older poweredge 1950. Its mostly just for labbing/education. I usually access it through rdp. As of right now however it does not boot. either hanging on black, or purple splash screen. if I boot to USB recovery i can get into recovery mode, and fsck, repair boot, dpkg, and drop shell. what i cannot do is enable networking, likely because of a configuration error i made while trying to set up nic teaming. i got the error failed to start raise networking, and networking was inactive, and unable to be reset. since this is the case, and enabling networking is what enables anything to be written to filesystem, i am unable to write, therefore unable to make changes. so question is how do i fix that error, or the other error i have noticed, "failed to start kernel module"? any help is appreciated. thanks.

---

### Post by iamviking214 on 2017-12-18
ok, so if anyone sees this thread and has the same issue i think i have it kinda figured out. 
first thing was dropping root shell. 
apply command ~# [I]mount -o rw,remount /
[/I]This remounts into read/write. This didn't work the first time i tried.
_force interface up:_ [I]~# sudo ifconfig eno1 <ip address> netmask <netmask> up
[/I]_append:_[I]~# sudo echo "nameserver 8.8.8.8" > /etc/resolv.conf

[/I]This adds a working nameserver to **/etc/resolv.conf **and fixed my internet connectivity for one of my ethernet adapters enabling me to have network access.

next up i applied the following commands to fix the kernel module problem:
[I]
~# sudo apt-get update
~# sudo dpkg --configure -a
~# sudo apt-get dist-upgrade
[/I]

i can now boot, but still network is not available unless i manually assign ip address and up interface after booting. resolv.conf is empty, and nothing sticks in /etc/network/interfaces. i cant ping domain or ip including just within lan but can update. upon boot ifconfig only shows loopback address. will update later when i get home from work.

---

