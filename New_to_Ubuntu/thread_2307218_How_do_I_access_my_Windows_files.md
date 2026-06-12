---
title: "How do I access my Windows files"
date: 2015-12-22
forum: New to Ubuntu
---

### Post by chzuck on 2015-12-22
I am new to Ubuntu and cannot figure out how to access my computer's Windows files.  I am running Ubuntu 14 on a flash drive.  I have been doing this with Mint for some time with excellent results.  With Mint I am able to mount Windows and access all my document files.

---

### Post by Vladlenin5000 on 2015-12-22
> **chzuck said:**
>   I have been doing this with Mint for some time with excellent results.  With Mint I am able to mount Windows and access all my document files.

So, what's preventing you from doing the same in Ubuntu?

---

### Post by chzuck on 2015-12-22
I get a window saying "unable to mount windows followed by > Error mounting /dev/sda2 at /media/charlie/Windows: Command-line `mount -t "ntfs" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,dmask=0077,fmask=0177" "/dev/sda2" "/media/charlie/Windows"' exited with non-zero exit status 14: The disk contains an unclean file system (0, 0).
Metadata kept in Windows cache, refused to mount.
Failed to mount '/dev/sda2': Operation not permitted
The NTFS partition is in an unsafe state. Please resume and shutdown
Windows fully (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option.


---

### Post by Vladlenin5000 on 2015-12-22
The error message says it all. Please do exactly that.
BTW, you couldn't possibly have had it mounted in Mint in the same condition - "unsafe state" = hybernated = DEFAULT state in any Windows 8/8.1/10 -.
Perhaps the Windows you accessed in Mint wasn't any of the aforementioned versions...

EDIT:
Either way you should absolutely AVOID what you're trying to do. Windows doesn't like it and can give you several issues. Use a shared partition (NTFS) to store your data, accessible from both OSs, a cloud, anything... Anything else than directly reading/writing files stored in the Windows main partition.

---

### Post by chzuck on 2015-12-22
You are most likely correct.  I will do what it says and see what happens.  I did not quite understand what it was saying at first.  Thanks for your quick response.

---

### Post by Vladlenin5000 on 2015-12-22
You're welcome.

Please be aware that you actually need to disable the new fast startup Windows feature and then shutdown, not just reboot.
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) (should be the same for any of the aforementioned versions).

---

### Post by chzuck on 2015-12-22
Thanks again, it worked just as the warning window said.  I need to read things more thorough.  And I really thought I had shut windows down properly.

---

### Post by Mark Phelps on 2015-12-24
> **chzuck said:**
> Thanks again, it worked just as the warning window said.  I need to read things more thorough.  And I really thought I had shut windows down properly.

It's NOT a matter of shutting down Windows properly.  With Win8-10, it automatically goes into Hibernation, no matter HOW you shut it down.  That's because it has something known as Fast Startup (which is not the same as fast boot) enabled by default.  With this turned on, you can NOT access the Windows partitions from Linux even after it is shut down because the partitions remain mounted to Windows.

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

### Post by chzuck on 2015-12-24
Apparently I do not have Fast Startup enabled because after shutting windows down I was able to access windows with Ubuntu running via the flash drive.

---

### Post by chzuck on 2015-12-25
> **Mark Phelps said:**
> It's NOT a matter of shutting down Windows properly.  With Win8-10, it automatically goes into Hibernation, no matter HOW you shut it down.  That's because it has something known as Fast Startup (which is not the same as fast boot) enabled by default.  With this turned on, you can NOT access the Windows partitions from Linux even after it is shut down because the partitions remain mounted to Windows.

There are two ways to disable FastStartup in Win8/10; (1) through the Control Panel, and (2) through an elevated command prompt.

Control Panel - Open Control Panel --> Power Options.
Select "Choose what the power buttons do"
Select "Change settings that are currently unavailable"
At the bottom of the Window, under Shutdown settings, uncheck the box regarding fast startup

Elevated command prompt - run the following command:
REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F

In both cases, reboot Windows.

NOW, FastStartup is disabled.


I checked and my Windows 10 does not have that option only **Sleep** and **Lock**.

---

### Post by Geoffrey_Arndt on 2015-12-25
Chzuck,

In your post #7, you said "Thanks again, it worked just as the warning window said" . . . . ***what exactly did you do*** to allow you to see or access the windows folders (what was different from your post #1, . . I'm not clear on that).    

Any information you can provide may be very helpful to future readers with same issue . . . . 

(note . . . I can't access/look at the power settings screens as I have only have classic windows (pre-UEFI) and Linux on all my machines.))  In fact - 75% of my PC's have Linux as the only OS as they came that way from the store . .

---

### Post by chzuck on 2015-12-25
[I]The NTFS partition is in an unsafe state. [U][B]Please resume and shutdown
Windows fully[/B][/U] (no hibernation or fast restarting), or mount the volume
read-only with the 'ro' mount option. 			 		

[/I]The phrase that is underlined is what I was referring to.  I shut down Ubuntu, removed the flash drive and started Windows 10, then shut it down using the "shut down" button, inserted the flash drive and restarted Ubuntu and I was able to access my Windows files that are on the laptop harddrive.

---

