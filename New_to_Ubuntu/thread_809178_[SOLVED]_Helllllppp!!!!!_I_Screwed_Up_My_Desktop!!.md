---
title: "[SOLVED] Helllllppp!!!!! I Screwed Up My Desktop!!!"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by appoloin on 2008-05-27
I dont know what i have done. but seems like ubuntu is not using my Nvidia 8400GS anymore. everything ig BIG!! I tried reinstalling the driver 5x but it seems like it does no effect 

screen resolution 800 x600 nothing higher PLEASE HELP ME!!! I DONT WANNA FORMAT AGAIN!!! WAHHHHHHHH!!!!!!!!!!!

---

### Post by philinux on 2008-05-27
This may help. The app is in Other. You have to enable it. 

Or use.

gksu displayconfig-gtk

---

### Post by appoloin on 2008-05-27
This may help. The app is in Other. You have to enable it.  <<<<<===what you mean?

gksu displayconfig-gtk  <===this only go as high as 800 x600 and i cant set it to my video card

---

### Post by housam on 2008-05-27
try this way 

```
sudo nano /etc/usplash.conf
```
 you will got something like that 


> # Usplash configuration file
# These parameters will only apply after running update-initramfs.
  

add the required resolution 

> # Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=[COLOR="Red"]1280[/COLOR]
yres=[COLOR="red"]1024[/COLOR] 
 


OR put the settings you want for [COLOR="red"]x & y[/COLOR] then reboot and type :


```
sudo dpkg-reconfigure usplash
```
 then check for the new settings -- System > Preferences > Screen Resolution and select the new one.
__________________

---

### Post by appoloin on 2008-05-27
That did not work too :(

Is there a way that i can remove all drivers and just re-install the Nvidia driver again?

---

### Post by appoloin on 2008-05-27
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=1024

^x
^X

^X
Exit


xres=1280
yres=1024  but resolution still 800 x 600

---

### Post by alienexplorers on 2008-05-27
Try running nvidia-xconfig.

---

### Post by appoloin on 2008-05-27
I tried it and i get this

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 


ed@ed-desktop:~$ nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.


ERROR: Unable to write to directory '/etc/X11'.

ed@ed-desktop:~$ sudo nvidia-xconfig

Using X configuration file: "/etc/X11/xorg.conf".

WARNING: The CorePointer device was not specified explicitly in the layout;
         using the first mouse device.


WARNING: The CoreKeyboard device was not specified explicitly in the layout;
         using the first keyboard device.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'


restarted and still same. OH MY GOD Dont tell me i need to format again

---

### Post by philinux on 2008-05-27
Should not need to reinstall to sort this out.

---

### Post by housam on 2008-05-27
try to reinstall the [[COLOR="Red"]_Nvidia drivers _[/COLOR]]("http://www.psychocats.net/ubuntu/nvidia")again.

---

### Post by appoloin on 2008-05-27
i have re-installed the driver again and now its only running 640 x 480

---

### Post by philinux on 2008-05-27
What shows under

System>Admin>Hardware Drivers

---

### Post by housam on 2008-05-27
try this :

```
Option  "DDC" "No"
```

in Section "Device" in the file /etc/X11/xorg.conf. This works with the open source radeon driver.

You can edit the file from the terminal with nano,


```
sudo nano -B /etc/X11/xorg.conf
```

---

