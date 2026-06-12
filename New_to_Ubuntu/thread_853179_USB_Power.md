---
title: "USB Power"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by BDNiner on 2008-07-08
I wanted to know if there is a way to set the power settings for devices such as the USB ports. I use the port to charge various devices like my phone and mp3 player. but when the computer goes to sleep the ports get turned off. I would like them to stay on so that i don't have to sit by the computer while the devices are charging.

---

### Post by ARhere on 2008-07-08
The only way to do that is modify a USB driver so it ignores the low power state command.  There is a surprising amount of data on the web about hacking USB drivers for Linux, might be a fun project.  The other option is to simply set your PC _not_ to goto sleep.

System-->Preferences-->Power Management

If you are worried about access to your PC, enable locking of the desktop when the screen saver comes on.

-AR

---

### Post by ARhere on 2008-07-08
Another easier option is to get an AC-USB adapter.

[Here are some examples.]("http://www.google.com/products?q=USB+power+adapter&ie=UTF-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&um=1&sa=X&oi=product_result_group&resnum=1&ct=title")

-AR

---

### Post by BDNiner on 2008-07-08
Well i have an AC charger for my blackberry, but i don't have a charger for my mp3 player. i was hoping that since they are both USB devices then the charger would be the same but i don't want to try just to find out. I was hoping that there was something along the line of what you find in XP where you can set any device not to turn off during power saving.

---

### Post by ARhere on 2008-07-08
If the power plug to your portable devices is USB, then you can swap adapters.  Otherwise I would not exchange AC adapters from one device to another unless you are **certain** they have the same voltage and power demands.

I found this interesting bit for you on manually controlling the ACPI on USB devices.  [Check out the full web site here.]("http://www.mjmwired.net/kernel/Documentation/usb/power-management.txt")
```
105		The user interface for dynamic PM
106		---------------------------------
107	
108	The user interface for controlling dynamic PM is located in the power/
109	subdirectory of each USB device's sysfs directory, that is, in
110	/sys/bus/usb/devices/.../power/ where "..." is the device's ID.  The
111	relevant attribute files are: wakeup, level, and autosuspend.
112	
113		power/wakeup
114	
115			This file is empty if the device does not support
116			remote wakeup.  Otherwise the file contains either the
117			word "enabled" or the word "disabled", and you can
118			write those words to the file.  The setting determines
119			whether or not remote wakeup will be enabled when the
120			device is next suspended.  (If the setting is changed
121			while the device is suspended, the change won't take
122			effect until the following suspend.)
123	
124		power/level
125	
126			This file contains one of three words: "on", "auto",
127			or "suspend".  You can write those words to the file
128			to change the device's setting.
129	
130			"on" means that the device should be resumed and
131			autosuspend is not allowed.  (Of course, system
132			suspends are still allowed.)
133	
134			"auto" is the normal state in which the kernel is
135			allowed to autosuspend and autoresume the device.
136	
137			"suspend" means that the device should remain
138			suspended, and autoresume is not allowed.  (But remote
139			wakeup may still be allowed, since it is controlled
140			separately by the power/wakeup attribute.)
141	
142		power/autosuspend
143	
144			This file contains an integer value, which is the
145			number of seconds the device should remain idle before
146			the kernel will autosuspend it (the idle-delay time).
147			The default is 2.  0 means to autosuspend as soon as
148			the device becomes idle, and -1 means never to
149			autosuspend.  You can write a number to the file to
150			change the autosuspend idle-delay time.
151	
152	Writing "-1" to power/autosuspend and writing "on" to power/level do
153	essentially the same thing -- they both prevent the device from being
154	autosuspended.  Yes, this is a redundancy in the API.

```

It looks pretty straight forward so give it a go and let me know if it works.
-AR

---

### Post by BDNiner on 2008-07-09
uuuummmm how do i know what each port's device ID is? i guess i will have to use trial and error to figure it out.

---

### Post by ARhere on 2008-07-09
> **BDNiner said:**
> uuuummmm how do i know what each port's device ID is? i guess i will have to use trial and error to figure it out.

```
lsusb
```
or
```
lspci
```
That's how.  ;-)
-AR

---

### Post by BDNiner on 2008-07-09
ok, i knew that much, i guess i have to plug a device into each port and then run lsusb to see which physical port is assigned which device ID. i will try that out when i get back home.

---

### Post by gefthebest on 2011-09-28
Hi,

I don't know if any body still looks at those posts but I am interested in the answer for ubuntu 11.04..
So far I've seen and read:


But no luck on this new ubuntu version
[http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/](http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/)
[http://www.ehow.com/how_7536984_configure-power-usb-ubuntu.html](http://www.ehow.com/how_7536984_configure-power-usb-ubuntu.html)
[http://www.linuxforums.org/forum/miscellaneous/98253-turn-off-power-usb-port.html](http://www.linuxforums.org/forum/miscellaneous/98253-turn-off-power-usb-port.html)
[http://www.linuxquestions.org/questions/linux-software-2/howdoi-turn-on-off-usb-light-by-time-514863/](http://www.linuxquestions.org/questions/linux-software-2/howdoi-turn-on-off-usb-light-by-time-514863/)
[http://ubuntuforums.org/showthread.php?t=327138](http://ubuntuforums.org/showthread.php?t=327138)

Any help would be appreciated, thanks alot!

---

### Post by Sergio_ on 2011-12-01
> **gefthebest said:**
> Hi,

I don't know if any body still looks at those posts but I am interested in the answer for ubuntu 11.04..
So far I've seen and read:


But no luck on this new ubuntu version
[http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/](http://www.linuxquestions.org/questions/debian-26/power-off-usb-509328/)
[http://www.ehow.com/how_7536984_configure-power-usb-ubuntu.html](http://www.ehow.com/how_7536984_configure-power-usb-ubuntu.html)
[http://www.linuxforums.org/forum/miscellaneous/98253-turn-off-power-usb-port.html](http://www.linuxforums.org/forum/miscellaneous/98253-turn-off-power-usb-port.html)
[http://www.linuxquestions.org/questions/linux-software-2/howdoi-turn-on-off-usb-light-by-time-514863/](http://www.linuxquestions.org/questions/linux-software-2/howdoi-turn-on-off-usb-light-by-time-514863/)
[http://ubuntuforums.org/showthread.php?t=327138](http://ubuntuforums.org/showthread.php?t=327138)

Any help would be appreciated, thanks alot!


SAME HERE! I use my laptop to charge my phone and other devices, and I would like to left powered an USB port when suspended, better so if possible when laptop is turn off, like a PC

---

