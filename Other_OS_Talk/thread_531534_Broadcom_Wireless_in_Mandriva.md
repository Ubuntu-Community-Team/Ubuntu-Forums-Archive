---
title: "Broadcom Wireless in Mandriva"
date: 2007-08-21
forum: Other OS Talk
---

### Post by jamieh on 2007-08-21
I just bought Mandriva PowerPack 2007 Spring, but how do I get my Broadcom wireless card to work? I can get it to work in Ubuntu 7.04, but I can't find any tutorials for Mandriva. Can anyone tell me how? I have an "hp pavilion zd7000"

---

### Post by init1 on 2007-08-21
> **jamieh said:**
> I just bought Mandriva PowerPack 2007 Spring, but how do I get my Broadcom wireless card to work? I can get it to work in Ubuntu 7.04, but I can't find any tutorials for Mandriva. Can anyone tell me how? I have an "hp pavilion zd7000"
You may need NDISwrapper like I did. Refer to this thread. It helped me. 
[http://ubuntuforums.org/showthread.php?t=515398](http://ubuntuforums.org/showthread.php?t=515398)

---

### Post by AdamWill on 2007-08-31
init1 is right. 2007 Spring defaults to using the native bcm43xx driver for Broadcom chips, but this was a bad decision, it doesn't really work in most cases. So it's best to use ndiswrapper instead.

You can configure ndiswrapper with the Mandriva Control Center's network configuration tool - when it gives you the choice between using a native driver and a Windows driver, tell it you want to use a Windows driver.

The only fly in the ointment is that you might have to force the native driver to stop being loaded. To do this, edit the file /etc/modprobe.conf and add this line:

blacklist bcm43xx

---

### Post by init1 on 2007-08-31
> **AdamWill said:**
> init1 is right. 2007 Spring defaults to using the native bcm43xx driver for Broadcom chips, but this was a bad decision, it doesn't really work in most cases. So it's best to use ndiswrapper instead.

You can configure ndiswrapper with the Mandriva Control Center's network configuration tool - when it gives you the choice between using a native driver and a Windows driver, tell it you want to use a Windows driver.

The only fly in the ointment is that you might have to force the native driver to stop being loaded. To do this, edit the file /etc/modprobe.conf and add this line:

blacklist bcm43xx
Yay! I'm right! You may need to compile a newer version of ndiswrapper, that's what I had to do. But Spring 2007 might have the newer version.

---

