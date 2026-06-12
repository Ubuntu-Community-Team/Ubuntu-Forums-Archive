---
title: "[SOLVED] virtualbox in intrepid"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-11-20
i cannot get my usb devices to mount. they show up in my drop down but are blacked out. anyone know a solution?

---

### Post by silverglade00 on 2008-11-20
Try adding this to the bottom of your /etc/fstab

```

# Added for USB support in VirtualBox
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0


```

You will need to reboot unless someone else knows a way to reload fstab without rebooting.

---

### Post by PatrickMoore on 2008-11-20
still nothing

---

### Post by drs305 on 2008-11-20
Check out this thread (works for Intrepid too): [http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html]("http://www.ubuntu-unleashed.com/2008/04/howto-install-virtualbox-in-hardy-heron.html")

I think I made the changes to fstab.

Once you have followed the thread, you mount the USB devices via the main VB menu, Devices. If you highlight USB Devices it should expand to show any connected usb devices. Click on the device to enable it. Enabled USB devices will have a check mark next to them.

---

### Post by PatrickMoore on 2008-11-20
heres my issue though when i edit my mountdevsubfs it looks like this

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          mountdevsubfs
# Required-Start:    mountkernfs
# Required-Stop:
# Should-Start:      udev
# Default-Start:     S
# Default-Stop:
# Short-Description: Mount special file systems under /dev.
# Description:       Mount the virtual filesystems the kernel provides
#                    that ordinarily live under the /dev filesystem.
### END INIT INFO
#
# This script gets called multiple times during boot
#

PATH=/lib/init:/sbin:/bin
TTYGRP=5
TTYMODE=620
[ -f /etc/default/devpts ] && . /etc/default/devpts

TMPFS_SIZE=
[ -f /etc/default/tmpfs ] && . /etc/default/tmpfs

KERNEL="$(uname -s)"

. /lib/lsb/init-functions
. /lib/init/mount-functions.sh

do_start () {
	#
	# Mount a tmpfs on /dev/shm
	#
	SHM_OPT=
	[ "${SHM_SIZE:=$TMPFS_SIZE}" ] && SHM_OPT=",size=$SHM_SIZE"
	domount tmpfs shmfs /dev/shm tmpfs -onosuid,nodev$SHM_OPT

	#
	# Mount /dev/pts. Master ptmx node is already created by udev.
	#
        domount devpts "" /dev/pts devpts -onoexec,nosuid,gid=$TTYGRP,mode=$TTYMODE
        
	

}

case "$1" in
  "")
	echo "Warning: mountdevsubfs should be called with the 'start' argument." >&2
	do_start
	;;
  start)
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: mountdevsubfs [start|stop]" >&2
	exit 3
	;;
esac

```

```
#
# Magic to make /proc/bus/usb work
#
#mkdir -p /dev/bus/usb/.usbfs
#domount usbfs "" /dev/bus/usb/.usbfs -obusmode=0700,devmode=0600,listmode=0644
#ln -s .usbfs/devices /dev/bus/usb/devices
#mount --rbind /dev/bus/usb /proc/bus/usb
``` is just not there

---

### Post by drs305 on 2008-11-20
I had those lines in earlier releases but do not have it in my current Intrepid setup. Apparently they are not necessary, as I have USB working fine.

**ADDED:** I think when I used that link I had to complete the section:
*If the above doesnt work try rebooting, if that doesnt enable usb you can try this:*

Note: I am using Intrepid and running an XP VM. Also note you have to enable USB via the Settings menu.

---

### Post by PatrickMoore on 2008-11-20
> **drs305 said:**
> I had those lines in earlier releases but do not have it in my current Intrepid setup. Apparently they are not necessary, as I have USB working fine.

did you have to modify anything?

---

### Post by stephanvaningen on 2008-11-20
> **silverglade00 said:**
> Try adding this to the bottom of your /etc/fstab

```

# Added for USB support in VirtualBox
none /proc/bus/usb usbfs devgid=126,devmode=664 0 0


```

You will need to reboot unless someone else knows a way to reload fstab without rebooting.

sudo mount -a

---

### Post by PatrickMoore on 2008-11-20
> **stephanvaningen said:**
> sudo mount -a

i added the line to my mountdevsubfs and it works like a pro thanks guys

---

