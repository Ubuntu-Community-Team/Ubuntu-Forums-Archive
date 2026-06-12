---
title: "problem with nvidia :'("
date: 2012-12-24
forum: New to Ubuntu
---

### Post by mohur on 2012-12-24
hi, im using dell inspiron 5420 14r,im very very new in ubuntu..
im having problem with nvidia GeForce GT 630M..
using ubuntu 12.04 lts 64 bit
first i saw this : 

[[IMG]http://www3.picturepush.com/photo/a/11761886/640/11761886.png[/IMG]]("http://picturepush.com/public/11761886")

then i tried to googling and try to fix that nvidia problem, but i didnt know what i did, i just type the code that i found from google :(, and problems coming..
the screen went 640 x480, but i managed to fix it  by installing another nvidia driver, but now my compiz config doesnot working..

i see in google to try optirun glxgears, this is the output:

[  970.393216] [ERROR]Cannot access secondary GPU - error: [XORG] (EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module. Please see the

[  970.393277] [ERROR]Aborting because fallback start is disabled.

---

### Post by seenthelite on 2012-12-24
Have a look at this thread

[http://ubuntuforums.org/showthread.php?t=2078461](http://ubuntuforums.org/showthread.php?t=2078461)

---

### Post by monkeybrain2012 on 2012-12-25
In the terminal type

```
sudo nvidia-xconfig
```

Then reboot.

---

