---
title: "Hibernate not Working"
date: 2015-04-25
forum: New to Ubuntu
---

### Post by Murad_Khan on 2015-04-25
I am not sure what it is called exactly when you flip the lid of the laptop down, but the problem occurs when I do that. The laptop will turn off as usual with the lights on my laptop (Lenovo Z50-70) turning off and the screen turning off. When I flip the lid back up to resume using the laptop the lights will turn back on but the screen will not come back on and I cannot use my laptop. I have to hold the power button and turn it back on to use it again. I have a dual booted laptop with Ubuntu 14.04 LTS installed. Help please

---

### Post by sandyd on 2015-04-26
When you close the lid, by default, the laptop suspends.

The issue sounds similar to [http://askubuntu.com/questions/586387/laptop-doesnt-wake-up-after-puting-it-to-suspend-using-ubuntu-14-10](http://askubuntu.com/questions/586387/laptop-doesnt-wake-up-after-puting-it-to-suspend-using-ubuntu-14-10), but with 14.04.

After a suspend (and then reboot), can you post the output of
```

cat /var/log/Xorg.0.log.old
```

Thanks.

Side note: please use code tags to make things easier to read

---

