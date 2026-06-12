---
title: "[Solved] Increase screen resolution with Nvidia"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by nacnac on 2008-08-14
It seems that quite a few others shared my frustration with getting the X server working correctly if after install, enabling the restricted drivers still will not allow you to increase the screen resolution past 640x480. After installing the nvidia drivers manually from their site, I didn't even have to modify my xorg file, the driver correctly identified my screen, and it's even an HDTV, not a monitor). Here's my work around:

summary:
    1)download Nvidia drivers to desktop
    2)completely remove Nvidia-glx and Nvidia-glx-new drivers
    3)install downloaded Nvidia drivers after shutting down X

Easy right? Here we go:

1) Go to nvidia.com, download the drivers to the desktop.
2) In synaptic, completely remove nvidia-glx and nvidia-glx-new drivers then restart.
3)After restart, press ctrl-alt-F3 (this will close X, but we still need to exit.
  -type "sudo /etc/init.d/gdm stop" (without quotations)
  -type "cd /usr/username/Desktop" (sub username for your 
    login name - this changes directories to our desktop)
  -type sh NVIDIA-Linux-x86-1xx.xx.xx.pkg1.run (or whatever the 
    filename of the driver you downloaded is. If you forget, 
    type '-ls' for a list of files/folders on your desktop. Let 
    the driver install)
  -if the installer gives you an error about being in runlevel 
    3, type "sudo -i" to login as root (get super special 
    privileges, don't do anything dumb) then type "runinit 3" 
    then sh NVIDIA-Linux.... 
  -restart. Just type "runinit 6" (runlevel 6 is restart. 
    runlevel 3 is normal, the nvidia installer needs this to 
    access certain parts of your computer, but X cannot be 
    running, hence the confusion about installing this driver).


Hope this prevents people from screwing around for 2 days like me.

---

### Post by SuperSonic4 on 2008-08-14
I've never had a problem with system -> Admin -> hardware and it detected my nvidia geforce 8500 gt

---

### Post by Gannon8 on 2008-08-14
You don't need to log in as root, the only part that needs root privileges is installing the driver.

Anyway, I am sure there are multiple "tutorials" on how to do this, so I don't think this is entirely necessary... Mostly because I needed help with it :)

---

### Post by Tictoon on 2008-12-02
can't find the nvidia-glx and nvidia-glx-new in synaptic, what now?

---

### Post by nacnac on 2008-12-02
try searching for just nvidia in the package manager. alternatively you can also use the command line:

sudo apt-get remove nvidia-glx

sudo apt-get remove nvidia-glx-new

if that doesn't work, i'd just try to move on to the next step.

good luck

---

