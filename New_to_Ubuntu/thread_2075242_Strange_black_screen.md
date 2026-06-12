---
title: "Strange black screen"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by destro2k on 2012-10-23
Dell 4400
Bios Version A06
Pentium 4 1.6Ghz
Memory 256MB
HD 40GB Maxtor
Monitor Dell E771a

This is strange. I installed xubuntu. When the PC is connected to my TV it starts up fine. But when connected to the Dell PC monitor the screen goes black. To be exact, for a split second I see the xubuntu screen with the bar sliding back and forth before the screen goes black.

The PC is certainly continuing the start up process as verified by plugging back into the TV. If I start up the PC attached to the TV, wait for start up to complete, then switch the cable to the PC monitor, everything is fine.

One more thing, while plugged into the PC monitor I start up using a Puppy Linux CD and the screen shows fine. I don't think the monitor is faulty so what is going on here?

---

### Post by dolphin194 on 2012-10-23
If you press Alt-F1 while the computer is booting (with the dell monitor plugged in), are you able to see a terminal and use the computer through it?

---

### Post by destro2k on 2012-10-23
I tried pressing and holding Alt-F1 to reach a terminal. No luck. I tried repeatedly pressing Alt-F1 to reach a terminal. No luck. I do see a flashing command line during start up for a moment but the boot up process marches right on past that point.

---

### Post by dolphin194 on 2012-10-23
So, when you turn on the computer with the Dell monitor, does the computer actually boot?

---

### Post by destro2k on 2012-10-23
Yes it does. First I see the system information screen. Next I see a black screen with flashing prompt. Last I see the xubuntu screen with bar sliding back and forth but only for a second or two.

---

### Post by destro2k on 2012-10-24
Anyone have a suggestion for me.

---

### Post by squakie on 2012-10-24
Try adding nomodeset to the boot line.  If you need help doing that and don't find it on the forum (there are MANY posts on this), then post back and someone can walk you through it.

---

### Post by destro2k on 2012-10-25
I searched nomodeset but everything I found assumes I'm performing a new installation. Could someone walk me through selecting nomodeset after installation?

---

### Post by maniandram on 2012-10-25
Hold F8 when the computer starts. The GRUB bootloader prompt should appear. Press e. It should open an editor. There should be a line starting with "linux".  add "nomodeset" to the end of the line. The line should look like "linux ... nomodeset" press ctrl+x and xubuntu will boot temporarily with nomodeset (after reboot it won't have nomodeset)

---

