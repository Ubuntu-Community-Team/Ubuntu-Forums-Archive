---
title: "mount point for wifi usb card"
date: 2012-06-27
forum: New to Ubuntu
---

### Post by emekadavid on 2012-06-27
when I slot in a wifi card into my laptop usb port, how do I verify where it is mounted to? I know that ubuntu can detect the card, because it is highlighted in the network manager, but I want to know the mount point ubuntu uses for it? I called the 'mount' command but could only find my usb drive mounted on /media/_cardname_ from /dev/sdb1 and not the wifi card. Newbie. Help.

---

### Post by sudodus on 2012-06-27
I don't think you mount a wifi card. You mount storage devices (hard disk drives, ssd drives, other flash drives, cd and dvd drives).

---

### Post by matt_symes on 2012-06-27
Hi
 
Udev should create a device node for it in /dev. Take a look in there.
 
You can also see all the connected USB devices using (from the terminal)
 
```
lsusb
``` 
 
You can check to see what the kernel did when mounting it by opeing a terminal and typing
 
```
 
tail -f /var/log/syslog

```
 
_Then_ plug the device in. As the kernel recognises the devices it will display a number of log messages that can tell you information about the device.
 
That should get you started.
 
Kind regards

---

### Post by emekadavid on 2012-06-27
then how do you access it from a terminal. i do not want to be using the gui network manager from the menu bar. i tried /dev and /etc/fstab and could not find it. 
tanx

---

### Post by sudodus on 2012-06-27
Are you curious about what is happening behind the GUI curtain? Or are you actually asking for help to get the connection working?

*Edit: OK, so you are curious about what is happening behind the GUI curtain. I guess it means that you can connect via the GUI, so that we know the device is cooperating with your Ubuntu system :-) I don't know the command line details, but I think *matt_symes* does.*

---

### Post by matt_symes on 2012-06-27
Hi
 
> **emekadavid said:**
> then how do you access it from a terminal. i do not want to be using the gui network manager from the menu bar. i tried /dev and /etc/fstab and could not find it. 
tanx
 
What exactly are you trying to do ?
 
Are you trying to connect to a wireless network using the device from the command line and not using the gui ? Why do you think you need it mounted for this.
 
Explain what you are trying to do and not what you think you need to do and we can take it from there.
 
You are really not clear in what you are asking advice and help for.
 
Kind regards

---

### Post by emekadavid on 2012-06-27
> **matt_symes said:**
> Hi
 
Udev should create a device node for it in /dev. Take a look in there.
 
You can also see all the connected USB devices using (from the terminal)
 
```
lsusb
```You can check to see what the kernel did when mounting it by opeing a terminal and typing
 
```
 
tail -f /var/log/syslog

```_Then_ plug the device in. As the kernel recognises the devices it will display a number of log messages that can tell you information about the device.
 
That should get you started.
 
Kind regards
thanks. that's what i wanted. lol

---

### Post by emekadavid on 2012-06-28
> **matt_symes said:**
> Hi
 

 
What exactly are you trying to do ?
 
Are you trying to connect to a wireless network using the device from the command line and not using the gui ? Why do you think you need it mounted for this.
 
Explain what you are trying to do and not what you think you need to do and we can take it from there.
 
You are really not clear in what you are asking advice and help for.
 
Kind regards
gui's mask what the system is doing when it starts up a device. that is what i wanted to know by using the terminal. somebody has already sent me the right way. tanx

---

### Post by matt_symes on 2012-06-28
Hi

> **emekadavid said:**
> gui's mask what the system is doing when it starts up a device. that is what i wanted to know by using the terminal. somebody has already sent me the right way. tanx

Ahh. I see. No problem. 

If you need any more help with that then post here and i'll explain how the kernel detects the device in kernel space, an event gets created that is picked up in user space, a driver gets loaded in user space, udev creates a device node.....

Kind regards

---

