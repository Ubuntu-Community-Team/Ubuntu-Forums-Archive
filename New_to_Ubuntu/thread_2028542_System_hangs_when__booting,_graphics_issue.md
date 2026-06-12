---
title: "System hangs when  booting, graphics issue?"
date: 2012-07-18
forum: New to Ubuntu
---

### Post by atarisal on 2012-07-18
Hi everybody,

It often happens to me that when the computer starts, it hangs during the loading  of the OS. After that, the only option is to reboot and try again. Other times, the system hangs after showing the desktop image. It seem to be a problem of the graphical system (Bumblebee, unity 3D) because when starting in safe mode, the problem does  not happen. 

I am working with a dell 14z on ubuntu 12.04.

Any ideas?

Best wishes 
atarisal

---

### Post by oldos2er on 2012-07-18
Post moved to its own thread.

---

### Post by NikTh on 2012-07-18
Hi , 
can you provide more info ? 
Open a terminal (ctrl+alt+t) , copy-paste these commands from here to your terminal and post back the results.
```
uname -r 
lspci -nnk | grep -iA2 vga
```**Put the results inside [CODE] tags , by highlighting the text and click at # symbol on top of message pane. **
Thanks

---

### Post by atarisal on 2012-07-19
Hi NikTh,

Here are the results:

titin$ uname -r 
3.2.0-26-generic

titin$ lspci -nnk | grep -iA2 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0126] (rev 09)
    Subsystem: Dell Device [1028:0522]
    Kernel modules: i915
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF119 [GeForce GT 520M] [10de:1050] (rev ff)
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
    Subsystem: Dell Device [1028:0522]

Any idea?

---

