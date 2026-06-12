---
title: "messup grub and mbr(i think on the latter)"
date: 2013-03-19
forum: New to Ubuntu
---

### Post by rburkartjo on 2013-03-19
need some help and i should know better trying to install a program to add the option to boot from a usb messed up grub. on a live cd now. note i had win7 installed on a separate partition and now can only get to boot into win7. checked with live cd and my linux is still there. any ideas of the best way to resolve. have been messing for a few hrs and using boot repair doesnt seem to help. tks

---

### Post by Bashing-om on 2013-03-19
rburkartjo;

Give this one a try:

1. Highlight an old, working kernel from the Grub 2 menu.
2. Press "e" to open the menu entry for editing.
3. Remove the entire "search" line. Use the Up/Dn cursor to place at the start of the line and hold the DEL key.
4. On the "linux" line, change the part "root=UUID=<long number>" to "root=/dev/sdXY" with X being your Ubuntu drive and Y being your Ubuntu partition. Leave the rest of the line as is.
5. CTRL-x to boot.
if works -> 
```
sudo update-grub
```[INDENT=2]
hope it works for you

[/INDENT]

---

### Post by rburkartjo on 2013-03-20
got it solved. problem was i tried to add an option to force my computer to boot from flash drive if inserted. i burned a copy of plop   [http://www.instructables.com/id/Boot-from-usb-on-an-old-pc-without-modding-the-BIO/#step1](http://www.instructables.com/id/Boot-from-usb-on-an-old-pc-without-modding-the-BIO/#step1)        and then installed it. that change my mbr ; however, while the new mbr offered option to boot from cd or flash it only list win7 (which i have on another partition) and not ubuntu.
i had to first use my copy of boot repair and remove grub then i used my live dvd copy of ubuntu 12.04 reinstalled grub and then installed boot-repair when using live cd. fixed the problem by running boot-repair.

---

### Post by Bashing-om on 2013-03-20
rburkartjo; Good .

The more I relate with this operating system the more I am impressed with it.
Good backups and a liveCD, can fix anything that perchances.
[INDENT=2]
keep'n on keep'n on

[/INDENT]

---

