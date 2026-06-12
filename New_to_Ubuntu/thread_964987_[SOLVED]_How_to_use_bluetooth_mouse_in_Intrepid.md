---
title: "[SOLVED] How to use bluetooth mouse in Intrepid"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by aridus on 2008-10-31
Hello All

I have made a fresh install of Intrepid on a Dell Latitude D830 and I have a logictech bluetooth mouse that I was able to use, on the same machine, with Ubuntu 8.04. However I cannot get the mouse to work. When I use Setup new device... from the bluetooth icon in the system tray there are no device listed for me to select, no matter how many times I switch the mouse on and off (and the batteries are new). I have been unable to figure out, from anywhere, how to fix this.

I would greatly appreciate any help from users more savvy than msyelf.

---

### Post by kWahab on 2008-10-31
I had a similar issue. 

In hardy I would just enable the input service from the services tab and add my device to the input service device list.

But ibex is missing the services tab entirely. The following finally worked for me.

- deleted my input device from the Known devices list.  
- typed this in a terminal (to start the bluetooth input service)
```
dbus-send --system --type=method_call --dest=org.bluez /org/bluez/service_input org.bluez.Service.Start
```

- added the device using the "Setup new device ..." wizard. 

Haven't restarted the system yet but have a feeling that this fix won't survive a reboot.

Hope it helps.

---

### Post by aridus on 2008-10-31
Many thanks. This does nothing for me, and my mouse doesn't yet appear in the list of known devices (either before or after). Any idea what happened to hidd? I used to be able to use 

sudo hidd --search 

but now the command is no longer recognized.

With thanks.

---

### Post by nhasian on 2008-10-31
This might be a silly question, but did you set your mouse to pairing mode before you clicked on Setup new Device?  

> **aridus said:**
> I cannot get the mouse to work. When I use Setup new device... from the bluetooth icon in the system tray there are no device listed for me to select, no matter how many times I switch the mouse on and off

---

### Post by aridus on 2008-10-31
Hi
I don't know whether it is a silly question or not... but how would I do that?
With thanks.

---

### Post by sampi on 2008-11-01
It solved my problem.

I just clicked on my little on mouse "Connect" button and then started wizard.

Now working fine.

---

### Post by aridus on 2008-11-01
Thank you.
I clicked on a button underneath the mouse several times and it actually appeared in the box!
All now well. I am marking this as solved, therefore!
With thanks!

---

