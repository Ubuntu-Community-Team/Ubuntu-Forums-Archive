---
title: "Sony VAIO VPCCA brightness doesn't work"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by dumont-maxence on 2013-12-27
Hi guys, :)

I have a Sony VAIO VPCCA1S1E (intel core i5-2410M CPU @ 2.30GHz, AMD RADEON HD 6470M) and Ubuntu 13.04 64 bits, with Unity. I have a brightness problem:
when I press the hot keys, the slide bar appears but the luminosity does not change.

I've red numerous of thread about that, but I did not find THE solution... The most precise I get is that one:
[http://ubuntuforums.org/showthread.php?t=2088190](http://ubuntuforums.org/showthread.php?t=2088190)

In my grub file, I have the line:
GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"

I have made a "sudo update-grub" and rebooted.

Here's the result of the command line that are given in the link above:
```
cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.8.0-34-generic root=UUID=18deeeb1-fc0d-4af4-9424-359f36b1613d ro acpi_osi=Linux quiet splash acpi_backlight=vendor vt.handoff=7
[/CODE

[CODE]for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
/sys/class/backlight/sony
168
242



```

```
sudo dmidecode -s system-manufacturer
Sony Corporation


```

```
sudo dmidecode -s system-product-name
VPCCA1S1E


```
```

sudo lspci -vnn | grep -A12 VGA
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series] [1002:6760] (prog-if 00 [VGA controller])
    Subsystem: Sony Corporation Device [104d:9081]
    Flags: bus master, fast devsel, latency 0, IRQ 51
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    Memory at f7e20000 (64-bit, non-prefetchable) [size=128K]
    I/O ports at d000 [size=256]
    Expansion ROM at f7e00000 [disabled] [size=128K]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Legacy Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Capabilities: [150] Advanced Error Reporting
    Kernel driver in use: fglrx_pci



```


After that, it's given other commands to manualy adjust the brightness (certainly related to the result of the first commands) but none of them are working in my case. Those commands are:
```
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 7 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 2441 | sudo tee /sys/class/backlight/intel_backlight/brightnessecho 4882 | sudo tee /sys/class/backlight/intel_backlight/brightness
```

all of tell me that the file was not found. So I watched for the same kind of file and I found that folder:
/sys/devices/virtual/backlight/sony
Here I find:
- actual_brightness which contains 242
- bl_power which contains 0
- brightness which contains 100
- max_birghtness which contains 242
- type which contains platform
- uevent which is empty

When I changed the value of brightness, nothing happens. When I try to change actual_brightness, I am refused, even if I'm sudo.

Others information:
-  I've never find a way to change the brightness (even manually)
- When I do acpi_listen, I get those hot keys code:
backlight down:
sony/hotkey SNC 00000001 00000010
sony/hotkey SNC 00000001 0000003b

backlight up:
sony/hotkey SNC 00000001 00000011
sony/hotkey SNC 00000001 0000003b

I created the file mentionned, but I've modifyed brightup.sh and brightdown.sh:
brightup.sh

```
#!/bin/bash
curr=`cat /sys/devices/virtual/backlight/sony/actual_brightness`
if [ $curr -lt 232 ]; then
   curr=$((curr+10));
   echo $curr  > /sys/devices/virtual/backlight/sony/brightness;
fi
```

brightdown.sh
```
#!/bin/bash
curr=`cat /sys/devices/virtual/backlight/sony/actual_brightness`
if [ $curr -gt 10 ]; then
   curr=$((curr-10));
   echo $curr  > /sys/devices/virtual/backlight/sony/brightness;
fi
```

Those files are runnable (-x for every user level)

Now, when I push the hotkeys, the file "brightness" see his content modifying, but brightness does not actually change.

Any ideas? What is the command line to change the brightness for AMD RADEON? I think I should first find a way to change manually the brighness. Then I would be able to adapt the files above to do it working.

Thanks in advance for your help.

Max

---

### Post by Toz on 2013-12-27
Hello and welcome to the forums.

Since your backlight interface is "sony", do the following commands adjust brightness?
```
echo 100 | sudo tee /sys/class/backlight/sony/brightness
echo 242 | sudo tee /sys/class/backlight/sony/brightness
```

If not, can you remove the **acpi_backlight=vendor** parameter from your kernel boot line and re-run:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/max_brightness; done
```

---

### Post by dumont-maxence on 2013-12-27
Thanks for your welcome ;)

I tryed the 2 commands you gave, but  none of them has any effect. So I've deleted acpi_backight=vendor from  my /etc/default/grub file.
So the folder tree has changed. The  /sys/devices/virtual/backlight tree has disappeared. A new folder tree  has been created:  /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/backlight/acpi_video0

Your command give that result:

```
/sys/class/backlight/acpi_video0
10
15
```

The backlight has drop down (thanks for my eyes :) ) but is stil not adjustable.

 
EDIT: The backlight seems to change from time to time. In the new folder tree, the max_brightness file contains 15. The brightness file content change from 0 to 15 when I hit the hot keys.
The actual_brightness file take the brightness value sometimes.

EDIT2: It seems that the new brightness value is applied afer a reboot or a standby/wake up.

---

### Post by Toz on 2013-12-27
> **dumont-maxence said:**
> Thanks for your welcome ;)

I tryed the 2 commands you gave, but  none of them has any effect. So I've deleted acpi_backight=vendor from  my /etc/default/grub file.
So the folder tree has changed. The  /sys/devices/virtual/backlight tree has disappeared. A new folder tree  has been created:  /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/backlight/acpi_video0

Your command give that result:

```
/sys/class/backlight/acpi_video0
10
15
```

The backlight has drop down (thanks for my eyes :) ) but is stil not adjustable.
Do these commands now adjust the brightness?
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness
```

 
> EDIT: The backlight seems to change from time to time. In the new folder tree, the max_brightness file contains 15. The brightness file content change from 0 to 15 when I hit the hot keys.
The actual_brightness file take the brightness value sometimes.
Does this mean that after so many brightness presses the brightness actually decreases (i.e. pressing the brightness down combination 10 times will decrease the brightness one level)?

> EDIT2: It seems that the new brightness value is applied afer a reboot or a standby/wake up.
Interesting. Can I see your dmesg log file?
```
pastebinit /var/log/dmesg
```
...and post back the link that is generated?

---

### Post by dumont-maxence on 2013-12-28
> Do these commands now adjust the brightness?
 
```
echo 5 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 10 | sudo tee /sys/class/backlight/acpi_video0/brightness
echo 15 | sudo tee /sys/class/backlight/acpi_video0/brightness 
```


These commands change the value in the brightness file, as hot keys do. But Brightness doesn't change actually.

> Does this mean that after so many brightness presses the  brightness actually decreases (i.e. pressing the brightness down  combination 10 times will decrease the brightness one level)?

In fact, the brightness just changed once. Now if I press the hot keys, nothing happens, even if the slide bar goes from min to max.

My dmes log file:
[http://paste.ubuntu.com/6650426/](http://paste.ubuntu.com/6650426/)

---

### Post by dumont-maxence on 2013-12-28
Hmm in fact when I press the hotkeys, the value in the brightness file  evolves, and is well transmitted to the acutal_brightness file (I have  to change folder and come back to see the actual_brightness value  changing). But the brightness does not change, except after a reboot or  suspend.
I tried:
```
sudo service acpid restart
```

but that doesn't refresh the brightness.

EDIT:
May be that's a compatibility problem between the ati (AMD) driver and the sony acpi driver...

Here's my xorg file:

Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
    Option      "RegistryDwords" "EnableBrightnessControl=1"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

and the result of lspci -nn | grep VGA

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Seymour [Radeon HD 6400M/7400M Series] [1002:6760]

Maybe that'll help : /

---

### Post by Toz on 2013-12-28
> **dumont-maxence said:**
> These commands change the value in the brightness file, as hot keys do. But Brightness doesn't change actually.

Something is blocking the brightness change. After some research, this appears to be a known bug (see: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=722737]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=722737") & [http://ati.cchtml.com/show_bug.cgi?id=711]("http://ati.cchtml.com/show_bug.cgi?id=711")). 

There is a suggested workaround:
```
aticonfig --set-pcs-u32=MCIL,PP_PhmUseDummyBackEnd,1
```
...and reboot that fixes the issue for some (you may need to install the experimental drivers for this to work). You can read more about it in the bug reports.

---

### Post by Toz on 2013-12-28
> **dumont-maxence said:**
> 
    Option      "RegistryDwords" "EnableBrightnessControl=1"

EnableBrightnessControl has no effect on ATI hardware, its an nvidia-specific hack for some of their video cards.

---

### Post by dumont-maxence on 2013-12-28
Oh thanks a lot! That command works! :p
Before that, I've updated my driver from:
[http://support.amd.com/fr-fr/download/desktop?os=Linux%20x86_64](http://support.amd.com/fr-fr/download/desktop?os=Linux%20x86_64)

I had some desktop problem after that but I've solved them (generating a new xorg file and reseting unity).

Thanks every body, that rocks! :guitar:

---

