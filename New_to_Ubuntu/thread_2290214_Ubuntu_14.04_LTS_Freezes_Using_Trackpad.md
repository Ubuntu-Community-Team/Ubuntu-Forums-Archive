---
title: "Ubuntu 14.04 LTS Freezes Using Trackpad"
date: 2015-08-10
forum: New to Ubuntu
---

### Post by jonathan90 on 2015-08-10
Hey guys! I'm new to Ubuntu and I've been having problems with the screen freezing on random occasions.  I've noticed that it only happens when I use the trackpad and that it's a graphics driver issue.  I've also seen posts of about on Launchpad, but I'm confused as to how to implement those solutions.  Can someone help me out?  Thanks!

Here's the link to the Launchpad page I was looking at. [https://bugs.launchpad.net/xorg-server/+bug/1220426/](https://bugs.launchpad.net/xorg-server/+bug/1220426/)

---

### Post by sandyd on 2015-08-10
If that's the bug, run
```

echo "options psmouse proto=imps" | sudo tee /etc/modprobe.d/psmouse.conf >/dev/null
sudo modprobe -r psmouse && sudo modprobe psmouse

```

in a terminal.

The terminal can be accessed by typing in 'terminal' in the unity dash (Ubuntu), or 'Konsole' in the Kubuntu menu.

---

### Post by jonathan90 on 2015-08-10
I tried running that, but it said "unable to resolve host *my username.*"  It also made my trackpad cursor move really slowly  while my mouse remained at the same speed, and after speeding up the mouse movement in the settings, the trackpad is back to normal speed but the USB mouse is flying.

---

### Post by jonathan90 on 2015-08-10
Accidentally posted a duplicate when the internet lagged! Sorry!

---

### Post by mörgæs on 2015-08-12
The Launchpad page to which you linked tells that it's fixed in 15.04. 
Time to leave 14.04 and move on?

---

### Post by jonathan90 on 2015-08-12
The IT department that covers me doesn't support Ubuntu 15 yet. I'm planning on bringing in my computer, but I need it to be functional soon and I don't know when they'll be available. What can I do until then?

---

### Post by mörgæs on 2015-08-13
Have you shown them the Launchpad page?

---

### Post by jonathan90 on 2015-08-16
Yeah so I gave it to them and it seems that all they could do was the fix on the Launchpad, which makes the touchpad movement bumpy and uneven.  Also, both the touchpad and the mouse only respond to the mouse setting in dconf editor, and at the same mouse speed, the touchpad and the mouse move at different speeds as before.

---

