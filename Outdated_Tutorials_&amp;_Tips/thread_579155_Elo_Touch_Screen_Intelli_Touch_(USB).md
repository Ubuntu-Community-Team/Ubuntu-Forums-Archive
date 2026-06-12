---
title: "Elo Touch Screen Intelli Touch (USB)"
date: 2007-10-18
forum: Outdated Tutorials &amp; Tips
---

### Post by chuy_max on 2007-10-18
First of all, this should work for touch screen monitors with IntelliTouch (Surface Acoustic Wave) technology, and hopefully other monitors.

[www.elotouch.com](www.elotouch.com) offers you precompiled binaries for their monitors, unfortunately they just work for kernels <= 2.6.17. If you want them to compile for a special kernel/distro for you, they will charge you just a few $1,500 bucks (Hell no!, monitors I bought were expensive enough). I've found an open source driver called evtouch that works great in my PC (I'm using USB), so, let's begin.

**1.-Sources, and an incomplete tutorial can be found here:**
[http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html]("http://stz-softwaretechnik.com/~ke/touchscreen/evtouch.html")

Basic installation is copied from the website, but added my monitor's right values for xorg.conf, and udev-rules so the right events are triggered.

**2.-The specs of the monitor I used, plus my PC specs:**

[LIST]
[*]Elo Touch Screen monitor with IntelliTouch (Surface Acoustic Wave). Model 1939L, I used USB although monitor also has Serial interface.
[*]Linux ubuntu 2.6.20-16-generic #2 SMP Sun Sep 23 19:50:39 UTC 2007 i686 GNU/Linux
[*]Ubuntu 7.04 Feisty Fawn
[*]CPU: Intel P4 3Ghz with HT
[/LIST]

**3.-Why this guide?**
This guide is meant to help people install touch screen monitors that use IntelliTouch technology (Surface Acoustic Wave), hopefully, other technologies will also work, although I don't have the hardware to test it. This guide was also meant to complement the source's website, as it lacked right values for Elo Touch monitor, and tutorial didn't mention udev-rules, which are needed to set the right handlers for the linux kernel.

**4.-Things you need:**
I used the precompiled binaries, you can find them in the website I mentioned in the first point. The latest at the time I'm writing this is: 

_Precompiled driver for X V0.8.7_

Also, you will need to copy udev-rules, the file you need can be found also in the same website, inside a sources tarball:

_X driver sources V0.8.4_

**5.-Installation**
Download precompiled binaries.

```
tar -zxvf evtouch-0.8.7.tar.gz
cd evtouch-0.8.7
sudo cp evtouch_drv.so /usr/lib/xorg/modules/input/
```

Open /etc/X11/xorg.conf and add this lines:

```
Section "InputDevice"
    Identifier "touchscreen"
    Driver "evtouch"
    Option "Device" "/dev/input/evtouch_event"
    Option "DeviceName" "touchscreen"
    Option "MinX" "4095"
    Option "MinY" "4095"
    Option "MaxX" "0"
    Option "MaxY" "0"
    Option "ReportingMode" "Raw"
    Option "Emulate3Buttons"
    Option "Emulate3Timeout" "50"
    Option "SendCoreEvents" "On"
EndSection

Section "InputDevice"
    Identifier "dummy"
    Driver "void"
    Option "Device" "/dev/input/mice"
EndSection
```

If Min/Max values don't work correctly for you, you'll have to adjust that values manually (calibration application doesn't work, the author of the sources himself has stated that, at least at the writing of this how to).

Now search for "ServerLayout" section in the same file, and add this lines just before EndSection

```

	InputDevice     "touchscreen"   "CorePointer"
	InputDevice 	"dummy" 
```

Note that Section "InputDevice" with Identifier "dummy" and InputDevice "dummy" are only needed if you use xorg > 7.2.

Next, you have to find your monitors name:

```
cat /proc/bus/input/devices
```

you'll get something like this:

```
I: Bus=0003 Vendor=04e7 Product=0020 Version=0100
N: Name=**"Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface"**
P: Phys=usb-0000:00:10.1-1/input0
S: Sysfs=/class/input/input2
H: Handlers=js0 event2
B: EV=b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3
```

Next, you have to add udev-rules to your system, download and extract "X driver sources V0.8.4":

```
tar -jxvf xf86-input-evtouch-0.8.4.tar.bz2
cd xf86-input-evtouch-0.8.4
```

Modify 69-touchscreen.rules file for your monitor, check the bold letters (or if you are using the same monitor as me, I will paste my file for you):

```
# Evtouch udev.rules
#
# Because Evtouch can't autoprobe devices we assume that we only
# Have one device so we can make it like this :P
#
# List here your touchscreen, check if it works  and send it to rpms_AT_ilmi_DOT_fi
# Name can be found in /proc/bus/input/devices (In console make command 'cat /proc/bus/input/devices')
#
# Tested on Telepeak  Model 800-Y-Y-V (http://www.telepeak.com). Should work on most eGalax based stuff!
KERNEL=="event*", SUBSYSTEM=="input", ATTRS{name}==**"Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface"**, SYMLINK+="input/evtouch_event"
#
# This could be also like this (eGalax Inc. USB TouchController)
# KERNEL=="event*", SUBSYSTEM=="input", ATTRS{idVendor}=="0eef", ATTRS{idProduct}=="0001", SYMLINK+="input/evtouch_event"
#
```

Now, copy the file to /etc/udev/rules.d/

That should be it, restart your system, and it should work.

---

### Post by buntu92104 on 2007-11-15
Ubuntu 7.10 comes with the elographics driver.  There's no need to download any drivers.  For my ELO serial touch screen I only had to add the following to /etc/X11/xorg.conf.   Then do ctrl-alt-backspace to restart the X server.

```

Section "InputDevice"
        Identifier "Touchscreen"
        Driver     "elographics"
        Option     "Device"     "/dev/ttyS1"
        Option     "AlwaysCore"
        Option     "screeno"    "0"
        Option     "MinX" "4024"
        Option     "MaxX" "-18"
        Option     "MinY" "4026"
        Option     "MaxY" "23"
        Option     "UntouchDelay" "3"
        Option     "ReportDelay" "1"
EndSection

```

In the Section "ServerLayout" add the line:

```

        InputDevice     "Touchscreen"

```

You'll have to figure out the correct calibration numbers for you screen (MaximumXPosition, etc).

To determine which port my touchscreen was connected to I just did
```
cat < /dev/ttyS1
``` and then moved my finger across the screen.  If the cat spit out a bunch of garbage I figured it was the correct port.

---

### Post by Ralphie on 2007-11-27
*deleted*

---

### Post by nicolas1 on 2007-12-03
Hello there,
  I have a trouble make ELO touchscreen (USB) work under Ubuntu 7.10 . I have tried solution provided here, but ubuntu can not start after modification of xorg.conf . Error message is : "The greeter application appears to be crashing. Attemting to use a different one". :(

Thanks

---

### Post by durand on 2007-12-04
I don't have a clue what this is about but nicolas1, you should post your xorg.conf.

When the greeter crashes, let it disable itself. Then press Ctrl + Alt + F1 and type your username and password. Then you can edit the /etc/X11/xorg.conf file.

X will load with bulletproof x configuration, then you can edit your file and upload them here.

---

### Post by nicolas1 on 2007-12-04
Hi,
xconf file is same as after installation of ubuntu 7.10 with modification according to evtouch instruction. I tried evtouch binary 0.8.7.
  Also how is it possible to use "ubuntu 7.10" elographics.so driver with usb touchscreen, how xconf must be modified?

---

### Post by durand on 2007-12-05
I'm sorry nicolas1 but I don't actually know anything about this. You can try sending a message to the original poster, chuy_max

---

### Post by chuy_max on 2008-01-04
> **nicolas1 said:**
> Hi,
xconf file is same as after installation of ubuntu 7.10 with modification according to evtouch instruction. I tried evtouch binary 0.8.7.
  Also how is it possible to use "ubuntu 7.10" elographics.so driver with usb touchscreen, how xconf must be modified?

Post xorg.conf and error logs, you can find the logs in /var/log, maybe Xorg.0.log, but check others as well to look for useful messages.

buntu92104: Can you please post your monitor model?, I couldn't make mine work with that specific driver. There is one official driver from ELO but it works for old kernels <= 2.6.17, and as you know, feisty has a newer kernel, however, I tried it in dapper and it worked great.

---

### Post by nicolas1 on 2008-01-09
Thanks, it works fine now!
Problem was my mistake.
By the way, how to run calibration program? What software packets are required to do it?

---

### Post by stoodleysnow on 2008-01-19
Hello
I have an Edge10 TS700 Touchscreen monitor and am wondering how to make it work in Ubuntu. Urgently. This is for a friend whose OS choice may well depend on this screen working!:-O

---

### Post by paterjbayliss on 2008-02-08
ok, this might sound like a stupid question... But how do you get permissions to save changed to the xorg.conf file? Sorry, complete newbie here :)

---

### Post by durand on 2008-02-09
In the terminal, type sudo gedit /etc/X11/xorg.conf. The key command here is sudo..It grants admin permissions to anyone in the /etc/sudoers file, which the first user that you created will be in.

---

### Post by rastaxe on 2008-02-12
Hi, I have to install a TouchScreen on Ubuntu Gutsy. I have downloaded the driver on elo website and the readme file says: "Elo Linux USB Driver package contains native Linux drivers designed for Linux kernel 2.4.18 and later..."

I have read also your posts and now I don't know what I do. The proprietary driver works on Gutsy or not?

I hope that you can help me for my installation problem. 

PS. My touchscreen is an Open frame 12 R12T600-OFL1.
PPS. Sorry for my english!

---

### Post by rastaxe on 2008-02-12
I'm trying to follow your post, but when I type this command:
cat /proc/bus/input/devices

I get an output that I don't understand (which is my monitor?). 
I attach my response.
Someone can help me?

Thanks!

---

### Post by Kriss.no on 2008-02-20
*You'll have to figure out the correct calibration numbers for you screen (MaximumXPosition, etc).*

How do I find this info? Going mad here atm, my Elo Accutouch works with the config you provided, but not as it shoul because the lack of correct calibration numbers. How di I determine the correct ones?

---

### Post by agisman on 2008-03-19
Hi everyone,

I know this thread has been open a long time but it seems like there has been some recent activity so I'll give it a shot.  I'm using a Jetway J7F5 mini-itx main board with 1Gb RAM and a 1.5GHz processor.

This is going to be a media server that uses a 15" Intellitouch touchscreen in a black walnut case.  Video is driven using the Via drivers for the unichrome chipset and they are working great with openGL and other acceleration.  The problems I'm having are with the touchscreen.

This is an ELO1545L.  It is a USB controlled surface acoustic wave touchscreen.  The controller is the 2500U which is the predecessor to the 2700.  I am running 7.10 (gutsy) and have been trying all different versions of possible drivers.  I have tried the ones from Via, the Unified USB drivers, elographics, elousb, and evtouch v0.8.6 and v0.8.7.  I have been running Ubuntu on an older computer for over a year now but this is the first time I've gotten into the terminal heavily to compile scripts and run make so please bear with me.

As with other people, the USB event changed every time I rebooted.  I modified /etc/udev/rules.d/65-persistent-input.rules to create a static reference to the monitor.  I labeled it touch2500.  When I "cat /dev/input/touch2500" I get random data when I touch the screen.  Sometimes it even messes up the text on the terminal so that I have to close terminal and re-open a new one.  I have been chasing this problem for a few weeks and having all sorts of luck crashing X and using the other VCs. /var/log/Xorg.0.log has been a big bit of fun.  Maybe there are some who would suggest editing the C code for one of these drivers.   I would really prefer not to because it's been about 4 years since I last wrote C and assembly.  The closest it's gotten to working is with the evtouch driver v0.8.7.  After compiling it (instructions were wrong), I can end up with no errors in Xorg log.  Whenever I touch the screen, the cursor jumps to one location and does not move.  Only the mouse will move it from that location. 

Here are the relevant sections from my xorg.conf:

> 
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier "touchscreen"
#	Driver "elo"
#	Driver "elographics"
	Driver "evtouch"
#	Option "debuglevel" "5"
	Option "Device" "/dev/input/touch2500"
	Option "DeviceName" "touchscreen"
#	Option "screeno" "0"
	Option "MinX" "98"
	Option "MaxX" "940"
	Option "MinY" "43"
	Option "MaxY" "925"
	Option "ReportingMode" "Raw"
	Option "Emulate3Buttons"
#	Option "UntouchDelay" "3"
#	Option "ReportDelay" "1"
	Option "Emulate3Timeout" "50"
	Option "SendCoreEvents" "On"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice 	"touchscreen"	"CorePointer"
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode 0666
	Group 0
EndSection




Please confirm that I have the persistent input done correctly.  It's not in the USB section but the system still recognizes the device when I cat the touch2500 input.

Here is my persistent input rule file: /etc/udev/rules.d/65-persistent-input.rules

> ACTION!="add", GOTO="persistent_input_end"
SUBSYSTEM!="input", GOTO="persistent_input_end"
KERNEL=="input[0-9]*", GOTO="persistent_input_end"

# usb devices
SUBSYSTEMS=="usb", IMPORT{program}="usb_id --export"
SUBSYSTEMS=="usb", ATTRS{bInterfaceClass}=="03", ATTRS{bInterfaceProtocol}=="01", ENV{ID_CLASS}="kbd"
SUBSYSTEMS=="usb", ATTRS{bInterfaceClass}=="03", ATTRS{bInterfaceProtocol}=="02", ENV{ID_CLASS}="mouse"

# other devices
DRIVERS=="pcspkr", ENV{ID_CLASS}="spkr"
DRIVERS=="atkbd", ENV{ID_CLASS}="kbd"
DRIVERS=="psmouse", ENV{ID_CLASS}="mouse"
ATTRS{name}=="*dvb*|*DVB*|* IR *", ENV{ID_CLASS}="ir"
ATTRS{modalias}=="input:*-*a[068],*|input:*-*a*,[68],*m*", ATTRS{modalias}!="input:*-*k*14A,*r*", ENV{ID_CLASS}="joystick"
ATTRS{name}=="Elo TouchSystems, Inc. Elo TouchSystems IntelliTouch 2500U", SYMLINK=="input/touch2500"

# fill empty serial number
ENV{ID_CLASS}=="?*", ENV{ID_SERIAL}=="", ENV{ID_SERIAL}="noserial"

# by-id links
KERNEL=="mouse*|js*", ENV{ID_BUS}=="?*", ENV{ID_CLASS}=="?*", SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-$env{ID_CLASS}"
KERNEL=="event*", ENV{ID_BUS}=="?*", ENV{ID_CLASS}=="?*", SYMLINK+="input/by-id/$env{ID_BUS}-$env{ID_SERIAL}-event-$env{ID_CLASS}"

# by-path
IMPORT{program}="path_id %p"
ENV{ID_PATH}=="?*", KERNEL=="mouse*|js*", SYMLINK+="input/by-path/$env{ID_PATH}-$env{ID_CLASS}"
ENV{ID_PATH}=="?*", KERNEL=="event*", SYMLINK+="input/by-path/$env{ID_PATH}-event-$env{ID_CLASS}"

LABEL="persistent_input_end"


As for the output of the Xorg.0.log.  I'll just append the items dealing with touch as well as warnings and errors.  Just piped through grep.

> less /var/log/Xorg.0.log | grep touch

(**) |-->Input Device "touchscreen"
(WW) Duplicate core pointer devices.  Removing core pointer attribute from "touchscreen"
(II) LoadModule: "evtouch"
(II) Loading /usr/lib/xorg/modules/input//evtouch_drv.so
(II) Module evtouch: vendor="Kenan Esau"
(**) Option "DeviceName" "touchscreen"
(**) touchscreen: always reports core events
(II) XINPUT: Adding extended input device "touchscreen" (type: TOUCHSCREEN)
(**) Option "Device" "/dev/input/touch2500"
(EE) touchscreen: Unable to grab device (Invalid argument).


"less /var/log/Xorg.0.log | grep EE" doesn't reveal anything more than those errors. 

The last thing that may be of interest is the output of lsmod for any usb devices.  There is no output for "lsmod | grep touch" or "lsmod | grep input".  Not that I thought there should be, but had no way of knowing whether evtouch would be properly loaded.

> lsmod | grep usb
usbhid                 29536  0 
hid                    28928  1 usbhid
usbcore               138632  5 usbhid,xpad,ehci_hcd,uhci_hcd



Wow! This is a lot of information.  I am really looking forward to being able to install the media programs I want and start populating it with media.  My friend has talked me down from the edge a couple of times when I considered switching to Windows.  If anybody could help get me pointed in the right directions I would really appreciate it.  I'm getting frustrated trying to compile XFree86 drivers and drivers for old kernels etc etc.

All my thanks in advance for any guidance and support.


Cheers!

---

### Post by freesftwr on 2008-05-02
Hi guys,

Thanks for posting the instruction.  After about a week of trying etc.., first with G-Vision touch LCD and it did not work. Actually, I tried this instruction for G-Vision, too, but some how I did not get it to work, may be I was not familiar with touch screen and driver setup on Ubuntu in generall.  Now that I get ELO to work, I think I might be able to get G-Vision to work; but I no longer have the monitor since I have already returned it.

After trying out G-Vision with no luck, I ordered an ELO IntelliTouch since this post said it works with ELO IntelliTouch.  Initially, I tried to download the driver from elotouch; followed their instruction and could not get their driver to work.  I then called their Tech Support, and they were not of any help either nor do they wanted to deal with LINUX support at all.  I would boycott them if I can get another vendor who is willing to support Ubuntu natively.  In any case, I followed the instruction on this post, and it worked like a champ.  The only thing that I had to do is to swap the Min and Max values for the Axes.  Logout and Log back in and viola every thing seems to be working fine.

Regards,

-Hay

---

### Post by frefly on 2008-05-08
agisman,
How about your status now?
I encountered the same issue:
          (EE) touchscreen: Unable to grab device (Invalid argument). 
Have you fixed this?

---

### Post by ZepoL~ on 2008-05-23
Hi, I would like some help.  I'm pretty new to Ubuntu.  Following the instructions I was able to get the touch screen to work, but the mouse moves backwards to what I move.  I go up, it goes down, I go right, it goes left.  I'm sure this is something easy.  Can anyone help?  I tried to compile the driver on the Elo site, but compiling is a little over my head at this time.  Thanks in advance for all your help!  I'm running 7.10.

---

### Post by patrick9999 on 2008-05-27
hi from france,

i just install elotouch 1515L USB, but i can't calibrate screen

OS : ubuntu hardy 8.04
drivers : 
hardy@ibm:~$ less /var/log/Xorg.0.log | grep elo
(II) LoadModule: "elographics"
(II) Loading /usr/lib/xorg/modules/input//elographics_drv.so
(II) Module elographics: vendor="X.Org Foundation"

working correctly, but when i start ./elova -u from :

[http://www.elotouch.com/Support/Downloads/dnld.asp#linux](http://www.elotouch.com/Support/Downloads/dnld.asp#linux)

Unified_USB_Driver.tar.gz
(140K) 	3.0

i can see the first "target" for calibrate, but no action when i press screen, and after i have this message :

hardy@ibm:/elo$ sudo ./elova -u
Timeout!!!!..Run the Calibration program again
To get back to the command prompt, touch the screen..!!


thanks you for your help !

---

### Post by patrick9999 on 2008-05-28
i call the technical support today, we can't use ubuntu 8.04 at this moment, only 7.10, i re-install all,and now i have same probs with unified usb driver 3.0 : 

```
gutsy@ibm-gutsy:~/Unified_USB_Driver/elousbctrl-src$ make

make -C /lib/modules/2.6.22-14-generic/build M=/home/gutsy/Unified_USB_Driver/elousbctrl-src modules
make[1]: entrant dans le répertoire « /usr/src/linux-headers-2.6.22-14-generic »
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /home/gutsy/Unified_USB_Driver/elousbctrl-src/.smartset.o.cmd for /home/gutsy/Unified_USB_Driver/elousbctrl-src/smartset.o
WARNING: modpost: GPL-incompatible module elousb.ko uses future GPL-only symbol 'usb_deregister'
WARNING: modpost: GPL-incompatible module elousb.ko uses future GPL-only symbol 'usb_register_driver'
make[1]: quittant le répertoire « /usr/src/linux-headers-2.6.22-14-generic »

gutsy@ibm-gutsy:~/Unified_USB_Driver/elousbctrl-src$ 


Xorg.conf :

Section "InputDevice"
           Identifier "elo"
           Driver "elo"
           Option "Device" "/dev/input/js0"
           Option "AlwaysCore"
#	Option "debuglevel" "5"
#	Option "screeno" "0"
#	Option "MinX" "4096"
#	Option "MaxX" "0"
#	Option "MinY" "4096"
#	Option "MaxY" "0"
#	Option "ReportingMode" "Raw"
#	Option "Emulate3Buttons"
#	Option "UntouchDelay" "3"
#	Option "ReportDelay" "1"
#	Option "Emulate3Timeout" "50"
	Option "SendCoreEvents" "On"
EndSection



gutsy@ibm-gutsy:~/Unified_USB_Driver/elousbctrl-src$ less /var/log/Xorg.0.log | grep elo

(**) |-->Input Device "elo"
(II) LoadModule: "elo"
(II) Loading /usr/lib/xorg/modules/input//elo_drv.so
(II) Module elo: vendor="X.Org Foundation"
(II) XINPUT: Adding extended input device "TOUCHSCREEN" (type: elo TouchScreen)
elo touchscreen on. local->fd ffffffff..

gutsy@ibm-gutsy:~/Unified_USB_Driver/elousbctrl-src$ cat /proc/bus/input/devices

I: Bus=0003 Vendor=04e7 Product=0020 Version=0100
N: Name="Elo TouchSystems, Inc. Elo TouchSystems 2700 IntelliTouch(r) USB Touchmonitor Interface"
P: Phys=usb-0000:00:1d.1-1/input0
S: Sysfs=/class/input/input4
U: Uniq=20000000
H: Handlers=event4 js0 
B: EV=b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3

gutsy@ibm-gutsy:~/Unified_USB_Driver/elousbctrl-src$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 04e7:0020 Elo TouchSystems 
Bus 002 Device 001: ID 0000:0000 

```

---

### Post by ZepoL~ on 2008-06-26
I figured out the problem I was having, which brought on more.  So I will share all of my problems and solutions.  Everything is working perfectly at the moment minus 1 small issue.  I reversed the #'s on the Y axis #'s that solved the issue that I posted above.  

Originally I used the Min an Max #'s that was posted in this tutorial b/c they seemed to be a close fit to my monitor, but the farther I would move out from the center the worse it would get.  I tried running the calibration, but it would error. I didn't understand the error, but a friend showed me what all of the lines meant.  The error that would call out is that the file "empty_cursor.xbm" was not in the root.  I copied the file there and ran the calibration with no errors.  After that the out.txt file contains the correct Min and Max #'s for you to input to the "xorg.conf" file.  If you need help running the calibration read the readme on it, it was pretty self explanatory.  If you want me to post the procedure I will not mind.  That's all I needed to do for 7.10.

8.04
I upgraded to 8.04 and the touchscreen was no longer functioning correctly.  I found a post in the bug reports about adding one line "Option "MoveLimit" "2"" to the xorg.conf file.  On the report the guy said start at a # < 50.  There was reported success for using Option "MoveLimit" "1", but for me 2 works the best.  I also adjusted my xorg.conf file to look more like the file on this page:  [http://www.mythtv.org/wiki/index.php/Zalman_HD160XT](http://www.mythtv.org/wiki/index.php/Zalman_HD160XT)  it made more sense to me.

So now it is currently working on both 7.10 and 8.04

The small issue that I'm having is that if you turn the monitor off and turn it back on when you come back the touch pointer is all messed up.  If you log out and log back in it is fine, if someone can help solve that one that would be great.

---

### Post by cybagorilla on 2008-08-01
Hi
I'm trying to install an Elo TouchSystems 2216 AccuTouch on an Ubuntu 8.04.
I picked many informations from several tutorials and forums to make a correct xorg.conf configuration. I connected the touchscreen with its USB interface, and i'm using the evtouch driver rather than elographics drivers that does not seems to work at all, nor the kernel module "elo" that does not works neither...

Here is my correct xorg.conf :

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "fr"
        Option          "XkbVariant"    "oss"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

#Virtual Device "touchscreen" defined by udev rule in /etc/udec/rules.d
Section "InputDevice"
        Identifier      "touchscreen"
        Driver          "evtouch"
        Option          "device"        "/dev/input/event3"
#       Option          "device"        "/dev/input/touchscreen"
        Option          "MinX"          "550"
        Option          "MinY"          "700"
        Option          "MaxX"          "3400"
        Option          "MaxY"          "3350"
        Option          "MoveLimit"     "1"
        Option          "sendCoreEvents"        "On"
        Option          "SwapY" "On"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        screen          "Default Screen"
        InputDevice     "touchscreen"   "SendCoreEvents"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

I took pretty time to set the MinX MaxX MinY MaxY options, by trying values and restarting gdm until i got a quite acceptable calibration, but now it works great.
It seems that the "movelimit" option is necesssary under Ubuntu 8.04, and i had to dig Xorg.conf man to discover the SwapY option :)

I only have 2 bugs left, that i'd like to fix :


1) I got a black screen EACH TIME i log off a gnome session. It seems to be a bug in the ati driver fglrx. I read somewhere that i had to choose between using the open driver with lesser graphics, or .. never login out :) i hope someone has a better solution ! I tried adding AlwaysRestartServer=true in gdm.conf-custom with no success, and setting sync settings in my xorg.conf screen settings ...with no success. Tell me if you have found something for this bug. Till i find something better, i just switch to console, then switch back to X with Ctrl+Alt+F1 then Alt+F7. Or sudo invoke-rc.d gdm restart when i feel brutal :p


2) The device selection of the touchscreen inputdevice section fails if i change usb connections... It's logical, the /dev/input/eventx depends of the order i plug usb devices ...

I tried to fix this with a udev rule. Here is the /proc/bus/input/device entry for my screen :

```
I: Bus=0003 Vendor=04e7 Product=0050 Version=0100
N: Name="EloTouchSystems,Inc Elo TouchSystems 2216 AccuTouch&#65533; USB Touchmonitor Interface"
P: Phys=usb-0000:00:0b.0-4/input0
S: Sysfs=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3
U: Uniq=50U70445
H: Handlers=mouse1 event3 js0 
B: EV=1b
B: KEY=10000 0 0 0 0 0 0 0 0
B: ABS=100 3
B: MSC=10
```

As there is a bad displayed character in the device name, i used its vender / product id to set my udev rule. Here is my /etc/udev/rules.d/10-touchscreen.rules :

```
SUBSYSTEM=="input", KERNEL=="event*", ATTRS{IdVendor}=="04e7", ATTRS{IdProduct}=="0050", SYMLINK+="input/touchscreen"
```

Of course i corrected the xorg.conf with inverting the commented lines

```

#       Option          "device"        "/dev/input/event3"
        Option          "device"        "/dev/input/touchscreen"
```

It seems to be well seen by udev, but xorg fails to use the Symlink...
I have a pretty udev log :

```

UDEV  [1217603885.959244] add      /devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3/js0 (input)
UDEV_LOG=3
ACTION=add
DEVPATH=/devices/pci0000:00/0000:00:0b.0/usb1/1-4/1-4:1.0/input/input3/js0
SUBSYSTEM=input
MAJOR=13
MINOR=0
SEQNUM=2685
UDEVD_EVENT=1
ID_VENDOR=EloTouchSystems,Inc
ID_MODEL=Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface
ID_REVISION=0100
ID_SERIAL=EloTouchSystems,Inc_Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface_50U70445
ID_SERIAL_SHORT=50U70445
ID_TYPE=hid
ID_BUS=usb
ID_CLASS=joystick
ID_PATH=pci-0000:00:0b.0-usb-0:4:1.0
DEVNAME=/dev/input/js0
DEVLINKS=/dev/input/by-id/usb-EloTouchSystems_Inc_Elo_TouchSystems_2216_AccuTouch_USB_Touchmonitor_Interface_50U70445-joystick /dev/input/by-path/pci-0000:00:0b.0-usb-0:4:1.0-joystick
```

And my Xorg.0.log :

```

(II) evaluating device (Generic Keyboard)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(II) evaluating device (Configured Mouse)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) evaluating device (EVTouch TouchScreen)
(II) XINPUT: Adding extended input device "EVTouch TouchScreen" (type: TOUCHSCREEN)
(--) Configured Mouse: PnP-detected protocol: "ExplorerPS/2"
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(**) Option "Device" "/dev/input/touchscreen"
(EE) xf86OpenSerial: Cannot open device /dev/input/touchscreen
        No such file or directory.
(WW) EVTouch TouchScreen: cannot open input device
couldn't enable device 4
SetClientVersion: 0 9
Warning: LookupDrawable()/SecurityLookupDrawable() are deprecated.  Please convert your driver/module to use dixLookupDrawable().
Receive 3D performance mode message with status: 00000001
```

Any suggestions ? i just don't understand why Xorg does not wants to use the device via Symlink whereas it's okay when setting the current /dev/intput/event ...

I hope i gave usefull informations, and thanks for helping !

---

### Post by Daisybodo on 2008-11-07
Hi!

I'm trying to make a touchscreen work on Ubuntu 8.04.
Unified_USB_Driver_v3.1 is the driver I'd like to use. On 7.10 it was OK with v3.0.

But on 8.04 I've got this message :

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  6 17:03:09 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) module ABI major version (0) doesn't match the server's version (2)
(EE) **Failed to load module "elo" (module requirement mismatch, 0)**
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) No Input driver matching `elo'


When I try :
od -w8 -d </dev/input/elo"
Everything is ok, I mean when I touch the screen I can see the coordinates X,Y



Do you see what could be my problem?

In the past I tried with evtouch, it was difficult to calibrate (I have to find a solution where anybody could calibrate the touchscreen).


Thank you

---

### Post by IntuitiveNipple on 2008-11-20
Debian/Ubuntu already includes an [Xorg input driver](http://packages.ubuntu.com/search?keywords=xserver-xorg-input-elographics&searchon=names&suite=all&section=all) for many ELO touch-screens. I've created an [Ubuntu Wiki article on how to install and configure it](https://help.ubuntu.com/community/EloTouchScreen).

---

### Post by Daisybodo on 2008-11-20
Hi, thanks for reply.

The problem is that we use something like 100 touchscreens a year, and I'm not the one who calibrate (it's people who don't know computing at all).

"Calibration

Manual calibration is required. It is a case of repeatedly changing the minimum and maximum X and Y axis values in xorg.conf, restarting and testing. An alternative is to build and then run touchcal from a non-X terminal to determine minimum and maximum values to use in xorg.conf. "

That's a big problem, that's why I use elo driver with "elova -u" for calibration.

---

### Post by prsmk on 2009-04-02
> **Daisybodo said:**
> Hi!

I'm trying to make a touchscreen work on Ubuntu 8.04.
Unified_USB_Driver_v3.1 is the driver I'd like to use. On 7.10 it was OK with v3.0.

But on 8.04 I've got this message :

(==) Log file: "/var/log/Xorg.0.log", Time: Thu Nov  6 17:03:09 2008
(==) Using config file: "/etc/X11/xorg.conf"
(EE) module ABI major version (0) doesn't match the server's version (2)
(EE) **Failed to load module "elo" (module requirement mismatch, 0)**
(II) Module "ddc" already built-in
(II) Module "i2c" already built-in
(II) Module "ramdac" already built-in
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
(EE) No Input driver matching `elo'


When I try :
od -w8 -d </dev/input/elo"
Everything is ok, I mean when I touch the screen I can see the coordinates X,Y



Do you see what could be my problem?

In the past I tried with evtouch, it was difficult to calibrate (I have to find a solution where anybody could calibrate the touchscreen).


Thank you


It looks like you are using the wrong version of the elo_drv.so file for the X Windows interface. Xorg is complaining that you are trying to load a module compiled for older version of Xserver.

Check your X server version (> X -version) and choose the proper binary file (example: elo_drv.so_1.4 for Xserver 1.4). Check the driver's readme.txt file for detailed instructions.


The Elo Touchsystems website also has compiled binary drivers for Ubuntu 8.04 (x86 32 bit only)and other Linux distributions that you can download and install. Download the driver that suits your kernel version.

[http://www.elotouch.com/Support/Downloads/privacy.asp?page=Linux/dnld_linux.asp](http://www.elotouch.com/Support/Downloads/privacy.asp?page=Linux/dnld_linux.asp)

If you cannot find a matching driver in the binary driver section try the Unified Drivers on the main download page.

[http://www.elotouch.com/Support/Downloads/dnld.asp](http://www.elotouch.com/Support/Downloads/dnld.asp)


Hope this helps.

---

### Post by Noob Programmer on 2009-04-23
I am unable to 'make' ./elousb.ko because the make command can't find .smartset.o.cmd.

Can anyone help me find a way past this? I'm using Ubuntu 9.04.

This is the error I get:

```
make -C /lib/modules/2.6.28-11-generic/build M=/elo/bin-usb/elousbctrl-src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /elo/bin-usb/elousbctrl-src/main.o
/elo/bin-usb/elousbctrl-src/main.c: In function &#8216;urb_completion_irq&#8217;:
/elo/bin-usb/elousbctrl-src/main.c:660: warning: the address of &#8216;elocontrol_XlateTouch&#8217; will always evaluate as &#8216;true&#8217;
  SHIPPED /elo/bin-usb/elousbctrl-src/smartset.o
  SHIPPED /elo/bin-usb/elousbctrl-src/mousemode.o
  SHIPPED /elo/bin-usb/elousbctrl-src/eloconfig.o
  SHIPPED /elo/bin-usb/elousbctrl-src/serial.o
  SHIPPED /elo/bin-usb/elousbctrl-src/usbcomm.o
  LD [M]  /elo/bin-usb/elousbctrl-src/elousb.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /elo/bin-usb/elousbctrl-src/.smartset.o.cmd for /elo/bin-usb/elousbctrl-src/smartset.o
FATAL: modpost: GPL-incompatible module elousb.ko uses GPL-only symbol 'usb_buffer_alloc'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
```

---

### Post by prsmk on 2009-04-24
> **Noob Programmer said:**
> I am unable to 'make' ./elousb.ko because the make command can't find .smartset.o.cmd.

Can anyone help me find a way past this? I'm using Ubuntu 9.04.

This is the error I get:

```
make -C /lib/modules/2.6.28-11-generic/build M=/elo/bin-usb/elousbctrl-src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CC [M]  /elo/bin-usb/elousbctrl-src/main.o
/elo/bin-usb/elousbctrl-src/main.c: In function ‘urb_completion_irq’:
/elo/bin-usb/elousbctrl-src/main.c:660: warning: the address of ‘elocontrol_XlateTouch’ will always evaluate as ‘true’
  SHIPPED /elo/bin-usb/elousbctrl-src/smartset.o
  SHIPPED /elo/bin-usb/elousbctrl-src/mousemode.o
  SHIPPED /elo/bin-usb/elousbctrl-src/eloconfig.o
  SHIPPED /elo/bin-usb/elousbctrl-src/serial.o
  SHIPPED /elo/bin-usb/elousbctrl-src/usbcomm.o
  LD [M]  /elo/bin-usb/elousbctrl-src/elousb.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: could not find /elo/bin-usb/elousbctrl-src/.smartset.o.cmd for /elo/bin-usb/elousbctrl-src/smartset.o
FATAL: modpost: GPL-incompatible module elousb.ko uses GPL-only symbol 'usb_buffer_alloc'
make[2]: *** [__modpost] Error 1
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [default] Error 2
```

_________________________________________________________________

It looks like you are using Elo's kernel driver that has proprietary license (non GPL). See error below.  

**FATAL: modpost: GPL-incompatible module elousb.ko uses GPL-only symbol 'usb_buffer_alloc'**

Non GPL USB drivers are not allowed in the kernel beyond 2.6.25 and hence the error. You cannot use this driver with Ubuntu 9.04.

Contact Elo's Tech support and request a driver for Ubuntu 9.04 (2.6.28-11-generic) distribution.   

[http://www.elotouch.com/Forms/Support/tech_sup_us.asp](http://www.elotouch.com/Forms/Support/tech_sup_us.asp)

Hope this helps.

________________________________________________________________

---

### Post by smaclean on 2009-09-04
Try using the Elo with the serial connection rather than the USB. I had loads of toruble with the USB calibration, etc...  When you use the serial connection, you don't need to worry about the event handler changing every reboot. If you board only has the one com port, then you know it connects to ttyS0 every time.

I am using an Elo 1515L with LTSP thin terminals, works like a charm.

---

### Post by smaclean on 2009-09-04
Thought posting my xorg.conf file might help, here ya go. The calibration numbers there aren't perfect, but they are as good as I could get in the amount of time I wanted to spend trying to calibrate it.

```

Section "ServerLayout"
        Identifier      "DefaultLayout"
        InputDevice     "TouchScreen"   "SendCoreEvents"
EndSection

Section "InputDevice"
       Identifier  "TouchScreen"
       Driver      "elographics"
       Option      "Device"           "/dev/ttyS0"
       Option      "DeviceName"       "Elo"
#       Option     "SwapXY"
#       Option     "SwapX"
       Option      "MaxX"             "3588"
       Option      "MinX"             "433"
       Option      "MaxY"             "3526"
       Option      "MinY"             "569"
       Option      "UntouchDelay"     "5"
       Option      "ReportDelay"      "5"
       Option      "AlwaysCore"


```

---

