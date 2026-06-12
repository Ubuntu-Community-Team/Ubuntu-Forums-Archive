---
title: "touchpad taps"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by raequin on 2008-05-22
Hi, all. I have been trying since installation of Hardy to get my touchpad working well when I type. I have edited xorg.conf, as shown below. Syndaemon has no effect when I run it. Also, System->Preferences->Mouse changes nothing, even when I uncheck the box "enable touchpad."

There are only two things that I can do to affect the touchpad, use Fn+F7 that is the touchpad on / off button that came with the laptop (an Acer), or use Mousetweaks pointer capture on the panel.

I would like to be able to either turn off the touchpad with either keyboard shortctus or by terminal command (which maybe I could bind to a keyboard shortcut), or get syndaemon working so that I can type without worrying about the touchpad.

Here is a part of xorg.conf:

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
Option "SHMConfig" "on"
# Option "MaxTapTime" "0"
EndSection

"MaxTapTime" did nothing either, so I commented it out. Nothing I do in gsynaptics has any effect.

I tried installing gsynaptic, and received the following message:

sudo apt-get install gsynaptic
...
Reading state information... Done
Note, selecting synaptic instead of gsynaptic
synaptic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I have also tried the following line instead of what is posted above, in xorg.conf:
Option "SHMConfig" "true"

---

### Post by dark_harmonics on 2008-05-30
it should be qsynaptics not gsynaptics. Tapping on my macbook pro works by default. Are you trying to turn it off? If so check this link [http://blog.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/](http://blog.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/)

---

### Post by raequin on 2008-05-30
> **dark_harmonics said:**
> it should be qsynaptics not gsynaptics. Tapping on my macbook pro works by default. Are you trying to turn it off? If so check this link [http://blog.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/](http://blog.rvdavid.net/disabling-the-laptop-touchpad-in-ubuntu-linux/)

Thanks.  I followed that post, but I am having a problem with qsynaptics.

bash: qsynaptics: command not found

When I installed it with aptitude, I received an error relating to timidity.  I installed Ubuntu Studio with apt, and timidity didn't install correctly or something.  Anyway I didn't like Ubuntu Studio and so I uninstalled it with apt.  I used synaptic to totally remove timidity.  Then I entered

$sudo aptitude get install qsynaptics

again.  After this I still got the bash message.  Why isn't "qsynaptics" found?
```
~$ sudo aptitude install qsynaptics
[sudo] password for rae: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for qsynaptics
No candidate version found for qsynaptics
The following partially installed packages will be configured:
  timidity 
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up timidity (2.13.2-19ubuntu1) ...
 * Starting TiMidity++ ALSA midi emulation...                            [fail] 
invoke-rc.d: initscript timidity, action "start" failed.
dpkg: error processing timidity (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 timidity
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
rae@rae-laptop:~$ qsynaptics
bash: qsynaptics: command not found
rae@rae-laptop:~$ qsynaptics
bash: qsynaptics: command not found
rae@rae-laptop:~$ sudo aptitude install qsynaptics
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
rae@rae-laptop:~$ sudo aptitude install qsynaptics
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
No candidate version found for qsynaptics
No candidate version found for qsynaptics
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
rae@rae-laptop:~$ qsynaptics
bash: qsynaptics: command not found

```

Looking back over that code, I thought maybe it's because I do not have the correct repositories enabled.  But if qsynaptics only operates as a GUI then I wouldn't really want it anyway.  I mean, if I was okay with taking my hands from the home position I could use Mousetweaks.

Getting syndaemon (or the like) working would be best.  Second best would be a command to disable the touchpad (like synclient TouchPadOff=1).

Thanks.

---

### Post by Technoviking on 2008-05-30
Check here
[http://ubuntuforums.org/showthread.php?t=271052](http://ubuntuforums.org/showthread.php?t=271052)

---

