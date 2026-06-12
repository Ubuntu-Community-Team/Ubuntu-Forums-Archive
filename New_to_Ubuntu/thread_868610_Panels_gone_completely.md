---
title: "Panels gone completely"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by carloslosgrande on 2008-07-24
I clicked on the calendar and it froze. Had to restart gdm.
Panels disappeared completely. Tried the fixes at;
[http://ubuntuforums.org/showthread.php?t=861448&highlight=panels+lost](http://ubuntuforums.org/showthread.php?t=861448&highlight=panels+lost)
and here;
[http://ubuntuforums.org/showthread.php?p=4988910](http://ubuntuforums.org/showthread.php?p=4988910)
all to no avail.
I don't believe I did anything to evolution or applets.
I've even tried a full re-install and still the same problem!
wtf?
Gnome failsafe works.

---

### Post by El Conquistador on 2008-07-24
try this in the terminal:

killall gnome-panel

---

### Post by carloslosgrande on 2008-07-24
Ok, did that, another restart now?

---

### Post by iaculallad on 2008-07-24
Open your terminal, try this:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by El Conquistador on 2008-07-24
umm every time ive ever ran that command i havent needed to restart. but why dont you try a Ctrl+Alt+backspace (that way you dont have to wait for the whole reboot)

---

### Post by carloslosgrande on 2008-07-24
Conquistador, thanks but it hasn't made any difference, after restart.
iaculallad, ditto for you, also now the keyboard will only accept typing at slloooowwwwww speed.
Any faster and letters get issed.

---

### Post by El Conquistador on 2008-07-24
ok ive found these commands on a number of sites so im guessing they might work. try them i would suggest stopping it first then starting it.

sudo /etc/init.d/gdm start

sudo /etc/init.d/gdm stop

Edit: ok well further reaserch tells me this is just the same as Ctrl+Alt+backspace. so sorry.

---

### Post by carloslosgrande on 2008-07-24
Yeah, I knew about those and tried them previously.
When gnome failsafe starts now it tells me various applets are incompatible (the panel had a problem loading it) and I need to delete it. These are applets I've used for a year or more.
Normally, with a problem like this, I just re-install and presto - fixed. Not now!

---

### Post by El Conquistador on 2008-07-24
try this

sudo apt-get update
sudo apt-get install --reinstall gnome-panel

---

### Post by carloslosgrande on 2008-07-24
Thanks Conquistador, that got me back normal typing speed. But no change to panels. I'm still resorting to failsafe mode.
This is really weird.

---

### Post by carloslosgrande on 2008-07-31
[FONT="Comic Sans MS"]Ok, finally back online. The next restart got me "ubiquity failed" and after that it was grub error 15. I tried super grub disc without any luck. I finally got everything working after deleting mandriva from my second hdd.
Weird.
I have a lot of trouble with the net at the moment, the local ISP has choked the net access to any connections outside china. I guess they're trying to give their netwatch people more time to check the outgoing traffic, rather than the usual random checks.
This makes for a very slow download rate, when I actually have any access.[/FONT]

---

