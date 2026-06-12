---
title: "Unresponsive touchpad"
date: 2011-11-28
forum: New to Ubuntu
---

### Post by agwblack on 2011-11-28
Hi all. There has been an issue affecting several people over the last few months in which the mouse or touchpad spontaneously becomes unresponsive. The cursor will still move, but you cannot click on anything. 

This thread ([http://ubuntuforums.org/showthread.php?t=1576094](http://ubuntuforums.org/showthread.php?t=1576094)) and others resolve the issue by unplugging their USB mouse and plugging it back in to a different USB port. However my problem occurs with the touchpad which I obviously cannot unplug. 

Does anyone know how I can reassign the touchpad to another port, or something like that which will mimic the unplugging/replugging solution that people have used with USB mice?

Also, any insight into the root cause of the issue would be appreciated. I guess it must be kernel problem. I am using a fully updated ubuntu 10.10 but I've had the same issue recently on Arch Linux as well, and on Gnome, XFCE, and XMonad.

---

### Post by Corporation on 2011-11-28
Turn off 'Disable Trackpad While Typing' worked for me on HP Pavilion DM1-3200SA with this issue.

Failing that:

ctrl-alt-f2
Log into tty
sudo rmmod psmouse
sudo modprobe psmouse

It's not a very elegant solution.

---

### Post by agwblack on 2011-11-28
Thanks, I'll try that this evening.

---

### Post by birdsarah on 2012-11-03
> **Corporation said:**
> 
sudo rmmod psmouse
sudo modprobe psmouse


I still have a functioning keyboard when this happens to me so a simple Ctl-Alt-T to pull up a terminal and then the above and my trackpad is back. Thank you so much.

Sarah Bird

---

