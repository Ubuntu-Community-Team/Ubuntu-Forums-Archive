---
title: "Beryl for Intel embedded Laptops"
date: 2006-10-26
forum: Outdated Tutorials &amp; Tips
---

### Post by sunny_nwho on 2006-10-26
Hi everybody, I had success in using Beryl with my Acer Laptop with a i810 chipset and 855GM This is what I did

Follow these intructions from 
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX)

Some might have a problem at this step

```
sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r 
```If you have the problem then replace the 'uname -r' with the kerner version if your kernel version is 2.XX.XXX-17 then replace it to 16 it does not harm (atleast it did not on my laptop)

and then do the rest fromt he wiki.beryl-project.com page I quoted earlier and at the end you will have a running beryl

Hope this helps

---

