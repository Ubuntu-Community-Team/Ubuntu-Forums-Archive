---
title: "How do I get my CPU / GPU fan under control ?"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by vincej on 2014-09-30
Hi - I have just come over to Ubuntu 14 from Win7. Under Win7 my CPU and GPU were whisper quiet, now however it is very noisy. Even if I just move the mouse you can hear the fan rpm increase. 

I managed to install lm-sensors and so I get read outs of the cores, but nothing is very hot. Only 39C or so. I have a Dell 8300 desktop with i7 and A04 Bios.  

It appears as though the CPU / GPU is being managed by the OS as the power supply fan is quiet. 

I tried installing i8kutils and that helped a little bit, maybe 10%. But compared to my win7 install it is noisy as heck. 

This the readout when I run sudo sources : 

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +39.0°C  (high = +80.0°C, crit = +98.0°C)
Core 0:         +39.0°C  (high = +80.0°C, crit = +98.0°C)
Core 1:         +34.0°C  (high = +80.0°C, crit = +98.0°C)
Core 2:         +36.0°C  (high = +80.0°C, crit = +98.0°C)
Core 3:         +37.0°C  (high = +80.0°C, crit = +98.0°C)


i8k-virtual-0
Adapter: Virtual device
Left Fan:    27390 RPM
Right Fan:   26370 RPM



If anyone can help - you will make a very happy - I have already spent nearly 2 days on this. 

Thanks !!

---

### Post by QIII on 2014-09-30
Hello!

Much of that may be the GPU.  What sort of graphics adapter do you have?  Have you installed a proprietary driver?

Do you have your dedicated GPU set as the default in your BIOS/EFI?

---

### Post by vincej on 2014-09-30
Hi - I have a radeon 5770. I installed the AMD linux adapter. 

Thanks

---

