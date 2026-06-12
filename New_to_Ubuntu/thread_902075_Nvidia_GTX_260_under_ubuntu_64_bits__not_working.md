---
title: "Nvidia GTX 260 under ubuntu 64 bits : not working ?"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by graben3 on 2008-08-27
Hello,

I just got a new computer with a nvidia gtx 260. Im planning to install only ubuntu on it and run XP only in VM...but I have a problem...

Usually nvidia cards works well under ubuntu.. I use EnvyNG and everything works nice in a couple of minutes.

But this card is not detected by ubuntu or by envy

What can I do to make this card work in more than 800x600 ?

I really do not want to go back to XP just because of that...

Any help would be appreciated

---

### Post by IanW on 2008-08-27
Your video card is too new for EnvyNG to find a driver for it, as EnvyNG will not use "Beta" drivers.

You need driver 177.68, and will have to manually compile & install it (EnvyNG is basically a script which does this for you).
Get it [here](ftp://download.nvidia.com/XFree86/Linux-x86_64/177.68/NVIDIA-Linux-x86_64-177.68-pkg2.run).

Installation instructions may be found [here](http://ubuntuforums.org/showpost.php?p=5086971&postcount=).

---

### Post by graben3 on 2008-08-27
Wow !

Thank you very much IanW ! that did work flawlessly !

---

### Post by aman.agx on 2008-08-27
Hi!!! Do tell if it still works after the reboot!! 

Thanks!
Aman

---

### Post by graben3 on 2008-09-09
Ya... it works flawlessly ! event after 5 reboots ! :)

---

