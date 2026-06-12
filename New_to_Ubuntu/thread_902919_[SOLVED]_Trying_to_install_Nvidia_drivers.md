---
title: "[SOLVED] Trying to install Nvidia drivers"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by DFord425 on 2008-08-27
So i downloaded NVIDIA drivers from the web site. I tried to install them but i got this error message:
```
ERROR: You do not appear to have libc header files installed on your system. 
       Please install your distribution's libc development package.
ERROR: Installation has failed.  Please see the file
       '/var/log/nvidia-installer.log' for details.  You may find suggestions
       on fixing installation problems in the README available on the Linux
       driver download page at www.nvidia.com.
```
Does anyone know where i get the libc development package?

---

### Post by Shazaam on 2008-08-27
Two things you will need which are available in Synaptic...
1. build-essential
2. header files for your installed kernel; this is the terminal code for that.....
```
sudo apt-get install linux-headers-$(uname -r)
```

---

### Post by DFord425 on 2008-08-27
i ran those two commands, and at the end of the second command i got this message:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Is that correct?

---

### Post by DFord425 on 2008-08-27
It seemed that it worked, thanks for the info.

---

### Post by Shazaam on 2008-08-27
> **DFord425 said:**
> i ran those two commands, and at the end of the second command i got this message:
```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Is that correct?

Yes. You must already have them installed. Glad it worked out. One thing you have to remember is when you do a kernel upgrade you MAY have to reinstall the Nvidia drivers.

---

### Post by erickghint on 2008-08-27
Don't forget to edit the restricted modules. 

```
 gksudo gedit /etc/default/linux-restricted-modules-common 
```

at the bottom of the document there will be something that says:

DISABLED MODULES ""

  Just put nv in the quotes,

```
 DISABLED MODULES "nv" 
```

 and you're good to go. If you don't do this, you'll have to install the drivers again, as they won't stick. You'll know after a reboot (it will default to low graphics mode if the drivers haven't stuck). In that case, (as long as you've disabled the modules) you just have to reinstall the nVidia driver and that should be that. :)

---

