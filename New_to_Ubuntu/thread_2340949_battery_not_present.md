---
title: "battery not present"
date: 2016-10-23
forum: New to Ubuntu
---

### Post by aman97aman on 2016-10-23
i recently installed ubuntu 15.10 on lenovo yoga 300 and it didn't display battery status and i checked it on terminal using command
acpitool -B
it displays:
Battery status : <not available>
and just checked command:

upower -i /org/freedesktop/UPower/devices/battery_BAT0


it display



  native-path:          (null)
  power supply:         no
  updated:              Thursday 01 January 1970 05:30:00 AM IST (1477251370 seconds ago)
  has history:          no
  has statistics:       no
  unknown
    warning-level:       unknown
    icon-name:          '(null)'

---

### Post by oldos2er on 2016-10-23
Best to install a supported version of Ubuntu; 14.04 LTS or 16.04 LTS or 16.10. The desktop LTS versions are supported for five years from their date of release; 16.10 is supported for nine months.

---

### Post by foodavel on 2016-11-08
There is a bug in the laptop's firmware which prevents the kernel from detecting the battery correctly. If you don't mind building your own kernel, I have a patch which makes it work,
[http://www.spinics.net/lists/linux-acpi/msg70108.html](http://www.spinics.net/lists/linux-acpi/msg70108.html)

Hope this helps.

Dave

---

### Post by thebalthasar on 2017-01-21
Hi, just for info, ... I was checking when this patch will be in the master, ... for now it looks it is included in the kernel version 4.10 RC, but not in 4.9

I haven't tried yet patching, ... :-) I still have no idea how to do it. I have the same problem in the Lenovo Ideapad 300S-11IBR 80KU with the latest bios Version C8CN31WW (published 1/11/2016, but released 08/05/2016).

Annoying if not the least, ... and I have another ERROR in the DMESG,.... which I do not know what it is:

[    0.202673] ACPI Error: No handler for Region [ECRM] (ffff8802770ab1f8) [EmbeddedControl] (20150930/evregion-163)
[    0.202683] ACPI Error: Region EmbeddedControl (ID=3) has no handler (20150930/exfldio-297)
[    0.202692] ACPI Error: Method parse/execution failed [\_SB.PCI0.LPCB.H_EC._REG] (Node ffff8802770ad848), AE_NOT_EXIST (20150930/psparse-542)


If someone has an idea of what is this, please help !

Thanks

---

### Post by thebalthasar on 2017-01-21
And, ... just to confirm,... after following the instructions on how to quickly pass to the new 4.10rc2 release ([http://www.ubuntumaniac.com/2017/01/update-to-linux-kernel-410-rc2-on.html](http://www.ubuntumaniac.com/2017/01/update-to-linux-kernel-410-rc2-on.html)) 

For Ubuntu 64 bit: ```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc2/linux-headers-4.10.0-041000rc2_4.10.0-041000rc2.201701011831_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc2/linux-headers-4.10.0-041000rc2-generic_4.10.0-041000rc2.201701011831_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.10-rc2/linux-image-4.10.0-041000rc2-generic_4.10.0-041000rc2.201701011831_amd64.deb
``` 
After download package is finished, Open terminal and follow this command: ```
sudo dpkg -i *.deb
``` 
Please a Few minuter untill installation is finished, and reboot your ubuntu system: ```
sudo reboot
```
and check ubuntu kernel version, open terminal and follow the command: ```
uname -a
```
For me, ... the errors with the battery have disappeared (Yes) and it remains to just solve or address the issue with the   SB.PCI0.LPCB.H_EC._REG 

Cheers!

---

