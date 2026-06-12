---
title: "Grub Problem"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by Akacheebe on 2013-01-14
I have a Dell 8400 computer with dual hard drives.  One drive has Windows XP and the other is Ubuntu 12.04.  

I recently had to reload the Windows XP drive and once I had finished, now I have some problems with Grub when I select that Windows drive to boot too?  

Error: no such device XXXXXXXXXXXXXXXX
 press enter to continue

So how do I get Grub to recognize that new Windows load?

Thanks,

---

### Post by adityamagadi on 2013-01-14
post the output of os-prober and try sudo update-grub..

---

### Post by NikTh on 2013-01-14
The grub's doctor called [boot repair](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu). 

Boot from a Live media of Ubuntu (CD/DVD/USB) and follow the instructions on link. 

Thanks

---

### Post by Akacheebe on 2013-01-14
I guess I should have been a little more specific.  I can boot to either Windows or Ubuntu now as the Grub menu does come up so do I really need to use the live CD to repair Grub?  Can't that be done while I'm booted in Ubuntu?

Thanks

I went ahead and fixed it without booting from the live CD and it worked. 

Thanks

---

