---
title: "Built-in bluetooth not working"
date: 2016-03-29
forum: New to Ubuntu
---

### Post by gari2 on 2016-03-29
Hi,

I've got an ASUS F552L with Ubuntu 14.04 LTS installed and bluetooth icon does not appear in the top bar. When trying to switch it on, it stays like this:
[ATTACH=CONFIG]268054[/ATTACH]

I've installed all the packages I've seen in other threads but I can't make it work.

Thank you

---

### Post by jeremy31 on 2016-03-30
Post results from terminal for ```
uname -a; rfkill list all; lspci -nnk | grep -iA2 net; lsusb; dmesg | egrep -i 'blue|firm'
```

---

