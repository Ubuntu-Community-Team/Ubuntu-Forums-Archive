---
title: "bluetooth keyboard with touchpad"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by bhuthogg on 2008-05-20
I have a bluetooth keyboard with touchpad (keysonic ack-b40bt).
I'm having a little trouble setting this up in Ubuntu and was wondering if anyone has an idea or guide of what i can do to pair it and get it working...

the bluetooth dongle is ok to go and recieve files etc but im new to pairing the KB requires passcode (ive had it running in windows)

also i have tryed this guide [http://ubuntuforums.org/showthread.php?t=586105](http://ubuntuforums.org/showthread.php?t=586105)
 

heres what happned

> brian@brian-laptop:~$ 00:18:00:00:64:98
bash: 00:18:00:00:64:98: command not found
brian@brian-laptop:~$ sudo hidd --connect 00:18:00:00:64:98





Can't get device information: Connection timed out
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ 
brian@brian-laptop:~$ sudo hidd --connect 00:18:00:00:64:98
brian@brian-laptop:~$ 0
bash: 0: command not found
brian@brian-laptop:~$ lsusb
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 1310:0001 Roper Class 1 Bluetooth Dongle
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
brian@brian-laptop:~$ hcitool dev
Devices:
	hci0	00:0B:0D:40:1B:9E
brian@brian-laptop:~$   sudo hidd --search
Searching ...
	No devices in range or visible
brian@brian-laptop:~$ hcitool dev
Devices:
	hci0	00:0B:0D:40:1B:9E
brian@brian-laptop:~$   sudo hidd --search
Searching ...
	Connecting to device 00:18:00:00:64:98
brian@brian-laptop:~$ sudo hidd --connect 00:18:00:00:64:98
HID create error 77 (File descriptor in bad state)
brian@brian-laptop:~$ sudo hidd --connect 00:18:00:00:64:98
HID create error 77 (File descriptor in bad state)
brian@brian-laptop:~$ sudo hidd --connect 00:18:00:00:64:98
HID create error 77 (File descriptor in bad state)
brian@brian-laptop:~$ 




thanks

b

---

### Post by alfonso78 on 2008-10-24
> **bhuthogg said:**
> I have a bluetooth keyboard with touchpad (keysonic ack-b40bt).
I'm having a little trouble setting this up in Ubuntu and was wondering if anyone has an idea or guide of what i can do to pair it and get it working...

the bluetooth dongle is ok to go and recieve files etc but im new to pairing the KB requires passcode (ive had it running in windows)

also i have tryed this guide [http://ubuntuforums.org/showthread.php?t=586105](http://ubuntuforums.org/showthread.php?t=586105)
 


Hi. Did you solve your issue? I'm having a similar one.
The error
```
HID create error 77 (File descriptor in bad state)
```
is because you are trying to connect more than once to the same device, in fact the error comes the 2nd time you type ```
sudo hidd --connect
``` so that's not really a problem.

The problem is that ```
sudo hidd --connect
``` does not report ANY error, but still the pairing doesn't work.

Even if I type a PIN on the keyboard, I don't get a prompt to repeat it in the linux box. Also, the standard PIN (1234) does NOT help.

Any idea?

alfonso

---

