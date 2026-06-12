---
title: "Ubuntu isn't starting [The system is running in low-graphics mode]"
date: 2017-06-20
forum: New to Ubuntu
---

### Post by nlreiniernl on 2017-06-20
Hi everyone,

After installing some additional AMD driver for my GPU my Ubuntu 16.04 refuses to start.
If i try to boot it normally it only shows me a /sda/ path in the left top corner.

I saw a lot of posts about this issue and tried quite a lot of guides without any success.
If i try to boot into recovery mode and pick the failsafeX option it will continue booting till the login screen without any problems.
But when i enter my passphrase a dialog pops up about a system error, after just 2 seconds the screen goes back to the login page. Logon as guest makes no difference. 

I tried everything described within this thread [Link to askubuntu thread]("https://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error").

Hopefully you guys can help me out.

Regards

---

### Post by deadflowr on 2017-06-20
Remove the driver.
There are no additional drivers for amd cards for 16.04.

How did you install the driver?

---

### Post by nlreiniernl on 2017-06-21
I installed the driver because i had the feeling Ubuntu isn't getting the full performance of my GPU. My GPU has 2GB of memory but the application that needs my GPU says it hasn't.
After reading around it seemed like an OpenCL issue and a link to this:
[Link](http://developer.amd.com/tools-and-sdks/opencl-zone/amd-accelerated-parallel-processing-app-sdk/)

The second from the top is the one i installed.
Btw i have no clue how to remove the driver.

---

### Post by deadflowr on 2017-06-21
I still do not know which method you used to originally install the driver...
I'm guessing since there are no AMD drivers available in the Ubuntu drivers utility for 16.04 that you installed the driver from AMD.
in which case you would need to run the amd uninstall command to remove them.

You would need to run from a console so press ctrl + alt + F1 (or F2,3,4,5,6)
Then login like normal, enter your username and then the user's password and it'll start a command line prompt for you
The uninstall command should be
```
sudo aticonfig --uninstall
```
You might also need to remove the xorg file if  one was made.

That should be
```
sudo rm /etc/X11/xorg.conf
```
Then you would need to reboot, just type
```
sudo reboot
```
Since this was laid out in the link you posted in post #1, I am not sure if you did any of this.

Not sure what is what about the OpenCL packages you tried as those seem to be developer kits.
(Not necessarily drivers and those require the drivers which are no longer installable on Ubuntu 16.04 anyway)

---

### Post by nlreiniernl on 2017-06-21
I did everything for sure but I didn't install a normal driver. Obviously, I accidentally installed the SDK. It says the command is not found if I try to execute it [aticonfig: command not found]. If I look around in /home/$username/ I see AMDAPPSDK-3.0, in that folder there is an log file, and Linux_fullInstall_root.gif. The last thing stated in the log is an request to reboot before the changes apply.

After that reboot my Ubuntu stopped working properly.

---

