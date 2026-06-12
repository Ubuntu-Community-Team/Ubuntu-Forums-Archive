---
title: "Video is completely messed up after update in 8.04"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by RedRat on 2008-10-15
OK this morning I had a synaptic update (not an upgrade). After the update, I had to reboot and now my graphics mode is completely botched. I have a nvidia 8600 GT card which is not being detected. I am in a strange resolution. I have downloaded and installed the nvidia-glx-new-envy driver. When I attempt to run nvidia-settings I get the message:
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

when I run I get this:
Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

What do I do now???

---

### Post by fooman on 2008-10-15
if your going to use the envy driver...then shouldn't you be using envy to install it?

i would uninstall the driver you installed,  then install envyng-gtk and use that to get the drivers installed.

```
sudo apt-get install envyng-gtk
```

then look in applications > system tools > envyng

click on envy and follow the prompts to install the nvidia driver.

if you don't want to use envy,  then uninstall the drivers you installed and install the "nvidia-glx-new" driver from synaptic or in a terminal:

```
sudo apt-get install nvidia-glx-new
```

see if that makes any difference.

---

