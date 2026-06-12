---
title: "nVidia Setting and input signal out of range problem"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by Unewbeginner on 2008-05-13
hello, I installed Ubuntu 7.04 (8.04 has some problem with my 3d software) and the new driver from nVidia. But now I have a problem with resolution.

I use the application (NVidia Settings) to setting the resolution I want (1440*900) and tried to save it to XConfiguration File. But the system seems not allowing me to do this. The message is: Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.

I also tried to configure it in terminal with ```
sudo dpkg-reconfigure xserver-xorg
```

But I didn't get the resolution parameter updated after I rebooted.

This means I have to set up the resolution everytime I login. Could anyone let me know how to fix it?

Thanks

---

### Post by BDNiner on 2008-05-13
What kind of hardware are you using? does your monitor support (1440*900)? what about setting the resolution from the System>Preferences>Screen Resolution?

---

### Post by alienexplorers on 2008-05-13
When using nvidia-setting you must start it with gksudo:
> gksudo nvidia-settings
It will now be able to store the config to xorg.conf.....

---

### Post by Unewbeginner on 2008-05-13
> **BDNiner said:**
> What kind of hardware are you using? does your monitor support (1440*900)? what about setting the resolution from the System>Preferences>Screen Resolution?

thanks. I fixed it with your solution

---

