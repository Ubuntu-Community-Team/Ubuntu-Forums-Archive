---
title: "[SOLVED] Ubuntu hangs on boot."
date: 2008-08-20
forum: New to Ubuntu
---

### Post by Zak Jones! on 2008-08-20
Okay, I've been getting a lot of problems from Ubuntu on a system that runs windows perfectly fine. I don't want windows though.

I've FINALLY installed Ubuntu. It booted successfully 2 or 3 times. Now, it won't boot. I get past the GRUB screen, and it hangs on the screen with the Ubuntu logo and a orange strip bouncing back and forth in a.. thing. The orange bar will just stop after going back and forth a couple times. The hard drive light comes on for a sec, then stops, and the machine seems to be 'idling' for lack of a better term. 

If anyone can help me with this, Thanks in advance.

---

### Post by alienexplorers on 2008-08-20
Have you tried booting into recovery mode.  If it boots you can edit /boot/grub/menu.lst  and remove the line quiet splash from the boot menu.  This way when you reboot it will show where the boot is hanging.  If it works post the line with the hang to this thread and hopefully someone will help.

---

### Post by Zak Jones! on 2008-08-20
Alright, I booted in recovery mode, even though it didn't complete the boot. The most recent line of text in the failed boot reads:

[   40.490899] Clocksource tsc unstable (delta = 4687315234 ns)

Does that mean there's something wrong with the clock on the motherboard?

---

### Post by alienexplorers on 2008-08-20
Try rebooting into recovery mode and add these to lines to your kernel line that you removed quiet splash from.  The lines are clocksource=acpi_pm and nohz=off in your kernel line?

---

### Post by Zak Jones! on 2008-08-21
Um. Sorry, but I've no idea what the kernel line is. And I never disabled that splash screen, it just didn't come up for the recovery mode boot. Which, by the way, didn't work either. :(

---

### Post by Zak Jones! on 2008-08-22
Anyone able to tell me what the kernel line is?

---

### Post by Gregmond on 2008-08-22
When you get to grub menu (where you selected recovery mode) there is an option to edit the main selection (I think its e). When you edit it look for the line that has quiet splash on the end. replace this with nopaic (i think its that, could be noacpi) and see what it does. Removing the "splash quiet" will mean that you don't see the orange bar, instead it should show you what its doing.
This will only work on this particular bootup once. If this allows you to boot, then you will need to edit the grub menulist.

---

### Post by Zak Jones! on 2008-08-22
k, I tried this, but I doubt I'm doing it right. at the first GRUB screen, I select: "Ubuntu 8.04.1, kernel 2.6.24-19-generic", and I edit it.

now, I pick the very bottom line for editing, which reads simply: 

quiet

Do I insert my code there? What code do in insert?

---

### Post by Zak Jones! on 2008-08-22
nevermind, I found the right line. I edited it, and removed the splash screen. Its hung up on the same line as in my earlier post. What now?

alienexplorers, I added the code you suggested to the same line, I hope that was right.

---

### Post by Zak Jones! on 2008-08-24
bump.

---

### Post by Zak Jones! on 2008-08-24
Oh, screw it. I'm just going to buy a new motherboard on ebay or something... Thanks to those that helped.

---

