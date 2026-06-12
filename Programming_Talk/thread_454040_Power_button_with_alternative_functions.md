---
title: "Power button with alternative functions"
date: 2007-05-25
forum: Programming Talk
---

### Post by kuscsik on 2007-05-25
Hi,

I would like to use the power button of a headless and keyboard-less server to initiate different actions:

For example:

Pushing 2x -> Start some service
Pushign 3x -> Stop the service
Pushgin 4x -> Restart

Where can I read the state of the power button?
Thank You

---

### Post by coxy on 2007-05-25
I have no idea if this is possible; I will be watching the post though as this could serve my MythTV box very well ;)

---

### Post by amo-ej1 on 2007-05-25
Well all button presses are events that ripple through ACPI. So if you look at /etc/acpi/events you will find defintion of all events. One of them is powerbtn. So /etc/acpi/events/powerbtn basicly contains:

```

event=button[ /]power
action=/etc/acpi/powerbtn.sh

```

Thus /etc/acpi/powerbtn.sh is executed. Now you can put you magic code in /etc/acpi/powerbtn.sh ;)

---

### Post by kuscsik on 2007-05-25
Great,

 I wil write a small deamon for various "power button" pressing shemes. Thank you

---

