---
title: "HowTo: Run Mathematica 7 and Matlab R2008a as a regular, unprivileged user"
date: 2009-02-19
forum: Outdated Tutorials &amp; Tips
---

### Post by sarang on 2009-02-19
**Update (May 24, 2009):**
It appears that there is no need for performing these steps to get Mathematica 7 and Matlab to run well on Ubuntu Jaunty 9.04

**What Works:**
Running Mathematica 7 and Matlab R2008a with GUI under Gnome, KDE and also under tiling window managers like 'Awesome Window Manager'.

**What Doesn't Work:**
Everything seems to be working properly now.

**Tested on:**
Ubuntu 8.10 Intrepid Ibex with sun-java6-jre
Debian 5 Lenny with sun-java6-jre

**Steps**
[LIST]
[*]If you have previously had the problem of Java windows appearing as gray rectangles instead of actual windows and have solved it by
```
export AWT_TOOLKIT=MToolkit
``` undo that change. That is, make sure that the environment variable AWT_TOOLKIT is not set.
[*]Install the [FONT=Courier New]dwm-tools[/FONT] package to make Java stop misbehaving: ```
sudo apt-get install dwm-tools
```
[*]Create the file [FONT=Courier New]/etc/init.d/matlab_mathematica_env[/FONT] and paste into it the following contents:
```

#!/bin/bash

# Helps for tiling window managers
correct_wm_name ()
{
wmname LG3D
}

mount_dev_pts ()
{
if [ ! -e /dev/pts ]
then
echo "Creating mountpoint /dev/pts..."
mkdir /dev/pts
fi

if [ "$(mount | grep -P ^.*/dev/pts.*$)" == "" ]
then
echo "/dev/pts was not mounted before. Attempting mount..."
mount -t devpts -o users,dev devpts /dev/pts 
fi
}


mount_dev_shm ()
{
if [ ! -e /dev/shm ]
then
echo "Creating mountpoint /dev/shm..."
mkdir /dev/shm
fi


if [ "$(mount | grep -P ^.*/dev/shm.*$)" == "" ]
then
echo "/dev/shm was not mounted before. Attempting mount..."
mount -t tmpfs -o users,dev tmpfs /dev/shm
fi
}

umount_dev_pts ()
{
if [ "$(mount | grep -P ^.*/dev/pts.*$)" != "" ]
then
echo "/dev/pts was mounted before. Attempting unmount..."
umount /dev/pts
fi
}

umount_dev_shm ()
{
if [ "$(mount | grep -P ^.*/dev/shm.*$)" != "" ]
then
echo "/dev/shm was mounted before. Attempting unmount..."
umount /dev/shm
fi
}


if [ "$(id -u)" != "0" ]
then
echo "You need to run this script as root."
echo "Hint: use sudo"
exit 1
fi


case "$1" in
  start)
    echo "Correcting WM name..."
    correct_wm_name
    echo "Finished correcting WM name."
    echo "Mounting tmpfs to /dev/shm..."
    mount_dev_shm
    echo "Finished mounting /dev/shm."
    echo "Mounting devpts to /dev/pts..."
    mount_dev_pts
    echo "Finished mounting /dev/pts."
    ;;
  stop)

    echo "Unmounting /dev/pts..."
    umount_dev_pts
    echo "Finished unmounting /dev/pts."
    echo "Unmounting /dev/shm..."
    umount_dev_shm
    echo "Finished unmounting /dev/shm."
    ;;
  restart|force-reload)
    $0 stop
    $0 start
    ;;
  status)
    mount
    ;;
  *)
    N=/etc/init.d/matlab_mathematica_env
    # echo "Usage: $N {start|stop|restart|reload|force-reload|status}" >&2
    echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0

```
[*]Make it executable by running ```
sudo chmod +x /etc/init.d/matlab_mathematica_env
```
[*]Add it to multi-user run-levels by running ```
sudo update-rc.d matlab_mathematica_env defaults
```
[*]Reboot or run ```
sudo /etc/init.d/matlab_mathematica_env start
```
[*]Launch Mathematica and Matlab like any other program and they should work.
[/LIST]

**Troubleshooting**
[LIST]
[*]If you see only gray rectangles instead of Java windows even after following all the above steps, your window manager name as seen by Java has not been corrected. Just open a terminal and run [FONT="Courier New"]wmname LG3D[/FONT] and all Java windows opened after that should open just fine.
[/LIST]

---

