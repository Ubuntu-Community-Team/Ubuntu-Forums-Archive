---
title: "can I install ubuntu first the install xp ?"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by mlotfi on 2008-11-05
Hi,

I just changed my hadr drive , now I have 80 GB, can I install ubuntu first then install xp, I want to divid it :
40 Gb for ubuntu 
40 GB for xp

can you please help me on how to do it.

Thanks, your help is appreciated.

---

### Post by egalvan on 2008-11-05
Yes, you* CAN* install Ubuntu first, then XP,

but it is MUCH easier to install Ubuntu LAST, so that grub can set itself up correctly.

Any SPECIFIC reason(s) you want that particular install order?

---

### Post by jmszr on 2008-11-05
mlotfi,

       +1 for installing XP first, but if you have a reason not to,this may help you:[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

---

### Post by bodhi.zazen on 2008-11-05
You can install in any order you wish. If you install Ubuntu first you will either need to configure the windows boot loader to boot Ubuntu or re-install grub.

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

### Post by raydeen on 2008-11-05
I would do XP first and if you're not totally sure that Ubuntu is going to be a permanent fixture, use the wubi installer. That will install Ubuntu to a hidden file and not mess with your partitions. Only the Windows bootloader will be modified. The only downside to this is that you won't be able to easily share files between Ubuntu and Windows (you'd have to use a flash drive or external/network drive).

---

### Post by mlotfi on 2008-11-06
ok, I just installed windows XP professional in a 40GB partition, I lef the other 40GB unpartionned, now I am installing ubuntu, I am here in Step 4 of 7 in Preparing disk space :

Before:

52% /dev/sda1
47% Free space

How much space should I put for :
Root
Home
Swap

Please help me to install ubuntu in the Free Space.

Thanks

your help is appreciated.

---

### Post by bodhi.zazen on 2008-11-06
The easiest world be :

swap = ram X 2, max 1 Gb, or if you are on a laptop and wish to use sleep / suspend / hibernation Swap = ram.

Put the rest in root ( / ).

If you wish, make / 5-10 Gb and the rest in /home.

---

