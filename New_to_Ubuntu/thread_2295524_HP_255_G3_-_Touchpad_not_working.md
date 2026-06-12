---
title: "HP 255 G3 - Touchpad not working"
date: 2015-09-19
forum: New to Ubuntu
---

### Post by moffattsam on 2015-09-19
Hi all,

Purchased this laptop with Ubuntu 12.04 LTS pre-installed. Everything was working fine, no issues what so ever. 

Updated everything and then proceeded with an upgrade to 14.04 LTS.

Upgrade finished and laptop restarts. 

Mouse cursor shows up in centre of the screen at the login screen but will not move. I can type in my password and then login; the cursor vanishes. 

Desktop shows up, cursor returns, but will not move.

External USB mouse works fine. 

All solutions posed in other threads haven't worked so far. 

Any ideas?

Thanks

Sam

---

### Post by moffattsam on 2015-09-19
Get this response when trying to run Synaptics

sam@sam-HP-255-G3-Notebook-PC:~$ synaptiks
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
QDBusConnection: session D-Bus connection created before QCoreApplication. Application may misbehave.
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/synaptiks/kde/trayapplication.py", line 260, in newInstance
    self.icon.show_configuration_dialog()
  File "/usr/lib/python2.7/dist-packages/synaptiks/kde/trayapplication.py", line 241, in show_configuration_dialog
    self.touchpad, self.touchpad_manager, self._config)
AttributeError: 'SynaptiksNotifierItem' object has no attribute 'touchpad'

---

### Post by sandyd on 2015-09-19
Hi, can you post the output of
```

lspci
xinput list
```

---

### Post by moffattsam on 2015-09-19
sam@sam-HP-255-G3-Notebook-PC:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.1 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.3 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.4 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode]
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader (rev 01)
03:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

---

### Post by moffattsam on 2015-09-19
sam@sam-HP-255-G3-Notebook-PC:~$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; 2.4G Receiver                               id=9    [slave  pointer  (2)]
&#9116;   &#8627; 2.4G Receiver                               id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Webcam                                   id=12    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=13    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=15    [slave  keyboard (3)]
    &#8627; 2.4G Receiver                               id=10    [slave  keyboard (3)]
sam@sam-HP-255-G3-Notebook-PC:~$

---

### Post by Karen Vincent on 2015-10-12
I have exactly the same problem. HP selling this laptop with ubuntu 12.04 and all functioning perfectly but deliberately has 'upgrade to newer software versions' switched off. Upgrade to 14.04 and the touchpad is no longer detected - but of course HP then say you have deliberately changed the settings so nothing to do with them. Some threads suggest this was fixed in 14,10 and later but I have upgraded to 15.04 and the problem remains. My terminal output is exactly as per thread above. Problems with synaptics touchpads seem to abound, is there a patch to at least get the touchpad detected and functioning at a very basic level?

13/10 I have attempted to boot into the recovery modes available on the system, either the boot hangs almost immediately or it gets so far and does not complete with a dialogue box showing a cursor which cannot be moved by the Touchpad but a mouse still works. 

However, I have a Lubuntu 15.04 disk and booting from the disk encounters no problems, with a fully functioning Touchpad available.

---

### Post by Karen Vincent on 2015-10-13
POSSIBLE SOLUTION

I have got my Touchpad back. This was the route I took:

1 .Checked crash report files - this showed that a report had been sent against oem-input-synapticsled-1098063.dkms
2. Investigated this crash report and was led to Bug #1365534
3. Filer of this bug had solved his problem by uninstalling 3 packages: synaptics-touchpad 16.3.7.72 oem-input-synaptics-1057412 (3-stella) and oem-input-synapticsled-1098063.dkms
4. Took a look at packages installed on my system which a search of 'synaptics' found 
5, Removed the following two packages ONLY (I left alone the xorg packages):
             synaptics-touchpad 18.1.11.58
             oem-input-synapticsled-1098063-dkms  version 1.0stella2
6. Rebooted and all is well, with my touchpad functioning again

I have no technical knowledge to know why this worked but I guess that it is something to do with a conflict between the synaptics and xorg packages

Hope it works for you too - as non-tech I am not sure about marking this as solved without an explanation

Karen :D

---

