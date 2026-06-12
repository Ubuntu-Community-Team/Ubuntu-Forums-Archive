---
title: "Change com port name"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by somf on 2011-10-03
I have just started using Ubuntu and have had great success until now.  I am trying to use a marine navigation program under wine, it installed fine but when I try to interface the gps I am stuck. The program only gives options to connect through coms 1 thru 15 but Ubuntu lists the usb to serial port as USB0. I have confirmed that the data from the GPS is being sent by using the serial port terminal so now I just need a way for the Nav program to see this port. Any ideas???

---

### Post by matt_symes on 2011-10-03
Hi

Can you add a symlink using a udev rule. Will that work ? I have no idea if it will but it's a thought...

Kind regards

---

### Post by somf on 2011-10-03
As I am totally new to Ubuntu I have yet to learn the command lines. Your sugestion would likely work but I don't even know where to start changing rules.

---

### Post by matt_symes on 2011-10-03
Hi

Lets try a udev rule then. If it does not work we can try something else.

Plug the serial device into the usb port.

The first thing we need to do is gather information about the device. You say it's called USB0. Is this the device name under the /dev directory ?

Open a terminal and from the command line 

```
ls /dev/USB0
```

If it is then we need to use udevadm to gather information about the device.

```
udevadm info -a -p  $(udevadm info -q path -n /dev/USB0)
```

Post the results back here if /dev/USB0 is the device name. Let's see what that gives us.

Kind regards

---

### Post by somf on 2011-10-03
I tried the code and got the following response. I rechecked the serial terminal and the name was actually ttyusb0 so I tried that with no luck. Copy of response>
jerry@SOMFNAV:~$ ls /dev/USB0
ls: cannot access /dev/USB0: No such file or directory
jerry@SOMFNAV:~$ ls /dev/usb0
ls: cannot access /dev/usb0: No such file or directory
jerry@SOMFNAV:~$ ls /dev/ttyusb0
ls: cannot access /dev/ttyusb0: No such file or directory
jerry@SOMFNAV:~$

---

### Post by matt_symes on 2011-10-04
Hi

Sorry for the delay. Timezones can be a pain. 

Are you sure the device is not called ttyUSB0. Linux is case sensitive and we need the device name.
 
Try this.

1. Open a terminal.
2. Plug the device in. 
3. Wait 10 seconds for the device to be recgonised
4. In the terminal type

```
dmesg | tail -n15
```

5. Post the results back here.

Kind regards

---

### Post by somf on 2011-10-04
Matt, thanks for the help. I think I am going to enjoy this OS. You are right, it is ttyUSB0 when I find it in Serial terminal. Anyway here are the results from the command:
jerry@SOMFNAV:~$ dmesg | tail -n15
[   13.578997] [drm] size 5185536
[   13.578998] [drm] fb depth is 24
[   13.579000] [drm]    pitch is 5760
[   13.594721] fbcon: radeondrmfb (fb0) is primary device
[   13.594908] Console: switching to colour frame buffer device 128x48
[   13.594916] fb0: radeondrmfb frame buffer device
[   13.594918] drm: registered panic notifier
[   13.594928] [drm] Initialized radeon 2.8.0 20080528 for 0000:01:00.0 on minor 0
[   14.010043] i2c i2c-3: readbytes: ack/nak timeout
[   14.010107] [drm:radeon_dvi_detect] *ERROR* DVI-I-1: probed a monitor but no|invalid EDID
[   17.694605] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro,commit=0
[   21.600016] eth0: no IPv6 routers present
[   22.476205] EXT4-fs (sdc1): re-mounted. Opts: errors=remount-ro,commit=0
[   62.023912] UDF-fs: Partition marked readonly; forcing readonly mount
[   62.053808] UDF-fs INFO UDF: Mounting volume 'Maptech_Charts', timestamp 2011/10/03 12:02 (1e98)
jerry@SOMFNAV:~$

---

### Post by matt_symes on 2011-10-04
Hi

So 

```
ls /dev/ttyUSB0 
```does not say file not found ?

If that's the case then post the results of (with the device plugged in)
[FONT=monospace]
[/FONT]```
udevadm info -a -p  $(udevadm info -q path -n /dev/ttyUSB0)
```BTW: Please use code tags when you post the results back.

You post between code tags like this.

[noparse] ```
 results from udevadm info -a -p  $(udevadm info -q path -n /dev/ttyUSB0) 
``` [/noparse]

and you will get this

```
 results from udevadm info -a -p  $(udevadm info -q path -n /dev/ttyUSB0) 
```which is much easier to read.

Kind regards

---

### Post by somf on 2011-10-04
Here is the results for the codes,
```
 jerry@SOMFNAV:~$ ls /dev/ttyUSB0
/dev/ttyUSB0

```and ```
jerry@SOMFNAV:~$ udevadm info -a -p  $(udevadm info -q path -n /dev/ttyUSB0)

Udevadm info starts with the device specified by the devpath and then
walks up the chain of parent devices. It prints for every device
found, all possible attributes in the udev rules key format.
A rule to match, can be composed by the attributes of the device
and the attributes from one single parent device.

  looking at device '/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/ttyUSB0/tty/ttyUSB0':
    KERNEL=="ttyUSB0"
    SUBSYSTEM=="tty"
    DRIVER==""

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0/ttyUSB0':
    KERNELS=="ttyUSB0"
    SUBSYSTEMS=="usb-serial"
    DRIVERS=="pl2303"
    ATTRS{port_number}=="0"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-2/2-2:1.0':
    KERNELS=="2-2:1.0"
    SUBSYSTEMS=="usb"
    DRIVERS=="pl2303"
    ATTRS{bInterfaceNumber}=="00"
    ATTRS{bAlternateSetting}==" 0"
    ATTRS{bNumEndpoints}=="03"
    ATTRS{bInterfaceClass}=="ff"
    ATTRS{bInterfaceSubClass}=="00"
    ATTRS{bInterfaceProtocol}=="00"
    ATTRS{supports_autosuspend}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2/2-2':
    KERNELS=="2-2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="a0"
    ATTRS{bMaxPower}=="100mA"
    ATTRS{urbnum}=="512648"
    ATTRS{idVendor}=="067b"
    ATTRS{idProduct}=="2303"
    ATTRS{bcdDevice}=="0400"
    ATTRS{bDeviceClass}=="00"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="2"
    ATTRS{devpath}=="2"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="0"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Prolific Technology Inc. "
    ATTRS{product}=="USB-Serial Controller D"

  looking at parent device '/devices/pci0000:00/0000:00:02.0/usb2':
    KERNELS=="usb2"
    SUBSYSTEMS=="usb"
    DRIVERS=="usb"
    ATTRS{configuration}==""
    ATTRS{bNumInterfaces}==" 1"
    ATTRS{bConfigurationValue}=="1"
    ATTRS{bmAttributes}=="e0"
    ATTRS{bMaxPower}=="  0mA"
    ATTRS{urbnum}=="53"
    ATTRS{idVendor}=="1d6b"
    ATTRS{idProduct}=="0001"
    ATTRS{bcdDevice}=="0206"
    ATTRS{bDeviceClass}=="09"
    ATTRS{bDeviceSubClass}=="00"
    ATTRS{bDeviceProtocol}=="00"
    ATTRS{bNumConfigurations}=="1"
    ATTRS{bMaxPacketSize0}=="64"
    ATTRS{speed}=="12"
    ATTRS{busnum}=="2"
    ATTRS{devnum}=="1"
    ATTRS{devpath}=="0"
    ATTRS{version}==" 1.10"
    ATTRS{maxchild}=="10"
    ATTRS{quirks}=="0x0"
    ATTRS{avoid_reset_quirk}=="0"
    ATTRS{authorized}=="1"
    ATTRS{manufacturer}=="Linux 2.6.38-11-generic ohci_hcd"
    ATTRS{product}=="OHCI Host Controller"
    ATTRS{serial}=="0000:00:02.0"
    ATTRS{authorized_default}=="1"

  looking at parent device '/devices/pci0000:00/0000:00:02.0':
    KERNELS=="0000:00:02.0"
    SUBSYSTEMS=="pci"
    DRIVERS=="ohci_hcd"
    ATTRS{vendor}=="0x10de"
    ATTRS{device}=="0x005a"
    ATTRS{subsystem_vendor}=="0x1297"
    ATTRS{subsystem_device}=="0x5036"
    ATTRS{class}=="0x0c0310"
    ATTRS{irq}=="20"
    ATTRS{local_cpus}=="00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001"
    ATTRS{local_cpulist}=="0"
    ATTRS{numa_node}=="0"
    ATTRS{dma_mask_bits}=="32"
    ATTRS{consistent_dma_mask_bits}=="32"
    ATTRS{broken_parity_status}=="0"
    ATTRS{msi_bus}==""

  looking at parent device '/devices/pci0000:00':
    KERNELS=="pci0000:00"
    SUBSYSTEMS==""
    DRIVERS==""


```

---

### Post by matt_symes on 2011-10-04
Hi

Remove the usb-serial device.

Open a terminal and type

```
sudo nano /etc/udev/rules.d/usb-serial.rules
```Enter your password. It will not be echoed to the screen.

Copy and paste (or type) this into it

```
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="0001", SYMLINK+="COM1", MODE="0660"
```Press ctrl + o to save and ctrl + x to exit nano.

Restart udev just to be safe.

```
sudo service udev restart
```Plug the usb-serial device back in and wait five seconds.

```
ls /dev/COM*
```

Does that show a device at /dev/COM1 ?

Kind regards

---

### Post by somf on 2011-10-04
Matt, doesn't seem to be there yet.
```
jerry@SOMFNAV:~$ ls /dev/COM*
ls: cannot access /dev/COM*: No such file or directory
jerry@SOMFNAV:~$ 

```

---

### Post by matt_symes on 2011-10-04
Hi

Give me an hour and i will check to see what i have missed. It has been a while since i created a udev rule.

Kind regards

---

### Post by matt_symes on 2011-10-04
Hi

Sorry. My mistake...

Unplug device

```
sudo nano /etc/udev/rules.d/usb-serial.rules
```Change the rules as highlighted below.

```
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="[COLOR=Red]2303[/COLOR]", SYMLINK+="COM1", MODE="0660"
```Save file and then restart udev

```
sudo service udev restart
```Plug device back in, wait 5 seconds then

```
ls -l /dev/COM*
```Hopefully that will work to create the symlink.

Kind regards

---

### Post by somf on 2011-10-04
Sorry Matt, still no joy. ```
jerry@SOMFNAV:~$ ls -l /dev/COM*
ls: cannot access /dev/COM*: No such file or directory 
```

---

### Post by matt_symes on 2011-10-04
Hi

Hmmm. 

I have just managed to create a rule for my usb pen drive so i am scratching my head at the moment.

Can i see the rules file you have created while i have a think.

```
cat /etc/udev/rules.d/usb-serial.rules
```EDIT:

Do the above but also try this rule

```
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="[COLOR=Black]2303[/COLOR]", [COLOR=Red]NAME="COM1"[/COLOR], MODE="0660"
```Kind regards

---

### Post by somf on 2011-10-04
Here are both responses, ```
jerry@SOMFNAV:~$ cat /etc/udev/rules.d/usb-serial.rules
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", SYMLINK+="COM1", MODE="0660"

jerry@SOMFNAV:~$ KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", NAME="COM1", MODE="0660"
ATTRS{idVendor}==067b,: command not found
jerry@SOMFNAV:~$ 

```

---

### Post by audiomick on 2011-10-04
> **somf said:**
> ....
jerry@SOMFNAV:~$ KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", NAME="COM1", MODE="0660"
ATTRS{idVendor}==067b,: command not found
  You've misunderstood Matt here, I think.

You need to go back to his instructions in this post
[http://ubuntuforums.org/showpost.php?p=11309718&postcount=10](http://ubuntuforums.org/showpost.php?p=11309718&postcount=10)

and use those instructions to make the rule look like this.

    ```
KERNELS=="2-2", SUBSYSTEMS=="usb", ATTRS{idVendor}=="067b", ATTRS{idProduct}=="2303", NAME="COM1", MODE="0660"
```

---

### Post by bouncingwilf on 2011-10-04
I regularly use exactly the same type of software (Marine navigation) under wine and the standard method (for me) is :

cd .wine/dosdevices
ln -s /dev/ttyUSB0 com1

i.e create a symbolic link to /dev/ttyUSB0 called com1 in the dosdevices directory of wine.

The windows software should then have a com1 (com2... etc) port to work with.

Bouncingwilf

---

### Post by matt_symes on 2011-10-04
Hi

> **bouncingwilf said:**
> I regularly use exactly the same type of software (Marine navigation) under wine and the standard method (for me) is :

cd .wine/dosdevices
ln -s /dev/ttyUSB0 com1

i.e create a symbolic link to /dev/ttyUSB0 called com1 in the dosdevices directory of wine.

The windows software should then have a com1 (com2... etc) port to work with.

Bouncingwilf

That's interesting and easier than setting up a udev rule. 

Any problems when the device is disconnected ?

Kind regards

---

### Post by somf on 2011-10-04
Audiomick, I reinstalled rule per earlier post, still no luck. ```
jerry@SOMFNAV:~$ sudo nano /etc/udev/rules.d/usb-serial.rules
[sudo] password for jerry: 
jerry@SOMFNAV:~$ sudo service udev restart
udev start/running, process 3934
jerry@SOMFNAV:~$ ls -l /dev/COM*
ls: cannot access /dev/COM*: No such file or directory
jerry@SOMFNAV:~$ 

```
bouncungwilf, could you post steps for your method? 
Thanks to all for helping a simple minded newbie!:)

---

### Post by matt_symes on 2011-10-04
Hi

Bouncingwilf's method is this....

Plug the device in and type these two commands.

```
cd ~/.wine/dosdevices
ln -s /dev/ttyUSB0 COM1
```As long as when the device is plugged in udev always assigns it the name ttyUSB0 then this will work as it links /dev/ttyUSB0 to ~/.wine/dosdevices/COM1.

Problems will arise if udev calls the device something other than ttyUSB0. However that may not affect you.

I think bouncingwilf is right and you are not quite understanding what i am asking you to do so let's do the simpler method.

@bouncingwilf.

 ~/.wine/dosdevices is where wine looks for devices ? I did not know that so the rule would have had to have been slightly altered anyway. I'm not even sure if udev can create a symlink outside the /dev directory. Thanks for this information :) I suppose you could use a rule to ensure the device is always called a specific name and then set up a ln -s symlink to it in dosdevices. That would mitigate any name changes udev might make for the device.

Kind regards

---

### Post by bouncingwilf on 2011-10-04
Yes, setting up udev rules is ok but I've never found it necessary. Anytime you insert a usb-> serial converter, the com ports are sequentially numbered USB0, USB1.. etc. I also still have serial ports, these are usually called /dev/ttyS0 , dev/ttyS1 etc. and you can link these in the same way. In my setup I have two serial NMEA ports (GPS and AIS) and 1 serial/USB (depth) and I can move the serial-> USB converter to any available USB port and the link remains good.



Interestingly, I've found that recent kernels/wine sometimes find the serial ports without needing to set up symbolic links.

Bouncingwilf.

---

### Post by matt_symes on 2011-10-04
Hi

> **bouncingwilf said:**
> Yes, setting up udev rules is ok but I've never found it necessary. Anytime you insert a usb-> serial converter, the com ports are sequentially numbered USB0, USB1.. etc. I also still have serial ports, these are usually called /dev/ttyS0 , dev/ttyS1 etc. and you can link these in the same way. In my setup I have two serial NMEA ports (GPS and AIS) and 1 serial/USB (depth) and I can move the serial-> USB converter to any available USB port and the link remains good.



Interestingly, I've found that recent kernels/wine sometimes find the serial ports without needing to set up symbolic links.

Bouncingwilf.

Again, cheers for this information. 

I have never used a usb to serial convert under Linux; only under windows to interface and control storage machines and other devices so it's good to hear it from the Linux side and also under wine.

Kind regards

---

### Post by somf on 2011-10-04
Thanks everyone for the help. I can see I have a long way to go before I will be comfortable with this OS. The last commands did it, at least in the sense that the port is renamed when checked in the terminal. Unfortunately it still shows up in the serial port terminal as ttyUSB0 and is not shown in the two programs I am trying to run. Not sure where to go from here...
```
jerry@SOMFNAV:~$ ls -l /dev/COM*
lrwxrwxrwx 1 root root 7 2011-10-04 19:40 /dev/COM1 -> ttyUSB0
jerry@SOMFNAV:~$ 

```

---

### Post by bouncingwilf on 2011-10-05
What software are you trying to run under wine?

Bouncingwilf

---

### Post by pjd99 on 2011-10-05
As stated in a few posts, wine only needs a link created in ~/.wine/dosdevices

```

cd ~/.wine/dosdevices/
ln -s /dev/ttyUSB0 com1

```[http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)

---

### Post by somf on 2011-10-05
I was trying to get either Offshore Navigator or Opencpn to see a Raymarine 125 gps set to nema183 and going through a prolific usb to serial adapter. At first I was able to get GPS sentences in the Ubuntu serial port terminal as ttyUSB0. With help I was able to get it renamed as COM1 but still not seen by programs. Now at some point I seem to have caused a failure in the GPS itself as all I get now is garbage through the terminal and when hooked back up to my Windows system I get an error that there is no GPS connected. Bummer to lose a $250 GPS experimenting but at least I have a cheap GPS mouse that will interface with OSN in Windows. Thanks for all the help from the forrum but it looks to be a lost cause.:confused:

---

### Post by bouncingwilf on 2011-10-06
I suggest you try the Linux version of Opencpn - I use it with no problems at all. You can then connect direct to the /dev/ttyUSB0 port or optionally start the gpsd daemon and have the data available to multiple programs.

I doubt very much that you have "bricked" the Raymarine - talk to it nicely and it will come back to you.

Bouncingwilf

---

