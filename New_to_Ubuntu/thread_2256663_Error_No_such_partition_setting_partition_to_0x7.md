---
title: "Error: No such partition/ setting partition to 0x7"
date: 2014-12-14
forum: New to Ubuntu
---

### Post by bannnnab on 2014-12-14
Hello,

 First of all i'm new to this forum so i hope i post my thread in the right place.
Oh, i'm also not a native english speaker, so forgive my grammar and other writting problems ):P


I have an Asus laptop with a dual boot Ubuntu 14.04 and Windows 8.1, and it was working well for quite a while (more than one year).
But yesterday, suddently, i open the computer and choose windows in the (grub if i get it?) purpule page with my different OS (i have the choice between 4 differents boot, including windows 8.1 and Ubuntu).

The purpule page stay for a while and then i get this error on it:

No such partition : "number of the partition"
Setting partition to 0x7

press enter to continue...

Then black screen and nothing more.

I reboot and try to launch Ubuntu instead: it works perfectly.
I even see my Windows partition (with Gparted as well) and can enter in it when i mount it.

The day before, i just installed Skype and League of Legend on windows. No update, and nothing new on ubuntu as well.

Is the problem the path to access the partition?
Or something esle?

And how to fix that problem?
i would like to repair the windows partition without reinstall or delete if possible.

Thanks for your help!

---

### Post by oldfred on 2014-12-14
Boot-Repair cannot fix most Windows issues, but its summary report may show what they are.
You probably need a Windows repairCD or flash drive which you need to make when Windows is working. But if you know anyone with Windows 8 you can make the repair flash drive on their computer.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

