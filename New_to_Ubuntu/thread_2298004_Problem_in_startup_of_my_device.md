---
title: "Problem in startup of my device"
date: 2015-10-08
forum: New to Ubuntu
---

### Post by Danial_Rana on 2015-10-08
I am using a device ESX-TC3G device which contains ubuntu operating system.
I wanted to run an application at the startup of the device so i modified the contents of rc.local script at /etc/init.d.
Now the problem is on startup that application runs and hangs my device thus preventing the startup operation. Kindly tell me any method of reset that will not delete all the data from my device.

---

### Post by tgalati4 on 2015-10-08
How do you connect to this [device]("http://www.stw-technic.com/new-products/esx-tc3g/") to program it initially? Is there a provision to perform a factory reset?

Normally, one would mount the disk (1 GB flash NAND in this case) on another linux machine, navigate to /etc/rc.local and comment out the pathological code.  The script in /etc/init.d/rc.local is a specialized script to detect and run /etc/rc.local (if it exists) and modify Use Cases as to when to run it and at what Run Level.  I wouldn't modify it.  I would only put scripts in /etc/rc.local.

---

### Post by Danial_Rana on 2015-10-08
I use Gktterm to program the device, now the problem is the device automatically goes into a loop or something and doesn't break the instructions and the device doesn't even starts.

---

### Post by tgalati4 on 2015-10-08
Sometimes you can issue a Control-C to break a bootup loop.  Can you see the 1 GB flash if you plug into the JTAG or USB port of the device?  If so, then simply delete the rc.local file.  Perhaps there is a new firmware flash for this device, that would wipe the device and start from scratch.  Contract the manufacturer.

If the device has a JTAG or USB port, then plug a keyboard into it to issue the Control-C.

---

### Post by Danial_Rana on 2015-10-11
Thanks

---

