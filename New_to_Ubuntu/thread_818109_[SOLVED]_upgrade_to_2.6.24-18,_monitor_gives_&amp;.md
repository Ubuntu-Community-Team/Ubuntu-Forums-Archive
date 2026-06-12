---
title: "[SOLVED] upgrade to 2.6.24-18, monitor gives &amp;quot;out of range&amp;quot;"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by drewcoon on 2008-06-04
After updating my kernel version this morning, I get a blank screen with  "out of range" on it everytime I select to boot any non-recovery mode kernel from grub. But oddly, if I boot in recovery mode, then choose to "continue to normal boot", the computer works fine.

i've tried

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

but it does nothing, it spits out something about overwriting a possibly customised configuration, then it just bails on me and I never actually get to see the options, as you can see:

```
drewc@linxp:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for drewc: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080604075528
drewc@linxp:~$ 
```

Every other time I ran this command, I got the xorg settings, now it does nothing. Is something broken or did something change?

I reverted to a backup copy of xorg that I have, but it didn't solve my problem, despite the fact that it contains the proper screen resolutions. What's going on?

I've tried older kernels as well, but I get the same problem. Help!

---

### Post by philinux on 2008-06-04
Try installing and running startupmanager and set the resolution you want.

---

### Post by drewcoon on 2008-06-04
Screen resolution in startupmanager is set to 1280x1024, which my monitor can handle. I'll turn it down a step and try again, though :)

I thought that resolution was just for grub, am I wrong?

---

### Post by drewcoon on 2008-06-04
Excellent, your idea fixed it!

I didn't know startupmanager was that useful... I mostly used it to give grub pretty colors and stuff :p

---

