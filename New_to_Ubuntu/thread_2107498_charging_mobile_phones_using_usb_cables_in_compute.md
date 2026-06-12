---
title: "charging mobile phones using usb cables in computer"
date: 2013-01-22
forum: New to Ubuntu
---

### Post by pmohankumar on 2013-01-22
Hi,

charging mobile phones using usb cables in computer will reduce lifetime of mother board?

Pls clarify my doubt.

Thanks,
Mohan

---

### Post by Cheesemill on 2013-01-22
Why would it do that?

---

### Post by audiomick on 2013-01-22
I do not think so. The port is built to supply a certain amount of power, and as long as you are within those limits, nothing should happen. On the other side, the phone is built to be able to charge from a USB port. How much power it can draw is defined in the standard, so it wont draw too much.

Here is some reading
[http://en.wikipedia.org/wiki/Usb#Charging_ports_and_accessory_charging_adapters]("http://en.wikipedia.org/wiki/Usb#Charging_ports_and_accessory_charging_adapters")

---

### Post by pmohankumar on 2013-01-22
Thanks audiomick, i am clear now.

---

### Post by Warren Hill on 2013-01-22
Your computer should be protected against overload on the USB ports.  But in any case the the phone won't damage your computer by taking too much current if its been designed correctly.  If its a well known model from any major brand you can assume it has.

The only issue you may have is that it may not charge at all.  When you plug any device into your computer it goes through a process called enumeration in which the computer finds out about the device.  If this does not complete successfully, because you don't have the driver installed for example, the device should stop taking any current.  In practice a lot of devices ignore this rule and will charge anyway but a number follow the rules correctly and will not charge.

---

### Post by mcduck on 2013-01-22
> **Warren Hill said:**
> Your computer should be protected against overload on the USB ports.  But in any case the the phone won't damage your computer by taking too much current if its been designed correctly.  If its a well known model from any major brand you can assume it has.

It *can't* take more current than what the port is designed for, USB is fixed af 5V(+/-5%), and the current is controlled by the computer itself, with the default current of 100mA, and then the device can ask for more units from the computer (up to 5 units = 500mA).

On USB3 the load unit is 150mA, and max units is 6, making the max current 900mA.

Either way, the computer is the one responsible of how much current is available, not the connected device. If the device isn't able to ask for more than one load unit, or needs more current than the max units would add up to, the connected device might fail to work but the computer itself won't have any problems.

(The only exception here is if your computer has a dedicated charging USB port, which can deliver more current than one load unit without the normal negotiation process, and can also go above the normal max current limits, or drop the voltage lower to provide even higher current. On the other hand if your device has such charging connector, you can be pretty sure the connector has it's own safety mechanisms to shut down the connection if the load is too high)

---

### Post by audiomick on 2013-01-22
> **mcduck said:**
> It *can't* take more current than what the port is designed for, USB is fixed af 5V(+/-5%), and the current is controlled by the computer itself, with the default current of 100mA, and then the device can ask for more units from the computer (up to 5 units = 500mA)...

So basically it is more or less idiot proof. Good to know.

---

