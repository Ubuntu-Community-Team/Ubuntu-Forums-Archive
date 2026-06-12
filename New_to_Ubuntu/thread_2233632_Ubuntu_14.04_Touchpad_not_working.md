---
title: "Ubuntu 14.04 Touchpad not working"
date: 2014-07-09
forum: New to Ubuntu
---

### Post by Gregor_s on 2014-07-09
Hi, 
I have Ubuntu 14.04 installed and the system does not recognize Synaptics SMBus TouchPad. 
What should I do?

xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=10	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; USB2.0 HD UVC WebCam                    	id=11	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=12	[slave  keyboard (3)]

---

### Post by ubudog on 2014-07-09
Hi,

Try this:
```
sudo apt-get install xserver-xorg-input-synaptics

```

---

### Post by Gregor_s on 2014-07-10
I tried and got this:

xserver-xorg-input-synaptics is already the newest version.

---

### Post by ubudog on 2014-07-10
Is this a fresh install of Ubuntu, or an upgrade from a previous version?

---

### Post by Gregor_s on 2014-07-17
This is a fresh install - dual boot. Touchpad is working on windows 8.

---

### Post by ubudog on 2014-07-17
What is the model of your computer?  Also, can you post the output of:
```

cat /proc/bus/input/devices

```

---

### Post by Gregor_s on 2014-07-21
Model: MEDION AKOYA E7226

code: cat /proc/bus/input/devices

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
U: Uniq=
H: Handlers=kbd event0 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input1
U: Uniq=
H: Handlers=kbd event1 
B: PROP=0
B: EV=3
B: KEY=4000 0 0

I: Bus=0019 Vendor=0000 Product=0005 Version=0000
N: Name="Lid Switch"
P: Phys=PNP0C0D/button/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input2
U: Uniq=
H: Handlers=event2 
B: PROP=0
B: EV=21
B: SW=1

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button"
P: Phys=LNXPWRBN/button/input0
S: Sysfs=/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3
U: Uniq=
H: Handlers=kbd event3 
B: PROP=0
B: EV=3
B: KEY=10000000000000 0

I: Bus=0011 Vendor=0001 Product=0001 Version=ab83
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/devices/platform/i8042/serio0/input/input4
U: Uniq=
H: Handlers=sysrq kbd event4 
B: PROP=0
B: EV=120013
B: KEY=402000000 3803078f800d001 feffffdfffefffff fffffffffffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c046 Version=0110
N: Name="Logitech USB Optical Mouse"
P: Phys=usb-0000:00:14.0-1/input0
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1:1.0/input/input5
U: Uniq=
H: Handlers=mouse0 event5 
B: PROP=0
B: EV=17
B: KEY=ff0000 0 0 0 0
B: REL=143
B: MSC=10

I: Bus=0003 Vendor=04f2 Product=b3a3 Version=5465
N: Name="USB2.0 HD UVC WebCam"
P: Phys=usb-0000:00:14.0-4.3/button
S: Sysfs=/devices/pci0000:00/0000:00:14.0/usb1/1-4/1-4.3/1-4.3:1.0/input/input6
U: Uniq=
H: Handlers=kbd event6 
B: PROP=0
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0006 Version=0000
N: Name="Video Bus"
P: Phys=LNXVIDEO/video/input0
S: Sysfs=/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input7
U: Uniq=
H: Handlers=kbd event7 
B: PROP=0
B: EV=3
B: KEY=3e000b00000000 0 0 0

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH HDMI/DP,pcm=3"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
U: Uniq=
H: Handlers=event8 
B: PROP=0
B: EV=21
B: SW=140

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Headphone"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
U: Uniq=
H: Handlers=event9 
B: PROP=0
B: EV=21
B: SW=4

I: Bus=0000 Vendor=0000 Product=0000 Version=0000
N: Name="HDA Intel PCH Mic"
P: Phys=ALSA
S: Sysfs=/devices/pci0000:00/0000:00:1b.0/sound/card0/input8
U: Uniq=
H: Handlers=event10 
B: PROP=0
B: EV=21
B: SW=10

---

### Post by ubudog on 2014-07-21
The only thing I could find is this:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1302103](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1302103)

What kernel are you using?
```
uname -r
```

Sorry I haven't been of much assistance.

---

### Post by Gregor_s on 2014-07-27
Thanks for your help, looks like it's a bug and I'll have to wait a bit.

PS: kernel version is 3.13.0-32-generic

---

### Post by fg811 on 2014-08-21
Gregor, I have exactly the same problem, the same system config. 

Did you find a solution in the meantime?

ubudog, any news?

---

### Post by fred34 on 2014-09-01
Same problem,  3.13.0-35-generic.

External mouse works fine, but the track pad is dead.

---

### Post by zvisha on 2014-09-23
I have same issue.
After installing and compiling driver I see following when I move finger over it:

 dmesg | grep -i touch
[ 9119.364806] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.389146] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.415591] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.441420] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.467035] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.731333] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
[ 9119.754198] psmouse serio4: Touchpad at isa0060/serio4/input0 lost sync at byte 6
....

I found that some patches were released for specific models:
[https://bugzilla.kernel.org/show_bug.cgi?id=48161](https://bugzilla.kernel.org/show_bug.cgi?id=48161)

but I guess no patch for this model yet.

---

### Post by eddy6 on 2014-12-17
Hi...I'm having the same troubles on the same laptop (medion akoya E7226)...the last thing i tried is version 14.10 (kernel 3.16.0-23)...no changes :-( The kernel simply doesn't see the trackpad. Windows 8.1 indicates that it is a synaptics SMbus touchpad plugged into PS/2 mouseport but Ubuntu doesn't detects anything :-( This trackpad has little tp-off-symbol with a led in the left upper corner, if you tap it in windows, the tochpad is disabled an the led turns on, tap it again and it toggles back to enabled (led off), perhaps, by default, there is no power on the tochpad and therefore Ubuntu doesn't see it?

---

### Post by gary51 on 2014-12-25
> **eddy6 said:**
> Hi...I'm having the same troubles on the same laptop (medion akoya E7226)...the last thing i tried is version 14.10 (kernel 3.16.0-23)...no changes :-( The kernel simply doesn't see the trackpad. Windows 8.1 indicates that it is a synaptics SMbus touchpad plugged into PS/2 mouseport but Ubuntu doesn't detects anything :-( This trackpad has little tp-off-symbol with a led in the left upper corner, if you tap it in windows, the tochpad is disabled an the led turns on, tap it again and it toggles back to enabled (led off), perhaps, by default, there is no power on the tochpad and therefore Ubuntu doesn't see it?

I've a new laptop with a synaptics SMBus touchpad. At first it would not work (latest Ubuntu as at Dec2014), but another post suggested
```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

After a reboot and a apt-get update the touchpad works. 

I'm not sure if SMBus touchpad is a generic term, but this one has no separate buttons - they are part of the touchpad. The generic ubuntu driver does not handle this correctly and the pad is utterly unusable (when you click it treats it as a tap and moves the cursor). So I've revered to Windoze until I can find a solution.

---

### Post by Richard Menke on 2015-04-01
I'm just copy pasting this from askubuntu.com. But it worked for me on a Medion E7227.

You have to add "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" to the kernel boot options. You can do this permanently by adding these arguments to the "GRUB_CMDLINE_LINUX_DEFAULT" attribute in the file /etc/default/grub. Then it looks like this.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```

After that you just need to enter this command and reboot:

```
sudo update-grub
```

With thanks to cakelover from askubuntu.com

---

### Post by mytien on 2015-04-09
Is this a fresh install of Ubuntu, or an upgrade from a previous version?? help, please!

---

### Post by David_Zafra_Gmez on 2015-05-27
I had a similar problem and I've fixed it.
I recommend you to visit [https://wiki.ubuntu.com/DebuggingTouchpadDetection](https://wiki.ubuntu.com/DebuggingTouchpadDetection) and follow this instructions carefully. Be patient. I filled a [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1437755") against the kernel, then I was redirected to [Linux Kernel Upstream developers mailing list]("http://www.spinics.net/lists/linux-input/msg38000.html"). They provided me a patch form my kernel, I applied it, I built a patched kernel and... it worked! I'm very very grateful to them.

Long live free software community!

---

### Post by mattharris4 on 2015-05-28
> **gary51 said:**
> I've a new laptop with a synaptics SMBus touchpad. At first it would not work (latest Ubuntu as at Dec2014), but another post suggested
```

sudo modprobe -r psmouse
sudo modprobe psmouse proto=imps
```

After a reboot and a apt-get update the touchpad works.

I'm not sure if SMBus touchpad is a generic term, but this one has no separate buttons - they are part of the touchpad. The generic ubuntu driver does not handle this correctly and the pad is utterly unusable (when you click it treats it as a tap and moves the cursor). So I've revered to Windoze until I can find a solution.
  
I know this is an old post but the instructions fixed the touchpad on my Toshiba C55D-A5163 laptop.  In my case the touchpad works now and is usable (although in general I am not a fan of touchpads anyway -- but they do come in handy if you are using a laptop on your lap and not at a table).

---

### Post by carbm1 on 2015-06-15
This also fixed my Lenovo x131e on Lubuntu 14.04.2.

---

### Post by risacher on 2015-10-14
For what it's worth, my daughter brought me her laptop with a complaint that the touchpad wasn't working, (fortunately this laptop also has a touchscreen, and thus was still usable.)  After fussing with it for a few minutes, I realized that the touchpad was working at the login screen.  From there I deduced that it was a problem with just her account.

So...  in System settings/Mouse & Touchpad, the touchpad was disabled.  Problem solved.

---

### Post by rrawze on 2015-12-17
> **ubudog said:**
> Hi,

Try this:
```
sudo apt-get install xserver-xorg-input-synaptics

```

I used...
 apt-get install --reinstall xserver-xorg-input-synaptics 

and it fixed mine. I have an ASUS G751 laptop with the ETPS/2 Elantech Touchpad

---

### Post by lokesh4 on 2016-01-23
I have a problem of Touch pad not working in ubuntu 14.04.
Its working fine in windows 8.1(ubuntu as a dual boot)
Its working fine as a external mouse.
I checked xinput devices list
kernel is detecting the mouse as Synaptics Touchpad.
And i tried sudo apt-get install xserver-xorg-input-synaptics
but there is no positive result.
My laptop kernel version is 3.13.0-32-generic.
Please help me...

---

### Post by sanjay9 on 2016-02-26
i have the same problem .....touch pad not working anyone has a solution ???

---

### Post by allan758 on 2016-10-12
>  I'm just copy pasting this from askubuntu.com. But it worked for me on a Medion E7227.

You have to add "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" to  the kernel boot options. You can do this permanently by adding these  arguments to the "GRUB_CMDLINE_LINUX_DEFAULT" attribute in the file  /etc/default/grub. Then it looks like this.

 	Code:
 	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop" 




I know it's an old post, but big thanks for this Richard - worked perfectly with my Medion Akoya E6239 (running 16.04)

---

### Post by joejoethejoe on 2016-12-10
Tried bunch off stuff and in the end this worked for me :)

> **Richard Menke said:**
> I'm just copy pasting this from askubuntu.com. But it worked for me on a Medion E7227.

You have to add "i8042.reset i8042.nomux i8042.nopnp i8042.noloop" to the kernel boot options. You can do this permanently by adding these arguments to the "GRUB_CMDLINE_LINUX_DEFAULT" attribute in the file /etc/default/grub. Then it looks like this.

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset i8042.nomux i8042.nopnp i8042.noloop"
```

After that you just need to enter this command and reboot:

```
sudo update-grub
```

With thanks to cakelover from askubuntu.com

---

