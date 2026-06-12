---
title: "HOWTO: Get your joystick(s) working under Dapper"
date: 2006-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by techweenie on 2006-11-11
[COLOR=Red]NOTE: THIS IS NOT MY GUIDE. I FOUND IT[/COLOR][COLOR=Red] [HERE]("http://ubuntux.wordpress.com/2006/05/25/howto-get-joysticks-working-under-dapper/") AND AM REPOSTING IT AS A CONVENIENCE

[/COLOR]         Linux joystick support has always been sort of hit-or-miss: the support is definitely there, but you generally feel like you have to go through an arcane ritual every time you want your joystick or gamepad to actually work. Here’s a simple little script though which will let you ditch the tradition of waving a dead chicken in favor of a more Ubuntu-style “it just works” mentality.
  Open up a terminal window and change to the initscript directory:
 ```
cd /etc/init.d
``` Now, start a new file there named “joystick” as root:
 ```
sudo gedit ./joystick
``` Copy and paste the following shell script:
 ```
#! /bin/sh
# /etc/init.d/joystick
#
# Carry out specific functions when asked to by the system
# Must have 755 permissions
# To use, add to rc.d:  sudo update-rc.d joystick defaults
 case "$1" in
start)
echo “Enabling Joystick”
cd /dev/input
rm js*
cd ..
rm js*
mknod input/js0 c 13 0
ln -s input/js0 js0
modprobe joydev
modprobe analog
modprobe ns558
sleep 0.5
rmmod ns558
modprobe ns558
echo “DONE!”
;;
stop)
rmmod joydev
rmmod analog
rmmod ns558
echo “DONE!”
;;
*)
echo “Usage: /etc/init.d/joystick {start|stop}”
exit 1
;;
esac
exit 0
``` Save the file and close gedit. Next, follow the directions that were included in the comments of the script - change permissions to 755:
 ```
sudo chmod 755 joystick
``` And then set it up to run at startup:
 ```
sudo update-rc.d joystick defaults
``` To get joystick support working right away without having to reboot your computer, just run the script:
 ```
sudo /etc/init.d/joystick start
``` Now you should be all set. Keep in mind though that this only sets up a single joystick device; you’ll need to tweak the script a bit if you want two or more joysticks at the same time (you’ll need another mknod line for js1, and you’ll need to make another symlink from /dev/input/js1 to /dev/js1). The ns558 module gets loaded twice because some motherboards have timing issues that cause it to load incorrectly the first time.
 When combined with a console controller-to-usb adapter, this script can greatly enhance your enjoyment of emulated systems. If you’ve got a Playstation or PS2 lying around, I highly recommend the SmartJoy Dual Plus adapter (available from [Lik-Sang]("http://www.lik-sang.com/info.php?category=160&products_id=3176&PHPSESSID=7ea603012c897ea01a3d9c0bb8017548") or [Jandaman]("http://www.jandaman.com/games.mvc?p=psxsmartjoydualplus&Category_code=PC")), which lets you plug two Playstation-compatible controllers into a single USB port. There are other adapters available for XBox, GameCube, and even SNES controllers, so be sure to take advantage of hardware you already own.

---

### Post by Jojo12a on 2006-11-11
There's a much better solution for this, working in both dapper and edgy.

1. Create the file /etc/udev/rules.d/62-symlinks-user.rules as root:
```
sudo gedit /etc/udev/rules.d/62-symlinks-user.rules
```

2. Copy and Paste the following text into that file:
```
# Define user-defined symlinks here
KERNEL=="js[0-9]*", SYMLINKS+="%k"
```

3. Save and Exit.

Another possibility, which I personally use is editing the existing file /etc/udev/rules.d/60-symlinks.rules and attaching the lines shown above, but the solution explained here is a bit cleaner.

---

