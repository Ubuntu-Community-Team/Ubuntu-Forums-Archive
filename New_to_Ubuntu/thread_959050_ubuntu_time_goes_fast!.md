---
title: "ubuntu time goes fast!"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by sonof on 2008-10-26
Hi, I'm a new user of Ubuntu 8.04 (Hardy Heron) and I have a problem. My time goes very fast. In a second the time of Ubuntu goes like 5 seconds. 
How can I solve this problem? Thanks.

---

### Post by eternalnewbee on 2008-10-26
Remove it from the panel ( with your mouse right-click on it and remove ), Right-click on the panel and click add to panel, and scroll down to clock and add it again and see if the problem is solved.
Good luck.

---

### Post by sonof on 2008-10-26
Hi, I followed the instructions, but it didn't solve the problem. Time is still going faster.

---

### Post by eternalnewbee on 2008-10-26
Then try to reboot the system, and see if the problem still persists.

---

### Post by Kevbert on 2008-10-26
If you can go into bios it might be worth checking what's happening there as it could be a hardware problem with the timer chip or battery.

---

### Post by sonof on 2008-10-26
I checked the bios setup. there the time runs normally. and if the problem was sth about the bios, then shouldn't the windows time run faster, too?
Because the windows time runs normally. 
I think my problem is the same which was mentioned at [http://ubuntuforums.org/archive/index.php/t-77021.html](http://ubuntuforums.org/archive/index.php/t-77021.html) .
because  I have a motherboard ABIT NF-M2S and a cpu AMD ATHLON 64X2.
and also my key repitition runs too fast. 
But I didn't understand quite the suggestion at the end of the page.

---

### Post by Kevbert on 2008-10-26
If you're refering to notsc, I think you net to add this to the end of the line that you boot with e.g.
```
kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=ac4f091c-d379-475c-8f76-b6e9ca0b5865 ro quiet splash [COLOR="Red"]notsc[/COLOR]
```

---

### Post by sonof on 2008-10-26
I've installed Ubuntu 8.10 for AMD 64 and I don't have this problem anymore.
Thanks again for replies!

---

### Post by sonof on 2008-10-27
After a day I installed Ubuntu 8.10, I've the same problems now again. The clock runs fast, the key repitition runs fast. 
I have an ABIT NF-M2S MotherBoard (NVIDIA GeForce 6100+405 Chipset)  When I googled "NF-M2S" i found out other people have the same problem. They have nf-m2s, Ubuntu and the same problem.  Should I send my problem to the Ubuntu developer team, since it may be a bug?

---

### Post by dracayr on 2008-10-27
in a terminal, type:```
sudo gedit /boot/grub/menu.lst
``` Then search for the 1. line that begins with 

kernel		/boot/vmlinuz

and append "notsc" to it. save and reboot.

dracayr

---

### Post by reg4c on 2008-10-27
OOoooooooorrr maybe Ubuntu is so awesome that you think time is going so fast but its actually running normally? 

:D

Stupid post I know

---

### Post by sonof on 2008-10-27
hi dracayr, I followed the instructions , but it didn't work.

---

### Post by Keen101 on 2008-10-27
> After a day I installed Ubuntu 8.10, I've the same problems now again. The clock runs fast, the key repitition runs fast.
I have an ABIT NF-M2S MotherBoard (NVIDIA GeForce 6100+405 Chipset) When I googled "NF-M2S" i found out other people have the same problem. They have nf-m2s, Ubuntu and the same problem. Should I send my problem to the Ubuntu developer team, since it may be a bug?

Yeah first help report the bug on launchpad. [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Next try doing updates... maybe it has already been fixed in an update.

```
sudo apt-get update
```

---

### Post by dracayr on 2008-10-28
Just to make sure... you added the "notsc" (without quotes) to the first line that began with kernel... (note: there should NOT be a '#' in front of the line).

Try to use the option "clock=pit" (without the quotes) instead of "notsc". Also, there is a patch that seems to work sometimes (but not always): [http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view](http://bugzilla.kernel.org/attachment.cgi?id=5993&action=view)

But If you are unexperienced in linux, I wouldn't recommend to try to patch your kernel...

dracayr

---

### Post by sonof on 2008-10-28
Hi, i disabled the cool n quiet in the bios setup. So the problem's solved. I think when it's able (auto), the cpu runs in a uncontrolled way with Ubuntu. 
But I'm not sure whether disabling it is harmful to my hardware or not. Has anybody an idea?

---

### Post by dracayr on 2008-10-28
[http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_9485_9487%5E10272,00.html](http://www.amd.com/us-en/Processors/ProductInformation/0,,30_118_9485_9487%5E10272,00.html)

dracayr

---

