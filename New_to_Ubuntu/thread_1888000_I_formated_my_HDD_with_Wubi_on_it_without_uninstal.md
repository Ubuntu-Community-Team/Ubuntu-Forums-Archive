---
title: "I formated my HDD with Wubi on it without uninstalling it :("
date: 2011-11-28
forum: New to Ubuntu
---

### Post by xiaokai on 2011-11-28
I formated my HDD with Wubi and reinstalled windows on it without uninstalling it :(

So now, I have this problem
that it asks me if i want to log in to Windows 7 or Ubuntu, but there is no Ubuntu anymore.

I checked msconfig to see if it was still there but because i reinstalled windows too it not there to delete it...

---

### Post by JKyleOKC on 2011-11-28
Search for a file named "boot.ini" which, on XP Pro, is in the root of C: and which provides that boot-time menu. If you find it, remove the line that refers to Ubuntu and save the edited file -- but be sure to first make a backup copy just in case it's needed. That should be all that you need to do, but Win 7 might be a bit more complicated...

---

### Post by oldfred on 2011-11-28
I think with Windows 7 it is BCDEdit to edit entries in the BCD.

[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)

[URL="https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?"]
[/URL]

---

### Post by lolpenguin on 2011-11-29
bcdedit will work, modifying boot.ini is not recommended, the easiest, and less dangerous way is to boot into Windows Recovery Environment (a recovery disk, install disk or recovery mode), start a Command Prompt and run
```
Bootrec.exe /FixMbr
```
This will replace the MBR with a pure Windows one, so all other entries, including Ubuntu will be removed.

---

### Post by Non-Sequitur on 2011-11-29
The very best and easiest solution to this problem is to boot into Windows 7 then create a "Windows 7 Repair disk".  Actually this is the first thing one should do following Windows 7 installation.  A problem like yours is then very simply fixed by booting to the repair disk and after it loads, select the dos prompt.  Next type: bootrec.exe /fixmbr.  Problem will be solved.  Remove the repair disk and reboot into Windows 7.

---

### Post by Mark Phelps on 2011-11-29
You don't need to repair the MBR, since you're able to boot into Win7.

Simply use EasyBCD to remove the extra OS selection in the boot menu.  That didn't get removed because you did not uninstall Wubi.

Also, the advice to create a Win7 Repair CD is good advice.  It's helpful to have this around, should you need to repair the Win7 boot loader.

---

