---
title: "HOWTO: Get your remote control working on the Hauppauge NOVA-T 500 (Ubuntu)"
date: 2009-08-27
forum: Outdated Tutorials &amp; Tips
---

### Post by EcKstasy on 2009-08-27
This is a updated tutorial of [***this post***]("http://ubuntuforums.org/showthread.php?t=183545"), It allows you to get your remote control working on Ubuntu with LIRC for the Hauppauge NOVA-T 500 USB DVB stick. I thought I'd post this here because I was having some trouble with my remote control.

Step 1: Open up your terminal and enter in the following command

```
 $ cat /proc/bus/input/devices
```

Look for something similar to:

```
I: Bus=0003 Vendor=2040 Product=7070 Version=0100
N: Name="IR-receiver inside an USB DVB receiver"
P: Phys=usb-0000:00:1d.7-4/ir0
S: Sysfs=/devices/pci0000:00/0000:00:1d.7/usb1/1-4/input/input4
U: Uniq=
H: Handlers=kbd event4 
B: EV=3
B: KEY=14afc336 284284d 0 0 0 4 80058000 2190 40000801 9e96c0 0 900200 ffd
```

Step 2: You'll need to get your vendor name for your device.

```
 $ udevinfo -a -p $(udevinfo -q path -n /dev/input/event4)
```

Replace "event4" with the "H:" field in your output in step 1, eg: 

```
H: Handlers=kbd event4
```

After that, find something similar to: ATTRS{vendor}=="0x8086" in the output.
Create a new text file by: sudo nano /etc/udev/rules.d/10-local.rules
copy and paste this into that file: 

```
KERNEL=="event*",ATTRS{vendor}=="0x8086",SYMLINK="input/irremote"
```

remember to replace "0x8086" with YOUR value in /dev/input as shown in step 2
(once done, CTRL + O to save the file, CTRL + X to exit nano)

Step 3: you'll now have to restart UDEV, simply:

```
 $ sudo /etc/init.d/udev restart
```

Step 4: To confirm the configuration is a success, enter the following:  

```
$ ls -l /dev/input
```

you should see a line that says something similar to: 

```
lrwxrwxrwx 1 root root      6 2009-08-27 21:25 irremote -> event4
```

Now, you'll need to install LIRC. simply type:

```
 $ sudo aptitude install lirc
```

a dialog will popup, you will have to pick your device. Scroll down until you see "Hauppauge NOVA-T 500"
Another dialog will popup after you hit enter, just select "none". Check if it now works by typing "irw" in your terminal.
Press some buttons on your remote, for example. the volume buttons. That's you hopefully done!

---

