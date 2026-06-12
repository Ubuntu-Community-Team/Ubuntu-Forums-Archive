---
title: "flashing/jumping screen after install."
date: 2013-06-11
forum: New to Ubuntu
---

### Post by arranskye on 2013-06-11
hello all.

just installed ubuntu 12.10 on my laptop. HP Compaq CQ60  series. Nvidia Ge8200 G graphics card. The installation went ok but even after rebooting several times the screen still keeps jumping and flashing.  Looks like I need a different driver. Please can someone advise how to do this please.

Also wireless card not recognised. tried dongle, same result. but will open another thread for this.

---

### Post by papibe on 2013-06-11
Hi arranskye.

Could you post the output of these commands?
```
lspci -nnk | grep -iA2 vga

lsmod | grep -E '(nvidia|nou)'

apt-cache policy nvidia-current

xrandr

xvidtune -show
```
Regards.

---

### Post by arranskye on 2013-06-12
margaret@laptopvista:~$ lspci -nnk | iA2 vga
No command 'iA2' found, did you mean:
 Command 'if2' from package 'ctsim' (universe)
iA2: command not found
margaret@laptopvista:~$ lsmod | grep -E '(nvidia |nou)'
nouveau               823577  3 
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  5 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
wmi                    18590  3 hp_wmi,nouveau,mxm_wmi
margaret@laptopvista:~$ apt-cache policy nvidia-current
nvidia-current:
  Installed: (none)
  Candidate: 304.88-0ubuntu0.1
  Version table:
     304.88-0ubuntu0.1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal-updates/restricted i386 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) quantal-security/restricted i386 Packages
     304.51.really.304.43-0ubuntu1 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/restricted i386 Packages
margaret@laptopvista:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
LVDS-1 connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1366x768       60.0*+
   1024x768       59.9  
   800x600        59.9  
   640x480        59.4  
   720x400        59.6  
   640x400        60.0  
   640x350        59.8  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
margaret@laptopvista:~$ xvidtune -show
"1366x768"     69.31   1366 1382 1416 1466    768  770  776  788 -hsync -vsync

margaret@laptopvista:~$ 
 
Thanks papibe     screen getting worse.  fragmenting, flashing, breaking up etc. and sound and wireless being effected too
sound & wifi breaking up. also could not close down rythme box.  thank you regards margaret

---

### Post by papibe on 2013-06-12
Thanks.

Could you run this again? Make sure to copy exactly the syntax:
```
lspci -nnk | grep -iA2 vga
```
Regards.

---

### Post by arranskye on 2013-06-13
sorry papibe  here it is:                            margaret@laptopvista:~$ lspci -nnk | grep -iA2 vga
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation C77 [GeForce 8200M G] [10de:0845] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:360a]
    Kernel driver in use: nouveau
margaret@laptopvista:~$ 

thanks

---

### Post by papibe on 2013-06-13
Thanks.

Since you have an Nvidia card, installing the proprietary driver may provide better support.

Open a terminal, and run these commands:
```
sudo apt-get install nvidia-current

sudo nvidia-xconfig
```
Then restart your machine.

The worst case scenario is that you boot into a black screen. Avoid pressing your power button to restart or power down your machine. Instead, you can get into a text-mode console by pressing Ctrl+Alt+F1 (or F2). You can login there using your regular user. There you can restart by running:
```
sudo reboot
```
and turn it off by running:
```
sudo poweroff
```
In any case, booting into a black screen using the Nvidia driver may indicate that your card does not support the kernel mode. To allow compatibility set the flag 'nomodeset' on the grub options.

While in text mode, edit this file:
```
sudo nano /etc/defualt/grub
```
Look for a like that looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
Add nomodeset to it so it looks like this:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
Save the file, and reboot.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by arranskye on 2013-06-14
Hiya  papibe.

Checked the screen resolution (laptop 15") Set at  1024 x768 16.9. changed it to 1024 x 768 4.3 and it initially appeared  to stablise but after using it for a few seconds it went bananas.  flashing badly when trying to open icons and trying to access the  internet produced a  really fragmented screen like a digital TV losing  signal. Tried setting back to 16.9 but no good.Rebooted to find text  appearing with missings fonts and little brown boxes instead of letters,  fragmented flashing screen jumping around.** Worst of all lost wifi & sound.** Reset to 4.3 rebooted and message appeared "*System Problem Detected" *(reported  problem)  Shut down. Returned this morning, fired up and screen almost  stable but no sound or wifi.  Then a text saying updates required. said  it would take 2 hours to download.  left it, returned 1/2 hour later and  laptop had shut down.  Rebooted, screen almost stable but showed an  error:  "Problem with the system," no details, so took the opportunity  to open the terminal and input the text .
[HTML]
sudo apt-get install nvidia-current                 This is as far as i  got. as immediately after displaying the output the screen froze.

  	 	 	 	   Could not resolve 'security.ubuntu.com' 
 Err http://security.ubuntu.com/ubuntu/ quantal-security/main nvidia-settings i386 304.88-0ubuntu0.2  
   Could not resolve 'security.ubuntu.com'  
 Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.2.0.3-1.1ubuntu1.1_all.deb  Could not resolve 'gb.archive.ubuntu.com'  
 Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.18.4-2_i386.deb  Could not resolve 'gb.archive.ubuntu.com'  
 Failed to fetch http://security.ubuntu.com/ubuntu/pool/restricted/n/nvidia-graphics-drivers/nvidia-current_304.88-0ubuntu0.1_i386.deb  Could not resolve 'security.ubuntu.com'  
 Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/x/x-kit/python-xkit_0.5.0_all.deb  Could not resolve 'gb.archive.ubuntu.com'  
 Failed to fetch http://gb.archive.ubuntu.com/ubuntu/pool/main/s/screen-resolution-extra/screen-resolution-extra_0.15_all.deb  Could not resolve 'gb.archive.ubuntu.com'  
 Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/n/nvidia-settings/nvidia-settings_304.88-0ubuntu0.2_i386.deb  Could not resolve 'security.ubuntu.com'  
 E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?  

 margaret@laptopvista:~$  

looks like ubuntu cant find nvidia.   had to reboot 6/7 times to  get this output and in the course of this, one terminal message. "said  unable to locate nvidia."  

On one another "terminal" try,  following the incomplete updates, the output included:  6 newly  installed, 0 to remove, 0 upgrade, 304 not fully installed. Complete  page froze before I could copy.

Screen kept freezing so could not  use mouse to copy, or close terminal.    Input  sudo nvidia-xconfig    =   output:  assuming driver cache failed/asking for cache data failed.   Ctrl alt F1/F2 did not work but terminal responded to reboot and  poweroff.
Tried to run from disks  2 x  12.10 ubuntu, but much the  same results. instability, icons slow to open, screen freezing no sound  or wifi.

looks like some options: try to get compatible version  of nvidia : --fix missing   upgrade, or possibly the best option wipe  disk and start again with 13.04.  What would you advise please.  Thanks

---

### Post by arranskye on 2013-06-14
Hi Dont know if this is relevant but wiping windows vista off this machine and replacing it with XP pro has frequently produced wifi & sound problems.

When XP was installed the device manager showed 2 audio  components with no drivers. Windows couldnt supply the drivers and neither could Driver Solutions. Eventually after many weeks of work I discovered that a component was installed in the (vista) laptop in anticipation of HDMI and it could only be mounted off a universal audio architecture platform  which was not included in the XP disk.The other driver was a conxent HD Audio 221 but further confusion and difficulty arose until I discovered that in order in to install the conxent driver I had to disable the the HDMI component.  Anyway I eventually got the sound working normally but the wifi has always been a bit intermittent and I now suspect that its due to the vista/XP conflict. It works and then stops for no apparent reason.

Why is it that we can run 20 + different distro/OS on lots of machines and windows cannot make 2 of their own OS run with compatibility on one machine.   just stupid.

Dont know if this would effect how ubuntu "sees" the driver compatibility and its causing confusion.??

I can wipe XP & reinstall Vista or just wipe windows altogether however your help and instructions are all very very helpful and part of my learning curve.  Thanks

---

