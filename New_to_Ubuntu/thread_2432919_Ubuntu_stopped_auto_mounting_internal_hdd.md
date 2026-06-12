---
title: "Ubuntu stopped auto mounting internal hdd"
date: 2019-12-11
forum: New to Ubuntu
---

### Post by ejr32123 on 2019-12-11
Hello!

I just got ubuntu. Randomly, my second HDD stopped mounting. If I go to other locations, it shows as local disk, /dev/sdc2. If I try to click it it says "unable to access this location. Not authorized to perform operation. It started doing this after I updated windows. I noticed that the windows update turn fast boot on again. So I turned it off but I am still having the problem. After searching the forums, if I run this ```
udisksctl mount -b /dev/sdc2
``` I can mount the hard drive and use it normally. I have to do this every time now. How can I get it to automount and what could have caused it to change?

Thanks

---

### Post by ejr32123 on 2019-12-11
well, I just rebooted and it auto mounted as normal. Some how after hours and hours then a writing a forum post it magically worked. Thanks : )

---

### Post by oldrocker99 on 2019-12-11
Sometimes the magic works:p, and sometimes the magic doesn't work](*,).

---

