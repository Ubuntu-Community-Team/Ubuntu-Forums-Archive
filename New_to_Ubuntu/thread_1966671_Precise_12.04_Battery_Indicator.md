---
title: "Precise 12.04 Battery Indicator"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by Bob Henson on 2012-04-27
I have updated to Precise 12.04 and am using Gnome and cannot get the battery level indicator to show in the panel. Using System Tools > System Settings > Power allows me to select "show battery status in the menu bar" from the drop down, but the setting I select will not stick. It's quite difficult with a laptop and no obvious battery indicator - how do I get my selection to stick, please? 

Regards,

Bob

---

### Post by cromat on 2012-04-27
When you change the selection to show did you log out or restart of restart the gnome shell.  I have found that when something doesn't work, reloading the gnome shell makes it work. ALT + F2, type r as the command and run.

---

### Post by Bob Henson on 2012-04-27
> **cromat said:**
> When you change the selection to show did you log out or restart of restart the gnome shell.  I have found that when something doesn't work, reloading the gnome shell makes it work. ALT + F2, type r as the command and run.

Yes - several times, but it doesn't make any difference. If you try to make a selection, close the program and immediately re-open it, the selected item has already disappeared, so re-starting won't save the change anyway. It's obviously something to do with Gnome (it works fine in Unity) but I've no idea how to fix it - if indeed it can be fixed.

---

### Post by cromat on 2012-04-27
Ok, fair enough. Which version of gnome shell?

---

### Post by Bob Henson on 2012-04-27
> **cromat said:**
> Ok, fair enough. Which version of gnome shell?

Gnome 3.4.1. I've tried logging in and out and changing from "Gnome Classic" to "Gnome" and "Gnome Classic (No Effects)" - that makes no difference.

---

### Post by cromat on 2012-04-27
Do you get anything asking for a crash report?

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg364049.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg364049.html)

It looks like there are multiple bugs reporting to the Debian base about this.

---

### Post by Bob Henson on 2012-04-27
> **cromat said:**
> Do you get anything asking for a crash report?

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg364049.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg364049.html)

It looks like there are multiple bugs reporting to the Debian base about this.

No crashes in Ubuntu - it just won't stay selected. I haven't seen any problems with Debian, but then they haven't reached Gnome 3 yet.

---

### Post by Phasmus on 2012-05-04
I have encountered this same problem.  This was on an upgrade from 11.10.  Maybe it does not occur with a fresh install?

---

### Post by TM720 on 2012-05-04
No, I'm having the same problem as well and I did a clean install of 12.04. Same problem as described above.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
do you have [indicator-power](apt:indicator-power) installed

---

### Post by Stunt Double on 2012-05-04
Same problem.
Dual boot: 10.04 and 12.04. Running Classic (no effects). Indicator-power is installed.
Thanks

---

### Post by Bob Henson on 2012-05-05
> **pqwoerituytrueiwoq said:**
> do you have [indicator-power]("apt:indicator-power") installed

Yes.

---

### Post by bela83 on 2012-05-05
Same problem.
Running Gnome Classic (no effects) in Precise. Indicator-power is installed.

---

### Post by Steve White on 2012-05-10
Yeah I'm seeing it too.

Possibly related: 
System Settings -> Power
    Show battery status in the menu bar
        
is blank when the window opens, and although you can pull down the menu and pick a value, the value doesn't take hold.  It shows blank the next time the dialog is opened.

is bug.

---

### Post by Steve White on 2012-05-10
OK I reported a bug
[https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/997758](https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/997758)

---

### Post by Erica647 on 2012-07-01
I have the same issue on a clean install of 12.04 on a desktop system with a UPS connected via USB port.

---

### Post by black veils on 2012-07-01
maybe you could install a different desktop environment, xfce has options like that of old gnome, and is easy to use.

```
sudo apt-get install xubuntu-desktop
```

---

