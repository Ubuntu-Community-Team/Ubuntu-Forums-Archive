---
title: "nvidia settings save"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by Zopiac on 2008-05-20
so i changed my resolution in the nvidia settings window, clicked apply, then save to x configurations, but when i try to save, it says that it cannot write to it...perhaps i need to run the settings manager as root? it doesnt prompt for that...

well since i last restarted, when i open the config it says: 

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

so i say in terminal:

zopiac@zopiac-secondary:~$ sudo nvidia-xconfig
[sudo] password for zopiac: 

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


????

---

### Post by iaculallad on 2008-05-20
What if you do this since I don't know the exact configured device on your xorg.conf.


On your terminal issue the command: 

Backup the xorg.conf first, we'll be using it later:
**sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak**

Then, to re-configure the xorg.conf file to re-generate the xorg.conf with your valid device:
**sudo dpkg-reconfigure -phigh xserver-xorg**

Then, open both your newly created xorg.conf and the xorg.conf.bak. Copy the valid driver line and paste it on your xorg.conf.bak.
Save your xorg.conf.bak overwriting xorg.conf

sudo cp etc/X11/xorg.conf.bak etc/X11/xorg.conf

---

### Post by noynac on 2008-05-20
There are a number of way to fix things. I would backup xorg.conf and then run the following command in a terminal window:

sudo dpkg-reconfigure -phigh xserver-xorg

You should now have a generic xorg.conf file. After restarting, install the proprietary nvidia driver using the hardware driver tool. You can then run 'sudo nvidia-settings' and save whatever setting you decide on to the xorg.conf file.

---

