---
title: "Radeon HD 7500G: Black screen on suspend-resume"
date: 2014-01-31
forum: New to Ubuntu
---

### Post by connor4 on 2014-01-31
Hi,

I'm completely new to linux, so sorry if i'm being stupid!

I have a Samsung series 5 laptop, running Ubuntu 13.10(64 bit). Whenever I close the lid or suspend the laptop, I then turn it on again, just to have a black screen. The laptop is definitely doing something, however nothing i press has any effect. 

I've recently switched from windows 8, and I had no problems at all, so i'm assuming its a setting or something in Ubuntu.

Let me know if any more information is required!

Thanks,
Connor

---

### Post by Toz on 2014-01-31
Hello and welcome to the forums.

Can you provide the following information? To do so, open a terminal window, type in the command and post back the results within **[noparse]```
 
```[/noparse]** tags.

1. The exact model of your laptop:
```
sudo dmidecode -s system-product-name
```

2. Info about your video card(s) and the drivers being used:
```
lspci -k | grep -A2 VGA
```

3. The contents of your pm-suspend.log file:
```
pastebinit /var/log/pm-suspend.log
```
...and post back the link that is generated.

4. PM-related messages in your syslog:
```
cat /var/log/syslog | grep PM:
```

---

### Post by bc.haynes on 2014-01-31
No such thing as a stupid question (unless you already know the answer).

Let us know morw about your laptop and your video card:
```
lspci | grep VGA
```

use Capital letters in VGA
Someone more experienced than I will, with enough info, will help you.

---

### Post by connor4 on 2014-01-31
Hi,

Thanks for the quick response!


The model:
```

35U3C

```

The video card and drivers:

```

[COLOR=#333333][FONT=lucida grande]00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7500G]    Subsystem: Samsung Electronics Co Ltd Device c660    
Kernel driver in use: radeon[/FONT][/COLOR]

```

[COLOR=#000000]contents of mypm-suspend.log file:

[/COLOR]```
[COLOR=#333333][FONT=lucida grande]http://paste.ubuntu.com/684963[/FONT][/COLOR]
```[COLOR=#000000]

[/COLOR][COLOR=#000000]PM-related messages in my syslog:
[/COLOR][COLOR=#000000]
[/COLOR]```
[COLOR=#333333][FONT=lucida grande]
Jan 31 12:57:23 connor-535U3C kernel: [ 2707.618782] PM: Syncing filesystems ... done.
Jan 31 12:57:23 connor-535U3C kernel: [ 2707.842550] PM: Preparing system for mem sleep
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.050354] PM: Entering mem sleep
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.679069] PM: suspend of devices complete after 627.399 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.679337] PM: late suspend of devices complete after 0.264 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.763201] PM: noirq suspend of devices complete after 83.772 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.931440] PM: Saving platform NVS memory
Jan 31 12:57:38 connor-535U3C kernel: [ 2708.941278] PM: Restoring platform NVS memory
Jan 31 12:57:38 connor-535U3C kernel: [ 2709.246771] PM: noirq resume of devices complete after 127.105 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2709.247013] PM: early resume of devices complete after 0.155 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2711.105395] PM: resume of devices complete after 1856.493 msecs
Jan 31 12:57:38 connor-535U3C kernel: [ 2711.106234] PM: Finishing wakeup.
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x0009f000-0x0009ffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e35a000-0x9e4ecfff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e4ed000-0x9e4f9fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e4fa000-0x9e839fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9e83a000-0x9ef8bfff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9ef8d000-0x9f18ffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f598000-0x9f7f3fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x9f800000-0xfebfffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfec0ffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec10000-0xfec10fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfec11000-0xfecfffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed00000-0xfed00fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed01000-0xfed7ffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed80000-0xfed8ffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xfed90000-0xfeffffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0xff000000-0xffffffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x100000000-0x100000fff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.000000] PM: Registered nosave memory: [mem 0x94000000-0x97ffffff]
Jan 31 12:59:14 connor-535U3C kernel: [    0.209162] PM: Registering ACPI NVS region [mem 0x9e4fa000-0x9e839fff] (3407872 bytes)
Jan 31 12:59:14 connor-535U3C kernel: [    0.209249] PM: Registering ACPI NVS region [mem 0x9ef8d000-0x9f18ffff] (2109440 bytes)
Jan 31 12:59:14 connor-535U3C kernel: [    1.223271] PM: Hibernation image not present or could not be loaded.[/FONT][/COLOR]
```[COLOR=#000000]


[/COLOR]

---

### Post by Toz on 2014-01-31
The paste upload from #3 above isn't working, I'm getting a "Paste no found" message. Can you try that again?

You have an ATI card and are using the radeon driver. Suspend works better with the proprietary driver. Have you tried enabling it? See if its listed as available in Software Centre -> Sources -> Additional Drivers tab or by running:
```
software-properties-gtk --open-tab=4
```

---

### Post by connor4 on 2014-01-31
Hi,

Try this link instead, should work!
```
http://paste.ubuntu.com/6850670/
```

Here's the options I have for graphics drivers, any suggestions?

[IMG]http://s21.postimg.org/mggap8t7r/Options.jpg[/IMG]

---

### Post by Toz on 2014-01-31
Yes, your pm-suspend.log file confirms what you are seeing, that the system is successfully suspending/resuming but that the screen is staying dark.

[This bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093644") seems to be about a similar system to yours. A few interesting things to note:
1. Installing the proprietary drivers resulted in a black screen that required recovery.
2. The regular proprietary drivers didn't work (they had to use the ones from the ATI website).
3. The issue seemed to resolve itself.

[This link]("http://www.linlap.com/samsung_np535u3c") has an entry that states that the kernel parameter **acpi_osi=Linux** solved the suspend/resume issue.

I would recommend trying this kernel parameter. There are instructions on how to temporarily boot with this parameter in the "Kernel Boot Parameters" link in my signature.

If that doesn't work, you should try installing the proprietary ATI drivers. Unfortunately, I don't have any experience with ATI drivers and won't be able to assist if something goes wrong - though others on this forum will probably be able to help.

---

### Post by connor4 on 2014-02-04
Update: Upon resuming from suspend, if i plug an external monitor in via HDMI, that works and I can use that, however the laptop screen remains black.

I tried changing the kernel parameter as described and nothing happened differently, suspend still went to the black screen upon resume. 

I downloaded the drivers from the ATI website however i'm having trouble installing them. I unzipped them to a ".run" file however nothing seems to be able to run that, which seems a bit ironic. 

Thanks for the help!

Connor

---

