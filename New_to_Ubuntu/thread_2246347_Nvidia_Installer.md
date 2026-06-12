---
title: "Nvidia Installer"
date: 2014-09-30
forum: New to Ubuntu
---

### Post by Grimmnyr on 2014-09-30
I've downloaded the requisite file from nvidia's website.  I tried using the instructions to install the installer but it can't find the file.  I tried the other method to just extract it, that didn't work either.  My Nvidia Server Settings only has Application Profiles and nvidia-settings configuration as options in the sidebar (can't adjust resolution or refresh rate).  I tried forcing a config file but it's empty.  Any tips?

---

### Post by Vladlenin5000 on 2014-09-30
Hi, welcome.

First question is why are you doing that? The following questions are about everything that's missing in your post like your system configuration, ie, hardware specs.

---

### Post by UltimateCat on 2014-09-30
To find out exactly what Nvidia card you have please run this command so we know which driver you need.
```
lspci | grep -i VGA

```

Adjusting your resolution should be somewhere in your Settings or Power Management Settings.

You might also want to post the output of :
```
lspci

```
To help others to become familiar with your machine.

---

### Post by Jordan_Cameron on 2014-10-01
Also, just a stab in the dark, but have you tried installing Nvidia via the Additional Drivers app?  I've found it to be the easiest and simplest method of getting Nvidia Drivers up and running.

---

### Post by oldrocker99 on 2014-10-01
> **Jordan_Cameron said:**
> Also, just a stab in the dark, but have you tried installing Nvidia via the Additional Drivers app?  I've found it to be the easiest and simplest method of getting Nvidia Drivers up and running.

He is correct. Installing the .sh file from nVidia is not for the beginner, and, even if you get it installed correctly, after a kernel update, it may not work. There's a way around this, of course, but you really are better off using the Additional Drivers in Preferences.

---

### Post by SeijiSensei on 2014-10-01
An alternative to the Additional Drivers application is to run this command at the prompt:
```
sudo apt-get install nvidia-current
```
It has always installed compatible drivers for my machines with NVIDIA hardware.

One problem with installing the driver at NVIDIA versus these methods is what happens when your kernel is upgraded.  The driver needs to be recompiled to be integrated with the new kernel.  Installing via the Additional Drivers app or the apt-get method brings in the required "dependencies" that enable compilation of kernel modules.  When the kernel changes, the driver code will be automatically recompiled.

---

