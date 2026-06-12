---
title: "Bluetooth is disabled"
date: 2015-11-27
forum: New to Ubuntu
---

### Post by Drowz0r on 2015-11-27
Hello all

I have today inserted a Bluetooth 2.0 USB adaptor. It is plugged into a USB port that connects directly to my motherboard (not a PCI USB or anything).

The adaptor lights up, showing it has power and is connected. The light is solid and does not flicker.

Ubuntu has not detected the device in any way that is clear.

If I go into the Bluetooth settings I can toggle the "Bluetooth ON/OFF" slider in the top left but nothing happens. I can also toggle the "show bluetooth status in the menu bar" but nothing changes with that either.

Everything else shows"Visibility OFF" (top right) and the left column shows "Bluetooth is disabled".

I have so far tried installing the bluetooth stuff from the software centre in case I was missing a package or something. I have installed:

Bluetooth support
Bluetooth Transfer
Bluetooth Manager
Bluetooth Device Set-up
Bluetooth

In the terminal if I type: "rfkill list" here is the output:

```
0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
```

I have tried "sudo hciconfig hci0 reset" but this is the output:

```
Can't init device hci0: Operation not supported (95)
```

Finally I tried the fix [here]("https://askubuntu.com/questions/465442/bluetooth-is-disable-on-ubuntu-14-04") which is typing "sudo apt-get install gksu -y" into the terminal, then I did "gksudo gedit /etc/rc.local" and added the line "rfkill unblock bluetooth" before exit 0.

However this did not seem to make any changes either.

So I'm pretty much out of ideas. I've had a go at fixing it myself but don't seem to be getting anywhere. Is anyone able to help?

EDIT:

lsusb gives the following:

Bus 003 Device 007: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)


Thanks in advance

---

### Post by matt_symes on 2015-11-27
Hi

Open a terminal and type

```
tail -f /var/log/syslog
```

Plug the dongle in, wait 10 seconds, then post the output from the terminal here.

What version of ubuntu are you running ?

Kind regards

---

### Post by Drowz0r on 2015-11-27
```
Nov 27 13:15:13 Prime NetworkManager[802]: <info> (eth0): DHCPv4 state changed renew -> renew
Nov 27 13:15:13 Prime NetworkManager[802]: <info>   address 192.168.8.7
Nov 27 13:15:13 Prime NetworkManager[802]: <info>   prefix 24 (255.255.255.0)
Nov 27 13:15:13 Prime NetworkManager[802]: <info>   gateway 192.168.8.1
Nov 27 13:15:13 Prime NetworkManager[802]: <info>   nameserver '192.168.8.1'
Nov 27 13:15:13 Prime NetworkManager[802]: <info>   domain name 'Vault-Tec'
Nov 27 13:15:13 Prime dbus[670]: [system] Activating service name='org.freedesktop.nm_dispatcher' (using servicehelper)
Nov 27 13:15:13 Prime dbus[670]: [system] Successfully activated service 'org.freedesktop.nm_dispatcher'
Nov 27 13:17:01 Prime CRON[8861]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov 27 13:26:34 Prime dhclient: DHCPREQUEST of 192.168.8.7 on eth0 to 192.168.8.1 port 67 (xid=0x6a8071ca)
Nov 27 13:36:49 Prime kernel: [ 6047.816001] usb 3-6: USB disconnect, device number 9
Nov 27 13:36:58 Prime kernel: [ 6056.806531] usb 3-6: new full-speed USB device number 10 using xhci_hcd
Nov 27 13:36:59 Prime kernel: [ 6056.880303] usb 3-6: New USB device found, idVendor=0a12, idProduct=0001
Nov 27 13:36:59 Prime kernel: [ 6056.880312] usb 3-6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
Nov 27 13:36:59 Prime kernel: [ 6056.880316] usb 3-6: Product: Bluetooth V2.0 Dongle
Nov 27 13:36:59 Prime kernel: [ 6056.880320] usb 3-6: Manufacturer: Bluetooth v2.0
```

My full spec and OS are in my signature :)

---

### Post by matt_symes on 2015-11-27
Hi

I'll take a look when i get home tonight for you.

Kind regards

---

### Post by Drowz0r on 2015-11-27
Great, thanks!

---

### Post by matt_symes on 2015-11-27
Hi

I have a dongle by the same vendor and with the same device ID but, unlike yours, it's not version two. It does get enabled unlike yours.

```
Nov 27 20:27:06 matthew-laptop kernel: [305336.728198] usb 7-1: new full-speed USB device number 6 using uhci_hcd
Nov 27 20:27:07 matthew-laptop kernel: [305337.342302] usb 7-1: New USB device found, idVendor=0a12, idProduct=0001
Nov 27 20:27:07 matthew-laptop kernel: [305337.342314] usb 7-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: sap-dummy interface org.bluez.SimAccessTest init failed on path /org/bluez/test
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: Sap driver initialization failed.
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: sap-server: Operation not permitted (1)
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: hci1: Load Long Term Keys (0x0013) failed: Not Supported (0x0c)
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: hci1: Set Discoverable (0x0006) failed: Not Powered (0x0f)
Nov 27 20:27:07 matthew-laptop bluetoothd[1050]: Adapter /org/bluez/1050/hci1 has been enabled

```

What kernel are you running ?

```
uname -a
``` 

With the device plugged in, are all the generic drivers being loaded ?

```
lsmod | grep btusb
```

Can hcitool see any devices ?

```
hcitool dev
```

I take it that this command is not unblocking the softblock ( try it from the terminal and not from rc.local in case there's some odd race condition) ?

```
sudo rfkill unblock bluetooth
```

I'm trying to discover if this is a bug, if you need to upgrade, if this a firmware issue or just something is miconfigured on your system.

BTW:

> Nov 27 13:36:58 Prime kernel: [ 6056.806531] usb 3-6: new full-speed USB device number 10 using **xhci_hcd**

Have you tried a USB 2 port instead of USB 3 ? 

**EDIT**

Can we check that bluetooth is being enabled correctly.

```
dmesg | grep -i bluetooth
```

Kind regards

---

### Post by Drowz0r on 2015-11-27
```
drowz0r@Prime:~$ uname -a
Linux Prime 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```

```
lsmod | grep btusb
```

(does nothing)

```
drowz0r@Prime:~$ hcitool dev
Devices:
```

I guess it doesn't see any?

```
drowz0r@Prime:~$ dmesg | grep -i bluetooth
[    2.857007] Bluetooth: Core ver 2.17
[    2.857019] Bluetooth: HCI device and connection manager initialized
[    2.857024] Bluetooth: HCI socket layer initialized
[    2.857026] Bluetooth: L2CAP socket layer initialized
[    2.857028] Bluetooth: SCO socket layer initialized
[    2.859919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.859921] Bluetooth: BNEP filters: protocol multicast
[    2.859928] Bluetooth: BNEP socket layer initialized
[    2.861998] Bluetooth: RFCOMM TTY layer initialized
[    2.862005] Bluetooth: RFCOMM socket layer initialized
[    2.862008] Bluetooth: RFCOMM ver 1.11
```

> Have you tried a USB 2 port instead of USB 3 ?

I've only tried it in this one port - they might all be USB 3.0 though, I'll have to check.

---

### Post by jeremy31 on 2015-11-27
Matt, I have heard about fake CSR bluetooth devices and wonder if there is a way to tell if Drowz0r might have one of the fakes, possibly comparing the hciconfig -a info

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b)

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3)

---

### Post by matt_symes on 2015-11-27
Hi

> **Drowz0r said:**
> ```
drowz0r@Prime:~$ uname -a
Linux Prime 3.13.0-68-generic #111-Ubuntu SMP Fri Nov 6 18:17:06 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```


You're on an old stack hardware stack. I would update to vivid. See link below.

> ```
lsmod | grep btusb
```

(does nothing)


None of the drivers are being loaded. That explains....

> 
```
drowz0r@Prime:~$ hcitool dev
Devices:
```

I guess it doesn't see any?


...the above.

> ```
drowz0r@Prime:~$ dmesg | grep -i bluetooth
[    2.857007] Bluetooth: Core ver 2.17
[    2.857019] Bluetooth: HCI device and connection manager initialized
[    2.857024] Bluetooth: HCI socket layer initialized
[    2.857026] Bluetooth: L2CAP socket layer initialized
[    2.857028] Bluetooth: SCO socket layer initialized
[    2.859919] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    2.859921] Bluetooth: BNEP filters: protocol multicast
[    2.859928] Bluetooth: BNEP socket layer initialized
[    2.861998] Bluetooth: RFCOMM TTY layer initialized
[    2.862005] Bluetooth: RFCOMM socket layer initialized
[    2.862008] Bluetooth: RFCOMM ver 1.11
```


The good thing is that the stack bluetooth is being initialised sucessfully.
 
> I've only tried it in this one port - they might all be USB 3.0 though, I'll have to check.

You could try that but i'm not sure if that will make much difference.

I would update to the Vivid hardware enablement stack for Trusty, reboot and try the dongle again.

You may just want to update the kernel or you may want to update the entire stack including xorg.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

***Backup all important data before you do this. I usually image the entire drive.***

***Backup all important data before you do this. I usually image the entire drive.***

***Backup all important data before you do this. I usually image the entire drive.***

:D

**EDIT:**

Of course if this does not fix it, post back and we'll continue trouble shooting for you.

Kind regards

---

### Post by matt_symes on 2015-11-27
Hi

> **jeremy31 said:**
> Matt, I have heard about fake CSR bluetooth devices and wonder if there is a way to tell if Drowz0r might have one of the fakes, possibly comparing the hciconfig -a info

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b)

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3)

I missed your post jemery31. Sorry about that. I think we must have cross posted.

In this case i don't think that will help because *hcitool* is not finding any devices so *hciconfig -a info* will most likely not work, however i could well be wrong.

The OP is most welcome to try the commands though and post the results back here.

Thanks for posting those links as there's a worrying number of fake devices on the market at the moment.

Caveat emptor :|

Kind regards

---

### Post by jeremy31 on 2015-11-27
I wonder if ```
rfkill unblock all
``` will work since it is soft blocked

---

### Post by matt_symes on 2015-11-27
Hi

> **jeremy31 said:**
> I wonder if ```
rfkill unblock all
``` will work since it is soft blocked

I would suggest the OP tries this as well as post the output from hciconfig.

I do remember, years ago, a situation where a Bluetooth device was soft blocked and unblocking it did not work. It was due to a firmware issue the driver loaded. That may or may not be the case here. Running your command will show either way.

Unfortunately, the Bluetooth stack is one of the subsystems i know less about so all suggestions are really welcome :)

Kind regards

---

### Post by Drowz0r on 2015-11-28
So I've backed everything up. I tried to update the kernel:

```
drowz0r@Prime:~$ sudo apt-get install --install-recommends linux-generic-lts-vivid xserver-xorg-core-lts-vivid xserver-xorg-lts-vivid xserver-xorg-video-all-lts-vivid xserver-xorg-input-all-lts-vivid libwayland-egl1-mesa-lts-vivid
[sudo] password for drowz0r: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 wine : Depends: wine1.6
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

It seems like I just need to install Wine 1.6, though it does seem odd to me that updating the kernel would need wine. Just wanted to check my interpretation was correct before proceeding.

---

### Post by Drowz0r on 2015-11-28
> **jeremy31 said:**
> Matt, I have heard about fake CSR bluetooth devices and wonder if there is a way to tell if Drowz0r might have one of the fakes, possibly comparing the hciconfig -a info

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=6cafcd959599d91d0fa4615feae7f1e7ab407c4b)

[http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3](http://git.kernel.org/cgit/linux/kernel/git/bluetooth/bluetooth-next.git/commit/drivers/bluetooth?id=81cac64ba258ae823f52cfaec0cad26ecb31adc3)

hciconfig -a does not produce any output in the terminal.

Was there another command you wanted me to try and run? I must admit I can't quite work it out from the links.

---

### Post by Drowz0r on 2015-11-28
Actually scrap that, installed some wine packages that were seemingly missing from the software centre and it updated.

When I restarted there were a bunch of errors, black screen white text but the desktop eventually loaded fine.

Still not able to turn on the bluetooth adaptor thing. Some of the errors seemed to specifically relate to the USB port in question (I guess it cannot recognise the device)

I'll post an image of what the output is from my phone later today.

In the mean time when opening the Bluetooth software thing, I can no longer slide the top left toggle and all else remains the same.

---

### Post by Drowz0r on 2015-11-28
Actually, some progress, rebooted to take pictures of the errors and no errors appeared - guess it just needed a reboot.

I can now turn on bluetooth and the visibility of my device. It detects both my phone and my game controller it seems. I'll do some tests and let you know if it's all in working order now.

---

### Post by Drowz0r on 2015-11-28
So bluetooth seems to be working fine now. I paired my phone fine but when trying the same with my gamepad it detects it as a keyboard. Any idea how to fix that? Obviously I cannot pair it because it wants me to enter a pair code on my "keyboard" but naturally the gamepad doesn't have keys.

When selecting no code or don't pair or any other option it defaults to automatic pin.

---

### Post by matt_symes on 2015-11-28
Hi

> **Drowz0r said:**
> So bluetooth seems to be working fine now. I paired my phone fine but when trying the same with my gamepad it detects it as a keyboard. Any idea how to fix that? Obviously I cannot pair it because it wants me to enter a pair code on my "keyboard" but naturally the gamepad doesn't have keys.

When selecting no code or don't pair or any other option it defaults to automatic pin.

That's excellent news about the Bluetooth dongle being recognised. 

You were using an old hardware stack and updating it has obviously fixed it.

This is exactly why hardware enablement stacks were introduced to LTS releases and is a good part of the reason that I'm also still on 14.04 as my stable release :)

I'm really busy at the moment - just stopping for a quick coffee - but we can look at your next problem later if you like.

Kind regards

---

### Post by matt_symes on 2015-11-28
Hi

> ... when trying the same with my gamepad it detects it as a keyboard. ...


What kind of gamepad is this ? Make and model please.

Kind regards

---

### Post by Drowz0r on 2015-11-29
Hello

Yeah the update seems to have worked a treat. Thanks for walking me through the fix.

The pad is actually this one: [http://www.ebay.co.uk/itm/391197225510?_trksid=p2060353.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT](http://www.ebay.co.uk/itm/391197225510?_trksid=p2060353.m2749.l2649&ssPageName=STRK%3AMEBIDX%3AIT)

Bluetooth detects it as a "BT Controller" which seems to co-inside with various online for the device. However under "type" it shows as "keyboard". This is seemingly what causes the problems when it is asking me to enter a pin on the device in order to pair it. There aren't any markings on the controller

I thought I would be able to get around that by trying one of the fixed pins or by selecting "do not pair" but the Bluetooth New Device Setup seems to revert to "automatic pin selection". Some-what confusing.

I've tried messaging the seller for support but they haven't replied as of yet. I'm wondering if the issue might just be with the gamepad itself and otherwise unavoidable - but I was hoping there was a way to pair it without a pin or something.

---

### Post by matt_symes on 2015-11-29
Hi

Hmm. Not come across that controller before. Maybe we can get more information about it.

Can you connect the controller via USB, open a terminal and type

```
lsusb
```

Unplug from USB and with bluetooth enabled on the gamepad (this is to check the device class - you can obfuscate the MAC address in your reply if that worries you)

```
hcitool inq
```

With the mac address from the command above (once again you can obfuscate the mac if you like - i'm interested in the manufacturer really).

```
sudo hcitool info <mac_address>
```

Let's see where that gets us for a start.

Kind regards

---

### Post by Drowz0r on 2015-12-01
Alrighty. When plugging in the controller via USB the "Home" central button flashes in the same manner as if it was searching via bluetooth, so power seems to get to it fine.

Here are is the output from the terminal:

```
drowz0r@Prime:~$ lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0c45:7403 Microdia Foot Switch
Bus 001 Device 005: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 004: ID 06a3:8020 Saitek PLC Eclipse Keyboard
Bus 001 Device 003: ID 046d:0a12 Logitech, Inc. 
Bus 001 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
drowz0r@Prime:~$ hcitool inq
Inquiring ...
Inquiry failed.: No such device
```

Naturally I cannot seem to do "sudo hcitool info <mac_address>"

---

On a side note, since the kernel update, whenever I open Steam I get this message pop-up in a terminal window. Upon trying to follow the instruction to install the additional packages, it doesn't seem to work.

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for drowz0r: 
.............................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

I have tried installing the lower-mentioned packages separately and their dependencies but the terminal outputs that they are already installed and the most recent version. Steam does actually seem to behave fine if I just close the terminal window though.

---

### Post by matt_symes on 2015-12-01
Hi

> **Drowz0r said:**
> Alrighty. When plugging in the controller via USB the "Home" central button flashes in the same manner as if it was searching via bluetooth, so power seems to get to it fine.

Here are is the output from the terminal:

```
drowz0r@Prime:~$ lsusb
Bus 004 Device 002: ID 8087:8000 Intel Corp. 
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 8087:8008 Intel Corp. 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 006: ID 0c45:7403 Microdia Foot Switch
Bus 001 Device 005: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 004: ID 06a3:8020 Saitek PLC Eclipse Keyboard
Bus 001 Device 003: ID 046d:0a12 Logitech, Inc. 
Bus 001 Device 002: ID 1532:000d Razer USA, Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I'm having trouble determining which device above is your gamepad. 

I suspect it's either the Eclipse keyboard or the Razer device. 

Even after getting the newest usbid file, I'm still not sure.

Anyway, to determine which device the gamepad is, can you run lsusb without the gamepad connected via USB, connect the gamepad and run lsusb again and post the new entry that appears.

I'm hoping that, when we determine the vendor and device id, that'll give us a place to start looking for a fix.

BTW: To update the usb ids used by lsusb:

```
sudo update-usbids
```

> ```
drowz0r@Prime:~$ hcitool inq
Inquiring ...
Inquiry failed.: No such device
```

Naturally I cannot seem to do "sudo hcitool info <mac_address>"

Hmm. I didn't expect that.

> On a side note, since the kernel update, whenever I open Steam I get this message pop-up in a terminal window. Upon trying to follow the instruction to install the additional packages, it doesn't seem to work.

```
Steam needs to install these additional packages: 
    libgl1-mesa-dri:i386, libgl1-mesa-glx:i386
[sudo] password for drowz0r: 
.............................................................................................................................
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libcheese-gtk23 : Depends: libclutter-gtk-1.0-0 (>= 0.91.8) but it is not going to be installed
                   Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libcheese7 : Depends: libclutter-gst-2.0-0 (>= 0.10.0) but it is not going to be installed
              Depends: gstreamer1.0-clutter but it is not going to be installed
 libclutter-1.0-0 : Depends: libcogl-pango15 (>= 1.15.8) but it is not going to be installed
                    Depends: libcogl15 (>= 1.15.8) but it is not going to be installed
 libgl1-mesa-glx:i386 : Depends: libglapi-mesa:i386 (= 10.1.3-0ubuntu0.5)
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
```

I have tried installing the lower-mentioned packages separately and their dependencies but the terminal outputs that they are already installed and the most recent version. Steam does actually seem to behave fine if I just close the terminal window though.

Raise another thread on this problem as I'm am not a steam user.

There are other users on this forums who are steam users, however, and they may be better equipped to help you with this problem.

PM me the link though and I'll keep an eye on that thread and if i come across a fix, I'll post in the thread for you.

Kind regards

---

### Post by Drowz0r on 2015-12-01
Weirdly the Steam issue seemed to resolve itself after an update today. Which is nice.

Sorry I should have clarified before that the lsusb output is the same regardless of if the controller is connected via USB or not.

---

### Post by Drowz0r on 2015-12-01
I also ran sudo update-usbids but nothing seemed to change (but here is the output where it seemingly saved something)

```
drowz0r@Prime:~$ sudo update-usbids
[sudo] password for drowz0r: 
--2015-12-02 01:18:07--  [http://www.linux-usb.org/usb.ids](http://www.linux-usb.org/usb.ids)
Resolving [www.linux-usb.org]("http://www.linux-usb.org") ([www.linux-usb.org]("http://www.linux-usb.org"))... 216.34.181.97
Connecting to [www.linux-usb.org]("http://www.linux-usb.org") ([www.linux-usb.org)|216.34.181.97|:80]("http://www.linux-usb.org)|216.34.181.97|:80")... connected.
HTTP request sent, awaiting response... 200 OK
Length: 556422 (543K) [text/plain]
Saving to: ‘/var/lib/usbutils/usb.ids.new’

100%[======================================>] 556,422      579KB/s   in 0.9s   

2015-12-02 01:18:08 (579 KB/s) - ‘/var/lib/usbutils/usb.ids.new’ saved [556422/556422]

Done.
```

---

### Post by matt_symes on 2015-12-02
Hi

> **Drowz0r said:**
> Weirdly the Steam issue seemed to resolve itself after an update today. Which is nice.

Excellent. That's good news.

> Sorry I should have clarified before that the lsusb output is the same regardless of if the controller is connected via USB or not.

I have no idea what your gamepad is. 

hcitool and lsusb are not finding it from what you have posted.

Looking at razor's website, they sell game controllers (xbox compatible) but the pictures they have of their controllers look different than the one you linked to from ebay. However, I'm wondering if you have an xbox controller clone.

BTW: Do you have a Bluetooth keyboard ? I'm wondering if it's trying to pair with a keyboard you may have and not the controller.

 I can give you no definitive answers but if it's an xbox gamepad clone then this may help.

[http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working](http://askubuntu.com/questions/165210/how-do-i-get-an-xbox-360-controller-working)

Notice that it's for Ubuntu 12.04 however the packages are available even for the 16.04 development version.

```
matthew-xu-16-04:/home/matthew:0 % acse ^joystick 
joystick - set of testing and calibration tools for joysticks
jstest-gtk - joystick testing and configuration tool
jstest-gtk-dbg - joystick testing and configuration tool - debug
matthew-xu-16-04:/home/matthew:0 % acse xboxdrv
xboxdrv - Xbox360 gamepad driver for the userspace
matthew-xu-16-04:/home/matthew:0 % 

```

I can't really help you much more than that. I'm not even sure it's an xbox controller clone but it does give you a place to research a solution.

If you have luck then please post back and mention it.

Kind regards

---

### Post by Drowz0r on 2015-12-02
Sorry, my fault again:

Bus 001 Device 004: ID 06a3:8020 Saitek PLC Eclipse Keyboard (this is my normal USB keyboard)
Bus 001 Device 002: ID 1532:000d Razer USA, Ltd (this is my normal USB mouse)

The seller managed to get back to me. They issued a refund without asking for the item back without any real conversation so maybe there is a fault with the items being detected on PCs properly. Worked on my android phone... so I suppose this fault sometimes goes unnoticed.

At least bluetooth is working now though, for when I get a proper controller working :)

---

### Post by matt_symes on 2015-12-02
Hi

> **Drowz0r said:**
> Sorry, my fault again:

Bus 001 Device 004: ID 06a3:8020 Saitek PLC Eclipse Keyboard (this is my normal USB keyboard)
Bus 001 Device 002: ID 1532:000d Razer USA, Ltd (this is my normal USB mouse)

The seller managed to get back to me. They issued a refund without asking for the item back without any real conversation so maybe there is a fault with the items being detected on PCs properly. Worked on my android phone... so I suppose this fault sometimes goes unnoticed.

At least bluetooth is working now though, for when I get a proper controller working :)

Excellent. All the issues are sorted out then.

Kind regards

---

### Post by Drowz0r on 2015-12-02
Yup! Thank you so much for your help. I was really stuck there.

---

