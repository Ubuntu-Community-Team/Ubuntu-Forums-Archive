---
title: "[SOLVED] Can't Connect to My Internet Router"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by RedStarYellowSun on 2008-09-01
I am new to Ubuntu, but I like it. My only problem so far is that I cannot connect to my wireless Internet router. How do I do this?

Thanks for your time.

Sincerely,
RedStarYellowSun

---

### Post by halitech on 2008-09-01
we need a little more detail. Do you have a laptop or a desktop? built in card or usb device? Did it work in windows? Do you have any security on the router?

---

### Post by prshah on 2008-09-01
> **RedStarYellowSun said:**
>  I cannot connect to my wireless Internet router. 

Step 1: what is your wireless device? Open a terminal (Applications-Accessories-Terminal), Then give the command as below and post output back here. ```
lspci | grep -i wireless
```

Step 2: Is the wireless device recognized? Post the output of ```
iwconfig
```

Other steps can be advised after the above information is posted; what steps follow next depend on the output of the above.

---

### Post by RedStarYellowSun on 2008-09-02
Thanks for responding, but the problem was fixed. Apparently, all I had to do was click on the icon beside the clock, choose the router, and it will connect immediately.

Thanks for your time though.

Sincerely,
RedStarYellowSun

---

