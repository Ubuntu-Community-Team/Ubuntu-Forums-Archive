---
title: "[Howto] Get Touchscreen working with Acer T230H on Karmic (Ubuntu 9.10)"
date: 2010-01-07
forum: Outdated Tutorials &amp; Tips
---

### Post by euxneks on 2010-01-07
So, it looks like all you need to do in order to get Touchscreen working nicely is install the latest version of the linux kernel (sweet!):
[SIZE="5"]New Solution!
[/SIZE]> **thejeswi.nk said:**
> For those who still haven't figured out how to get their touchscreen running; Just go ahead and install the latest Linux Kernel which has native touch support.
You can find instructions [here]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/").

I finally got my Acer T231H Touch Screen running on Ubuntu.
Thanks Ubuntu Forums :KS

[SIZE="5"]My howto for posterity:
[/SIZE]
I've recently had the pleasure of getting an Acer T230H 23" touchscreen monitor up and running with Ubuntu 9.10. This is a great bright monitor with a fairly responsive touchscreen that would work great for kiosks, and is extremely inexpensive. I was able to get this monitor for $400 CAD!!! 

A major source of help for me I've found is a debian lenny wiki documentation of installation on a HP onetwo computer, which surprisingly, uses the same touchscreen system.
(src:  [http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny](http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny))

Anyhow, let's get started - it may get a bit complicated so if you're shaky on the CLI, you may want to get some help from a friendly linux geekuru.

Firstly, to make sure this works right, please make sure that your lsusb lists this:
```

:~$ lsusb | grep Quanta
Bus 002 Device 002: ID 0408:3000 Quanta Computer, Inc.

```and that your lshal lists the correct device name:
```

:~$ lshal -u /org/freedesktop/Hal/devices/usb_device_408_3000_noserial_if0_hiddev | grep "hiddev.product"
  hiddev.product = 'Acer T230H'   (string)

```If you don't get similar results to the above, the next couple of configuration file entries may need to be changed to match your system. (Specifically, what product string does lshal list for the touchscreen? What does the lsusb list for the Device ID?  Maybe you need a different piece of software?)

[SIZE=3]Udev Rules
[/SIZE]
We need to make sure we create a couple of symlinks for system stuff - create a new udev rules file so that we can add the touchscreen as an input device and also reference by name instead of hiddev0
```

:~$ sudo vim /etc/udev/rules.d/99-touchscreen.rules

```(You can use a different editor if you like.)
add this into the file:
```

SUBSYSTEM=="usb", ATTRS{idVendor}=="0408", ATTRS{idProduct}=="3000", SYMLINK+="usb/quanta_touch"
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{idVendor}=="0408", ATTRS{idProduct}=="3000", SYMLINK+="input/quanta_touch"

```Restart udev:
```
sudo service udev restart
```[SIZE=3]Compile the xorg module[/SIZE]
Next, grab the xf86-input-hidtouch module from the [HidTouch Site]("http://sourceforge.net/projects/hidtouchsuite/") on SF.net and apply the attached patch which I took from here:
[http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny](http://wiki.debian.org/InstallingDebianOn/PackardBell/OneTwo/Lenny)
If you don't know how to apply patches, check out this page:
[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

Go to the parent folder of the extracted hidtouch tarball to apply the patch successfully.

Next, compile. You will need xorg-dev and possibly xorg-server-dev as well as build-essential to compile and install this.
```

:~$ cd /path/to/extracted/
:~$ ./configure --prefix=/usr
:~$ make && sudo checkinstall
:~$ sudo service gdm restart

```[SIZE=3]Edit xorg.conf[/SIZE]

Edit your xorg.conf (/etc/X11/xorg.conf - create one if necessary) and add this to it:
```

Section "InputDevice"
 Identifier      "Acer T230H"
 Driver          "hidtouch"
 Option          "SendCoreEvents"        "true"
 Option          "ReportingMode"         "Raw"
 Option          "Device"                "/dev/usb/quanta_touch"
 Option          "PacketCount"           "13"
 Option          "OpcodePressure"        "852034"
 Option          "OpcodeX"               "65584"
 Option          "OpcodeY"               "65585"
 Option          "CalibrationModel"      "1"
 Option          "CornerTopLeftX"        "0"
 Option          "CornerTopLeftY"        "0"
 Option          "CornerTopRightX"       "1920" # 1920 for 23"
 Option          "CornerTopRightY"       "0"
 Option          "CornerBottomLeftX"     "0"
 Option          "CornerBottomLeftY"     "1080"  # 1080 for 23"
 Option          "CornerBottomRightX"    "1920" # 1920 for 23"
 Option          "CornerBottomRightY"    "1080"  # 1080 for 23"
 Option          "CornerScreenWidth"     "1920" # 1920 for 23"
 Option          "CornerScreenHeight"    "1080"  # 1080 for 23"
EndSection

Section "ServerLayout"
    Identifier "Touchscreen"
    InputDevice "Acer T230H" "SendCoreEvents"
EndSection

```Next, just restart GDM and you should be rocking a new Touchscreen Monitor!

[SIZE=2][COLOR=Red]Caveats:[/COLOR][/SIZE]
[LIST]
[*]This is not a true multitouch monitor, but it can detect two fingers. HOWEVER, the driver does not support the multitouch - yet.
[*]Some of this stuff may not be needed, but I wanted to give you all the steps I took to get this working just in case. If some of you more experienced people out there can tell me what isn't needed, please feel free to comment.
[/LIST]

Special thank you goes out to *kingtaurus* for helping me get this going.

---

### Post by StCh on 2010-01-11
I have just completed a kernel driver that fully handles the T230H: multitouch events plus single touch emulation. When this kernel driver is activated, the device can be used as a touchscreen with the evdev X.org driver, and as a multitouch screen with a patched evdev driver, as explained at [http://lii-enac.fr/en/projects/shareit/xorg.html]("http://lii-enac.fr/en/projects/shareit/xorg.html")

The driver was submitted for inclusion in Linux 2.6.33. Meanwhile, it is available at [http://lii-enac.fr/en/projects/shareit/hid-acer.c]("http://lii-enac.fr/en/projects/shareit/hid-acer.c") and there are instructions at [http://lii-enac.fr/en/projects/shareit/linux-howto.html]("http://lii-enac.fr/en/projects/shareit/linux-howto.html")

Thanks to euxneks, I have found out that the panel in the T230H is the same as in some HP displays. This probably means that the driver will be renamed into hid-quanta.c at some point in the future.

---

### Post by euxneks on 2010-01-11
> **StCh said:**
> I have just completed a kernel driver that fully handles the T230H: multitouch events plus single touch emulation. When this kernel driver is activated, the device can be used as a touchscreen with the evdev X.org driver, and as a multitouch screen with a patched evdev driver, as explained at [http://lii-enac.fr/en/projects/shareit/xorg.html]("http://lii-enac.fr/en/projects/shareit/xorg.html")

The driver was submitted for inclusion in Linux 2.6.33. Meanwhile, it is available at [http://lii-enac.fr/en/projects/shareit/hid-acer.c]("http://lii-enac.fr/en/projects/shareit/hid-acer.c") and there are instructions at [http://lii-enac.fr/en/projects/shareit/linux-howto.html]("http://lii-enac.fr/en/projects/shareit/linux-howto.html")

Thanks to euxneks, I have found out that the panel in the T230H is the same as in some HP displays. This probably means that the driver will be renamed into hid-quanta.c at some point in the future.


Oh wow! That's fantastic! Thanks for doing this StCh!

---

### Post by willtriv on 2010-01-13
Thanks,
you two are helping linux out a lot :)

---

### Post by phiworld on 2010-01-18
Hello all!

I am also very interested in this monitor. 

What is your feeling about it? Is it accurate enough for a professional usage? Can you use a pen (instead of you fingers) and hit small things on the display reliably? For example to do some image editing with Gimp or so...?

Thanks for any comments!

---

### Post by bryanagee on 2010-01-18
Hey all-

I just bought the HP L2105tm to use in a kiosk application, and these instructions worked perfectly with Karmic. Many thanks to euxneks!

Unfortunately my luck has been different so far with Jaunty. It's not crucial for me to have it work on Jaunty, but it would be handy. It looks like it should be up, as you can see from the dmesg:

```
[  235.868018] usb 4-2: new full speed USB device using uhci_hcd and address 3
[  236.027259] usb 4-2: configuration #1 chosen from 1 choice
[  237.950908] usb 4-2: ctrl urb status -75 received
[  237.958904] usb 4-2: ctrl urb status -75 received
[  237.960032] generic-usb 0003:0408:3000.0004: hiddev96,hidraw2: USB HID v1.10 Device [Quanta Computer Inc. Optical Touch Screen] on usb-0000:00:1a.1-2/input0

```

Any thoughts on this?
[UPDATE]
On second reboot, it works perfectly with Jaunty. Yay!

---

### Post by bryanagee on 2010-01-18
BTW- @phiworld: HP L2105tm comes with a stylus. I haven't played with it enough to issue an opinion on the accuracy, but at first run it seems pretty solid. Better than the little signature pads at the grocers.

---

### Post by bryanagee on 2010-01-18
Oddly, the accuracy is better with fingers than with the included stylus; it seems to track a ways to the right and a hair below the stylus pointer. The edges of the screen are also a challenge, but the majority of it is very usable.

There is also an odd behavior when operating in multi-head mode; it works, but the X doesn't correct for the additional screen, which makes the cursor off proportionately by touch screen:other screen.
 
Does anyone know if there is a calibration tool that can be used on this?

---

### Post by euxneks on 2010-01-19
> **phiworld said:**
> Hello all!

I am also very interested in this monitor. 

What is your feeling about it? Is it accurate enough for a professional usage? Can you use a pen (instead of you fingers) and hit small things on the display reliably? For example to do some image editing with Gimp or so...?

Thanks for any comments!

I would say it's more suited to applications such as a public kiosk. The touch screen is a bit sensitive and sometimes it's not too accurate. For what we're using it for, it's perfect, however, I would not recommend using this screen to do intensive editing like gimp or photoshop work :)

---

### Post by euxneks on 2010-01-19
> **bryanagee said:**
> Oddly, the accuracy is better with fingers than with the included stylus; it seems to track a ways to the right and a hair below the stylus pointer. The edges of the screen are also a challenge, but the majority of it is very usable.

There is also an odd behavior when operating in multi-head mode; it works, but the X doesn't correct for the additional screen, which makes the cursor off proportionately by touch screen:other screen.
 
Does anyone know if there is a calibration tool that can be used on this?

You should probably edit the corresponding values in your xorg.conf and add the appropriate offset. For instance, if the touchscreen monitor is your second monitor, add the width of your first monitor to the Corner[Top|Bottom][Left|Right]X value - however, I haven't tested this so you'll have to tell me how well it works out for you :) (The computer hooked up to it is a small eeeBox)

---

### Post by bryanagee on 2010-01-20
We are using the L2105 for a kiosk app as well--particularly since this is in the same price range as many of the 15" counterparts, and boasts a lot wider operating temp range. One of our clients wants a kiosk in a building that has no heat and gets well below 0F on occasion. Another benefit is the ability to put a protector on the screen, since it is IR on the surface that tracks the coordinates.

As for the calibration, the tracking is off only in a certain area, so adjusting X and Y would only make things worse. It was a good thought though. For some reason the upper mid right is off and the rest is decent.

---

### Post by euxneks on 2010-01-20
> **bryanagee said:**
> 
As for the calibration, the tracking is off only in a certain area, so adjusting X and Y would only make things worse. It was a good thought though. For some reason the upper mid right is off and the rest is decent.

You should figure out the coordinates of the area where it starts to go crazy, maybe that will give some clues..?

---

### Post by bruceleo on 2010-02-19
ubuntu 9.10
HP l2105tm
I keep getting the following when trying to make:

bruceleo@homeComp:~/Desktop/xf86-input-hidtouch-9.04.04$ make && sudo checkinstall
make  all-recursive
make[1]: Entering directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function ‘HdtRawData__fillFromInputInfo’:
hidtouch__HdtRawData.h:38: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function ‘hdtOnDeviceOff’:
hidtouch__body.h:115: warning: unused variable ‘pDevice’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes’:
hidtouch__body.h:175: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected ‘int’ but argument is of type ‘int (*)(struct _DeviceIntRec *, struct xTimecoord **, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)’
hidtouch__body.h:175: error: too many arguments to function ‘InitValuatorClassDeviceStruct’
In file included from hidtouch.c:71:
hidtouch__body.h:430:5: warning: "/*" within comment
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2

Any thoughts?

---

### Post by euxneks on 2010-02-20
> **bruceleo said:**
> ubuntu 9.10
HP l2105tm
I keep getting the following when trying to make:

bruceleo@homeComp:~/Desktop/xf86-input-hidtouch-9.04.04$ make && sudo checkinstall
make  all-recursive
make[1]: Entering directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function ‘HdtRawData__fillFromInputInfo’:
hidtouch__HdtRawData.h:38: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function ‘hdtOnDeviceOff’:
hidtouch__body.h:115: warning: unused variable ‘pDevice’
hidtouch__body.h: In function ‘hdtOnDeviceInit__initAxes’:
hidtouch__body.h:175: warning: passing argument 3 of ‘InitValuatorClassDeviceStruct’ makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected ‘int’ but argument is of type ‘int (*)(struct _DeviceIntRec *, struct xTimecoord **, long unsigned int,  long unsigned int,  struct _Screen *, BOOL)’
hidtouch__body.h:175: error: too many arguments to function ‘InitValuatorClassDeviceStruct’
In file included from hidtouch.c:71:
hidtouch__body.h:430:5: warning: "/*" within comment
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/bruceleo/Desktop/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2

Any thoughts?


Did you apply the patch? I don't really know why you'd get that error except if they've changed the source or the patch wasn't applied :)

---

### Post by phatdunny on 2010-02-22
I also had a similar problem after applying the patch. Something must must have changed. In hidtouch__body.h on line 175 InitValuatorClassDeviceStruct is called with the wrong number
 of arguments. I looked at the unpatched version and changed the arguments of the patched call to that of the unpatched call. It compiled but I still have no working touch screen - infact XWindows packed up. Something to do with the new Serverlayout section I think. Any help would be very much appreciated, particularly with this make error . I'm running on Debian Lenny - hope that doesn't scare anyone.

---

### Post by bruceleo on 2010-02-26
Nope. It was the patch for me. I'm embarrassed to admit that I didn't know how to.
This helped: [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

---

### Post by euxneks on 2010-02-26
> **bruceleo said:**
> Nope. It was the patch for me. I'm embarrassed to admit that I didn't know how to.
This helped: [http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

Thanks for the link Bruceleo, added it to the main post :)

---

### Post by everythingsround on 2010-03-04
How would I go about troubleshooting this?  Everything went fine, no errors, and completed all steps of the instructions and nothing works. I get video display of course, but no touch. 

I am running this on 2.6.31-20 with a dual display setup and the T230H is the second (hostname:1) display, could my xorg have something to do with it.  If anyone can point me in the right direction, that would be great. I am happy to post any additional info upon request.

Syslog, Kernel Log etc. show nothing either.  Any help would be appreciated.  Thank you :)

edit: Just ran the hidDeviceDump and the output corresponding to touch, so I'm just not getting cursor and system control with it. Again, any help appreciated.

---

### Post by euxneks on 2010-03-04
> **everythingsround said:**
> How would I go about troubleshooting this?  Everything went fine, no errors, and completed all steps of the instructions and nothing works. I get video display of course, but no touch. 

I am running this on 2.6.31-20 with a dual display setup and the T230H is the second (hostname:1) display, could my xorg have something to do with it.  If anyone can point me in the right direction, that would be great. I am happy to post any additional info upon request.

Syslog, Kernel Log etc. show nothing either.  Any help would be appreciated.  Thank you :)

edit: Just ran the hidDeviceDump and the output corresponding to touch, so I'm just not getting cursor and system control with it. Again, any help appreciated.

Can you try it with only the T230H to see if it works? It may be something to do with the dual display setup.

---

### Post by everythingsround on 2010-03-04
I was waiting all day to come home and try that out.  That was the next step I was going to take as well.  Thanks for the tip, but I have ruled that out as a possibility.  I tried it dry - didn't help, and then recompiled the NVidia driver and got new source and re-patched/built/installed the touch support.  Didn't change a thing, unfortunately.  Could it be the NVidia driver? (running latest stable - 190.53, well now 	
195.36.08, just looked and found they release another stable/certified driver for linux and tried it with that.  Didn't help either.

I'm so happy, but jealous, for those of you enjoying 23' of touchscreen in Ubuntu.  Where to go from here? I'm thinking of trying out the 2.6.33 kernel.  Anyone know if ENAC got their multitouch support added to the kernel for native support?

Hoping to get this working, Thanks.

---

### Post by euxneks on 2010-03-05
You may not need to go directly to the 2.6.33 kernel, just download the source from the following quote and try it out.

I can't confirm that this works but it's worth a shot. If so, post back and let me know :)
> **StCh said:**
> I have just completed a kernel driver that fully handles the T230H: multitouch events plus single touch emulation. When this kernel driver is activated, the device can be used as a touchscreen with the evdev X.org driver, and as a multitouch screen with a patched evdev driver, as explained at [http://lii-enac.fr/en/projects/shareit/xorg.html]("http://lii-enac.fr/en/projects/shareit/xorg.html")

The driver was submitted for inclusion in Linux 2.6.33. Meanwhile, it is available at [http://lii-enac.fr/en/projects/shareit/hid-acer.c]("http://lii-enac.fr/en/projects/shareit/hid-acer.c") and there are instructions at [http://lii-enac.fr/en/projects/shareit/linux-howto.html]("http://lii-enac.fr/en/projects/shareit/linux-howto.html")

Thanks to euxneks, I have found out that the panel in the T230H is the same as in some HP displays. This probably means that the driver will be renamed into hid-quanta.c at some point in the future.

Also, just to be sure, are you getting anything listed with lsusb?
```

lsusb | grep Quanta

```

---

### Post by davedumas0 on 2010-03-05
i have this monitor but im running 64bit ubuntu 9.10
can some one help me the driver wont work in 64bit




thx

---

### Post by tekgeek- on 2010-03-08
I tried to follow the directions on the first post for this 

but... I am confused on this part

------------------------------------
Next, compile. You will need xorg-dev and possibly xorg-server-dev as well as build-essential to compile and install this.
Code:

:~$ cd /path/to/extracted/
:~$ ./configure --prefix=/usr
:~$ make && sudo checkinstall
:~$ sudo service gdm restart

------------------------------------

I have been using kubuntu/ubuntu for a couple years and have 
never really had to do any compiling and I have no clue how 
or what to compile.  I did install the xorg-dev, xorg-server-dev 
and build-essential 

I figured out everything else on the post over the past couple
of days except this part....

---

### Post by everythingsround on 2010-03-08
> **tekgeek- said:**
> I tried to follow the directions on the first post for this 

but... I am confused on this part

------------------------------------
Next, compile. You will need xorg-dev and possibly xorg-server-dev as well as build-essential to compile and install this.
Code:

:~$ cd /path/to/extracted/
:~$ ./configure --prefix=/usr
:~$ make && sudo checkinstall
:~$ sudo service gdm restart

------------------------------------

....

Make sure to apt-get xorg-dev and xserver-xorg-dev
What does the console spit out when you run ./configure --prefix=/usr  ??
Did the patch appear to run successfully?

This help inform you more on compiling from a make source:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)
[http://liquidweather.net/howto/index.php?id=82](http://liquidweather.net/howto/index.php?id=82)

---

### Post by everythingsround on 2010-03-08
While I'm here:

To reply @euxneks thanks again for your help.
lsusb does give:  
Bus 008 Device 002: ID 0408:3000 Quanta Computer, Inc.
Of course I can change and have tried every usb bus/id possible on my motherboard.

A little snippet of hidDeviceDump:
> 
sudo hidDeviceDump /dev/usb/quanta_touch 
hid-device-dump 9.04.04
Send bug reports to [http://sporniket-studio.com](http://sporniket-studio.com)
Device '/dev/usb/quanta_touch' could be open : ok
Packets in a row : 6
d0042	0	d0032	0	d0047	0	d0051	0	10030	1210	10031	306	
d0042	0	d0032	0	d0047	0	d0051	1	10030	996	10031	593	
d0054	0	d0042	0	d0032	0	d0047	0	d0051	0	10030	1210	
10031	306	d0042	0	d0032	0	d0047	0	d0051	1	10030	996	
10031	593	d0054	0	d0042	0	d0032	0	d0047	0	d0051	0	
10030	1210	10031	306	d0042	0	d0032	0	d0047	0	d0051	1	
10030	996	10031	593	d0054	0	d0042	0	d0032	0	d0047	0	
d0051	0	10030	1210	10031	306	d0042	0	d0032	0	d0047	0	
d0051	1	10030	996	10031	593	d0054	0	d0042	0	d0032	0	
d0047	0	d0051	0	10030	1210	10031	306	d0042	0	d0032	0	
d0047	0	d0051	1	10030	996	10031	593	d0054	0	d0042	1	
d0032	1	d0047	1	d0051	0	10030	685	10031	257	d0042	1	
d0032	1	d0047	1	d0051	1	10030	690	10031	822	d0054	2	
d0042	1	d0032	1	d0047	1	d0051	0	10030	685	10031	257	
d0042	1	d0032	1	d0047	1	d0051	1	10030	690	10031	822	
d0054	2	d0042	1	d0032	1	d0047	1	d0051	0	10030	685	
10031	257	d0042	1	d0032	1	d0047	1	d0051	1	10030	690	


I did try these instructions:
[http://lii-enac.fr/en/projects/shareit/linux-howto.html](http://lii-enac.fr/en/projects/shareit/linux-howto.html)

Although a bit over my head I think I did everything properly up until:
> 
copy the files hid-{yourscreen}.ko and hid.ko into your OS modules, that is in //lib/modules/2.6.xxx/kernel/drivers/hid. If you don't have hid.ko, this means that hid is not configured as a module but as a static part of the kernel; you will need to change this or compile and install the whole kernel. 


Following the Kernel Git Tree it appears the touch support didn't make it in 2.6.33 but seems to getting in there for 2.6.34 (Apr.-May?be): You :guitar: Stephane!
[http://lkml.indiana.edu/hypermail/linux/kernel/1002.2/00581.html](http://lkml.indiana.edu/hypermail/linux/kernel/1002.2/00581.html)

I gave the initial post a go again with 2.6.33 just for kicks and got the same results.  I am now running 10.04 Kernel 2.6.32-15
Stuck with a good looking dump and no xorg mouse/touch functionality :-&

Anyone out there with any direction on making the hid a module and/or where to find those .ko files from ENAC's instructions? I'd even be happy to recompile the kernel if there was better instruction specific to Ubuntu.

---

### Post by petrovski77 on 2010-03-12
I managed to setup my Acer T230H under Kubuntu 9.10, yesterday evening, following the general instructions given above. My Kernel is 2.6.31-19, my system is 64-bit.

This is already impressive, thanks a lot for the integration.

Two problems remain:

I could not handle the nvidia twinview setup with the T230H on the right of my Dell Precision M4400 Maybe, I did not understand the related xorg settings. Maybe, I start with the working configuration where the T230H is on the left of my internal display.

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Acer T230H" "SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Acer T230H"
    Driver         "hidtouch"
    Option         "SendCoreEvents" "true"
    Option         "ReportingMode" "Raw"
    Option         "Device" "/dev/usb/quanta_touch"
    Option         "PacketCount" "13"
    Option         "OpcodePressure" "852034"
    Option         "OpcodeX" "65584"
    Option         "OpcodeY" "65585"
    Option         "CalibrationModel" "1"
    Option         "CornerTopLeftX" "0"
    Option         "CornerTopLeftY" "0"
    Option         "CornerTopRightX" "3840" # 1920 for 23"
    Option         "CornerTopRightY" "0"
    Option         "CornerBottomLeftX" "0"
    Option         "CornerBottomLeftY" "1200" # 1080 for 23"
    Option         "CornerBottomRightX" "3840" # 1920 for 23"
    Option         "CornerBottomRightY" "1200" # 1080 for 23"
    Option         "CornerScreenWidth" "1920" # 1920 for 23"
    Option         "CornerScreenHeight" "1080" # 1080 for 23"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Acer T230H"
    HorizSync       30.0 - 80.0
    VertRefresh     55.0 - 75.0
    Option         "DPMS"
    Option         "UseEdidDpi" "False"
    Option         "DPI" "100x100"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "Quadro FX 1700M"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option       "NoLogo" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "CRT: 1920x1080 +0+0, DFP: 1920x1200 +1920+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```Basically, the CornerTopRightX/CornerBottomRightX cover the complete width of my virtual screen. I am not sure how to adapt this so that the T230H is on the right of the internal display. Just changing 
```

    Option         "metamodes" "CRT: 1920x1080 +0+0, DFP: 1920x1200 +1920+0"

```to
```

    Option         "metamodes" "CRT: 1920x1080 +1920+0, DFP: 1920x1200 +0+0"
 
```does not suffice. The cursor will then move on the internal display  while touching on the external. Does anybody know how this could be fixed?

The second problem is that the xserver seems to hang after logging out of kde/gnome (I tried both).
Restarting kdm from the console however properly shuts down X and brings it up again.

Would be nice get into contact with somebody who also uses a twinview configuration. Most of you should work on notebooks nowadays, aren't you?

---

### Post by petrovski77 on 2010-03-12
> i have this monitor but im running 64bit ubuntu 9.10
can some one help me the driver wont work in 64bit

It works. I am running the same setup, 64-bit U/Kubuntu 9.10, please see my other posting.

---

### Post by davedumas0 on 2010-03-15
ok just did a fresh instal of ultimate edition 2.4 wich is 9.10 i think
and im going to try again

---

### Post by davedumas0 on 2010-03-15
ok im stuck at the patch part is is a kenel patch?? or what?

---

### Post by davedumas0 on 2010-03-15
ok i got everything installed but there is no touch???
mmmm

---

### Post by petrovski77 on 2010-03-18
> **davedumas0 said:**
> ok i got everything installed but there is no touch???
mmmm
Please give some more information about your setup!
Is your system updated to the latest versions?
Was there anything unclear or strange during the described setup procedure?
xorg.conf!

---

### Post by genericUserName on 2010-03-31
Edit: After checking the #xorg irc channel it appears that the undefined defines (sic) are only available in xserver-properties.h in xserver >= 1.7 and the xorg version in 9.10 is only 1.6.4, i'm now going to try the above steps in lucid.

We've recently purchased a T230H for evaluation as to use in our ePOS systems and following the instructions given at the start of this thread have failed to compile the X module.

The system the module is being compiled for is a vanilla install of the i686 9.10 with the latest updates.

From dpkg the xserver-xorg-dev, build-essential and xorg-dev packages were installed, [this](http://sourceforge.net/projects/hidtouchsuite/files/xf86-input-hidtouch/v9.04.04/xf86-input-hidtouch-9.04.04.zip/download) hidtouch package was extracted and [this](http://sourceforge.net/projects/hidtouchsuite/files/xf86-input-hidtouch/v9.04.04/xf86-input-hidtouch-9.04.04__xorg-7.zip/download) patch was applied. When make is ran the compilation fails with the following error:

```
******@****:~/hid/xf86-input-hidtouch-9.04.04$ make
make  all-recursive
#make[1]: Entering directory `/home/hnurseries/hid/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/hnurseries/hid/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function &#8216;HdtRawData__fillFromInputInfo&#8217;:
hidtouch__HdtRawData.h:38: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function &#8216;hdtOnDeviceOff&#8217;:
hidtouch__body.h:118: warning: unused variable &#8216;pDevice&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initButtons&#8217;:
hidtouch__body.h:154: error: &#8216;BTN_LABEL_PROP_BTN_LEFT&#8217; undeclared (first use in this function)
hidtouch__body.h:154: error: (Each undeclared identifier is reported only once
hidtouch__body.h:154: error: for each function it appears in.)
hidtouch__body.h:155: error: &#8216;BTN_LABEL_PROP_BTN_MIDDLE&#8217; undeclared (first use in this function)
hidtouch__body.h:156: error: &#8216;BTN_LABEL_PROP_BTN_RIGHT&#8217; undeclared (first use in this function)
hidtouch__body.h:163: warning: passing argument 3 of &#8216;InitButtonClassDeviceStruct&#8217; from incompatible pointer type
/usr/include/xorg/input.h:276: note: expected &#8216;CARD8 *&#8217; but argument is of type &#8216;Atom *&#8217;
hidtouch__body.h:163: error: too many arguments to function &#8216;InitButtonClassDeviceStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes&#8217;:
hidtouch__body.h:183: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:184: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:187: warning: passing argument 3 of &#8216;InitValuatorClassDeviceStruct&#8217; makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected &#8216;int&#8217; but argument is of type &#8216;Atom *&#8217;
hidtouch__body.h:187: error: too many arguments to function &#8216;InitValuatorClassDeviceStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes__MinMax&#8217;:
hidtouch__body.h:221: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:227: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h:230: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:236: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes__FourCorners&#8217;:
hidtouch__body.h:249: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:255: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h:258: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:264: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
In file included from hidtouch.c:71:
hidtouch__body.h:446:5: warning: "/*" within comment
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/hnurseries/hid/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/hnurseries/hid/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2


```
I think i've followed the instructions provided to the letter but I cannot figure out why those defines are undeclared. The patched hidtouch__body.h looks like this: 

```

/****
HidTouch input driver.
(c)2008 David SPORN
 ****/

/*
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 3 of the License, or
 * (at your option) any later version.
 *
 * This program is distributed in the hope that it will be useful,
 * but WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
 * GNU General Public License for more details.
 *
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA 02111-1307 USA
 */

#ifndef HIDTOUCH__BODY__H
#define HIDTOUCH__BODY__H

#include <xorg/exevents.h>
#include <xorg/xserver-properties.h>


/**** Device control event handler -- declaration ****/
static int
hdtOnDeviceInit(DeviceIntPtr device) ;

static int
hdtOnDeviceInit__initButtons(DeviceIntPtr device);

static int
hdtOnDeviceInit__initAxes(DeviceIntPtr device);

static void
hdtOnDeviceInit__initAxes__MinMax(DeviceIntPtr device, HdtDevicePtr pDevice, ScrnInfoPtr pScreen);

static void
hdtOnDeviceInit__initAxes__FourCorners(DeviceIntPtr device, HdtDevicePtr pDevice, ScrnInfoPtr pScreen);

static int
hdtOnDeviceOn(DeviceIntPtr device) ;

static int
hdtOnDeviceOff(DeviceIntPtr device) ;

static int
hdtOnDeviceClose(DeviceIntPtr device) ;

static int
hdtOnReadInput(InputInfoPtr pInfo) ;

static int
hdtOnReadInput__updatePosition(InputInfoPtr pInfo, HdtDevicePtr pDevice, HdtRawDataPtr rawData) ;

static void
hdtOnReadInput__updatePosition__MinMax(InputInfoPtr pInfo, HdtDevicePtr pDevice) ;

static void
hdtOnReadInput__updatePosition__FourCorners(InputInfoPtr pInfo, HdtDevicePtr pDevice) ;

static void
hdtOnReadInput__postMotionEvent(InputInfoPtr pInfo, int x, int y) ;

static void
hdtOnReadInput__postButtonEvent(InputInfoPtr pInfo, int x, int y, int leftButtonState) ;





/**** Device control event handler -- definition ****/
static int
hdtOnDeviceInit(DeviceIntPtr device)
{
    hdtOnDeviceInit__initButtons(device) ;
    hdtOnDeviceInit__initAxes(device) ;

    return Success;
}

static int
hdtOnDeviceOn(DeviceIntPtr device)
{
    InputInfoPtr pInfo = device->public.devicePrivate;
    HdtDevicePtr pDevice = pInfo->private;

    xf86Msg(X_INFO, "%s (%s): On.\n", pInfo->name, pDevice->myConfiguration.device);
    if (device->public.on)
    {
        xf86Msg(X_ERROR, "%s: device already open.\n", pInfo->name);
        return BadRequest;
    }

    SYSCALL(pInfo->fd = open(pDevice->myConfiguration.device, O_RDONLY | O_NONBLOCK));
    if (pInfo->fd < 0)
    {
        xf86Msg(X_ERROR, "%s: cannot open device.\n", pInfo->name);
        return BadRequest;
    }

    xf86FlushInput(pInfo->fd);
    xf86AddEnabledDevice(pInfo);
    device->public.on = TRUE;

    return Success;
}

static int
hdtOnDeviceOff(DeviceIntPtr device)
{
    InputInfoPtr pInfo = device->public.devicePrivate;
    HdtDevicePtr pDevice = pInfo->private;

    xf86Msg(X_INFO, "%s: Off.\n", pInfo->name);
    if (!device->public.on)
    {
        xf86Msg(X_ERROR, "%s: device already off.\n", pInfo->name);
        return BadRequest;
    }

    xf86RemoveEnabledDevice(pInfo);
    pInfo->fd = -1;
    device->public.on = FALSE;

    return Success;
}

static int
hdtOnDeviceClose(DeviceIntPtr device)
{
    return Success;
}


static int
hdtOnDeviceInit__initButtons(DeviceIntPtr device)
{
    InputInfoPtr        pInfo = device->public.devicePrivate;
    CARD8               *map;
    Atom                *labels;
    int                 i;
    const int           num_buttons = 3;
    int                 ret = Success;

    map = xcalloc(num_buttons, sizeof(CARD8));
    labels = xcalloc(num_buttons, sizeof(Atom));

    labels[0] = XIGetKnownProperty(BTN_LABEL_PROP_BTN_LEFT);
    labels[1] = XIGetKnownProperty(BTN_LABEL_PROP_BTN_MIDDLE);
    labels[2] = XIGetKnownProperty(BTN_LABEL_PROP_BTN_RIGHT);

    for (i = 0; i < num_buttons; i++)
    {
        map[i] = i;
    }

    if (!InitButtonClassDeviceStruct(device, num_buttons, labels, map)) {
        xf86Msg(X_ERROR, "%s: Failed to register buttons.\n", pInfo->name);
        ret = BadAlloc;
    }

    xfree(labels);
    xfree(map);
    return ret;
}

/******** Init axes section ********/

static int
hdtOnDeviceInit__initAxes(DeviceIntPtr device)
{
    InputInfoPtr pInfo = device->public.devicePrivate;
    HdtDevicePtr pDevice = pInfo->private;
    const int           num_axes = 2;

    Atom labels[num_axes];
    labels[0] = XIGetKnownProperty(BTN_LABEL_PROP_BTN_X);
    labels[1] = XIGetKnownProperty(BTN_LABEL_PROP_BTN_Y);

    if (!InitValuatorClassDeviceStruct(device,
            num_axes, labels, GetMotionHistorySize(), Absolute))
    {
        return BadAlloc;
    }

    pInfo->dev->valuator->mode = Absolute;
    if (!InitAbsoluteClassDeviceStruct(device))
    {
        return BadAlloc;
    }

    ScrnInfoPtr   pScreen = xf86Screens[0];

    switch(pDevice->myConfiguration.calibration.model)
    {
    case HDT__CONFIGURATION_VALUE__CALIBRATION__MODEL__MIN_MAX:
        hdtOnDeviceInit__initAxes__MinMax(device, pDevice, pScreen);
    	break;
    case HDT__CONFIGURATION_VALUE__CALIBRATION__MODEL__FOUR_CORNER:
    	hdtOnDeviceInit__initAxes__FourCorners(device, pDevice, pScreen);
    	break;
    default:
    	//do nothing (silently fail)
    	xf86Msg(X_ERROR, "%s: no calibration model specified, will do nothing from now...\n", pInfo->name);
    	break;

    }

    return Success;
}

static void
hdtOnDeviceInit__initAxes__MinMax(DeviceIntPtr device, HdtDevicePtr pDevice, ScrnInfoPtr pScreen)
{
    Atom xLabel = XIGetKnownProperty(BTN_LABEL_PROP_BTN_X);
    xf86InitValuatorAxisStruct(device, 0, xLabel,
            pDevice->myConfiguration.calibration.minX,
            pDevice->myConfiguration.calibration.maxX,
            pScreen->virtualX,
            0,
            pScreen->virtualX);
    xf86InitValuatorDefaults(device, 0);

    Atom yLabel = XIGetKnownProperty(BTN_LABEL_PROP_BTN_Y);
    xf86InitValuatorAxisStruct(device, 1, yLabel,
            pDevice->myConfiguration.calibration.minY,
            pDevice->myConfiguration.calibration.maxY,
            pScreen->virtualY,
            0,
            pScreen->virtualY);
    xf86InitValuatorDefaults(device, 1);

}

/*
 * In the "four corners" model, we compute screen coordinate
 * directly, thus we set up axis using
 * 0-->screenWidth and 0-->screenHeight.
 */
static void
hdtOnDeviceInit__initAxes__FourCorners(DeviceIntPtr device, HdtDevicePtr pDevice, ScrnInfoPtr pScreen)
{
    Atom xLabel = XIGetKnownProperty(BTN_LABEL_PROP_BTN_X);
    xf86InitValuatorAxisStruct(device, 0, xLabel,
            0,
            pDevice->myConfiguration.calibration.screenWidth,
            pScreen->virtualX,
            0,
            pScreen->virtualX);
    xf86InitValuatorDefaults(device, 0);

    Atom yLabel = XIGetKnownProperty(BTN_LABEL_PROP_BTN_Y);
    xf86InitValuatorAxisStruct(device, 1, yLabel,
            0,
            pDevice->myConfiguration.calibration.screenHeight,
            pScreen->virtualY,
            0,
            pScreen->virtualY);
    xf86InitValuatorDefaults(device, 1);
}

/******** Read Input section ********/

static int
hdtOnReadInput(InputInfoPtr pInfo)
{
    HdtDevicePtr pDevice = pInfo->private;

    HdtRawDataRec raw_data ;
    raw_data.pressure = -1 ;
    raw_data.x = -1 ;
    raw_data.y = -1 ;
    HdtRawData__fillFromInputInfo(&raw_data, pInfo) ;

    int has_changed = 0 ;
    hdtOnReadInput__updatePosition(pInfo, pDevice, &raw_data) ;

    if (0 != has_changed)
    {
        pDevice->myRawData.timestamp = GetTimeInMillis();
    }

    return Success ;
}

/*
 * Translate raw data into axis coordinate
 * and post event as needed
 * return >0 if raw data has changed
 */
static int
hdtOnReadInput__updatePosition(InputInfoPtr pInfo, HdtDevicePtr pDevice, HdtRawDataPtr rawData)
{
    int has_changed = 0 ;
    if ((-1 < rawData->x && rawData->x != pDevice->myRawData.x)
            || (-1 < rawData->y && rawData->y != pDevice->myRawData.y))
    {
        has_changed += 1 ;
        pDevice->myRawData.x = rawData->x ;
        pDevice->myRawData.y = rawData->y ;

        switch(pDevice->myConfiguration.calibration.model)
        {
        case HDT__CONFIGURATION_VALUE__CALIBRATION__MODEL__MIN_MAX:
        	hdtOnReadInput__updatePosition__MinMax(pInfo, pDevice);
        	break;
        case HDT__CONFIGURATION_VALUE__CALIBRATION__MODEL__FOUR_CORNER:
        	hdtOnReadInput__updatePosition__FourCorners(pInfo, pDevice);
        	break;
        default:
        	break;
        }

        hdtOnReadInput__postMotionEvent(pInfo
        		, pDevice->myTranslatedData.x
        		, pDevice->myTranslatedData.y);

    }
    if (-1 < rawData->pressure && rawData->pressure != pDevice->myRawData.pressure)
    {
        has_changed += 2 ;
        pDevice->myRawData.pressure = rawData->pressure ;
        /*no need for a special translation process*/
        pDevice->myTranslatedData.pressure = pDevice->myRawData.pressure ;
        hdtOnReadInput__postButtonEvent(pInfo
        		, pDevice->myTranslatedData.x
        		, pDevice->myTranslatedData.y
        		, pDevice->myTranslatedData.pressure);
    }

    return has_changed ;
}

static void
hdtOnReadInput__updatePosition__MinMax(InputInfoPtr pInfo, HdtDevicePtr pDevice)
{
    /*no need for a special translation process*/
    pDevice->myTranslatedData.x = pDevice->myRawData.x ;
    pDevice->myTranslatedData.y = pDevice->myRawData.y ;
}

static void
hdtOnReadInput__updatePosition__FourCorners(InputInfoPtr pInfo, HdtDevicePtr pDevice)
{
    /*Use fishnet locator*/
    pDevice->myTranslatedData.x =
    	HdtFishNetLocator__locateHorizontalPosition(&(pDevice->myLocator)
    			,FixedPoint8__new(pDevice->myRawData.x)
    			,FixedPoint8__new(pDevice->myRawData.y)
    			,HDT__FISH_NET_LOCATOR__STEP_COUNT_FOR_LOCATE) ;
    pDevice->myTranslatedData.y =
    HdtFishNetLocator__locateVerticalPosition(&(pDevice->myLocator)
			,FixedPoint8__new(pDevice->myRawData.x)
			,FixedPoint8__new(pDevice->myRawData.y)
			,HDT__FISH_NET_LOCATOR__STEP_COUNT_FOR_LOCATE) ;
    /*
    xf86Msg(X_INFO, "Position : %i, %i.\n",
                    pDevice->myTranslatedData.x, pDevice->myTranslatedData.y);
    */

}

static void
hdtOnReadInput__supportXrandr(InputInfoPtr pInfo, int* pX, int* pY)
{
    HdtDevicePtr pDevice = pInfo->private;
    HdtConfigurationRec configuration = pDevice->myConfiguration ;

    /* skip if min_max model */
    if (HDT__CONFIGURATION_VALUE__CALIBRATION__MODEL__MIN_MAX == configuration.calibration.model)
    {
    	return ;
    }

	ScrnInfoPtr   pScreenInfo = xf86Screens[0];
	ScreenPtr pScreen = pScreenInfo->pScreen ;
	Rotation rotation = xf86GetRotation(pScreen) ;

	int _hard_width = configuration.calibration.screenWidth ;
	int _hard_height = configuration.calibration.screenHeight ;
	int x = (*pX) ;
	int y = (*pY) ;

	/*
    xf86Msg(X_INFO, "Rotation : %i among %i, %i, %i, %i.\n",
    		rotation, RR_Rotate_0, RR_Rotate_90, RR_Rotate_180, RR_Rotate_270);
	*//*
	 * TODO: find how to get the current rotation !
	 */
	switch(rotation)
	{
	case RR_Rotate_0:
		break;
	case RR_Rotate_90:
	{
		fp8 tempy = FixedPoint8__new(_hard_width - x) ;
		tempy = FixedPoint8__div(tempy, FixedPoint8__new(_hard_width)) ;
		tempy *= (fp8) _hard_height ;
		fp8 tempx = FixedPoint8__new(y) ;
		tempx = FixedPoint8__div(tempx, FixedPoint8__new(_hard_height)) ;
		tempx *= (fp8) _hard_width ;
		*pX = FixedPoint8__toInt(tempx) ;
		*pY = FixedPoint8__toInt(tempy) ;
	}
		break;
	case RR_Rotate_180:
	{
		*pX = _hard_width - x ;
		*pY = _hard_height - y ;
	}
		break;
	case RR_Rotate_270:
	{
		fp8 tempy = FixedPoint8__new(x) ;
		tempy = FixedPoint8__div(tempy, FixedPoint8__new(_hard_width)) ;
		tempy *= (fp8) _hard_height ;
		fp8 tempx = FixedPoint8__new(_hard_height - y) ;
		tempx = FixedPoint8__div(tempx, FixedPoint8__new(_hard_height)) ;
		tempx *= (fp8) _hard_width ;
		*pX = FixedPoint8__toInt(tempx) ;
		*pY = FixedPoint8__toInt(tempy) ;
	}
		break;
	default:
		/*do nothing*/
		break;
	}
}

static void
hdtOnReadInput__postMotionEvent(InputInfoPtr pInfo, int x, int y)
{
	int trans_x = x ;
	int trans_y = y ;
	hdtOnReadInput__supportXrandr(pInfo, &trans_x, &trans_y);

    /* /
    xf86Msg(X_INFO, "Position : %i, %i ==> %i, %i.\n",
                    x, y, trans_x, trans_y);
    /* */
	xf86PostMotionEvent(pInfo->dev, 1
            , 0, 2
            , trans_x, trans_y);
}

static void
hdtOnReadInput__postButtonEvent(InputInfoPtr pInfo, int x, int y, int leftButtonState)
{
	int trans_x = x ;
	int trans_y = y ;
	hdtOnReadInput__supportXrandr(pInfo, &trans_x, &trans_y);

    xf86PostButtonEvent(pInfo->dev, 1, HDT__BUTTON_EVENT__LEFT_BUTTON
            ,leftButtonState ,0, 2
            ,trans_x, trans_y) ;

}



#endif /** ifndef HIDTOUCH__BODY__H **/

```

If someone who has this working could compare their version of this file to my own that might help us narrow down the problem.

Thanks in advance

---

### Post by genericUserName on 2010-04-01
Okay, I now have a (sorta) working touchscreen using 10.4 and a patched hidtouch driver - the remaining issue is that in order to get the touchscreen functioning one finger must be placed stationary on the screen while the other is used to click buttons etc. If anyone knows how to make it so that the monitor works correctly for single touch it would be much appreciated.

---

### Post by genemk on 2010-04-04
Edit: OK, I got the touchscreen working. The problem I had (and probably genericUserName had) is that we used the patch from [http://sourceforge.net/projects/hidtouchsuite/files/xf86-input-hidtouch/v9.04.04/xf86-input-hidtouch-9.04.04__xorg-7.zip/download](http://sourceforge.net/projects/hidtouchsuite/files/xf86-input-hidtouch/v9.04.04/xf86-input-hidtouch-9.04.04__xorg-7.zip/download) instead of using the patch the original poster attached at the end of his first post. Once I started in a fresh directory and used the correct patch things went smoothly.

Thanks so much for taking the time to explain the process. 

I'm leaving original post below in case it is useful for other people.

######################################################################

Hi, I'm having same problem running the make command. Lots of undefined constants leading to error.

I'm stuck using Ubuntu 9.10 for a product. It has all the most recent updates like the original poster said. Sounds like some issues are resolved by upgrading to Lucid, but if other posters have gotten it working on 9.10 I'd like to know how to do that as well. I am trying to get the HP Compaq L2105tm touchscreen working.

I created the 99-touchscreen.rules file.

The patch seemed to work fine. I ran command below as advised in README file that came with patch. Does location of extracted directory matter? I have it in my home area.

~/touchscreen/xf86-input-hidtouch-9.04.04$ patch -Np1 <xf86-input-hidtouch-9.04.04_xorg_7.patch

The make execution and output are pasted below. Any advice is really appreciated. Let me know if I can help with any additional information about my system.

I'm running kernel 2.6.31-20-generic.

//////////////////////////////////////////////////////
~/touchscreen/xf86-input-hidtouch-9.04.04$ make && sudo checkinstall
make  all-recursive
make[1]: Entering directory `/home/gene/touchscreen/xf86-input-hidtouch-9.04.04'
Making all in src
make[2]: Entering directory `/home/gene/touchscreen/xf86-input-hidtouch-9.04.04/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..    -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c -o hidtouch_drv_la-hidtouch.lo `test -f 'hidtouch.c' || echo './'`hidtouch.c
 gcc -DHAVE_CONFIG_H -I. -I.. -Wall -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT hidtouch_drv_la-hidtouch.lo -MD -MP -MF .deps/hidtouch_drv_la-hidtouch.Tpo -c hidtouch.c  -fPIC -DPIC -o .libs/hidtouch_drv_la-hidtouch.o
In file included from hidtouch.c:66:
hidtouch__HdtRawData.h: In function &#8216;HdtRawData__fillFromInputInfo&#8217;:
hidtouch__HdtRawData.h:38: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
In file included from hidtouch.c:71:
hidtouch__body.h: In function &#8216;hdtOnDeviceOff&#8217;:
hidtouch__body.h:117: warning: unused variable &#8216;pDevice&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initButtons&#8217;:
hidtouch__body.h:153: error: &#8216;BTN_LABEL_PROP_BTN_LEFT&#8217; undeclared (first use in this function)
hidtouch__body.h:153: error: (Each undeclared identifier is reported only once
hidtouch__body.h:153: error: for each function it appears in.)
hidtouch__body.h:154: error: &#8216;BTN_LABEL_PROP_BTN_MIDDLE&#8217; undeclared (first use in this function)
hidtouch__body.h:155: error: &#8216;BTN_LABEL_PROP_BTN_RIGHT&#8217; undeclared (first use in this function)
hidtouch__body.h:162: warning: passing argument 3 of &#8216;InitButtonClassDeviceStruct&#8217; from incompatible pointer type
/usr/include/xorg/input.h:276: note: expected &#8216;CARD8 *&#8217; but argument is of type &#8216;Atom *&#8217;
hidtouch__body.h:162: error: too many arguments to function &#8216;InitButtonClassDeviceStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes&#8217;:
hidtouch__body.h:182: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:183: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:186: warning: passing argument 3 of &#8216;InitValuatorClassDeviceStruct&#8217; makes integer from pointer without a cast
/usr/include/xorg/input.h:281: note: expected &#8216;int&#8217; but argument is of type &#8216;Atom *&#8217;
hidtouch__body.h:186: error: too many arguments to function &#8216;InitValuatorClassDeviceStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes__MinMax&#8217;:
hidtouch__body.h:220: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:226: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h:229: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:235: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h: In function &#8216;hdtOnDeviceInit__initAxes__FourCorners&#8217;:
hidtouch__body.h:248: error: &#8216;BTN_LABEL_PROP_BTN_X&#8217; undeclared (first use in this function)
hidtouch__body.h:254: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
hidtouch__body.h:257: error: &#8216;BTN_LABEL_PROP_BTN_Y&#8217; undeclared (first use in this function)
hidtouch__body.h:263: error: too many arguments to function &#8216;xf86InitValuatorAxisStruct&#8217;
In file included from hidtouch.c:71:
hidtouch__body.h:445:5: warning: "/*" within comment
make[2]: *** [hidtouch_drv_la-hidtouch.lo] Error 1
make[2]: Leaving directory `/home/gene/touchscreen/xf86-input-hidtouch-9.04.04/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gene/touchscreen/xf86-input-hidtouch-9.04.04'
make: *** [all] Error 2
//////////////////////////////////////////////////////////////////////

---

### Post by lightnb on 2010-04-26
I'm also confused by this part:

> Next, grab the xf86-input-hidtouch module from the HidTouch Site on SF.net and apply the attached patch which I took from here:
[http://wiki.debian.org/InstallingDeb...l/OneTwo/Lenny](http://wiki.debian.org/InstallingDeb...l/OneTwo/Lenny)
If you don't know how to apply patches, check out this page:
[http://www.linuxhq.com/patch-howto.html](http://www.linuxhq.com/patch-howto.html)

Go to the parent folder of the extracted hidtouch tarball to apply the patch successfully.

I don't have an hidtouch tarball,.. I have a patch file, and a zip archive with another patch file inside it. Am I supposed to get source code from somewhere? And am I using just one of the patch files, or both?

---

### Post by quadra on 2010-05-17
To all of you having trouble in Ubuntu 10.04: Better check this slightly modified version: [http://ubuntuforums.org/showthread.php?t=1462536]("http://ubuntuforums.org/showthread.php?t=1462536")

---

### Post by luopio on 2010-06-07
We've had success with the HID raw -method but in hopes of making the touchscreen a bit more usable (less cursor jumping, etc.), we're now playing with the evdev driver.

We have xubuntu 10.04 and so far we've:

1. updated include/linux/hid.h & compiled and replaced hid.ko
2. gotten the xf86-input-evdev from git, compiled and installed

dmesg says:
```
quanta-touch 0003:0408:3000.0005: hiddev96,hidraw3: USB HID v1.10 Device [Acer T230H] on usb-0000:00:1d.0-1/input0
```

Xorg.0.log has no mention of quanta

$ sudo cat /dev/hidraw3 produces a lot of garbage, which is of course good :)

any pointers greatly appreciated! do we need xorg.conf or something?

will write definitive howto if this works!

---

### Post by luopio on 2010-06-07
Installing a new kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb) solves the issue and we have working touchscreen that works A LOT better than the hidtouch-driver.

Multitouchd still claims: 
> $ ./multitouchd 
Error: no multitouch devices found.

So we don't have multitouch, which would be really, really nice.

Tips?

---

### Post by euxneks on 2010-06-07
> **luopio said:**
> Installing a new kernel from [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.34-rc7-lucid/linux-image-2.6.34-020634rc7-generic_2.6.34-020634rc7_i386.deb) solves the issue and we have working touchscreen that works A LOT better than the hidtouch-driver.

Multitouchd still claims: 


So we don't have multitouch, which would be really, really nice.

Tips?

If you have the T230H, it's technically not really a multitouch, but can only mimic some certain two fingered gestures. I'm not sure if that would be recognized on the linux software side as multitouch :\

---

### Post by pcgirl on 2010-08-07
I have no idea what to do with all this information - I feel like I've come in half way through a conversation.  Can anyone help me to install the T230h on Ubuntu 10.x?  I'm totally confused. I'm newish to this type of operating system, but am a quick learner. :)

Thanks all.

Mandy :p

---

### Post by EToreo on 2010-08-13
Hey guys,
Thanks for the great information.  I tried to install the drivers and follow the directions that the OP had and I am seeing the issue where the first touch does not register, but the second gives the correct X events.

When I tried:
 lshal -u /org/freedesktop/Hal/devices/usb_device_408_3000_noserial_if0_hiddev | grep "hiddev.product"

Instead of seeing this:
 hiddev.product = 'Acer T230H'   (string)

I get blank output.

That is probably because  /org/freedesktop/Hal/devices/usb_device_408_3000_noserial_if0_hiddev is not listed as a device in the output of lshal.  When I run:
 lshal | grep Acer

I get the output:
  info.product = 'Acer T230H'  (string)
  input.product = 'Acer T230H'  (string)

I noticed that it lacks the "hiddev." string and think this could be the problem.  Is there a way to add my Acer T230H to the system so that lshal reports it correctly?

Any other advice would be greatly appreciated.

Thank you,
~Eric

---

### Post by thejeswi.nk on 2010-11-07
For those who still haven't figured out how to get their touchscreen running; Just go ahead and install the latest Linux Kernel which has native touch support.
You can find instructions [here]("http://www.ramoonus.nl/2010/05/linux-kernel-2-6-34-installation-guide-for-ubuntu-linux-10-04/").

I finally got my Acer T231H Touch Screen running on Ubuntu.
Thanks Ubuntu Forums :KS

---

