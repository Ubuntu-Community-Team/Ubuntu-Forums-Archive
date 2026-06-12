---
title: "Graphics Card Installation"
date: 2012-01-06
forum: New to Ubuntu
---

### Post by Ephemeralmemory on 2012-01-06
Hello, all, I am finally serious about getting up to speed in Ubuntu, and i have a question about graphics drivers.

Sorry if I seem newbish, I've tried Ubuntu before but I never got far before going back to Windows.

I have a GTX460, and I do not know whether or not it was installed correctly.

I suspect this because I cannot enable the desktop effects. I downloaded the NVIDIA driver from the site, and I couldn't run the installer because nouveau x-server was running.

Is it okay if I uninstall nouveau and use the command:

sudo sh "drver" to install the NVIDIA driver?

Every time I check under additional drivers it never shows up.

Thanks for the help, and go Ubuntu!

---

### Post by Basher101 on 2012-01-06
hello

i had similar problems with my GTX 570...due to not having the correct driver

so to get the correct driver you will first need the right packages and dependencies. this can be done the easiest with the synaptic package manager. just download it and install via software center.

now open synaptic package manager and type in the search box "nvidia-common" and rightclick it, then mark for installation. do the same for "nvidia-current" and "nvidia-settings" and then click the arrow at the top to apply.

after you have done that, go to your system settings and click on "additional drivers" and it should display that you have the driver installed, but it is not used. the only thing left to do is a reboot to use the new driver



regards

---

