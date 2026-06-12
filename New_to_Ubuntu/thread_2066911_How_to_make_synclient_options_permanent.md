---
title: "How to make synclient options permanent?"
date: 2012-10-05
forum: New to Ubuntu
---

### Post by Mohammad_Khalid_Hussain on 2012-10-05
Assalamu'alaikum,
and Hi! to everyone else.

I like to have 2 finger tap on my laptop perform middle-click and 3 finger tap perform right-click. The command I have found for this is:
```
synclient TapButton3=3 TapButton2=2
```
The only problem is that this dissapears after a reboot. Is there a way I can make this permanent?

Thanks for the all the help.

---

### Post by mikewhatever on 2012-10-05
Add the command to startup programs.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-07
Didn't think I could do that, thanks a lot for this.

---

### Post by Mohammad_Khalid_Hussain on 2012-10-07
Apparently I found out that it doesn't stay after a Suspend. Any idea how to resolve this?

Thanks.

---

### Post by szosa on 2012-10-09
> **Mohammad_Khalid_Hussain said:**
> Apparently I found out that it doesn't stay after a Suspend. Any idea how to resolve this?

Thanks.

Szia! 
etc/X11/xorg.conf


```
Section "InputDevice"
..........
Option "TapButton3" "3" 
Option "TapButton2" "2"
.........
EndSection

```
if not exist xorg.conf,
CTRL+Alt+F1 or F2. ...
sudo /etc/init.d/gdm stop
sudo Xorg configure
sudo cp /root/xorg.conf.new /etc/X11/
cd /etc/X11
sudo nano -w xorg.conf

sudo /etc/init.d/gdm start

Üdv

---

