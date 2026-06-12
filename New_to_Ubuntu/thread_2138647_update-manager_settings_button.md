---
title: "update-manager settings button"
date: 2013-04-24
forum: New to Ubuntu
---

### Post by phil66 on 2013-04-24
Ubuntu 12.04

Update-manager settings button is greyed out

Cannot open to set settings

I want to change this time settings

---

### Post by fantab on 2013-04-24
I think you may have to be 'sudo' / 'gksudo' to see the active settings button. Run *'gksudo update manager*' from terminal to open the application with Elevated Privileges.

---

### Post by deadflowr on 2013-04-24
The settings button is only the software sources.
So you can find another way in.
Go to the software center and I think in the dropdown menu you can access it somewhere in there.
Or run
```
software-properties-gtk
```
in a terminal.

---

### Post by phil66 on 2013-04-25
> **fantab said:**
> I think you may have to be 'sudo' / 'gksudo' to see the active settings button. Run *'gksudo update manager*' from terminal to open the application with Elevated Privileges.

Fantab

Have already tried this ..It is the same as the normal display ..no settings

Thanks for the reply

---

### Post by phil66 on 2013-04-25
> **deadflowr said:**
> The settings button is only the software sources.
So you can find another way in.
Go to the software center and I think in the dropdown menu you can access it somewhere in there.
Or run
```
software-properties-gtk
```
in a terminal.

Deadflowr

Downloaded and installed software-properties-gtk
Open same and was able to set time of events
Now when I open update-manager the settings button available

Problen solved .Thanks for the help

---

