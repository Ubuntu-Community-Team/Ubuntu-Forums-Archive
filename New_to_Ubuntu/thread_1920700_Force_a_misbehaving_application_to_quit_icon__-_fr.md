---
title: "Force a misbehaving application to quit icon  - freezes computer."
date: 2012-02-05
forum: New to Ubuntu
---

### Post by a.v.l on 2012-02-05
In Ubuntu 11.10 - "Force a misbehaving application to quit" icon, freezes my computer and I'm unable to do anything else, other than to reboot the system. Is there a fix for this?

---

### Post by Carborundum on 2012-02-05
I'm not familiar with that error, but IIRC that button invokes the xkill command. Do you observe the same behavior if you run xkill from a terminal?

---

### Post by a.v.l on 2012-02-05
> **Carborundum said:**
> I'm not familiar with that error, but IIRC that button invokes the xkill command. Do you observe the same behavior if you run xkill from a terminal?

Once I press the "force a misbehaving application to quit" icon the program opens and the mouse curser is replaced by a + symbol. from there the system freezes immediately and I'm unable to  click on anything else. Can't use the keyboard either. The system locks up tight so I have to reboot to get things working again. This happens every time I use it. I'm afraid I'm unfamilier with xkill, how do I try this in the terminal?

---

### Post by Carborundum on 2012-02-05
Open a terminal (ctrl+alt+t), write "xkill" (without the quotation marks) and press the Enter key.

---

### Post by a.v.l on 2012-02-05
> **Carborundum said:**
> Open a terminal (ctrl+alt+t), write "xkill" (without the quotation marks) and press the Enter key.

Thank you, that worked perfectly without freezing.

---

### Post by oldspammer on 2012-11-25
> **a.v.l said:**
> Once I press the "force a misbehaving application to quit" icon the program opens and the mouse curser is replaced by a + symbol. from there the system freezes immediately and I'm unable to  click on anything else. Can't use the keyboard either. The system locks up tight so I have to reboot to get things working again. This happens every time I use it. I'm afraid I'm unfamilier with xkill, how do I try this in the terminal?
On Ubuntu 12.10 this happened to me too. I found that if I crtl-Alt-F1, login on that screen, then

```
cd ~/Desktop
ln -s /usr/bin/gnome-panel
sudo su -
```I made a shell script as root: "killgnomepanel.sh"
```
#!/bin/bash

# killgnomepanel.sh

killall gnome-panel
```Back in the command prompt:
```
chmod +x killgnomepanel.sh
./killgnomepanel.sh
exit
```that it would result in the "killing" of "the kill program" that froze the x window screen session.  I switch back to that screen via Alt-F7, then restart the gnome-panel by double clicking the link to it that I just created above on the desktop.

On another occasion I found that a terminate or kill of gnome-panel would not work if running as a regular user who supposedly owned the gnome-panel process, but instead, killing worked nicely as root, the super user.

---

