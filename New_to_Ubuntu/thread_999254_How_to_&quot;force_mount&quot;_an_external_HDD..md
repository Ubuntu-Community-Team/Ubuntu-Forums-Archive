---
title: "How to &quot;force mount&quot; an external HDD."
date: 2008-12-01
forum: New to Ubuntu
---

### Post by random turnip on 2008-12-01
My freind told me that to get my external HDD to work I should "force mount" it, but he didn't have time to tell me how to do it.

Can someone explain please?

---

### Post by lettermachine on 2008-12-01
[http://www.linuxquestions.org/questions/mandriva-30/mount-an-external-ntfs-usb-hard-disk-201441/](http://www.linuxquestions.org/questions/mandriva-30/mount-an-external-ntfs-usb-hard-disk-201441/)

Should also work on Ubuntu.

---

### Post by bodhi.zazen on 2008-12-01
> **random turnip said:**
> My freind told me that to get my external HDD to work I should "force mount" it, but he didn't have time to tell me how to do it.

Can someone explain please?

use the -o force flag

sudo mount /dev/sdxy /mount/point -o force

Take care, although rare, forcing a mount can cause data loss.

Better mount the drive win Widows and remove it properly.

---

### Post by xjcannonx on 2008-12-01
Also, just a quick point, if the HDD was ever connected to windows you need to be sure that the last time it was removed from the windows machine it was done properly by "Safely removing it"

---

