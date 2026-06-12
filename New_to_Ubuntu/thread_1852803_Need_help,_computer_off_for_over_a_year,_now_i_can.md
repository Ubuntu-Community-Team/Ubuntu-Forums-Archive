---
title: "Need help, computer off for over a year, now i can't get on."
date: 2011-09-30
forum: New to Ubuntu
---

### Post by l3onbryan on 2011-09-30
I have not used this computer in over a year, it has been off, when I tried to use it again three messages pop up no matter how many times I restart the computer
1.)"could not update ICEauthority file /home/andrew/.ICEauthority
2.)"there is a problem with the confiquration server. (/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)"
3.)"nautilus could not create the following required folders: /home/andrew/Desktop, /home/andrew/.nautilus."

I have no idea how to do anything with a computer, so if anyone wants to help me out step by step i would greatly appreciate it.

---

### Post by bodhi.zazen on 2011-09-30
boot to recovery mode, you will have a root shell (command line) without a graphical interface.

run the following command

```
chown -R andrew:andrew ~andrew
```

then reboot

---

### Post by LowSky on 2011-10-01
Go into the BIOS and reset the date and time. Being off for so long probably drained the CMOS battery and could be causing some strange issues too. You may need to replace it too.

---

### Post by l3onbryan on 2011-10-01
okay I booted in recovery mode, then it went straight to a "recovery menu" what do i do now?

---

### Post by l3onbryan on 2011-10-01
okay I booted in recovery mode, then it went straight to a "recovery menu" what do i do now?

---

### Post by bodhi.zazen on 2011-10-01
> **l3onbryan said:**
> okay I booted in recovery mode, then it went straight to a "recovery menu" what do i do now?

Select root shell

---

