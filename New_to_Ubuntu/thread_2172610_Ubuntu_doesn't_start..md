---
title: "Ubuntu doesn't start."
date: 2013-09-05
forum: New to Ubuntu
---

### Post by carlos16 on 2013-09-05
I've posted in the wrong place.
 			 				[INDENT] 					Hello, my name is carlos and i'm from portugal.

I'm trying to make an HTPC with a ASRock 4core dual sata 2; a 2.6G intel  dual core and a ati hd2600xt graphic board and 4Gbytes ram and 1T HDD, a  NOX2 case with a soundgraphic imon lcd and IR control, all that working  with ubuntu 12.04 and xbmc.

My problem start when i install the ubuntu and restart the pc. Then  nothing happens, just the default orange wallpaper without start menu.

Can any body help me?

Sorry about my poor english. I'm new on Linux software, but i want to learn it and love it.

Thanks. 				
[/INDENT]

---

### Post by Kirk Schnable on 2013-09-05
> **carlos16 said:**
> My problem start when i install the ubuntu and restart the pc. Then  nothing happens, just the default orange wallpaper without start menu.

What version of Ubuntu are you running?

Do you believe you are ever getting to the login screen, or to the desktop?

(Perhaps a picture of your screen so we know what stage you're at would be helpful).

Kirk

---

### Post by carlos16 on 2013-09-06
Hello Kirk.
Thank you for reply.
I'm using the ubuntu-12.04.2-desktop-i386 version, and i configured to login automatically without password.
The image that appears is the default desktop wallpaper (all orange) but without the taskbar.
I left click and right cilck with the mouse on the 4 sides of the screen, but nothing happens. the taskbar don't appears.

Carlos16

---

### Post by VMC on 2013-09-06
Can you get to grub boot screen? If so, edit 'e' the ubuntu you want to boot, go to the end of the 'linux' line and remove 'splash quiet', then add 'nomodeset' and see if it boots. If not see what the messages tell you.

---

### Post by carlos16 on 2013-09-06
Hello VMC,
i can't get the grub menu. is a single boot system.
how can i get it?

---

### Post by Bashing-om on 2013-09-06
carlos16; Hi !
Grub boot menu:
From a cold boot, as soon as the bios screen clears depress and hold the shift key,

[INDENT][INDENT]all in knowing how
[/INDENT][/INDENT]

---

