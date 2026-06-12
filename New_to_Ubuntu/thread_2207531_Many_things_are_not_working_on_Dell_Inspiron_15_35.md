---
title: "Many things are not working on Dell Inspiron 15 3537 with Ubuntu 13.10"
date: 2014-02-24
forum: New to Ubuntu
---

### Post by vatzcar on 2014-02-24
I have a new Dell Inspiron 15 3537 ([http://www.ubuntu.com/certification/hardware/201305-13649/components/](http://www.ubuntu.com/certification/hardware/201305-13649/components/)). It came with pre-installed Ubuntu 12.04. After update my WiFi stopped working, so I decided to install Ubuntu 13.10. Now after installation and update I'm having following problems:

[LIST=1]
[*]Brightness is not working. Though brightness keys are working and brightness bar is increasing/decreasing but that's no coming in effect, my screen is remaining on full brightness.
[*]Touchpad is not working properly. Like scrolling is not working when moving finger by right edge of touchpad, multi-gesture is not working.
[*]WiFi is not working, it's getting disconnected frequently and sometime asking for password over and over. When connected, no data is being transferred.
[/LIST]

---

### Post by sandyd on 2014-02-24
> **vatzcar said:**
> I have a new Dell Inspiron 15 3537 ([http://www.ubuntu.com/certification/hardware/201305-13649/components/](http://www.ubuntu.com/certification/hardware/201305-13649/components/)). It came with pre-installed Ubuntu 12.04. After update my WiFi stopped working, so I decided to install Ubuntu 13.10. Now after installation and update I'm having following problems:

[LIST=1]
[*]Brightness is not working. Though brightness keys are working and brightness bar is increasing/decreasing but that's no coming in effect, my screen is remaining on full brightness.
[*]Touchpad is not working properly. Like scrolling is not working when moving finger by right edge of touchpad, multi-gesture is not working.
[*]WiFi is not working, it's getting disconnected frequently and sometime asking for password over and over. When connected, no data is being transferred.
[/LIST]

1. Have you tried any of the acpi_backlight fixes?
Try adding acpi_osi=Linux apci_backlight=vendor to /etc/default/grub

You can edit the file by running
```

sudo nano /etc/default/grub
```
and pressing Control+X to save
Should look something like
```
GRUB_CMDLINE_LINUX="acpi_osi=Linux apci_backlight=vendor"
```

Run```
sudo update-grub
``` after editing the file
2. Post output of
```

lspci
xinput

```

---

### Post by vatzcar on 2014-02-24
Hi sandyd, thank you very much for the help. I've followed your instruction.

here's the output of lspci

```
00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
00:03.0 Audio device: Intel Corporation Device 0a0c (rev 09)
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation Lynx Point-LP HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation Lynx Point-LP HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation Lynx Point-LP PCI Express Root Port 4 (rev e4)
00:1d.0 USB controller: Intel Corporation Lynx Point-LP USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Lynx Point-LP LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Lynx Point-LP SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
02:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)

```

and xinput

```
Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=13	[slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad              	id=11	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Laptop_Integrated_Webcam_HD             	id=9	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]
    &#8627; Dell WMI hotkeys                        	id=12	[slave  keyboard (3)]

```

---

### Post by Daliz on 2014-02-24
2. Have you set the touchpad scrolling mode to the right edge setting? It can be found in the mouse/touchpad system settings. The default is two finger scrolling iirc.

---

### Post by vatzcar on 2014-02-24
Thank you Daliz, that worked :) can you please help me with my wi-fi issue?

---

### Post by barbarah2 on 2014-02-24
Wow, maybe I'm having all my Ubuntu issues because of the laptop brand, too (I also own Dell)? It never occured to me and I'm almost desperate to fix the issues

---

### Post by vatzcar on 2014-02-24
Update: I didn't get chance to reboot my laptop when I posted and I did few minutes ago. Apparently ```
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor"
``` didn't work. On login top menubar icons (system tray) aren't loading, wallpaper isn't loading, only left launcer bar (icons etc.) loading but icons are not clickable. Keyboard keys are not working except brightness buttons, mouse buttons are not working. So practically that one is making my system unusable.

is there any other way to fix it?

---

