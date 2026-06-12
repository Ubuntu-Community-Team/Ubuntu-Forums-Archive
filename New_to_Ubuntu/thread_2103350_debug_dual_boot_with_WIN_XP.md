---
title: "debug dual boot with WIN_XP"
date: 2013-01-09
forum: New to Ubuntu
---

### Post by spincraft on 2013-01-09
Hi 
I have a single hard drive PC with WIN_XP SP3 installed and then u12.10 installed from DVD. The start-up dual-boot menu is missing. Otherwise, I think the setup is OK. I re-partitioned the h/d OK and the sizes work, just the boot up always starts WIN_XP with no option to boot u12.10.
Your suggestions are welcome.
Thanks

---

### Post by jtarin on 2013-01-09
Did you install Ubuntu in a seperate partition or did you install "WUBI" within WIN?

---

### Post by spincraft on 2013-01-10
Thanks for your reply.
I installed u12.10 from the DVD not inside WIN_XP.
I can see the partitions and select which one to boot from.
I choose the wrong one since it gives the err,"missing Windows HAL'. 

Your suggestions are appreciated.

---

### Post by oldfred on 2013-01-10
Missing hal.dll is not a missing file normally, but a boot.ini that is not correct. You may have to edit boot.ini.

       Fix WinXP hal.dll 
[http://ubuntuforums.org/showthread.php?t=1410696](http://ubuntuforums.org/showthread.php?t=1410696)
Missing hal.dll not always missing, but other errors or boot.ini wrong partition
[http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt](http://members.iinet.net.au/~herman546/p15.html#hal.dll_is_missing_or_corrupt)
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
Error message: "Windows could not start because of a computer disk hardware configuration problem"
[http://support.microsoft.com/kb/314477](http://support.microsoft.com/kb/314477)

    
If you want specific suggestions, run the BootInfo report and post the link it creates.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by spincraft on 2013-01-11
It's working.
Thanks for your help!

---

