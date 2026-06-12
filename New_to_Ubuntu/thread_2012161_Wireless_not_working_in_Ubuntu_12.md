---
title: "Wireless not working in Ubuntu 12"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by kumars on 2012-06-28
Hi,

I am very new to ubuntu. I have installed ubuntu on my Sony Vaio CR 363.

when i try to connect through Wireless network it says Connected, but internet is not working. I tried to find documents. I reached here: 

ping 4.2.2.2 -c 4 says Destination Net Unreachable..

Any help would be highly appreciated..

thanks in advance

---

### Post by josephmills on 2012-06-28
can you please open your terminal (ctrl+alt+t)
then enter in
```
lspci -nn
```
```
lsmod
```
```
rfkill list all
```


And paste those things here please and thanks.

---

