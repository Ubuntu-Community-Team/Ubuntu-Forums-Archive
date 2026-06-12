---
title: "added a drive with xp, updated grub and now xp is wrecked"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by timothy69 on 2011-11-14
ok.  so i have ubuntu and xp.  xp was strictly for games(FO3, BF2) and crashed when someone took it online and got a virus.  i reinstalled xp on the 2nd drive, updated grub just like last time.  Now xp is set to absolute min video res.  it wont change, but does show other settings.  the driver is still installed, reinstalling did nothing.  system restore did nothing.  
did  sudo update-grub mess up my boot sector?
if so, why did it only affect the video resolution and not make any error messages? everything still runs fine(when i can see it) can it be fixed without reinstalling again?

did i do something wrong and how can i avoid doing it again?

---

### Post by mr.suchy on 2011-11-14
Hi,

One again. Why U think than was a virus ? I think U have still problem with graphic driver and this is not related with grub.

Best regards.

---

### Post by Matt__ on 2011-11-14
hmmm...is this even an ubuntu question at all?
and what has grub got to do with xp graphics display?

that aside, did you reinstall all the motherboard drivers (ie vga) once you reinstalled xp?
THEN whatever proprietary drivers your gfx need.

---

### Post by Mark Phelps on 2011-11-14
Doing "sudo update-grub" only regenerates the GRUB menu.  It does not reinstall GRUB; therefore, it did nothing to your boot sector.

If XP is on its own drive, you should NOT have GRUB installed there.  It does nothing for XP and only prevents the drive from being bootable on its own.

If you have an XP CD, I would recommend the following:
1) Disconnect the Ubuntu drive, leaving only the XP drive connected
2) Boot from your XP CD
3) Go into the Recovery Console from the XP CD (this is done by entering "R")
4) Run the command "fixmbr". This will overwrite GRUB in the MBR, returning it to its original state.

Then, see if XP will then boot using only that drive.  If it will, you will then need to fix the video drivers problem. That has nothing to do with Ubuntu or GRUB.

Once you get XP working, reconnect the Ubuntu drive and boot from THAT drive.

Open a terminal and enter "sudo update-grub". That will regenerate the GRUB menu on the Ubuntu drive.  You should now get a GRUB menu when you reboot, that allows you to select XP or Ubuntu.

---

### Post by timothy69 on 2011-11-14
yes, xp was up and running on its own with all drivers installed.  it worked fine until i plugged ubuntu drive back in and booted from it.  after i updated grub xp worked....but not well.  i have reinstalled all drivers to no effect.

anyways, i am going to reinstall it again and do what Phelps suggested, which is what i did last time.
we'll see how it goes.  i'll keep you posted.

---

### Post by grahammechanical on 2011-11-14
I am of the opinion (how correct I am I do not know) that unless the Windows drive/partition is formatted then the re-install process skips those files that it finds are already on the drive. This would mean that corrupted files do not get overwritten and the problem remains.

I could be wrong about this.

Regards.

---

### Post by Mark Phelps on 2011-11-14
If, after you got XP working OK, and reconnected the Ubuntu drive, and changed boot to the Ubuntu drive, you said you updated GRUB.

By that, I hope you meant that you opened a terminal and entered "sudo update-grub".  All that will do is regenerate the GRUB menu, pointing to where the OSs are located NOW.  That will have no effect at all on your XP install.

If you then select XP and something is wrong, it's not related to Ubuntu nor to GRUB.  All GRUB does, in the case of Windows OSs, is hand off control to the Windows boot loader in the partition named in the GRUB config file.  If Windows then does not boot right, or has other problems, that has nothing to do with GRUB.

---

### Post by timothy69 on 2011-11-16
i had a windows guy look at it.  something to do with a file on the boot sector.  the problem just didn't show until after a reboot, but i had loaded ubuntu and sudo update-grub before i ran windows again.  so i had just ASSUMED it was grub.
the windows problem may be why i had to update grub 3 times before it saw the xp install.
anyways, problem solved.  thanks for the help guys.

---

