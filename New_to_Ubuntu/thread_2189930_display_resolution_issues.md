---
title: "display resolution issues"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by grbaker101 on 2013-11-24
hello everybody, and thank you in advance for all you do!
My problem is that ubuntu 12.04 does not see my graphics driver (nvidia 320), and reverts to the lowest possible resolution. When I try to download available drivers (304, 316) I get an error messsage that says to check the log file.  Being a new user, I cannot make any sense of the code.  When I downloaded the graphics driver to windows, I did not install the full package (NView, HDAudio and Physics). I'm kind of stuck here and appreciate any advice, keeping in mind that I am an absolute noob...Sigh...

---

### Post by deadflowr on 2013-11-24
Press the windows key on your keyboard to open the dash and type "Additional Drivers" (normally you only need to type addi for it to come up in the results)
Then open that and let it run.
When it finishes its search and the main window opens, select the option for recommended, if one does(usually called nvidia-current).
Then press activate and it will download and install the driver.
Follow along and do as it asks, if it asks to restart then restart.

When it restarts, open the dash with the windows key again and type nvidia-settings, or nvidia-Xserver-setting, it should bring up the nvidia control panel.(You should see it listed with just nvidia, or nv even)
Open it and you should be able to set the resolution and setting here.

You can also read through this for any additional help you might need
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by grbaker101 on 2013-11-25
That is a great link;  Thank you for the help.  I rebooted into safe mode of a previous version and repaired the damaged package.:D

---

