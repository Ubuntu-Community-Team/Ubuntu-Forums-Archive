---
title: "Hiding Linux drives from Windows and vice versa in a dual boot?"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by codenameSQL on 2013-07-09
Half of this question - how to hide drives in 'Buntu - I found answered in detail here:

[http://ubuntuforums.org/showthread.php?t=1782823](http://ubuntuforums.org/showthread.php?t=1782823)

Now, do any of you more experienced dual booter know how to stop WinXP (and/or other flavors) from automatically trying to discover/etc linux drives?  I'd prefer to have windows ignore the drive entirely since it doesn't have a clue what to do with it yet discovers and attempts to install it anyway.  Probably nothing critical, but I'd rather win just leave my linux drives alone if possible.

Thanks

---

### Post by farrinux on 2013-07-09
> **codenameSQL said:**
> Half of this question - how to hide drives in 'Buntu - I found answered in detail here:

[http://ubuntuforums.org/showthread.php?t=1782823](http://ubuntuforums.org/showthread.php?t=1782823)

Now, do any of you more experienced dual booter know how to stop WinXP (and/or other flavors) from automatically trying to discover/etc linux drives?  I'd prefer to have windows ignore the drive entirely since it doesn't have a clue what to do with it yet discovers and attempts to install it anyway.  Probably nothing critical, but I'd rather win just leave my linux drives alone if possible.

Thanks

Are you using a WUBI installation?  I have several dual boot machines with Ubuntu 12.04, and / or Win xp or Win 7 and none of the Win installations can see the Ubuntu installs other than the partitions under disc management. Then they show up as unknown file systems.  Not sure what you have going on.  Do you have a screen shot of the Window desktop with the linux partition shown?

---

### Post by codenameSQL on 2013-07-10
No, not a wubi install.  Clean installs (2 distros) on a separate disk.  No NTFS partitions on that disk - one swap and 5 ext4's.  It also shows unknown file systems in disk manager.

At boot time in WinXP, the "New hardware found"/"Installing drivers"/"Reboot to use" (the latter is ignored of course) dialogues are popping up for the linux drive with every startup.  After that it seems to be fine - just annoying that is occurs every time. Thought perhaps there could be a Reg hack or setting somewhere to stop it.

---

### Post by su:bhatta on 2013-07-10
i have dual booted ubuntu with win7 & am currently dual booting Ubuntu 13.04 with Win8, but never have seen these "new Hardware found" message or anything like that ever...
Only time Win7/8 is aware of Ubuntu  or ext4 logical drives is when it shows them in Disk Management....

Since you have got a separate drive for Linux, i guess u r getting these options because windows wants to use that drive just like it would do with  external HDD or flash drive...

---

### Post by farrinux on 2013-07-10
> **codenameSQL said:**
> No, not a wubi install.  Clean installs (2 distros) on a separate disk.  No NTFS partitions on that disk - one swap and 5 ext4's.  It also shows unknown file systems in disk manager.

At boot time in WinXP, the "New hardware found"/"Installing drivers"/"Reboot to use" (the latter is ignored of course) dialogues are popping up for the linux drive with every startup.  After that it seems to be fine - just annoying that is occurs every time. Thought perhaps there could be a Reg hack or setting somewhere to stop it.

I think i would let the new hardware found complete.  I dual boot and have my linux on a separate hdd than my win installs.  (win xp or win 7) and have not had this behavior. As I stated above I have 5 machines and they do not show this problem.

I have a question to help trouble shoot this.  When you installed your distros on the separate hdd. Did you install grub there as well?  If you did, a troubleshoot that we could do would be to unplug that hdd from the system.  Then if you were using that hdd to boot from (which you should have been doing).  Start your system up and go into the bios and set the hdd that has windows on it as first priority at boot, save  and restart.  Your system should then boot into win and if that hardware found dialogue comes up it is something in windows.  Check device manager for any new hardware etc.  It really is impossible for windows to see or to even mount a linux drive.  On my dual boots the hdd with the linux installs do not even show up in "my computer".  Only in disc management and then as drives with unknown file systems.  I have never had to monkey in the win registry for dual boot. 

One last thought I have is would that hdd that you put ubuntu on be one of the newer Hybrid type drives?  Like the ones from Seagate?  If it is maybe that is putting a monkey wrench in the works.

---

### Post by codenameSQL on 2013-07-11
I think the issue has gone away.  No, not a newer Hybrid type drive.  Just a standard internal 3.5 IDE Barracuda.

WinXP seems to have made the adjustment.  
Here's what I did, but I really don't know if this solved the problem or which step may have.

I removed all external drives and unplugged the Seagate.
Changed the Bios to boot from the windows drive.
Let Win boot normally. OK
Shut down. 
Add the Seagate.
Boot from Win drive again with Seagate Attached. - OK
Shut down
Changed Bios to boot from Linux/Seagate.
Booted into Win from Grub - OK
Added all external drives back one at a time. - OK
Restart Win - OK
Restart into Linux - OK

No more "New hardware found" on the internal Linux drive". 

Don't know exactly what caused the issue, or exactly what solved it - but at any rate it's gone..
Thanks!

---

