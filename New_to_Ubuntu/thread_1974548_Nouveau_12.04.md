---
title: "Nouveau 12.04"
date: 2012-05-06
forum: New to Ubuntu
---

### Post by morkovka078 on 2012-05-06
Hello,

I can t get rid of the nouveau kernel driver in 12.04, any help please ?! 

doing ```
apt-get --purge remove xserver-xorg-video-nouveau
``` didn t do the trick as on Lucid..

thanks for any help, regards

---

### Post by NikTh on 2012-05-06
Hi , 
if you get rid of nouveau driver then who will control your graphics ? 
I think you mean to blacklist it , then you must install the nvidia's proprietary driver . 
```
sudo apt-get install nvidia-current
``` 
This driver will automatically blacklist nouveau. 
After installation you must reboot for driver take place. 
Thanks

---

### Post by morkovka078 on 2012-05-06
Hello Nikth,

Thanks for your answer. unfortunately this doesnt work either, and installing nvidia manually puts it on the blacklist it you want to, which didn t work either, but in any case it shouldn t have detected it as after the --purge command, if i do it again it says it s not installed, so i m completly puzzled here..

---

### Post by NikTh on 2012-05-06
Hi , 
wait a minute cause i am little confused now. Can you or you can't install nvidia's proprietary driver ? 
Try to install nvidia's driver with official way. ```
jockey-gtk
``` command will open the additional drivers window. Install it(activate) from there and reboot. 
Then open a terminal and give the output of command ```
lscpi -nnk|grep -iA2 vga
```Thanks

---

### Post by VanR on 2012-05-06
apt-get remove --purge xserver-xorg-video-nouveau libdrm-nouveau1a
Always works for me

---

