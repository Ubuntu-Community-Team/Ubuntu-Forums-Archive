---
title: "Dual boot Windows 7 failure"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by P_Sears on 2013-08-01
Hi, I have a dual-boot Ubuntu/Windows 7 computer. It was working fine, then last week I logged into the Windows side and ran some Microsoft updates. Next time I rebooted, I was not able to get into Windows. It gets stuck on the 'Loading Windows' screen and never boots. I tried safe mode, where it gets to CLASSPNP.SYS and then hangs. Upon reboot it says Windows didn't start properly last time, do I want to repair? If I say yes, it gets hung on the horizontal bar with the green stripes going across it. If I say no it gets stuck on 'Loading Windows.'  I tried booting from a Windows 7 install disk and it also hangs, I get the 'press a key to boot from disk' prompt but I don't ever get to the language selection screen so I can't do a restore or reinstall in place or fixmbr.

The Ubuntu side is fine. I can boot, log in, see and mount and umount the Windows partition and I can manipulate files on it so I replaced SAM, SOFTWARE, SYSTEM, SECURITY and DEFAULT, from the Windows partition's regback. That did not help. I used ntfsfix, and lilo and neither of those changed Windows' behavior.

I am not sure what to do next. I updated the grub file and after that I noticed the grub menu timeout was no longer set to wait for user input to select a boot OS, instead it automatically loaded Ubuntu. I went back in and changed that.  Windows system files are in sda2 and the Windows 7 loader is on /dev/sda1. I'm not sure if there is anything else I can do in Ubuntu to solve the problem. Or if I should take this to a Windows support site instead. I'd be grateful for any suggestions.

---

### Post by igodspeed on 2013-08-01
i have a similar problem and the windows gets to the welcome screen and then stops loading. I dont want to format my computer but i have tried almost everything.

---

### Post by westcoast01 on 2013-08-01
Same thing here ... this worked for me ... [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) ... Still to this day anytime I update either Ubuntu or Windows I have problems loading windows ultimate7x64. Sometimes I can not boot into Ubuntu until I select the memory test, let it run for a few seconds then hit esc to reboot. Hope this helps you as well as it helped me. Best of luck, West.

---

### Post by oldfred on 2013-08-01
Boot-Repair can add a Windows boot loader and only do minor fixes to Windows. Most Windows repairs need a Windows repairCD or Flash drive with the repair console or booting with f8 directly to repair console. It usually is too quick from grub menu to Windows for f8 to work. Some say if pressed at same time so it really is fractionally after it may work. Better to have repairCD.

Often  Windows chkdsk is the first thing to try, otherwise full Windows repairs. And those can only be done from a Windows repair console or some third party Windows repair tools like PartitionWizard, Easus, EasyBCD, or Hirens.
       [http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[http://www.bleepingcomputer.com/tutorials/tutorial148.html](http://www.bleepingcomputer.com/tutorials/tutorial148.html)

---

