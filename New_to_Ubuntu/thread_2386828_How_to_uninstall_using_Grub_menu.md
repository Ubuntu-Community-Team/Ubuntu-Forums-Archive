---
title: "How to uninstall using Grub menu"
date: 2018-03-10
forum: New to Ubuntu
---

### Post by wrongusername2 on 2018-03-10
After I ran the following command, my Ubuntu 16.04 is not showing Log-in screen, just stays for ever in red-screen. 
But I can go to Grub menu. Is there a way I can uninstall this using Grub menu?

```
sudo apt-get install exfat-fuse exfat-utils  
```

TIA

---

### Post by yancek on 2018-03-11
> Is there a way I can uninstall this using Grub menu?

No.  Grub is just a bootloader.  There is no reason installing or trying to install the utilities you refer to would cause an inability to login.  What else happened?  Is this new hardware?  Can you boot a Live CD/usb?

---

### Post by wrongusername2 on 2018-03-11
> **yancek said:**
> What else happened?  Is this new hardware?  Can you boot a Live CD/usb?
Thanks for responding

This is a laptop, I did not modify any hardware. I just installed EXFAT s/w package. Live CD works, and I checked *etc\fstab,* and it looks good  I **resolved the issue** by re-imaging the OS using **CloneZilla**

This is the 3rd time that an installation broke the log-in. On every previous instance I resolved it using **CloneZilla**. After the 2nd failure, made a rule for myself 
-Turn off all *auto-update* for both OS and Apps.
-Do not install any *new* software, instead add them to a *future list*. 
-Once a month update and also install *new* s/w. Before installing take a clone using CloneZilla, and if update breaks the OS simply restore the old image.

I followed the above rules for over a month, and had no issue. But yesterday *instant gratification* rushed me in to installing EXFAT. I should stick to rules that i set up. I have job interviews going on so want to avoid such issues.

---

### Post by coffeecat on 2018-03-11
> **wrongusername2 said:**
> 
This is the 3rd time that an installation broke the log-in. On every previous instance I resolved it using **CloneZilla**. After the 2nd failure, made a rule for myself 
-Turn off all *auto-update* for both OS and Apps.
-Do not install any *new* software, instead add them to a *future list*. 
-Once a month update and also install *new* s/w. Before installing take a clone using CloneZilla, and if update breaks the OS simply restore the old image.

I followed the above rules for over a month, and had no issue. But yesterday *instant gratification* rushed me in to installing EXFAT. I should stick to rules that i set up. I have job interviews going on so want to avoid such issues.

I suggest you have a careful think about what else might be causing your system to break so regularly. With one well-documented exception in 2006, I have not had either an update or an installation of a new software break my system in over 12 years of using Ubuntu on multiple machines. Perhaps you have a rogue ppa that is causing problems. Perhaps something else. If you can identify any other factors, I'm sure the members of this forum will be more than happy to help you prevent this happening in the future.

---

