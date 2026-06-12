---
title: "HOWTO: Speed up touchpad Dell XPS M1530 Ubuntu 8.10"
date: 2008-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by Den_Citronen on 2008-11-01
[SIZE="5"]Speed up touchpad on the DELL XPS M1530 Ubuntu 8.10[/SIZE]

[SIZE="4"]Please look here for a better solution: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame)[/SIZE]

*Created with the help of [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)*

Worked for me, lets hope it works for you too.

Open up a terminal and type:
```

gksudo gedit /etc/hal/fdi/policy/shmconfig.fdi
```

Paste this into the file:

```
<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>
```


Save the file. 

Type this into a terminal:
```
sudo apt-get install gsynaptics
```

Reboot your computer (the documentation suggests you log out, and back in. Didn't work for me, had to reboot.)

Go to System -> Preferences - Touchpad and edit the settings to your liking. 

Screenshot of my "Acceleration tab attached

---

### Post by hackel on 2008-12-22
This is certainly useful, and it's exactly what I have done, however it is not a real solution, merely a workaround.  For some reason, this touchpad just responds extremely slowly.  It seems like it must have something to do with the i8042.nomux kernel option that is requried for it to work properly.  I don't want to use "acceleration", I want the actual linear speed to be higher.  My Dell Mini touchpad does not have this problem--by default, it's not set to any acceleration at all, and the pointer is much faster and more responsive.  I don't know if this is simply because their are fewer pixels to transverse (my m1530 is 1920x1200), or because is has a real Synaptics touchpad insead of this ALPS piece of garbage they put in the much more expensive XPS laptop.  I just wish there was a real solution.

---

### Post by Den_Citronen on 2009-01-05
I found a better solution to the problem, here:
[https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#Touchpad%20speed%20is%20lame)

---

