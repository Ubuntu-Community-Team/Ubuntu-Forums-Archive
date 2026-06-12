---
title: "Problems With Reboot After Kernel Upgrade"
date: 2013-04-19
forum: New to Ubuntu
---

### Post by wydchr on 2013-04-19
Hi, I just upgraded my kernel on Ubuntu 12.04.02 from linux-image-3.2.0-29-generic-pae to linux-image-3.2.0-40-generic-pae and now when rebooting my machine hangs half way through. I had to hold down the power button for several seconds to switch off the machine but when I did that and rebooted I got the Grub menu and picked a normal boot from linux-image-3.2.0-40-generic-pae and this booted up OK. However each time I do subsequent reboot I have the same rigmarole of my machine hanging and then doing a hard reset. Any advice would be appreciated.

David.

---

### Post by ibjsb4 on 2013-04-19
Thats a weird one.  Try

```
sudo update-grub
```

See if that does any good.

---

### Post by wydchr on 2013-04-19
OK thanks for your help... tried update-grub and it returned this error : not foundrub-mkconfig: 5: /etc/default/grub:

---

### Post by ibjsb4 on 2013-04-19
I have no experience with this problem, but I did get several hits here.  Hope you can sort this out.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=error+%3A+not+found+grub-mkconfig%3A+5%3A+%2Fetc%2Fdefault%2Fgrub%3A+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=error+%3A+not+found+grub-mkconfig%3A+5%3A+%2Fetc%2Fdefault%2Fgrub%3A+&sa=Search&cof=FORID:9)

---

### Post by wydchr on 2013-04-19
OK thanks anyway, I'll wait to see if anyone else has any suggestions before delving into old messages as Ubuntu 12.04.02 uses Grub 2 now I think.

---

### Post by wydchr on 2013-04-20
Can anyone please explain to me how to remove/re-install Grub2... this might help to solve my problem I hope.

Cheers, David.

---

### Post by wydchr on 2013-04-20
All has now changed and machine will not boot at all, screen just shows this...  **grub>**

Any help would be appreciated...

---

### Post by mörgæs on 2013-04-20
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wydchr on 2013-04-21
I stuck to the first one I tried, does that have some relevance or are you just curious??

---

### Post by mörgæs on 2013-04-21
The text at the bottom below the line is called a signature, and it's part of all posts (like this one). General advice.

I'm encouraging people to make an informed decision. Many posters here do not have the hardware for running Ubuntu, but they have not heard of anything else.

---

### Post by wydchr on 2013-04-21
Ah OK, I'll have a read through your **'I upgraded, and now I have this error...'** thread and see if it will help me and if not then maybe it will help me make a better choice of 'buntu'. I have resigned myself to re-installing buntu and starting a-fresh. I have it installed on a DOM so it will (should) not affect my raid 5 disks.

Cheers, David.

---

