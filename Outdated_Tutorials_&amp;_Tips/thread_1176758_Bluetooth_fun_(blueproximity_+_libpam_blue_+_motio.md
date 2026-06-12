---
title: "Bluetooth fun (blueproximity + libpam_blue + motion)"
date: 2009-06-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Boondoklife on 2009-06-02
Ok I seen some info here on blueproximity but nothing as far as libpam_blue or useful scripts, so I thought I would put up my own.

After this guide you will be able to:

[LIST=1]
[*]Login to you compouter with a bluetooth device
[*]Have your computer run commands when you leave and return to it
[*]Have an idea as to what is going on around your computer when you are not in front of it.
[/LIST]
Ok first here are the packages and what they do:

[LIST]
[*]blueproximity - Monitors the status of a bluetooth connection and acts when a particular device is in range or leaves said range.
[*]libpam_blue - Allows a user to login and skip certain password requests, ie. sudo, updater, gksu, etc.
[*]motion - allows you to use a webcam to "monitor" what is going on in front of it.
[/LIST]
First lets install the packages:```
sudo apt-get install blueproximity libpam_blue motion
```Next you will need to pair your device, in gnome you can do this by opening the bluetooth applet and pairing your device.


[SIZE=4]**BLUE PROXIMITY**[/SIZE]
Once your device is paired to the computer, then you want to fire up blueproximity;
Gnome Menu -> Applications -> Accessories -> Blueproximity

Click on the Blueproximity icon that will appear in your tray and from there you need to scan for your paired device, Make sure it is not currently connected as this can cause an issue. Once you see the device click it and then click "Use Selected Device", which will populate the MAC address field at the bottom. NOTE this MAC address as we will need it later.

Once you have the device setup you can flip to the proximity details page to setup the distance you wish to have trigger events, and then finally flip to the Locking tab. The locking tab is where you can specify what you want to happen when you come into range to leave. I have included the scripts that I am using for a base.

When I leave the computer:
```
#!/bin/bash

cd /home/YOURUSERNAMEHERE/Videos/SecurityCamera
amixer -c 0 set Master Playback mute
rhythmbox-client --no-start --pause
motion &> /dev/null &
gnome-screensaver-command -l
```When I come back to the computer:
```
#!/bin/bash

amixer -c 0 set Master Playback unmute
rhythmbox-client --no-start --play
killall motion
gnome-screensaver-command -d
```For those that want to know, when you leave the computer the script will change to the defined directory where motion should store its images, then mute the main speaker, then pause rhythmbox, then turn on motion, then lock the screen.

When you comeback it will, unmute the main speaker, unpause rhythmbox, stop the motion daemon, then unlock your screen.

You will want to paste the above scripts into a script file, might I suggest lock.sh and unlock.sh. Once you do this go into blueproximity and click the locking tab and replace the locking and unlocking commands with the scripts you made.

**NOTE:** Remember to make your scripts executeable
```
chmod +x lock.sh
chmod +x unlock.sh

```[B]
NOTE:[/B] If you are not using the motion package then just remove or comment out those lines.
**NOTE:** Unless you put the scripts in a place that is in your path you will have to give blueproximity the full path to your scripts: ex /home/USERNAME/lock.sh

[SIZE=4]**MOTION**[/SIZE]
Motion is the application that will allow you to use your webcam to take pictures of who or what is moving around your camera/computer.

This app really doesn't need any configuration, but you can edit /etc/motion/motion.conf and play with the settings if you like.

[SIZE=4]**LIBPAM-BLUE**[/SIZE]
This part will take care of logging you into your computer and letting you do those elevated functions, sudo, gksu, updates, with out the password prompt.

first you will need to edit /etc/pam.d/common-auth
```
sudo gedit /etc/pam.d/common-auth
```and you will want to add a line right above the line that looks like this:
```
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
```will now look like this:
```
auth    sufficient                      pam_blue.so
auth    [success=1 default=ignore]      pam_unix.so nullok_secure
```Then on to the last part which is adding your device to the list of used devices for your username.

```
sudo gedit /etc/security/bluesscan.conf
```Just clear out all of the entries and paste this into it:
```

general {
    timeout = 3;
}

YOURUSERNAMEHERE = {

    # bluetooth device name
    name    = DEVICENAME;

    # bluetooth mac address
    bluemac = DEVICEMAC;

    # a seaparate timeout
    timeout = 10;
}

```**NOTE: **Replace YOURUSERNAMEHERE with your username, DEVICENAME with the name of your bluetooth device that will be your authentication device, and replace DEVICEMAC with it's mac address. If you don't remember what they were then just open blueproximity and it will be listed in there.

Now reboot and enjoy the bluetooth fun!!!

---

