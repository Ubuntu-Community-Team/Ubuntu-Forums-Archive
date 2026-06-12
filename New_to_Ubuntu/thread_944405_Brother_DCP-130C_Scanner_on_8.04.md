---
title: "Brother DCP-130C Scanner on 8.04"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by CupcakeM on 2008-10-11
After using this forum to find my answers for the printing problem (thanks to everyone who helped with those past questions), I thought that the scanner would work easily.

I downloaded brscan and brscan-skey and tried it, until I realized that I had the wrong brscan. Then, I uninstalled brscan and installed brscan2, the correct one. The I found this:
> If you have installed both “brscan” and “brscan2” drivers on your PC and you uninstall “brscan”, you may experience problems. If this happens, run the following command: "/usr/local/Brother/sane/setupSaneScan2 -i".

So, of course, I did that too.

Following the directions on [http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+130c](http://ubuntuforums.org/showthread.php?t=590793&highlight=brother+130c) , I received an I/O-Error from XSane, so I went on to step 5.
However, when I got to step 6, I typed 
```
sudo gedit /etc/udev/rules.d/45-libsane.rules
```
And up came a blank page. It seems that this "45-libsane.rules" file doesn't exist on this computer...

---

### Post by CupcakeM on 2008-10-17
*Bump* Thanks to TopEnder for helping me out
Heres what he suggested (slightly abbreviated):

First type 
```
gksudo gedit /etc/udev/rules.d/40-basic-permissions.rules
```
Into the terminal. When the file pops up, change:
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0664"
SUBSYSTEM=="usb_device", MODE="0664"
```
to:
```
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", MODE="0666"
SUBSYSTEM=="usb_device", MODE="0666"
```
and save the file.
Then, run:
```
sudo rm /etc/udev/rules.d/45-libsane.rules
```
to remove the 45-libsane.rules file and finally type in
```
gksudo gedit /etc/udev/rules.d/45-libsane.rules
```
to open the blank file of that name. Add:

#Brother
SYSFS{idVendor}=="04f9",MODE="666",GROUP="scanner"

Note that the "04f9" is from what comes up from Brother Industries wen you type lsusb in the terminal.

to the file, and save it. And voila! Now my scanner works fine

---

### Post by anewguy on 2008-10-17
There is only one problem with the solution - it leaves all of your other USB devices "wide open" on the system.  

I had a similar problem with some cameras and Linux.

With 8.04 came a change in the way the permissions files (/etc/udev/rules.d/).  It looks at the files in a numerical sequence order - so 40-basic-permissions.rules is processed before something like 41-xxxxx.  The files above 40 are to offset or override defaults defined in 40.  So, I know in my case I left 40-basic-permissions.rules alone and added my 4x-xxxx file to add the similar constraints as you have.

So basically, your 40-basic-permissions.rules file is leaving every USB device open to the world, while your 45-libsane-rules file is defining an offset for that saying in the case of vendor id 04f9 use these rules instead.

In my case, I was able to leave 40-basic-permissions.rules alone and only use the 4x-xxx file to override its permission just for my cameras - the system is a little "tighter" that way.  I would suspect if you left your 40-basic-permissions.rules file alone and just added the 45-libsane-rules file you would have been fine.

If you are on a single user system the idea that your USB devices are wide open may not be a concern.

Dave :)

---

### Post by CupcakeM on 2009-04-18
Now I've updated to to 8.10, and am having the same problem. I've checked through everything, and done the same things as I would have for 8.04, but it still doesn't recognize the scanner. However, it prints just like before.

This time I'm not getting an I/O-Error, I just end up with "No devices available".

---

