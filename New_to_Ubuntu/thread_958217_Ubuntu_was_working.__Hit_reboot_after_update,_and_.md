---
title: "Ubuntu was working.  Hit reboot after update, and now hard hang"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Kusho on 2008-10-25
I have googled this, and not finding a good answer for what I"m having...  Thought I'd just post it.  Anyway.  This is a second PC...  and an old one at that...  but use it alot...  and would like to get it back up.  Had this before, but formatted, but Windows ME back on...  got fed up with that again...  and came back to Ubuntu for another round.  These issues might be related to old hardware...  but honestly when it's running, Ubuntu has been very stable on this system.  Issue is in bootup.

Okay, this is a Gateway p2 motherboard, with a p3 550 processor in it...  SBLive Value, and Vodoo 5500 Video card...

Everything was up and running fine, Ubuntu got some kind of update, and wanted to reboot.  Now it hangs.  

Escape gives me the options---  (And i'm typing from notes...  so this is somewhat close)

Ubuntu 8.04.1  ---  2.6.24.21 (boot normal.)
                               (recovery)
                     2.6.24.19 (normal)
                                 (recovery)
                      2.6.24.16 (normal)
                                   (recovery)

Every option hangs.  If I do normal, I never get to the Ubuntu screen.  (3 normal error messages, that I always get...  Something about 2000 bios issue...  and something else...  but I don't think that's the problem as it showed up when Ubuntu was working, and went right past it.

If I click Recovery the last two lines shown are
63.075.886  PCI Enabling device   0000.00.0f.0  (0104 -> 0105)
63.075.969  PCI Found IRQ 10 for device 0000.00.0f.0

Then it hangs.

Does this mean anything to anyone.  Now if I load the Ubuntu disk, it also hard hangs.  It will come up to the option to install, or run without changes...  but i choose either, it starts thinking...  then it hangs.

Last time I got this and it hit the same way, I just gave up on Ubuntu, formatted back to Windows ME and surfed till I got a hard virus that I could no longer fix...  (all virus software won't update with ME being old, but PC to old to load XP)

So went back to Ubuntu again...  ran great for like 6 months...  now some patch, and it's hanging HARD.  Don't know enough to even know what to check.  Any thoughts??

---

### Post by fikelfikel on 2008-10-25
Try waiting till Interpid Ibex comes out in 5 days. I think from the installation, you can do an upgrade. Did a window come up while updating like "Not Authenticated" or something? If that happened, and you remember the name, please post it. We will be able to verify it. Usually that happens with GStreamer. Did you have Backports ticked in Software Sources? That could be a problem. It won't infect it or anything, but they can do some bad damage to your PC.

If I were you, I would try one of these solutions. You may not be able to access your PC to disable Backports, so if you are really wanting to fix it straight away, get the unstable beta of Interpid Ibex, or wait 5 days for the stable release.

There is also might be a way to fix it with GRUB, you'd have to be good at the commands. I think you should Google it.

---

### Post by fikelfikel on 2008-10-25
Try formatting it and installing Interpid. You will (duh!) loose everything, or you can partition it with both versions left, but it uses a lot more space. Of course, you can backup everything on an external HDD.

---

### Post by Kusho on 2008-10-25
Yea I do think something said it couldn't authenticate...  Didn't think much of it at the time.

Wonder why I can't just reload off of the disk...  but sounds like a good solve.

Thanks.

I'll probally have to rehack it to make it detect my Vodoo 5500...  but it doesn't work at all now.

Thanks for the explination.  I also do think I added like 1 other distro on it per some forum for looking for a driver for the 5500...  that would be funny for a reason that this happened.

Still think I should be able to reload from the freakin CD thou.

---

### Post by Kusho on 2008-10-31
Ubuntu 8.10 out, i download it.  burn the iso...  come in here...  and this is after multiple copies of 8.04 that would hang on either the test ubuntu off the cd, or install...  different spots of hangage...  and now, for some reason it doesn't detect the disk.  ubuntu shows it as a blank cd, but it freaking booted right up into ubuntu on the old install...  no reasons why...  nothing.  i'm almost scared to reboot and just see how long it will stay up before i have to.  how odd.  was looking on here how i can turn off any unauthorized distros just as the possible culprit...  but now curious if it was some weird hardware glitch that fixed itself.  but i guess we can call this one resolved...  cleared before isolation

---

### Post by Kusho on 2008-10-31
Okay I figured this out.  Boot after this one hung as well.  Tried 8.10 cd and it also hung.  I went thru the boards in the pc and I had a pci hard drive controller card I added to this box to attempt to add larger hard drives.  (won't recognize larger hard drives)  When I removed this card, it booted right up.  So for some reason this second controller card was hanging the hd.

---

