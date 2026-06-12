---
title: "CrossOver Quickbooks Hardy"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by cwmoser on 2008-06-01
FYI, if you run CrossOver (variant of wine) and Quickbooks, you might find that your Quickbooks that ran properly in Gutsy will not run in Hardy.

The solution, via CrossOver's forum, is:

vi /etc/sysctl.conf
change:
# vm.mmap_min_addr = 65536
vm.mmap_min_addr = 0

then reboot.

Carl

---

### Post by wgbuntu on 2008-08-27
This fixed my problem after upgrading Gutsy to Heron.  Thanks

---

