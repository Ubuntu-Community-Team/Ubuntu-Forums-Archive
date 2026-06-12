---
title: "Ubuntu 12.10 froze now won't get to sign on screen during boot."
date: 2013-04-12
forum: New to Ubuntu
---

### Post by alhefner on 2013-04-12
I was playing solitaire when my system froze up. I couldn't get anything to respond at all. No ability to get to te3rminal or anything else. I had to remove power to shut down the laptop since even the power button had no effect.

Now, I can't get to the sign on screen as the boot process seems to stop or hang up. It's looking like I may have to reinstall but that would wipe out my work with drivers and programs getting the system to where I wanted it.

Oh, yeah, I didn't bother making any kind of "rescue" disk either.](*,)

If I gotta start over, so be it but if there is a guru out there with a magic fix, I'll take it!

---

### Post by MG&amp;TL on 2013-04-13
'Hung' linux installs are rarely completely broken, just needing a bit of assistance. :-)

Before you start anything, boot a live CD and make a backup of your work on the hard drive. This means you can restore everything should your recovery attempt accidentally wipeout data.

Try holding the shift key down while your computer boots (as soon as it boots, holding it through BIOS if need be). You should get to a bootloader menu. From here, select 'recovery mode' for your kernel version (probably the second option down). You should then get to a friendly screen with options such as a filesystem check, a root shell prompt, or continuing to boot. Try selecting the filesystem check, as I suspect you have a corrupt filesystem, then when that's done (might take a while), try the 'continue to boot'. Your graphics drivers and things may be broken this boot, but that'll be fixed the next time you reboot.

Post back on your successes/failures.

---

### Post by alhefner on 2013-04-13
Well, I didn't do anything other than "try again" and it booted up... slowly but it got there and once the desktop appeared, it ran well. I'll mark this solved in a day or three if it keeps working...

---

### Post by MG&amp;TL on 2013-04-14
> **alhefner said:**
> Well, I didn't do anything other than "try again" and it booted up... slowly but it got there and once the desktop appeared, it ran well. I'll mark this solved in a day or three if it keeps working...

*shrugs* software does odd things sometimes. Glad you got it working!

---

