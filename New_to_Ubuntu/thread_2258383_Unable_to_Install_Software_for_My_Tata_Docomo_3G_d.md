---
title: "Unable to Install Software for My Tata Docomo 3G dongle."
date: 2014-12-27
forum: New to Ubuntu
---

### Post by Omkar_Nath_Singh on 2014-12-27
I am able to connect to internet using network manager. But i want my Tata Docomo Dashboard for some more settings.
I am getting error dependency is not satisfieable : libaudio2.

Please resolve soon.

---

### Post by Jonathan Precise on 2014-12-27
Hello Omkar_Nath_Singh, welcome to the forums!

> I am getting error dependency is not satisfieable : libaudio2.

Seems like you need to install libaudio2.

Close Software Updater, Software Center, etc. Then open a terminal (press CTRL-ALT-T), and type:

```
pkexec apt-get install libaudio2
```

Post any errors with copy/paste.
BTW: What version of ubuntu are you using? You can check in System Settings -> Details

In 14.04 LTS, it seems a package is available: [https://launchpad.net/ubuntu/trusty/+package/libaudio2](https://launchpad.net/ubuntu/trusty/+package/libaudio2)

Post all of these questions so we can further help you solve this dependency problem.

---

### Post by newbie13 on 2014-12-27
I don't know about Tata docomo 3g dongle, but I know about tata photon plus with which I had faced the same problem, so in case my solution works for you

Open terminal and type

```
lsusb
```

something like this will appear

```
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 04f2:b34f Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 007 Device 002: ID 12d1:1505 Huawei Technologies Co., Ltd. E398 LTE/UMTS/GSM Modem/Networkcard
Bus 007 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

My modem is at 'Bus 007 Device 002'
Vendor id is 12d1 & product id is 1505, your ids might be different

1. Create a new document on desktop and name it 12d1:1505 (note:change '12d1:1505' according to your id)
2. Open it and paste this code in it and save
```

DefaultVendor= 0x12d1 
DefaultProduct=0x1505 


MessageContent="55534243123456780000000000000011062000000100000000000000000000"

```

( I have no idea what it is but it has worked for me and I hope it will work for you too)

4 Open terminal and type
```
sudo nautilus
```
This will open a window
Navigate to "[COLOR=#000000]/etc/usb_modeswitch.d" and paste the file which we created in the folder

5 Open terminal and type
[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]cd /etc/usb_modeswitch.d
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo usb_modeswitch -I -W -c 12d1\:1505[/FONT][/COLOR]
```

[COLOR=#000000]If everything goes right then terminal will say "[/COLOR]-> Run lsusb to note any changes. Bye!" at the last line.
[COLOR=#000000]Now, what I did was just unplug the modem and plug it again. It got detected and after this moment, it automatically gets connected whenever I plug it in.

Hope this helps you.

[/COLOR]source: [http://ubuntuforums.org/showthread.php?t=1814583](http://ubuntuforums.org/showthread.php?t=1814583)[COLOR=#000000]

P.S. don't forget to replace vendor and product ids with your ids[/COLOR]

---

