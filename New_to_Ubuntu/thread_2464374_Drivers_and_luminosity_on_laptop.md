---
title: "Drivers and luminosity on laptop"
date: 2021-06-30
forum: New to Ubuntu
---

### Post by alexo91 on 2021-06-30
Hello !

I am a total beginner on Linux, with my Lenovo Legion 5 laptop
I installed ubuntu recently and my brightness keybind fn+F5 and fn+F6 does show brightness control bar but it doesn't change my screen brightness. I tried many tutorials to resolve this problem but it looks like nothing worked...
The keybind for sound does work.
In /sys/class/backlight i do not have intel folder (despite my gpu is RTX 3060), i had "acpi_video0" and after changing some grub settings i know have "ideapad" folder in /sys/class/backlight and when i check the file /sys/class/backlight/ideapad/brightness, the brightness level does change based on my keybind fn+F5/F6 but my screen brightness doesn't change. 
Do you have any solution ?

I think it is a driver problem but I am not able to find any easy way to manage drivers under linux... So I also wanted to ask if there is a software to inspect drivers version and update drivers easily ? 

Thanks for the help !

---

### Post by TheFu on 2021-06-30
Lenovo laptops have better support for power management stuff than most other laptop vendors.  I think there is a package in the repos specifically to deal with power-stuff on Lenovo laptops. Run:
```
sudo apt search lenovo
```
to see which packages are available for your specific Ubuntu release. 

BTW, whenever posting questions here, we need to always know the exact release and the DE being used.
**inxi -S** provides that information.

Sometimes Linux drivers cannot control everything that Windows does because the vendor doesn't create any software/drivers for Linux. That leaves it upto the community. Lenovo has plenty of Linux users, so support for their stuff is a little greater than most others.

---

