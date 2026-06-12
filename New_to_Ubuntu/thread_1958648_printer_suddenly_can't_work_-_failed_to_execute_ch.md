---
title: "printer suddenly can't work - failed to execute child process"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by Rrory on 2012-04-14
My HP officjet which always worked perfectly suddenly stopped. I went to system settings and clicked on printers and got this message:

could not launch printers
Failed to execute child process
su-to-root (no such directory)

on two computers 11.10 can't even find my wireless network. On this one I get the above message.
 heelp please
rory

---

### Post by daslinkard on 2012-04-14
I'm thinking this sudo command will work:

```
sudo apt-get --reinstall install hplip hplip-cups hplip-data
```

If this doesn't automatically fix it, try rebooting the machine and try again.

---

### Post by Rrory on 2012-04-14
okay did that, pasted in my terminal, rebooted, added my printer, and when I try to print it says:

printer not connected

arrgh...

---

### Post by daslinkard on 2012-04-17
Have you tried using a different USB cable by chance?

---

### Post by daslinkard on 2012-04-17
Please try the following and let me know what you get...

[LIST=1]
[*]Make sure that the printer is connected to your system and powered on. 
[*]Open a terminal/console and check if the usb kernel modules are loaded: 
 $ lsmod | grep usb 
[*]Unplug the USB printer cable from your computer and enter this command: 
 $ tail -f /var/log/syslog  
[*]Reconnect the USB printer cable, you should see some messages appearing. 
[*]Press Ctrl-C to stop the logging. 
[*]Check  whether the printer gets correctly detected by the USB subsystem and  determine its USB vendor/product IDs and the USB bus and device  addresses: 
 $ lsusb 
 Note: The USB bus and device addresses change if you turn off or unplug the printer. Please re-run this command if needed. 
[*]Check  whether the device files for the printer get created and the ownerships  ("root lp") and permissions (non-HP: "crw-rw-r--", HP: "crw-rw-r--+")  correctly set: 
 $ ls -l /dev/usb/lp* /dev/bus/usb/*/* 
[*]Determine the printer's device ID strings: 
 $ sudo usb_printerid /dev/usb/lp0 
 $ sudo usb_printerid /dev/usb/lp1 
 ... 
 For HP printers also use 
 $ hp-info -i 
 and choose the printer with the problem from the text menu, then copy  the "deviceid" entry from the output (can be several lines). 
[*]For HP printers: Check whether HPLIP connects to them: 
 $ hp-makeuri <Bus>:<Device> 
 Replace "<Bus>" and "<Device>" by the bus and device  numbers from the "lsusb" output (not vendor and product ID). The numbers  must be supplied with three digits, zero-padded from the left, like  "008:015". 
[*]Find out if your printer gets detected by CUPS: 
 $ lpinfo -v
[/LIST]

---

### Post by Rrory on 2012-04-17
woah, tried 
 1.
 2.
 and even under 8. this option:  $ hp-info -i

all I get for all three is : command not found

this is so weird....

---

### Post by Rrory on 2012-04-17
re-booting didn't help. I still get the same : command not found.

meant to say my HP officejet 6500 is wireless.  My computers recognize the printer but there is no link configuration and my printer's status is disconnected. 

It's so weird as this suddenly happened to all 3 of my computers which all run Ocelot. In the past, the few times I had printing problems, I'd go to system settings - printers then delete and then re-add my printer; not this time.

---

