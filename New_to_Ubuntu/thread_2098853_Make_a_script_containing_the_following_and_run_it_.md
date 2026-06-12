---
title: "Make a script containing the following and run it on startup"
date: 2012-12-27
forum: New to Ubuntu
---

### Post by heatpumpcontrol on 2012-12-27
Hi,

I'm trying to get my PCI-E USB 3.0 to work. I found this in AskUbuntu but don't know how to go about it...

> Make a script containing the following and run it on startup:

cd /sys/bus/pci/drivers/ehci_hcd/

sudo sh -c 'find ./ -name "0000:00:*" -print| sed "s/\.\///">unbind'

That should solve the problem.

Source: here


Thx

Running 12.10

---

### Post by mtreece on 2012-12-27
Drop whatever commands you want ran on startup into /etc/rc.local.

Try running this:

```
gksudo gedit /etc/rc.local
```

Just make sure > exit 0 is the last thing in the script.

---

### Post by heatpumpcontrol on 2012-12-27
> **mtreece said:**
> Drop whatever commands you want ran on startup into /etc/rc.local.

Try running this:

```
gksudo gedit /etc/rc.local
```

Just make sure  is the last thing in the script.

Thanks.. that didn't work.. bad command maybe.. ?

---

### Post by mtreece on 2012-12-27
Did you get an error message?

The goal of the gksudo gedit command was just to open the file, /etc/rc.local, in a file-editor so you can add commands to that file.

---

### Post by heatpumpcontrol on 2012-12-28
> **mtreece said:**
> Did you get an error message?

The goal of the gksudo gedit command was just to open the file, /etc/rc.local, in a file-editor so you can add commands to that file.

Oh sorry, your command did help. It was the script that didn't work. Ubuntu doesn't seem to support this PCI-E USB 3.0 adaptor. It works in Windows. Logged in that environment just to check and do a bios update.. Boy, havent been in Windows in a while. lol 

The PCI-E card has power on bios boot but is turned off by Ubuntu upon boot.

I can't find any support or threads.

Thank you

---

