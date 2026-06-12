---
title: "screen resolution gone bad, no driver anymore... and keyboard gone bad too!"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by t0p on 2008-08-27
Up until 10 minutes ago I was using the nVidea proprietary TNT driver, and had a screen resolution of 1024 x something.  Then I had an update... kernel headers I think... and when I restarted I got 800 x 600 res, and when I went to System > Administration > Hardware Drivers, it just says No proprietary drivers are in use on this system.

Plus my keyboard has gone bad... the wrong symbols are coming up...

And I don't know what to do!! :confused:

---

### Post by t0p on 2008-08-27
Okay, I've got a temporary fix - by using the old kernel (2.6.24-16, instead of 2.6.24-19) I can use the nVidea driver and have my old res (1280 x 1024).  But how come the new kernel means the nVidea driver isn't available at System > Administration > Hardware Drivers?  Does this mean I need to go to nVidea's site and download the driver to install myself?  Or am I missing something?

And what about my keyboard?  How do I go about fixing that?

---

### Post by TheLions on 2008-08-27
you need to reinstall NVidia drivers from NVidia page or with Envy. 
To install it from NV page:
1. download this file :[http://us.download.nvidia.com/XFree86/Linux-x86_64/71.86.06/NVIDIA-Linux-x86_64-71.86.06-pkg2.run](http://us.download.nvidia.com/XFree86/Linux-x86_64/71.86.06/NVIDIA-Linux-x86_64-71.86.06-pkg2.run) (64bit)
[http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/96.43.07/NVIDIA-Linux-x86-96.43.07-pkg1.run) (32.bit)

2. in terminal type "chmod 777 NVIDIA-Linux-x86_64-71.86.06-pkg2.run" for 64 bit or "chmod 777 NVIDIA-Linux-x86-96.43.07-pkg1.run" for 32 bit

3. press Ctrl+Alt+F1 and login

4. type "sudo /etc/init.d/gdm stop"

5. type "./Linux-x86_64/71.86.06/NVIDIA-Linux-x86_64-71.86.06-pkg2.run" for 64bit or "./NVIDIA-Linux-x86-96.43.07-pkg1.run" for 32 bit

6. press "Yes" on all Q

7 type "reboot"

and about keyboard go to System->Settings->Keyboard and there click on Layout and choose your Language

---

