---
title: "Turn off bluetooth?"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by cacs on 2011-12-18
Hi.
Since the 11.10 upgrade my bluetooth is always **on** when I torn on the pc. Is there a way to turn it off automatically?
Ty, C.S.

---

### Post by Rex Bouwense on 2011-12-18
I'm not sure where it is in Ubuntu but there should be a tab under system tools or preferences that is start-up applications.  Just un-tick bluetooth manager or whatever it happens to be called.  I am not using Unity so I don't know the exact terminology.

---

### Post by 2F4U on 2011-12-18
Open /etc/default/bluetooth with an editor of you choice and set

BLUETOOTH_ENABLED=1

to 

BLUETOOTH_ENABLED=0

---

### Post by audiomick on 2011-12-18
System settings in Unity is one of the options in the list you get when you click on the shut down icon in the top bar.

Startup programes is in there, and the option to not start the bluetooth program at start is in there.

---

### Post by audiomick on 2011-12-18
> **2F4U said:**
> Open /etc/default/bluetooth with an editor of you choice and set

BLUETOOTH_ENABLED=1

to 

BLUETOOTH_ENABLED=0
That will be needed to be done with "sudo". The directory /etc belongs to root.

---

### Post by cacs on 2011-12-18
> **audiomick said:**
> That will be needed to be done with "sudo". The directory /etc belongs to root.

Ty guys. It's disable! :)

---

### Post by cacs on 2011-12-18
> **audiomick said:**
> System settings in Unity is one of the options in the list you get when you click on the shut down icon in the top bar.

Startup programes is in there, and the option to not start the bluetooth program at start is in there.

There's no bluetooth in my startup applications...
Now it's disable!
Ty

---

