---
title: "Can't get udev and lightdm to launch a script"
date: 2017-07-06
forum: New to Ubuntu
---

### Post by barrywhyte on 2017-07-06
Hello people,
I spent two evenings on this already and now I gotta ask for help (I'm new to Linux). I want to run this script 1) when I turn on my TV which is connected to my PC, 2) when I login.

/usr/share/mycustomdesktopvideo.sh
```

#!/bin/bash
xrandr --output HDMI-A-1 --mode 1920x1080 --output HDMI-A-0 --mode 1920x1080 --same-as HDMI-A-1 || true
```

It does what is expected when run manually. However neither my udev solution (1) nor my lightdm.conf solution (2) works.


this is for (1)

/etc/udev/rules.d/10-user.rules (I also tried to place it in /lib/udev/rules.d)
The script is not called, I can place gedit command in it for example and it's not started.
```
ACTION=="change", SUBSYSTEM=="drm", ENV{HOTPLUG}=="1", RUN+="/usr/share/mycustomdesktopvideo.sh"
```
When I run *udevadm test -a -p  $(udevadm info -q path -n /dev/ttyS1) *my rule file seems to be valid.

When I run *udevadm monitor --property *udev fires this event when the TV is connected:
```

KERNEL[361.463371] change   /devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0 (drm)
ACTION=change
DEVNAME=/dev/dri/card0
DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
DEVTYPE=drm_minor
HOTPLUG=1
MAJOR=226
MINOR=0
SEQNUM=3084
SUBSYSTEM=drm

UDEV  [361.465967] change   /devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0 (drm)
ACTION=change
DEVNAME=/dev/dri/card0
DEVPATH=/devices/pci0000:00/0000:00:01.0/0000:01:00.0/drm/card0
DEVTYPE=drm_minor
HOTPLUG=1
ID_FOR_SEAT=drm-pci-0000_01_00_0
ID_PATH=pci-0000:01:00.0
ID_PATH_TAG=pci-0000_01_00_0
MAJOR=226
MINOR=0
SEQNUM=3084
SUBSYSTEM=drm
TAGS=:master-of-seat:seat:uaccess:
USEC_INITIALIZED=10672343

```

Another source I found had this syntax but didn't work either: HOTPLUG=="1"

I couldn't find info on which keys are adressed with ENV or ATTR or ATTRS and which aren't.



(2) I also tried to get the script to run when I login by putting this into my /etc/lightdm/lightdm.conf
```
[SeatDefaults]
greeter-session=unity-greeter
user-session=ubuntu
# for your login screen, e.g. LightDM (Ubuntu 11.10) or GDM (11.04 or earlier)
#display-setup-script=/usr/share/mycustomloginvideo.sh
# for your desktop session
session-setup-script=/usr/share/mycustomdesktopvideo.sh

```

It has no effect either, it DID however lead to the greeter to crash/loop when I hadn't included the return true part in my script yet (so it returned an error code when the TV wasn't connected). 


Any help would be greatly appreciated! Ubuntu 16.04 LTS

---

### Post by barrywhyte on 2017-07-07
I was able to solve (2) 

Apparently calling xrandr in a session-setup-script is too early, I just added my script as a startup application.

As for the udev thing... does noone know? Only 1 View after a day...?

---

