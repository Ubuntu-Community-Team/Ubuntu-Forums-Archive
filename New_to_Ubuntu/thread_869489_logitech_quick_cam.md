---
title: "logitech quick cam"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by slickh20 on 2008-07-24
trying to install my webcam and i am finding inforation but everyone is a few steps ahead of me on the internet or are doing stuff that i dont quite understand yet.  Any ways i have the webcam pluged in and skype installed

after that i am lost.

thanks

logitech quick cam IM plus (e 3500 Plus)

---

### Post by Squid Tamer on 2008-07-24
Apparently Ubuntu has problems with webcams... But apparently it can be done. I have the same problem as you. All of the tutorials I've found don't explain HOW to do it. Hope someone else can help...

---

### Post by slickh20 on 2008-07-24
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams) 

so this helped i was able to figure out that my camera does work but at the bottom of this wiki it talks about x window system and anyways when i try to test the output i just get this....

so does that mean it is working? 

when i test the imput the webcam works just fine 

so then when i go over to skype and test it i get nothing.

---

### Post by cariboo on 2008-07-24
If your webcam is listed here:

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

You can download the driver here:

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

Download the version for kernel version 2.6.11 and up, once you have downloaded the file, double click it and let file-roller extract it. I would suggest creating a directory  called sources in you home directory and extract it there.

> Compiling it
============
The driver module can be built without modifying your kernel source tree.

Before trying to compile the driver, ensure that you've configured your
kernel, and updated the dependencies:
'make [config|menuconfig|xconfig]; make dep'.

Make sure, when compiling the driver, you use the same version of compiler as
was used to compile your kernel. Not doing so can create incompatible binaries.

as root
goes to gspcav1 directory and run:
./gspca_build 

if all goes right the module is compiled and load in memory
if not, errors messages can be found in kgspca.err You should post this file to the maintainer
or in the sourceforge project bugs report. <http://sourceforge.net/projects/spca50x/>.

Once you have extracted the file, in a terminal cd to the directory you extracted it to then while still in a terminal, as it says above in the qoute:

```
sudo ./gspca_build
```

Just because I have given most of the pertinent info, you should still read the file called read_and_install.

Jim

---

