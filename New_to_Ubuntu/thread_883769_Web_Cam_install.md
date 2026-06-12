---
title: "Web Cam install"
date: 2008-08-08
forum: New to Ubuntu
---

### Post by ibbill on 2008-08-08
Hi have run the following commands in the terminal. Have not installed the Web cam driver not really sure how.:confused:Could use some help here have read about gosh 50 or so post still none the wiser (crikey)

 lsusb
Bus 003 Device 003: ID 046d:08b0 Logitech, Inc. QuickCam 3000 Pro [pwc]
Bus 003 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

 
ibbill@ibbill-desktop:~$ lsmod | grep videodev.
videodev               29440  1 pwc

---

### Post by hvac3901 on 2008-08-08
hummm, don't know about a driver per say. 

I enabled my logitech cam by loading from synaptic Kopete to use it, and then loading the "jasper library". thats how i got mine to work. 

there is a webcam tutorial somewhere in the ubuntu help stuff.

---

### Post by hvac3901 on 2008-08-08
try checking this out [https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by ibbill on 2008-08-08
I have this folder on my desk top its I hope the driver for the web cam what do I have to type in the terminal for it to install it.please.

folder name is   qc-usb-0.6.6

Note it was a  qc-usb-0.6.6.tar,gz I extracted it to my desk top.

Thanks

---

### Post by hvac3901 on 2008-08-08
> **ibbill said:**
> I have this folder on my desk top its I hope the driver for the web cam what do I have to type in the terminal for it to install it.please.

folder name is   qc-usb-0.6.6

Note it was a  qc-usb-0.6.6.tar,gz I extracted it to my desk top.

Thanks

Generally the tarball has a file in the package that is called "install" or "read-me" follow those instructions.

Question: Have you tried using the camera with a program that will utilize it yet?

---

### Post by ibbill on 2008-08-09
This is what I found in the read me file.No idea what command to run to install the driver. I know it works in windows just did not want to have to use windows.

Logitech Quickcam Express USB Driver
------------------------------------

1. How to compile?
Just use a plain "make" to compile the driver.

2a. The easiest way to load modules is to use the quickcam.sh shell script
To run it type ./quickcam.sh (If you have compiled USB and/or V4L support into
Kernel rather than as modules you should use method 2b)

2b. How to use with insmod?
Typing "insmod mod_quickcam.o" should do the trick.

3.  What are qce-ga's features?
 * 2.2 + 2.4 Support
 * Video4Linux compatible driver
 * ProcFS Support (+ VideoProcFS)
 * RGB24 and YUV* support
 * full mmap() and read() support
 * ....

4. What are the parameters wich are accepted by mod_quickcam.o?
Easily find it out with "modinfo -p mod_quickcam.o"
   insmod mod_quickcam.o debug=n (n=1,2,4,8,16,32 or any ored values).
   insmod mod_quickcam.o rgain=red bgain=blue ggain=green.
   red, blue and green are initial gain values this allows to correct the 
   colour of the images. The default values are rgain=192 bgain=192 ggain=176

---

### Post by hvac3901 on 2008-08-09
open a terminal and type "make" with the path to a file called make dirrectory.

make /home/ur name/desktop/qc-usb-0.6.6/.../.../makefile

---

### Post by ibbill on 2008-08-09
No dice nothing will look to buy a new camera that is Linux friendly right out of the box rather that trying to force this old one.

Thanks ever so much for your patience.

Bill

---

