---
title: "touchpad not working after installing updates for Ubunu 14.04"
date: 2015-07-27
forum: New to Ubuntu
---

### Post by vdpsdg on 2015-07-27
I am a new Ubuntu user.  The Dell Inspiron I purchased came with ubuntu 14.04. Everything worked until I got the latest updates.  The touchpad does not work now.  However, in diagnostics mode it works - so its not a h/w problem  I've tried various solutions from this forum - but no luck.  PLEASE HELP

---

### Post by NoWayWin8 on 2015-07-28
Not  much information to go on. Is it shown as disabled in "Mouse and Touchpad" settings? Press the windows key and type "Mouse and Touchpad" in the search box, then arrow key to highlight the app, enter to launch. Is there is an "ON/OFF" slider by "Touchpad" - and if so is it on?

---

### Post by Joshua_Camp on 2015-07-28
Open a terminal, and navigate to /etc/modprobe.d. Use sudo to open blacklist.conf with nano - "sudo nano blacklist.conf". Scroll to the bottom. Type the line "blacklist i2c-hid". Press ctrl+o, which saves it, and then press ctrl+x to exit nano. Make sure everything has been saved, and then type "sudo reboot".

---

