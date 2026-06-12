---
title: "[SOLVED] install catalyst control center"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by rache1111 on 2008-08-20
Hi,

I am currently using the ati restricted driver from the ubuntu repository (glrx). I know that I can configure some of the settings with aticonfig, but I heard ati has released a version of the catalyst control center for use on linux, can someone walk me through on how to install it properly?

Thanks!

---

### Post by skymera on 2008-08-20
I think it's this:

[http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

---

### Post by rache1111 on 2008-08-20
Thanks for the quick reply,

I found a link:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.7.29)

Does anyone know how I can find the version number of the driver that is installed on my system?

I tried to use fglrxinfo but that only returns the OPENGL version.
~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.1.7412 Release

---

### Post by rache1111 on 2008-08-20
OK I have it installed according to the previous instruction, and catalyst control center is working :)

This latest version by the way, solved the flash video tearing problem.

---

