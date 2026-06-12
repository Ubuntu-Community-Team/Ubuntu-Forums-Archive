---
title: "Computer problems on both windows and ubuntu"
date: 2008-08-16
forum: New to Ubuntu
---

### Post by eragon100 on 2008-08-16
Hello! As well as trying to get an umlaut out of my keyboard, [http://ubuntuforums.org/showthread.php?p=5601420#post5601420]("http://ubuntuforums.org/showthread.php?p=5601420#post5601420"), I am also trying to repair my parents computer, which has been having startup problems with windows xp sp2 for some time now. It hangs during startup reboots and then after a few times starts correctly and works perfectly with an occasional restart.

The ubuntu livecd crashed on startup with a kernel panic, giving a bios error about a non-implemented timer and an error about apic and that time not being in sync (or something like that). The boot option "noapic", which was recommended by the livecd, gives the ubuntu splash screen, but then startup hangs on a message "initramfs". I get a "busybox" terminal window, which recognizes my input an acts on it, so the computer clearly doesn't hang completely. However, the startup procedure never continues and the desktop doesn't load. Does anyone know which hardware components could cause this kind of problems with windows and ubuntu (ram, motherboard, whatever) ??

---

### Post by gabo.cr on 2008-08-16
I had a similar problem with live CD, and it got fixed with acpi=off instead of noapic.

---

### Post by Paqman on 2008-08-16
If the problem is in both Windows and Linux then you've got a hardware problem (or possibly BIOS)

Try flashing your BIOS, and then start going through all your componants one by one to find out which is at fault. You can try removing them (if possible), swapping them to different slots, or swapping them with componants from another machine. Taking notes as you go will help with fault-finding.

---

### Post by eragon100 on 2008-08-16
> **Paqman said:**
> If the problem is in both Windows and Linux then you've got a hardware problem (or possibly BIOS)

Try flashing your BIOS, and then start going through all your componants one by one to find out which is at fault. You can try removing them (if possible), swapping them to different slots, or swapping them with componants from another machine. Taking notes as you go will help with fault-finding.

I have only one other pc, namely my own, and it is very hard to open. I am not going to do that to save my parent´s pc, if at all avoidable :(

Which hardware component is the most likely at fault here?

---

### Post by Paqman on 2008-08-17
> **eragon100 said:**
> 
Which hardware component is the most likely at fault here?

Could be anything really. PSU, memory, graphics, mobo, even the hard drive. Can you provide a bit more detail about how it behaves when it fails to boot? Does it beep? At what point does it restart? Does it give any error messages before restarting? That kind of thing.

---

### Post by Crafty Kisses on 2008-08-17
Definietly sounds like a hardware issue like RAM, or even the BIOS, because kernel panics are almost always due to hardware issues.

---

### Post by fiddledd on 2008-08-17
It's also possible that the 2 are unrelated. You could have a driver problem with XP and Ubuntu not compatible with the hardware. Have you tried another Livecd that's not Ubuntu based?

---

