---
title: "Problem to acsess HDD"
date: 2017-09-20
forum: New to Ubuntu
---

### Post by mac187 on 2017-09-20
Hi people, need help to fix a problem..

I have 1 HDD that i have made 2 partitions, one with windowds and other with Ubuntu, and i have 1 more HDD where i store all music, files and etc..
When im using Ubuntu there is no problem, but everytime i boot into windows and use windows couple of days and go back to ubuntu i get this message:

Error mounting system-managed device /dev/sda1: Command-line `mount "/mnt/AC8CA01B8C9FDDE0"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.

How can i fix this problem so i dont have to fix that everytime ?

Thanx

---

### Post by SeijiSensei on 2017-09-20
How are you leaving Windows?  Don't use things like hibernate.  You must do a complete shutdown or reboot.

However first you must start Windows and run its disk-checking utility against the dirty partition.  There's a GUI for this, but it might be easier just to run "chkdsk d:" from a Windows command prompt.  (Replace d: with the appropriate identifier for the device.)

---

### Post by Mark Phelps on 2017-09-20
If you're running Win10, it AUTOMATICALLY goes into Hibernation when you shut it down, and ANY drives that were accessed in Windows will be unaccessible in Linux because Windows them keeps them mounted.

Win10 has enabled a new hibernation process known as Fast Startup -- which is different from Fast Boot.  This is supposed to dramatically speed up the booting process, but in some PCs, it actually slows it down or causes it to hang.  This could be what is happening to your PC.
 
Disabling Fast Startup might fix the booting problem.
 
There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.
 
Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup
 
Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
 
In both cases, reboot Windows.
 
NOW, FastStartup is disabled.

---

### Post by mac187 on 2017-09-24
I did what u said, but its still happening :/ another ways? Thanks

---

### Post by Geoffrey_Arndt on 2017-09-24
why is this thread marked "solved" . . . . ?

---

### Post by oldos2er on 2017-09-24
> **Geoffrey_Arndt said:**
> why is this thread marked "solved" . . . . ?

Unmarked.

@mac187 Don't mark your thread 'Solved' unless it truly is, and you no longer need help. To aid those looking for an answer to the same question, we would appreciate it if you would also post the solution, when/if it's found.

---

