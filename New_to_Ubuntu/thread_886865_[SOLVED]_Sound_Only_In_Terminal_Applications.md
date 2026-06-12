---
title: "[SOLVED] Sound Only In Terminal Applications"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by Patriot1776 on 2008-08-11
I tried a few nights ago to re-initialize ALSA only after something locked up the sound hardware and I lost all my sound.  Now, I only have sound in terminal-run applications, mostly mp3blaster.  GUI applications have no sound at all, including Firefox and Rhythmbox.  Any ideas?

---

### Post by Crafty Kisses on 2008-08-11
> **Patriot1776 said:**
> I tried a few nights ago to re-initialize ALSA only after something locked up the sound hardware and I lost all my sound.  Now, I only have sound in terminal-run applications, mostly mp3blaster.  GUI applications have no sound at all, including Firefox and Rhythmbox.  Any ideas?

Post the following output:
```
lspci
```

---

### Post by Patriot1776 on 2008-08-11
> **Codename said:**
> Post the following output:
```
lspci
```

```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)
05:08.0 Ethernet controller: Intel Corporation 82801G (ICH7 Family) LAN Controller (rev 01)
```

That's what I received.  Running Hardy 8.04.1, kernel 2.6.24-19-generic

---

### Post by lapubell on 2008-08-11
which sound server are you using?  8.04 comes with pulseaudio as the default and I am no t a fan.  try typing in the terminal

sudo killall pulseaudio

and restart any apps that need audio.

---

### Post by Patriot1776 on 2008-08-11
> **lapubell said:**
> which sound server are you using?  8.04 comes with pulseaudio as the default and I am no t a fan.  try typing in the terminal

sudo killall pulseaudio

and restart any apps that need audio.

Thanks much, that did it.  I'll now mark this as solved.

---

