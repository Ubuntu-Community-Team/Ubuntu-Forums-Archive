---
title: "No logon page after update from 10,10 to 11.04. Locked up."
date: 2011-10-03
forum: New to Ubuntu
---

### Post by Noble Bell on 2011-10-03
I done an update from 10.10 to 11.04. After the update ran and the computer rebooted it never came up to a log on screen. It locked up somewhere along the boot up sequence. It is a Toshiba laptop with an ATI video card, I have it set to dual boot windows and linux. I have not had time to play with it today and was wandering if anyone might have any thoughts or suggestions for me to try when I get a chance later?

Thanks in advance.

---

### Post by wildmanne39 on 2011-10-03
Hi, I suspect you are going to need a parameter like nomodeset to load ubuntu so you can install your video card driver.

Is your system booting past the grub menu?
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by alphacrucis2 on 2011-10-03
> **Noble Bell said:**
> I done an update from 10.10 to 11.04. After the update ran and the computer rebooted it never came up to a log on screen. It locked up somewhere along the boot up sequence. It is a Toshiba laptop with an ATI video card, I have it set to dual boot windows and linux. I have not had time to play with it today and was wandering if anyone might have any thoughts or suggestions for me to try when I get a chance later?

Thanks in advance.

Can you boot in recovery mode? If you were using the proprietary ati (fglrx) driver under 10.10 that could be causing the  problem. If you can get into a recovery shell then:

```
sudo apt-get --purge remove fglrx*
```

Then reboot via:

```
sudo shutdown -r now
```


If that lets you log in normally you should be able to manually reinstall fglrx via the hardware drivers function.

---

### Post by Noble Bell on 2011-10-04
Thank you folks for your responses. It was indeed the video card driver for the ATI card. alphacrucis2, I followed your steps and they worked great.

---

