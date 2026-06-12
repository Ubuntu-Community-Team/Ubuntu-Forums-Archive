---
title: "USB Gaming Mouse recognized as keyboard"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by Ismond on 2013-02-24
Hello,

I am trying to make my new usb gaming mouse (USB Nova Slider SX200) working without success.

First try on the french Ubuntu forum.
[http://forum.ubuntu-fr.org/viewtopic.php?id=782531](http://forum.ubuntu-fr.org/viewtopic.php?id=782531)

My system is 12.04 LTS
> Linux Ismond 3.2.0-38-generic #61-Ubuntu SMP Tue Feb 19 12:18:21 UTC 2013 x86_64 x86_64 x86_64 GNU/LinuxIt seems that the gaming mouse is recognize as a keyboard.
cat /proc/bus/input/devices
> I: Bus=0003 Vendor=04d9 Product=a04a Version=0110
N: Name=&quot;Newman USB Gaming Mouse&quot;
P: Phys=usb-0000:00:1a.0-1.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2
U: Uniq=
H: Handlers=sysrq kbd event2 
B: PROP=0
B: EV=120013
B: KEY=e080ffdf01cfffff fffffffffffffffe
B: MSC=10
B: LED=1fEvent viewer confirms that the mouse is configured as a keyboard.
> [    20.274] (**) Newman USB Gaming Mouse: always reports core events
[    20.274] (**) evdev: Newman USB Gaming Mouse: Device: &quot;/dev/input/event2&quot;
[    20.274] (--) evdev: Newman USB Gaming Mouse: Vendor 0x4d9 Product 0xa04a
[    20.274] (--) evdev: Newman USB Gaming Mouse: Found keys
[    20.274] (II) evdev: Newman USB Gaming Mouse: Configuring as keyboard
[    20.274] (**) Option &quot;config_info&quot; &quot;udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/input/input2/event2&quot;
[    20.274] (II) XINPUT: Adding extended input device &quot;Newman USB Gaming Mouse&quot; (type: KEYBOARD, id 8)
[    20.274] (**) Option &quot;xkb_rules&quot; &quot;evdev&quot;
[    20.274] (**) Option &quot;xkb_model&quot; &quot;pc105&quot;
[    20.274] (**) Option &quot;xkb_layout&quot; &quot;fr&quot;
[    20.274] (**) Option &quot;xkb_variant&quot; &quot;oss&quot;I try to modify my xorg.conf by adding an inputdevice, without success (not sure of what i did).
> 
Section "InputDevice"
    Identifier    "ConfiguredMouse"
    Driver        "evdev"
    Option        "CorePointer"
    Option        "Name"    "Newman USB Gaming Mouse"
EndSection

And
> 
Section "ServerLayout"
    InputDevice    "ConfiguredMouse" "CorePointer"
EndSection


At that point, my idea was to try to modify the handler and force it to mouse and i do not found any relevant method with google.

I need some help to go further.

Thanks for your help,

Ismond

---

### Post by Ismond on 2013-02-25
Hello,
 
I found another thread dealing about the same problem
[http://ubuntuforums.org/showthread.php?t=1697286&highlight=usb+gaming+mouse](http://ubuntuforums.org/showthread.php?t=1697286&highlight=usb+gaming+mouse)
 
The anwser points:
[http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html](http://forums.opensuse.org/english/get-technical-help-here/hardware/473200-usb-gaming-mouse-04d9-a078-not-working-linux-plus-workaround.html)
 
But I am not sure that I understand well the solution:
> In /usr/src/linux/include/linux/hid.h 
change the value of the constant in line 344
Code:
#define HID_MAX_USAGES 12288
from 12288 to a value greater than 32k, 
recompile and install the new kernel.

 
I have to :
- Modify the hid.h file.
- Uncomment this line and modify the value.
- Recompile and install the kernel
 
Could you confirm me the steps of that method ? Is it easy ?
 
Many thanks,
 
Ismond

---

### Post by audiomick on 2013-02-25
> **Ismond said:**
> 

I have to :
- Modify the hid.h file.
[COLOR="Red"]- Uncomment this line and modify the value.[/COLOR]
- Recompile and install the kernel


That is all well beyond my level of knowledge, but for what it is worth, I couldn't see anything there that instructs you to remove the #.

---

### Post by Ismond on 2013-02-25
Thanks for the anwser. You are right.
I missunderstood comments with shell (#) and #define in C language.

---

