---
title: "[SOLVED] device manager?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by dsmcginn on 2008-09-01
when troubleshooting mylaptop, it tells me to goto System>Preferences>Hardware Information.

but it's not there.

i tried running sudo apt-get install gnome-device-manager and sudo apt-get install hal-device-manager and they didnt work.

any thoughts?
=)

---

### Post by drs305 on 2008-09-01
System Tools, Device Manager is where you will find Device Manager.

You might need to elaborate on "didn't work". Didn't install, couldn't find them, didn't give you the information you wanted, etc?

---

### Post by porchrat on 2008-09-01
Are you sure it doesn't say "System --> Administration --> Hardware Drivers"

This should contain the information on HAL at least (if you have any restricted drivers running), I'm not sure about gnome though.

---

### Post by dsmcginn on 2008-09-01
> **drs305 said:**
> System Tools, Device Manager is where you will find Device Manager.

You might need to elaborate on "didn't work". Didn't install, couldn't find them, didn't give you the information you wanted, etc?

it's just not there...so i'd say i couldn't find them.

---

### Post by sayakb on 2008-09-01
Try at a terminal:
```
lspci
```

---

### Post by mapex on 2008-09-09
> **dsmcginn said:**
> when troubleshooting mylaptop, it tells me to goto System>Preferences>Hardware Information.

but it's not there.

=)

exactly. same here. and i can prove it:

[http://img228.imageshack.us/my.php?image=hardwareinformationrp2.jpg]("http://img228.imageshack.us/my.php?image=hardwareinformationrp2.jpg")

the above screenshot shows that the help tells you to go to System>Preferences>Hardware Information, but this item is just not there in the menu.

how do we get to device manager? i would prefer a GUI..

---

### Post by hyper_ch on 2008-09-09
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by roger_1960 on 2008-09-09
Hi

I agree, its not there! - but go to "system - preferences - main menu"  then select on the left "system" and then check the "control centre" box on the right.  Exit the dialogue and then go "system - control centre"  The "hardware" section should give you what you want as a gui

---

