---
title: "Xubuntu won't load"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-11-11
I installed Xubuntu on an older computer awhile back and it worked fine, but I wanted more speed and I did a RAM upgrade.

It worked fine for some time, speed improved and all that... but now xubuntu won't boot up for some reason.

I've tried using even the live CD but it wont boot either. 

I can't open a terminal. 

Anyone have any ideas?

---

### Post by Arlo012 on 2008-11-11
That sounds like it might be a memory problem. Have you tried removing the more recently installed memory and seeing if it boots, or instead removing the old and seeing if it will boot with only the new? I am not too knowledgeable in laptop hardware, but if that's at all possible it might be a good first step. Also see if you can boot to any other CDs before you try that.... It's a stretch, but maybe some other CD will boot?

---

### Post by Bigtime_Scrub on 2008-11-11
> **Arlo012 said:**
> That sounds like it might be a memory problem. Have you tried removing the more recently installed memory and seeing if it boots, or instead removing the old and seeing if it will boot with only the new? I am not too knowledgeable in laptop hardware, but if that's at all possible it might be a good first step. Also see if you can boot to any other CDs before you try that.... It's a stretch, but maybe some other CD will boot?

Actually I already tried that and it didn't work either. If I could just get it to boot into a terminal It would be ok and I could fix things.

---

### Post by oilchangeguy on 2008-11-11
> **Bigtime_Scrub said:**
> Actually I already tried that and it didn't work either. If I could just get it to boot into a terminal It would be ok and I could fix things.

how do you know that if you could get to a terminal you "could fix things"? what did you do to the computer other than adding ram?

---

### Post by Bigtime_Scrub on 2008-11-11
> **oilchangeguy said:**
> how do you know that if you could get to a terminal you "could fix things"? what did you do to the computer other than adding ram?

I didnt do anything else.

But, if If I could get to a terminal, I could run a shred command, wipe the HD, and reinstall. (Just so you know I dont use this computer, so my friend could have done anything to it)

---

### Post by lisati on 2008-11-11
Possibly something in your BIOS settings is hanging up the boot process.

Most of the BIOSes on computers I have regularly used have an option to reload defaults, which might be what is needed.

Depending on your BIOS you might also need to make sure that it has properly detected your hardware - an older machine I have has a habit of clearing out the settings for the HD and the CD-ROM when I reset it to defaults, making the system unbootable. This is usually easily fixed by telling the BIOS to auto-detect the hard drive and CD-ROM.

---

### Post by Bigtime_Scrub on 2008-11-11
I got this error when booting from Xubuntu from CD. 

[122.179536] unexpected IRQ trap at vector 3a

---

