---
title: "access recovery mode without rebooting???"
date: 2019-05-08
forum: New to Ubuntu
---

### Post by zakebramley on 2019-05-08
hi is there any way to get recovery mode without rebooting (ideally from terminal). im curious

---

### Post by oldrocker99 on 2019-05-08
Recovery mode is only available at boot time. If you don't see the menu when you boot, you'll need to do this:```
sudo nano /etc/default/grub
```

All the commands are on the margin of nano, so it's CTRL-O to Write Out, etc. It's easy to use.

Make one change. Add a # before GRUB_HIDDEN_TIMEOUT=0

Then,```
sudo update-grub
```

Then reboot, and you'll have the menu.

---

### Post by deadflowr on 2019-05-08
Old school used to be able to just run
```
sudo /sbin/init 1
```
but with the advent of systemd it seems you run
```
sudo systemctl rescue
```
to switch to rescue mode.
It's suppose to be reversible(?) with either exit or
```
systemctl default
```

More on it here:
[https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-managing_services_with_systemd-targets]("https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/7/html/system_administrators_guide/sect-managing_services_with_systemd-targets")
[https://askubuntu.com/questions/685946/how-to-exit-emergency-mode-and-boot-to-default-mode]("https://askubuntu.com/questions/685946/how-to-exit-emergency-mode-and-boot-to-default-mode")

---

### Post by electrosteam on 2019-05-08
I tried the following on my Lubuntu 18.04.2 desktop.
```

sudo systemctl rescue

```

Did some viewing of files, then
```

exit

```

The Rescue Mode worked fine, checked several files, no editing.
After exit got a blank screen for a short time, then in sequence:
- Lubuntu progressive dots screen,
- blank for a very long time,
 - the last screen of Rescue Mode,
 - blank for long time,
 - last screen of Rescue Mode,
 - several cycles of blank/last-screen before attempting recovery.

Tried REISUB, too quickly to be sure what worked, but got to my user logon.
Logged on, then blank again, and after a short delay, a normal GUI logon screen.

John

---

### Post by oldrocker99 on 2019-05-09
I always enable the GRUB menu, which allows me to enter recovery mode. It also have the very, very useful RAM checker, which has, over the years, caught bad RAM sticks.

So I have to reboot. BIG hairy deal.

---

