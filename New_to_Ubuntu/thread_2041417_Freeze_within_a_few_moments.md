---
title: "Freeze within a few moments"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by Marlbeire on 2012-08-12
Hi, I'm not really sure where to post this so I'm posting here.

I'm having a problem with my Acer aspire 522 freezing within a few moments. The installed OS is 12.04 64 bit. It had an encrypted home folder so the swap file was superfluous and if the screen was closed over without shutting down the result would be a black screen, no cursor, a problem I never got round to rectifying.
 Anyway, recently I inadvertently closed the lid and then decided to pull out the power cord.

On the installed ubuntu freezing occurs now without fail within a few seconds of meeting the lightdm login screen. With a 12.04 64 bit liveCD freezing happens on the splash screen. A Mint XFCE 64 bit liveCD gets to the desktop & freezes. I can sit & move across menus in bios for as long as I want, same in the liveCD menus. Does anybody have an idea into what's going on? Any help would be much appreciated.

edit: what I mean by freeze is no input is possible. No mouse movement, no keyboard input.

---

### Post by mr-woof on 2012-08-12
That sounds like a hardware related issue to me, especially if you're using a live cd. 

Things to try:

1) reseat your ram (i know it sounds silly, but it's helped me lots of times)
2) do you have another hard drive you can try in the machine?

---

### Post by mikechant on 2012-08-14
When you next get a freeze you can try the following:

Ctrl-ALT-F1 - This may get you a console screen if it's just the GUI freezing

ALTgr-SYSrq-REISUB - (I.e. hold down ALTgr and SYSrq keys, then type R,E,I,S,U,B one at a time in that order). If the monitor output is completely messed up but the kernel's still running this should reboot the system.

If either of the above work, your system is not completely frozen, you may have (e.g.) a graphics driver problem; if neither of these work you may have a hardware problem.

If it was just your installed OS freezing I'd say it might be corrupted from pulling the power cord; but as your live CDs freeze that pretty much rule that out.

---

