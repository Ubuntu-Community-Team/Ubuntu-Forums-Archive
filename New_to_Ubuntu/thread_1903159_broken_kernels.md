---
title: "broken kernels"
date: 2012-01-01
forum: New to Ubuntu
---

### Post by degarb on 2012-01-01
I made the mistake of upgrading the ubuntu,  my browser froze up and locked up the system.  I had to hit the power button.  Now none of the kernels will boot except the oldest and 4 kernels back.   I am getting kernel panick on most of these.

How do you repair the kernel.

I think I scheduled a scan on next boot, but cannot tell or recall, because the code was so cryptic.

---

### Post by degarb on 2012-01-01
I googled removing kernels, removed all but the oldest, only working kernel.  on deleting the latest kernel, it auto installed the latest kernel (newer than the kernel after the upgrade. )  Each kernel was taking up about 90 megs.  So I ended up gaining about 200 megs of space.   The one it chose boots, leaving me two working kernels. 

I really don't think the chkdsk worked.  But Then i don't think it has any screen.   

I am fairly certain my browser installation got damaged, had to reinstall it.

---

### Post by lolpenguin on 2012-01-01
Boot into a working kernel, then reinstall the broken kernels:```
sudo apt-get install --reinstall linux-headers-x.x.x-x linux-headers-x.x.x-x-generic linux-image-x.x.x-x-generic
```
I got ninja'ed!^^^

---

### Post by LinuxCharms on 2012-01-01
Unless someone else has a better idea, I'd back up any files you want to keep (if you can get into a terminal manually) and grab a new Ubuntu CD to boot up from.

---

### Post by bodhi.zazen on 2012-01-01
Upgrades can always go bad. I can not tell what the problem is from your post, but I would back up your data and do a fresh install.

---

