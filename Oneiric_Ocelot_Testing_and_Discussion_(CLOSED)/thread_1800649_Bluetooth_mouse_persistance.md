---
title: "Bluetooth mouse persistance"
date: 2011-07-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tlcstat on 2011-07-09
Greetings,
I know this will get fixed at some point but is anyone having a problem with bluetooth mouse auto-connect. I have to delete and reinstall my mouse when I reboot. It always works though.  If you have a magic pill for this I would appreciate knowing what it is.  This problem is the only thing keeping Natty on my main HD. 
tlcstat

---

### Post by haqking on 2011-07-09
> **tlcstat said:**
> Greetings,
I know this will get fixed at some point but is anyone having a problem with bluetooth mouse auto-connect. I have to delete and reinstall my mouse when I reboot. It always works though.  If you have a magic pill for this I would appreciate knowing what it is.  This problem is the only thing keeping Natty on my main HD. 
tlcstat

not sure about oneirc itself.

I know BT mice have been an issue for some in previous verions with perisitance etc.

you had to change the /etc/default/<BT FILe> usually bluez-utils

and edit HIDD enabled line to 1 etc and the options to the server using mac address

---

### Post by tlcstat on 2011-07-09
Greetings,

OP by Haqking
> you had to change the /etc/default/<BT FILe> usually bluez-utils

Yes, I'm getting lazy. 

This worked!
/etc/default/   didn't have a bluez-utils so I had to make one. 
Also a hcid.conf under /etc/bluetooth.
Mac address of mouse is needed for this operation.

sudo gedit /etc/bluetooth/hcid.conf

device 00:11:67:FC:43:50 {
name “ConnectLand Mouse”;
}

sudo gedit /etc/default/bluez-utils
HIDD_ENABLED=1
HIDD_OPTIONS=”--master --connect 00:11:67:FC:43:50 --server”


Of course change the mac address and mouse name to your own.

This works persistently.  Thanks for the tip and reminder.  Reminder=don't get lazy with linux.

tlcstat

---

### Post by haqking on 2011-07-09
> **tlcstat said:**
> Greetings,

OP by Haqking


Yes, I'm getting lazy. 

This worked!
/etc/default/   didn't have a bluez-utils so I had to make one. 
Also a hcid.conf under /etc/bluetooth.
Mac address of mouse is needed for this operation.

sudo gedit /etc/bluetooth/hcid.conf

device 00:11:67:FC:43:50 {
name “ConnectLand Mouse”;
}

sudo gedit /etc/default/bluez-utils
HIDD_ENABLED=1
HIDD_OPTIONS=”--master --connect 00:11:67:FC:43:50 --server”


Of course change the mac address and mouse name to your own.

This works persistently.  Thanks for the tip and reminder.  Reminder=don't get lazy with linux.

tlcstat

ha dont worry, i was lazy in my reply, i was hoping you would figure out the rest from what i wrote, i havent had enough coffee yet to dig back to whole thing needed ;-)

glad you got it sorted

---

### Post by tlcstat on 2011-07-09
Greetings,
P.S.  Even though my Natty BT Mouse was connecting, I copied over the two files and now it seems like a much smoother connect. So probably needed there also, especially when switching back and forth between the two OS's. 
tlcstat

Greetings,
I removed the Solved flag from this post.  The above instructions certainly enhance the hook up in Natty but fail in Oneiric.  Bluetooth in Oneiric is broken for now.
tlcstat

---

