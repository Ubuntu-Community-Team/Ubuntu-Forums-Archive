---
title: "Dual monitor suddenly not dual!"
date: 2012-08-14
forum: New to Ubuntu
---

### Post by malcmail on 2012-08-14
Not 100% sure if this is the right place but here goes.

A good while back I picked up a Radeon HD card to dual screen my 12.04 PC. About a week ago I had to reboot the machine ( a problem with using the gnome 3 shell it seemed). Anyway it then only came back on one screen. Queue holiday time.

So I came back to find it still only working on the screen that was attached to the card - no life at all in the onboard display. But the monitor still worked on another PC. Cue the race to get a new motherboard seeing as I've had the onboard graphics fail on me before. 

Swapped everything over and.... same problem. Suddenly had a good idea. Went to the BIOS and changed the primary display which had become PCI. Swapped it to onboard and lo and behold the onboard now works. So whats the problem? Now there's no life in the monitor via the PCI card.

If I do lspci I can see both the onboard graphics and the Radeon card. xrandr -q only suggests one monitor, as does the display settings. And I get an error message if I try to start the Catalyst Centre saying no driver (even though the monitor actually works when the BIOS sets it as primary). 

I didn't change a thing so what has happened? I really don't want to do a reinstall but I'm feeling like its about the only way at the moment. Anyone any ideas?

Thanks in advance.

---

