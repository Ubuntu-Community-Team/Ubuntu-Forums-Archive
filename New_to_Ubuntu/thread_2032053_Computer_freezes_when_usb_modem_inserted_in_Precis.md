---
title: "Computer freezes when usb modem inserted in Precise"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by mr.akik on 2012-07-23
Hi,
I'm using ubuntu 12.04. Sometimes my  computer freezes when I insert a modem in usb 
port. It also occurs when I unplug my usb modem. Desktop goes away and I can see a dark screen like console. I find many things written but I don't understand them.
I never faced this problem with any other version of ubuntu except Precise.
The problem remains when I installed Precise in other computers. So, it a problem of ubuntu not my hardware.
 Please solve my problem. Thanks in advance.

---

### Post by NikTh on 2012-07-23
> **mr.akik said:**
> 
The problem remains when I installed Precise in other computers. So, it a problem of ubuntu not my hardware.

Hi , 
to be sure about that , try to reproduce the problem with a live CD / Usb. 

Are you able to provide more info ? 
Can you open a terminal and write this command 
```
watch -n 1 "dmesg | tail -n 30"
``` 
then plug in your usb , and if you catch , post here the messages that will appear , when usb plugged in. 

Thanks

---

### Post by mr.akik on 2012-07-24
> **NikTh said:**
> Hi , 
to be sure about that , try to reproduce the problem with a live CD / Usb. 

Are you able to provide more info ? 
Can you open a terminal and write this command 
```
watch -n 1 "dmesg | tail -n 30"
```then plug in your usb , and if you catch , post here the messages that will appear , when usb plugged in. 

ThanksThis is the output but it may be only the last page displayed on terminal. Terminal lets me neither scroll down nor scroll up. There is no scroll bar: 
[   61.487261] scsi 2:0:0:1: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[   61.505246] sr0: scsi-1 drive
[   61.505259] cdrom: Uniform CD-ROM driver Revision: 3.20
[   61.505913] sr 2:0:0:0: Attached scsi CD-ROM sr0
[   61.506433] sr 2:0:0:0: Attached scsi generic sg1 type 5
[   61.507426] sd 2:0:0:1: Attached scsi generic sg2 type 0
[   61.532298] sd 2:0:0:1: [sdb] Attached SCSI removable disk
[   62.152166] usb 2-2: USB disconnect, device number 2
[   63.688131] usb 2-2: new full-speed USB device number 3 using uhci_hcd
[   63.867092] scsi3 : usb-storage 2-2:1.5
[   63.969233] usbcore: registered new interface driver usbserial
[   63.969366] USB Serial support registered for generic
[   63.975677] usbcore: registered new interface driver usbserial_generic
[   63.975694] usbserial: USB Serial Driver core
[   64.015578] USB Serial support registered for GSM modem (1-port)
[   64.018845] option 2-2:1.0: GSM modem (1-port) converter detected
[   64.019306] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB0
[   64.019534] option 2-2:1.1: GSM modem (1-port) converter detected
[   64.021818] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB1
[   64.022041] option 2-2:1.2: GSM modem (1-port) converter detected
[   64.022434] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB2
[   64.022647] option 2-2:1.3: GSM modem (1-port) converter detected
[   64.022977] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB3
[   64.023185] option 2-2:1.4: GSM modem (1-port) converter detected
[   64.023515] usb 2-2: GSM modem (1-port) converter now attached to ttyUSB4
[   64.023659] usbcore: registered new interface driver option
[   64.023672] option: v0.7.2:USB Driver for GSM modems

---

### Post by Bufeu on 2012-07-24
May be problems with the drivers, try re-install them.

---

### Post by NikTh on 2012-07-24
Hi , 
is your modem a ZTE ? 

Plug in your usb-modem and give this command 
```
lsusb
``` give the results here.. 

**Question: **is your usb port , a usb2 or usb3 port ? 

Thanks

---

### Post by mr.akik on 2012-07-24
> **NikTh said:**
> Hi , 
is your modem a ZTE ? 

Plug in your usb-modem and give this command 
```
lsusb
``` give the results here.. 

**Question: **is your usb port , a usb2 or usb3 port ? 

ThanksThis is the output:
akik@akik-Pine-Trail-M-CRB:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:5801 Realtek Semiconductor Corp. 
Bus 003 Device 003: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 003: ID 19d2:fff1 ZTE WCDMA Technologies MSM 
akik@akik-Pine-Trail-M-CRB:~$ 
My netbook's usb port's version is 2.0 . Thank you.

---

### Post by NikTh on 2012-07-24
Hi , 
we can try something , i don't know if works , but will see...

```
gksudo gedit  /lib/udev/rules.d/40-usb_modeswitch.rules
```You will go to the end and **before the line **_LABEL="modeswitch_rules_end"_
add this line 
```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff1", RUN+="usb_modeswitch '%b/%k'"
``` . Copy paste the line from here , for more accuracy. 
Save the file and reboot your pc. 
Plug in the usb and see if works.. 

**if not**.. then open a terminal and give the results of this command 
```
dmesg | tail -n 30
```

Thanks

---

### Post by mr.akik on 2012-07-25
> **NikTh said:**
> Hi , 
we can try something , i don't know if works , but will see...

```
gksudo gedit  /lib/udev/rules.d/40-usb_modeswitch.rules
```You will go to the end and **before the line **_LABEL="modeswitch_rules_end"_
add this line 
```
ATTRS{idVendor}=="19d2", ATTRS{idProduct}=="fff1", RUN+="usb_modeswitch '%b/%k'"
``` . Copy paste the line from here , for more accuracy. 
Save the file and reboot your pc. 
Plug in the usb and see if works.. 

**if not**.. then open a terminal and give the results of this command 
```
dmesg | tail -n 30
```Thanks
It didn't work. I forgot to mention one thing: if I insert the modem before login , that is before typing password on login screen, the problem never occurs.
The same problem occurred when I used another modem with another pc.
That modem was completely different but it was made by zte.
It seems to me that there is  a bug  with any built in package  of precise.
It may be in usb_modeswitch or in the driver.
Can it be solved by updating kernel?

This is the output: 

akik@akik-Pine-Trail-M-CRB:~$ dmesg | tail -n 30
[  101.589684] option 2-1:1.2: device disconnected
[  101.591423] option1 ttyUSB3: GSM modem (1-port) converter now disconnected from ttyUSB3
[  101.591514] option 2-1:1.3: device disconnected
[  101.592123] option1 ttyUSB4: GSM modem (1-port) converter now disconnected from ttyUSB4
[  101.592207] option 2-1:1.4: device disconnected
[  112.444170] usb 2-1: new full-speed USB device number 4 using uhci_hcd
[  112.612173] scsi4 : usb-storage 2-1:1.0
[  113.617292] scsi 4:0:0:0: CD-ROM            ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  113.620383] scsi 4:0:0:1: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  113.639256] sr0: scsi-1 drive
[  113.639901] sr 4:0:0:0: Attached scsi CD-ROM sr0
[  113.644204] sr 4:0:0:0: Attached scsi generic sg1 type 5
[  113.645405] sd 4:0:0:1: Attached scsi generic sg2 type 0
[  113.665251] sd 4:0:0:1: [sdb] Attached SCSI removable disk
[  113.984125] usb 2-1: USB disconnect, device number 4
[  115.464188] usb 2-1: new full-speed USB device number 5 using uhci_hcd
[  115.633619] option 2-1:1.0: GSM modem (1-port) converter detected
[  115.634465] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  115.636624] option 2-1:1.1: GSM modem (1-port) converter detected
[  115.637146] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  115.639640] option 2-1:1.2: GSM modem (1-port) converter detected
[  115.640238] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[  115.642467] option 2-1:1.3: GSM modem (1-port) converter detected
[  115.642749] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
[  115.645455] option 2-1:1.4: GSM modem (1-port) converter detected
[  115.645725] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB4
[  115.646217] scsi5 : usb-storage 2-1:1.5
[  116.659253] scsi 5:0:0:0: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  116.662160] sd 5:0:0:0: Attached scsi generic sg1 type 0
[  116.678265] sd 5:0:0:0: [sdb] Attached SCSI removable disk
akik@akik-Pine-Trail-M-CRB:~$

---

### Post by NikTh on 2012-07-25
Hi , 
if you want to revert the changes ... you know what to do.. 
open again the file 
```

gksudo gedit  /lib/udev/rules.d/40-usb_modeswitch.rules
```and delete the line we added . 

This is a loop 
> ```

[  113.617292] scsi 4:0:0:0: CD-ROM            ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  113.620383] scsi 4:0:0:1: Direct-Access     ZTE      USB Storage FFF1 2.31 PQ: 0 ANSI: 2
[  115.634465] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB0
[  115.636624] option 2-1:1.1: GSM modem (1-port) converter detected
[  115.637146] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB1
[  115.639640] option 2-1:1.2: GSM modem (1-port) converter detected
[  115.640238] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB2
[  115.642467] option 2-1:1.3: GSM modem (1-port) converter detected
[  115.642749] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB3
[  115.645455] option 2-1:1.4: GSM modem (1-port) converter detected
[  115.645725] usb 2-1: GSM modem (1-port) converter now attached to ttyUSB4
```and I think this creates the problem.
This Usb Device must has 2 interfaces .. 1 for modem and 1 for usb mass storage. But the confusing thing here is that , probably your device has Usb mass storage Interface FIRST , and modem second.
This confuses the kernel , or causes this loop thing. The result of this,  is X-server to be unable to handle this situation and crashes (so as you said , if you plug in Usb before go in to Desktop , this problem not occur)

I am almost certain that if we could tell to kernel that "This is a modem device and NOT a storage device" this will solve your problem , but I am not sure how to do that.
Sorry. 

Lets try another thing.. 
try to enable the automount option .. 
```

gsettings set org.gnome.desktop.media-handling automount "true"
gsettings set org.gnome.desktop.media-handling automount-open "true"
```and see if this is a workaround. 

If you had already enalbed automount , try to disable.. same commands but with "false" instead "true" 


Thanks

---

### Post by mr.akik on 2012-07-25
> **NikTh said:**
> 
This Usb Device must has 2 interfaces .. 1 for modem and 1 for usb mass storage. But the confusing thing here is that , probably your device has Usb mass storage Interface FIRST , and modem second.
This confuses the kernel , or causes this loop thing. The result of this,  is X-server to be unable to handle this situation and crashes (so as you said , if you plug in Usb before go in to Desktop , this problem not occur)

Yes , you are right. The modem has two devices in it. The first one is a virtual cdrom/storage and the second one is modem. And usb_modeswitch is working to switch it to modem mode , so kernel shouldn't be confused to handle it (as I didn't see it happening with other versions of ubuntu. And when login screen appears, x-server is already started as this is lightdm screen and its not console login system.  Is it possible that it is occurring due to any program that runs at startup ? 
Think, either I insert the modem before login or after login, the environment is graphical( x-server has already started). The problem occurs when the desktop fully loads it's components. Is any startup program causing the problem ? I didn't add or omit any startup program. 
I'm using gnome-classic desktop.

---

### Post by NikTh on 2012-07-25
Hi , 
did you try the commands with automount ? 
Is there a way to disable the interface of mass storage ? has this device any settings ? 

 What you saying about startup applications , yes..make sense.. 
All startup applications listed at /etc/xdg/autostart/ , but from default Canonical decided to hide them from user's eye . 
So when you open startup applications from GUI you see almost nothing. 
If you open a startup application to see the content e.g. 
```
cat /etc/xdg/autostart/bluetooth-applet.desktop
``` you will see an entry ```
NoDisplay=true
```this entry hides the autostart application from GUI (autostart applications). 
If you want to un-hide it you must either change the "true" to "false" or add before a symbol # and make the entry like this 
```
#NoDispaly=true
``` , then you can see it at startup applications and you can disable it.

Thanks

---

### Post by mr.akik on 2012-07-26
> **NikTh said:**
> Hi , 
did you try the commands with automount ? 
Is there a way to disable the interface of mass storage ? has this device any settings ? 

 What you saying about startup applications , yes..make sense.. 
All startup applications listed at /etc/xdg/autostart/ , but from default Canonical decided to hide them from user's eye . 
So when you open startup applications from GUI you see almost nothing. 
If you open a startup application to see the content e.g. 
```
cat /etc/xdg/autostart/bluetooth-applet.desktop
``` you will see an entry ```
NoDisplay=true
```this entry hides the autostart application from GUI (autostart applications). 
If you want to un-hide it you must either change the "true" to "false" or add before a symbol # and make the entry like this 
```
#NoDispaly=true
``` , then you can see it at startup applications and you can disable it.

Thanks
I tried with the command of automount but it didn't work.
But the good news is, finally I solved the problem. I removed usb-modeswitch and it's dependencies and installed an older version. Now there's no problem.
Thank you dear friend, NikTh. You did a lot for me.

---

### Post by NikTh on 2012-07-26
> **mr.akik said:**
> I tried with the command of automount but it didn't work.
But the good news is, finally I solved the problem. **I removed usb-modeswitch and it's dependencies and installed an older version.** Now there's no problem.
Thank you dear friend, NikTh. You did a lot for me.

Hi , 
so its was a problem (bug maybe) with the newer package of usb-modeswitch. Ok. 

Glad you solved . 
You can  mark this** thread as solved** from **thread tools**.

Thanks

---

