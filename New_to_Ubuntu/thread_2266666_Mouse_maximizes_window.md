---
title: "Mouse maximizes window"
date: 2015-02-24
forum: New to Ubuntu
---

### Post by numeric2 on 2015-02-24
HI,

How can I prevent the mouse from maximizing the window when I try and drag the window? 
Using Ubuntu 14.04 64 bit with latest updates.
Logitech wireless mouse
Logitech wireless keyboard
Logitech USB unifying blue tooth receiver 
ASUS AM350 pro plus (or something like this) mother board.

No MS Windows installed.

Your help is greatly appreciated.

---

### Post by CantankRus on 2015-02-24
Run in terminal....
```
dconf write /org/compiz/profiles/unity/plugins/grid/top-edge-action 0
```

or

install compizconfig-settings-manager (ccsm)...
```
sudo apt-get install compizconfig-settings-manager
```
Open ccsm > window management > grid > corners/edges
and set the "top edge" action.

---

### Post by numeric2 on 2015-02-24
Thank you for your reply. I tried both methods you describe. Unfortunately this did not fix the problem.
The window still maximizes as soon as I put the mouse in the top window darkened area and press the left mouse button. Only about one in ten tries will I be able to drag the window to a convenient screen location without full screen maximize. Its sorta like MS windows Aero Snap, a really annoying function.

---

### Post by CantankRus on 2015-02-24
Maybe you have a faulty left click mouse button.
In Settings > mouse and touchpad ...at the top right you can test your mouse.

Try disabling double-click for the titlebar.
In terminal....
```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar none
```

---

### Post by numeric2 on 2015-02-24
Thank ypu CantankRus,

Good insight.;) The mouse does produce a double click with just a single click. Either the mose is bad or needs adjustment. I do not remember having problems using it on a Windows machine. Both the mouse and keyboard are wireless and I use Logitech's unyfing receiver software to set up the mouse. The same software does not run under Wine for Linux. Other than using Windows, is there a way to set the keyboard and mouse paring under Ubuntu? While the problem is not a pairing issue, the unyfying software does provide mouse setup features.

---

### Post by buzzingrobot on 2015-02-24
I see there is a "logitech-applet" in the Trusty repo that does "Logitech mouse tweaking".  I've never used it.

There is also a PPA for Solaar, which offers some support to the Unifying Receiver for Linux ([https://launchpad.net/~daniel.pavel/+archive/ubuntu/solaar](https://launchpad.net/~daniel.pavel/+archive/ubuntu/solaar) and [http://www.webupd8.org/2013/07/pair-unpair-logitech-unifying-devices.html](http://www.webupd8.org/2013/07/pair-unpair-logitech-unifying-devices.html)).  I have used this briefly.  The left click worked fine but the mouse connection would drop out periodically.

---

### Post by gifford on 2015-02-24
Have you tried adjusting the click settings for the mouse under system settings, mouse and touchpad?

---

### Post by numeric2 on 2015-02-25
> **CantankRus said:**
> Maybe you have a faulty left click mouse button.
In Settings > mouse and touchpad ...at the top right you can test your mouse.

Try disabling double-click for the titlebar.
In terminal....
```
gsettings set org.gnome.desktop.wm.preferences action-double-click-titlebar none
```

I have tried all suggestions and your faulty mouse idea. The mouse is bad. I tried another mouse and it solved the problem. 
For now, I used my windows laptop to unify the new mouse with the existing keyboard. It worked great. I wish to thank all members for your suggestions.

---

