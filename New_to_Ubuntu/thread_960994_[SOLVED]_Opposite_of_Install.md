---
title: "[SOLVED] Opposite of Install"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by Kellemora on 2008-10-27
I tried to install a new Nvidia driver, didn't work, changes don't help.

I used sudo aptitude install nvidia-glx-new

Do you use remove or uninstall to get rid of it?

Thanks 
TTUL
Gary

---

### Post by ad_267 on 2008-10-27
You use "sudo aptitude remove package_name"

Try going to System - Administration - Hardware Drivers to install the nvidia drivers.

---

### Post by fooman on 2008-10-27
to remove a package: 

```
sudo aptitude remove package
```

to remove a package and its configuration: 

```
sudo aptitude purge package
```

---

### Post by Kellemora on 2008-10-27
Hi ad

I had the right drivers in there, and everything has been working A-OK until I messed around, was just experimenting again and loaded glx then loaded the glx driver and messed things up royally, hi hi....

I figure by removing it completely and putting back everything as it was, it might start working right again.

I must be brain dead tonight!

TTUL
Gary

---

### Post by ad_267 on 2008-10-27
You might want to try using
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to reconfigure your X server and then re-enable the drivers.

---

### Post by Kellemora on 2008-10-27
Hi ad

You won't believe this, but, after I put everything back and got everything back to normal, a message popped up on my screen that said I needed to install nvidia-glx-legacy for effects to be restored.  I did that and the computer booted up normally, in the right resolution too!
Prior to that it would boot up and jump into LOW-RES mode, after I messed with it.

Even with the latest new driver, I still can't get Effects to work, but it's no big deal on this particular computer.  It's just for work anyhow.

Have I nice evening, I'm hitting the horizontal!

TTUL
Gary

---

### Post by ad_267 on 2008-10-27
Awesome.

I wouldn't worry about the effects, I have them disabled myself as they cause too many issues with applications that use 3d graphics, but maybe that's just for me.

You can enable metacity compositing if you want some basic eye candy.

---

