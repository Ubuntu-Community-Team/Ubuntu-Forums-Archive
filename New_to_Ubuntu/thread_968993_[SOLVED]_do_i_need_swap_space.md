---
title: "[SOLVED] do i need swap space?"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by GumpTron on 2008-11-03
hello,

i have two partitions on my HD. one partitio is 190GIGs (this is used by Vista) and the other partition is 16GIGs for Ubuntu.

when i manually partitioned i did not enable swap space. there wasn't any other place to put it i think. is this bad? did i make a big mistake?

---

### Post by TenPlus1 on 2008-11-03
Not really, so long as you have adequate memory (1gb or more) then Ubuntu will run fine without a swap partition...  If you experience any problems then you could always add a swap file like windows, just go here for info:  [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by TenPlus1 on 2008-11-03
also, pop into terminal and type:

sudo gedit /etc/sysctl.conf

and add this line to the very bottom:

vm.swappiness=0

and save, as this stops Ubuntu trying to access virtual memory and uses the physical instead.

---

