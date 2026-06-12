---
title: "Lenovo Yoga 310-11 touchpad does not work"
date: 2018-12-01
forum: New to Ubuntu
---

### Post by tuczarnybuntu on 2018-12-01
Hi
Ubuntu 18.04.01 LTS 64 bit (installed today)
in Yoga 310-11 in xinput
touchpad is visible as:
SYNA7300:00 06CB:177C

synaptics drivers from:
xserver-xorg-input-libinput-hwe-18.04 
xserver-xorg-input-synaptics
xserver-xorg-input-libinput
not working

changed gnome settings to do not disable touchpad while I'm typing

as there is working touchpad on/off on F6 key
touchpad is turned on (ubuntu shows it)

checked thread:
[https://ubuntuforums.org/showthread.php?t=2385197&p=13741372#post13741372](https://ubuntuforums.org/showthread.php?t=2385197&p=13741372#post13741372)

any ideas ?

---

### Post by tuczarny on 2019-01-12
found solution but no idea how to apply it :(

there is a patch for kernel
 as this touchpad is ELAN0602

[https://patchwork.kernel.org/patch/9866777/](https://patchwork.kernel.org/patch/9866777/)

can someone help with instruction what to do ?

---

### Post by jeremy31 on 2019-01-12
tuczarny, please post results from terminal for ```
dmesg | grep -i elan
```
You have me a bit confused as the original post shows "SYNA7300:00 06CB:177C" but now you think it is "ELAN0602"

---

### Post by tuczarny on 2019-02-26
as you wish 
dmesq | grep -i elan
[    4.115007] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vdd not found, using dummy regulator
[    4.115043] i2c_hid i2c-ELAN0602:00: Linked as a consumer to regulator.0
[    4.115046] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vddl not found, using dummy regulator
[    7.441843] elan_i2c i2c-ELAN0602:00: i2c-ELAN0602:00 supply vcc not found, using dummy regulator


gmesg | grep -i e2c 
[    3.649201] i2c /dev entries driver
[    4.078458] i2c_hid i2c-SYNA7300:00: i2c-SYNA7300:00 supply vdd not found, using dummy regulator
[    4.078482] i2c_hid i2c-SYNA7300:00: Linked as a consumer to regulator.0
[    4.078484] i2c_hid i2c-SYNA7300:00: i2c-SYNA7300:00 supply vddl not found, using dummy regulator
[    4.115007] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vdd not found, using dummy regulator
[    4.115043] i2c_hid i2c-ELAN0602:00: Linked as a consumer to regulator.0
[    4.115046] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vddl not found, using dummy regulator
[    4.120742] input: SYNA7300:00 06CB:177C Touchscreen as /devices/pci0000:00/0000:00:16.3/i2c_designware.1/i2c-1/i2c-SYNA7300:00/0018:06CB:177C.0001/input/input3
[    4.120891] hid-generic 0018:06CB:177C.0001: input,hidraw0: I2C HID v1.00 Device [SYNA7300:00 06CB:177C] on i2c-SYNA7300:00
[    7.441843] elan_i2c i2c-ELAN0602:00: i2c-ELAN0602:00 supply vcc not found, using dummy regulator
[    7.730493] input: SYNA7300:00 06CB:177C as /devices/pci0000:00/0000:00:16.3/i2c_designware.1/i2c-1/i2c-SYNA7300:00/0018:06CB:177C.0001/input/input6
[    7.734195] hid-multitouch 0018:06CB:177C.0001: input,hidraw0: I2C HID v1.00 Device [SYNA7300:00 06CB:177C] on i2c-SYNA7300:00

looks that this Syna device is touchscreen (works) and Elan is touchpad
still no idea what next
Not workiing with xserver-xorg-input-libinput 



best regards
Czarny

---

### Post by tuczarny on 2019-02-28
Downloaded kernel sources
verified in sources in sources that ELAN0602 exists in elan_i2c_core.c 
recompiled kernel

no joy....

just to have clean system - reinstalling to vanilla 18.10

any suggestions ?

---

### Post by jeremy31 on 2019-02-28
What is the result for ```
mokutil --sb-state
```

---

### Post by tuczarny on 2019-03-07
# mokutil --sb-state
EFI variables are not supported on this system

#uname -rvi
4.19.0-13-generic #14-Ubuntu SMP Thu Feb 7 21:51:25 UTC 2019 x86_64

---

### Post by jeremy31 on 2019-03-07
```
sudo apt install dkms build-essential git
git clone https://github.com/jeremyb31/mouse-4.15.git 
sudo dkms add ./mouse-4.15
sudo dkms install mouse/1.0
```
Reboot

---

### Post by tuczarny on 2019-03-08
thanks :)
done
touchpad still  does not work

---

### Post by jeremy31 on 2019-03-08
Post results for ```
dmesg | grep -i elan
```

---

### Post by tuczarny on 2019-03-10
root@yogi:~# dmesg |grep -i elan
[    4.173652] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vdd not found, using dummy regulator
[    4.173689] i2c_hid i2c-ELAN0602:00: Linked as a consumer to regulator.0
[    4.173691] i2c_hid i2c-ELAN0602:00: i2c-ELAN0602:00 supply vddl not found, using dummy regulator
[    6.953918] elan_i2c: loading out-of-tree module taints kernel.
[    6.953994] elan_i2c: module verification failed: signature and/or required key missing - tainting kernel
[    6.973687] elan_i2c i2c-ELAN0602:00: i2c-ELAN0602:00 supply vcc not found, using dummy regulator

---

### Post by jeremy31 on 2019-03-10
what about ```
modinfo elan_i2c
```

---

### Post by tuczarny on 2019-03-10
filename:       /lib/modules/4.19.0-13-generic/updates/dkms/elan_i2c.ko
version:        JB2
license:        GPL
description:    Elan I2C/SMBus Touchpad driver
author:         Duson Lin <dusonlin@emc.com.tw>
srcversion:     3C9B6A218E28150BDF264FE
alias:          i2c:elan_i2c
alias:          acpi*:ELAN1300:*
alias:          acpi*:ELAN1203:*
alias:          acpi*:ELAN1000:*
alias:          acpi*:ELAN959A:*
alias:          acpi*:ELAN0622:*
alias:          acpi*:ELAN0620:*
alias:          acpi*:ELAN061E:*
alias:          acpi*:ELAN061D:*
alias:          acpi*:ELAN061C:*
alias:          acpi*:ELAN0618:*
alias:          acpi*:ELAN0612:*
alias:          acpi*:ELAN0611:*
alias:          acpi*:ELAN060C:*
alias:          acpi*:ELAN060B:*
alias:          acpi*:ELAN0609:*
alias:          acpi*:ELAN0608:*
alias:          acpi*:ELAN0605:*[B]
alias:          acpi*:ELAN0602:*[/B]
alias:          acpi*:ELAN0600:*
alias:          acpi*:ELAN0100:*
alias:          acpi*:ELAN0000:*
depends:        
retpoline:      Y
name:           elan_i2c
vermagic:       4.19.0-13-generic SMP mod_unload

0602 is there.... so what next ?

---

### Post by jeremy31 on 2019-03-10
Can you try ```
sudo sh -c 'echo -n "elantech" > /sys/bus/serio/devices/serio1/protocol'
```
See if it works then

---

### Post by tuczarny on 2019-03-11
sh: 1: cannot create /sys/bus/serio/devices/serio1/protocol: Directory nonexistent

no "serio1" "serio0" exists but there is no protocol directory there

---

### Post by tuczarny on 2019-05-11
any ideas ? as problem still unresolved and this would be nice to use touchpad instead of mouse...

---

### Post by jeremy31 on 2019-05-11
I am not sure why it is not working

---

### Post by tuczarny on 2019-05-11
SOLVED
Came to crazy idea....
disasembled this thing, checked physical connectors to touchpad (disconnected/connected)
assembled again - works...
....no comments...
Jeremy THANKS :)

---

