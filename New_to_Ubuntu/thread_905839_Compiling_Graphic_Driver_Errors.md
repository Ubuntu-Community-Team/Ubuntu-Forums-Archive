---
title: "Compiling Graphic Driver Errors"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by skymera on 2008-08-30
Hello =D

I have a laptop and recently bought a RAM upgrade and installed Ubuntu,yay.

Everything works flawless (i knew it would) apart from the graphics.

This is a VIA chipset (i know, i know, teh suck) and it's model name is the K8M800. Currently I'm using the OpenChrome driver which is working nicely apart from high CPU usage when opening windows and no 3D. The "VIA" driver doesn't work and it's not possible to have the UniChrome driver due to dependency issues. (Also i heard that UniChrome has been dropped?) 

Anyway after many many hours Googling i found a link to VIA Linux Portal which has nice installable Linux drivers. Sadly my chipset isn't on the list :( So i had to download the driver from Source. It compiles correct, but when it comes to installing i get errors. (I think the source code is too oudated).
I then went to the drivers page on the VIA Arena site and had a look at the Ubuntu page, Debian, Source and x86 generic. None had what i wanted, soi have to use source.

Here is the output after i run "sudo ./vinstall"

```
 
scott@scott-laptop:~/Desktop/CLE266CN400CN-CX700CN800XORG40072-kernel-src_20071213d/src$ sudo ./vinstall 
 -------- install start --------
Install VIA/S3G UniChrome family graphic driver!
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P), C7/C7M/C7D/Eden, Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
6. Intel Pentium 4 with 64 bits OS(x86_64)
4
Please wait...
Do you want VMI-ONLY(1) path or V4L(2) path?(1/2)
1
cp: cannot stat `XServer/videodev.ko': No such file or directory
cp: cannot stat `XServer/via_drv.o': No such file or directory
cp: cannot stat `XServer/via.ko': No such file or directory
cp: cannot stat `XServer/drm.ko': No such file or directory
cp: cannot stat `XServer/unichrome_dri.so': No such file or directory
cp: cannot stat `XServer/libddmpeg.so': No such file or directory
cp: cannot stat `XServer/libGL.so.1.2': No such file or directory
sed: can't read /etc/rc.d/rc.local: No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
sed: can't read /etc/rc.d/rc.local: No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
cp: cannot create regular file `/etc/rc.d/rc.local': No such file or directory
WARNING: /etc/modprobe.d/aliases line 18: ignoring bad line starting with 'lias'
FATAL: Error inserting via (/lib/modules/2.6.24-21-generic/kernel/drivers/char/drm/via.ko): Invalid module format
Now start to install VIA/S3G display utility...

Warning, system cannot find the /usr/X11R6/lib/libXv.so.1.0 file.
Please install XFree86-libs RPM package first.
You can find the package in the installation CD.

Abort, the utility is not installed.
scott@scott-laptop:~/Desktop/CLE266CN400CN-CX700CN800XORG40072-kernel-src_20071213d/src$ 

```

From that, is this driver installable on 8.04?
Since the driver was successfully compiled, is it possible for me to manually copy over the driver? If so, where to exactly?

(I've seen plenty of VIA threads, but none on compiling a driver for Ubuntu.)

Thanks a bunch guys.

---

### Post by Bachstelze on 2008-08-30
Those drivers are hugely outdated (they're for XF86, which is pretty much not used anymore), so they will not work on your Ubuntu.

---

### Post by nicedude on 2008-08-30
First errors I see are a bunch complaining about missing driver modules ( .ko files ) but then I see this

Please install XFree86-libs RPM package first.


Which the RPM part makes me nervous as it is asking you to use redhat rpm package to install that, and in ubuntu & debian you use deb packages not rpm's. So you might read the readme and install text files in the source and make sure it mentions debian etc and it may contain dependency lists which may help you figure out what you need or that this is not the correct source tarbar for you in Ubuntu.

Hope you figure it out as we all need compiz to make Vista users jealous :-)

---

### Post by skymera on 2008-08-30
This is a Source package, i might have grabbed the wrong one by mistake (There were 2 to choose from).

However i feel it is ALL outdated, i'll run the other source and post the outputs, thanks for replies.

---

### Post by skymera on 2008-08-30
ok here is the other source, not better at all.

```

scott@scott-laptop:~/Desktop/K8M64XF41061-kernel-src_20050926/src$ sudo ./makedriver 
 -------- Check source code --------
 -------- Start to make & copy driver --------
Which version driver you want to release ? 
61
mkdir: cannot create directory `/K8M64XF41061-kernel': File exists
mkdir: cannot create directory `/K8M64XF41061-kernel/': File exists
mkdir: cannot create directory `/K8M64XF41061-kernel//': File exists
cp: cannot create directory `/usr/src/xc/programs/Xserver/hw/xfree86/drivers/': No such file or directory
Which CPU do you use ? 
1. VIA C3-2(C5N/C5P), Intel Pentium 2/3/4
2. VIA C3
3. AMD K7
4. AMD K8 with 32 bits OS(x86)
5. AMD K8 with 64 bits OS(x86_64)
4
mkdir: cannot create directory `/K8M64XF41061-kernel//k8_x86': File exists
mkdir: cannot create directory `/K8M64XF41061-kernel//k8_x86/XServer': File exists
ln: target `/usr/src/linux' is not a directory
cp: cannot stat `.VIAVIDEORC': No such file or directory
./makedriver: line 219: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
cp: cannot stat `libddmpeg.so': No such file or directory
./makedriver: line 295: cd: V4L_X: No such file or directory
make: *** No rule to make target `clean'. Stop.
./makedriver: line 310: cd: vialinux: No such file or directory
cp: cannot stat `via_v4l_drv.ko': No such file or directory
./makedriver: line 321: cd: videodev//: No such file or directory
make: *** No rule to make target `clean'. Stop.
cp: cannot stat `videodev.ko': No such file or directory
./makedriver: line 367: cd: /usr/src/xc/programs/Xserver/hw/xfree86/drivers/via: No such file or directory
make: *** No rule to make target `Makefile'. Stop.
chmod: cannot access `mpatch_lite': No such file or directory
./makedriver: line 391: ./mpatch_lite: No such file or directory
make: *** No rule to make target `clean'. Stop.
cp: cannot stat `via_drv.o': No such file or directory
./makedriver: line 420: cd: /usr/src/linux: No such file or directory
dos2unix: Unable to access file drivers/char/drm/via*.c.
dos2unix: Unable to access file drivers/char/drm/via*.h.
make: *** No targets specified and no makefile found. Stop.
./makedriver: line 425: cd: drivers/char/drm: No such file or directory
cp: cannot stat `via.ko': No such file or directory
 -------- Complete to make & copy driver --------
scott@scott-laptop:~/Desktop/K8M64XF41061-kernel-src_20050926/src$ 

```

---

### Post by skymera on 2008-08-31
From lack of replies i can tell it's wrong :(

But that's all the source code they have =\ So looks like i can't have 3D enabled then :(

---

