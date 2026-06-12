---
title: "Display dimmed on boot"
date: 2011-09-23
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2011-09-23
The missus recently got herself a new laptop, a HP Pavillion dm4
I installed the oneiric beta 2 on it today and noticed that when booting, the screen seems to be black and nothing happens at all.

After seeing it in a dark room, it turns out I can JUST make out the login screen.  Rather than being a blank screen, it is actually very dimmed.
If I tap the brightness up key on the keyboard, the display is completely normal and from then on everything is working out of the box until the next boot.

Any ideas what could cause this?

I also installed the same beta 2 on my own HP G62 which doesn't suffer the same problem.

---

### Post by lonniehenry on 2011-09-23
My install is dim also - usable but fairly dark.  I have to adjust using system settings.  My brightness buttons don't work.  Like you it goes back to the annoying behavior at shutdown.  HP g72 with intel graphics.

---

### Post by x-shaney-x on 2011-09-23
System settings doesn't help me since there is no problem on the desktop.
During the boot I tap the brightness button as said so I can see the login screen but as soon as I login, the brightness returns to a normal level, what I would expect in fact.

Both this laptop and my own are intel HD graphics.  Mine works fine, hers doesn't.
Using same driver and the techie details in logs suggest we have the same graphics.

---

### Post by x-shaney-x on 2011-09-25
I have found adding "acpi_osi=" to the grub kernel line stops the screen dimming but when the splash screen appears as very blocky looking kubuntu text, rather than the normal plymouth splash.
Although blocky, the text is quite small so doesn't look like it's low res exactly.  Wierd.

---

### Post by frncz on 2011-09-26
> **x-shaney-x said:**
> I have found adding "acpi_osi=" to the grub kernel line stops the screen dimming but when the splash screen appears as very blocky looking kubuntu text, rather than the normal plymouth splash.
Although blocky, the text is quite small so doesn't look like it's low res exactly.  Wierd.

Indeed, replacing
GRUB_CMDLINE_LINUX=""
with
GRUB_CMDLINE_LINUX="acpi_osi="
in grub (sudo gedit /etc/default/grub)
fixed the brightness problem in my hp6735s laptop running oneiric.
Thanks shaney

Mike

---

### Post by MAFoElffen on 2011-09-26
> **frncz said:**
> Indeed, replacing
GRUB_CMDLINE_LINUX=""
with
GRUB_CMDLINE_LINUX="acpi_osi="
in grub (sudo gedit /etc/default/grub)
fixed the brightness problem in my hp6735s laptop running oneiric.
Thanks shaney

Mike
Have you tried "acpi_osi=linux"?

Also on some --> Will fix some backlighting Problems:
> **glococo said:**
> Hi,
The best workaround for solving backlight ISSUE was for me:
  Autorun "setpci -s 00:02.0 F4.B=00" each boot.

Steps:
1) edit rc.local
```
gksudo gedit /etc/rc.local
```2) Add the command before EXIT 0
```
setpci -s 00:02.0 F4.B-0
```3) Restart.


---

### Post by lonniehenry on 2011-09-26
Solved my problems also.  Keys now work and it opens with the brightness level that I shut down at.  Thanks.

---

### Post by x-shaney-x on 2011-09-26
I had tried adding Linux to the line but that made it dim again.

Alas, it seems this won't be a problem anymore.  The laptop itself has a horrid sleep problem (it won't wake up) and it isn't just on linux.
Googling suggests this laptop does indeed have serious problems so I will be trying to get a refund or swap tomorrow.

---

