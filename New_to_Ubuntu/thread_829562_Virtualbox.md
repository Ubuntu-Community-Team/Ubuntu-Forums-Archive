---
title: "Virtualbox"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by stalkier on 2008-06-14
Hello. I am insterested in getting Virtualbox to run on my system. I keep getting an error when trying to run it.


```
VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}
```

I know that the module is installed. Any ideas???

---

### Post by linfidel on 2008-06-14
I'm not certain, but I will guess that you have upgraded the kernel since you installed VB.  In fact, I just tried it, and sure enough, I got the same message.  I believe it, and VMWare, depend on a specific kernel, so you will need to update it for the current kernel.

You could try booting into the old kernel if you still have it available to see, and to temporarily use it.

What I'm not certain about is exactly what steps to take.  I'll go ahead and try, and check back in case nobody else chimes in.

---

### Post by rodo-&gt;dave on 2008-06-14
You might try running

> 
sudo /etc/init.d/vboxdrv setup


---

### Post by linfidel on 2008-06-14
It seems like there are some updates for the new kernel:
virtualbox-ose-guest module for linux-image-virtual
I installed them, but now I need to restart my system.

After installation, you will need to run:
sudo /etc/init.d/vboxdrv setup
in a terminal.

---

### Post by stalkier on 2008-06-15
Thanks for all the help guys. I DID install the modules I needed and then restarted. When I logged back in I got the whitescreen of death. I had to reinstall Ubuntu. Good thing I had a separate /home partition. (I REALLY love that too. All my settings etc were intact. You got to love Linux.)

Anyways I am not going to mess with VirtualBox anymore. Too much trouble for me.

---

