---
title: "How do I remove Ubuntu?"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Perad1 on 2013-02-05
Hello.

I have a dual-boot system with Windows 8 / Ubuntu. I no longer need Ubuntu. How do I uninstall it without breaking my computer?

Is there a simple uninstall disc? Can I do it from the Ubuntu install disc?

I read somewhere I may need a Windows disc. I downloaded Windows 8 and only have a Windows 7 disc. Do I need one? Is this a problem?

---

### Post by offgridguy on 2013-02-05
> **Perad1 said:**
> Hello.

I have a dual-boot system with Windows 8 / Ubuntu. I no longer need Ubuntu. How do I uninstall it without breaking my computer?

Is there a simple uninstall disc? Can I do it from the Ubuntu install disc?

I read somewhere I may need a Windows disc. I downloaded Windows 8 and only have a Windows 7 disc. Do I need one? Is this a problem?
This thread deals with uninstalling ubuntu, and keeping windows 7
I don't know if it would be any different for windows 8.

[http://ubuntuforums.org/showthread.php?t=2104613](http://ubuntuforums.org/showthread.php?t=2104613)

See post #4 for OS-uninstaller.

---

### Post by The Cog on 2013-02-05
You need to do two things in this order:

1: Replace the GRUB bootloader that Ubuntu installs with the normal windows bootloader. I have no idea whether you can use a win7 CD to replace the win8 bootloader. There is a downloadable CD called SystemRescueCd that can install a "normal" bootloader whigh I know works with win7 but don't know about win8.

2: Delete the no-longer-used Ubuntu partitions.

Note that deleting the unused partitons will disable the GRUB bootloader which is why I say to replace the bootloader first.

---

### Post by Jake Sweeney on 2013-02-05
You will firstly have to choose Windows 8 at the boot up screen and locate the Ubuntu partitions.
Once located, you can delete them and merge them with your existing partition. 
Now, if you just reboot now the GRUB menu will just report a failure because there is no Ubuntu OS present. 
Therefore before restarting you should install EasyBCD or a recovery disc and create a Windows bootloader  so your computer will boot from that rather than GRUB.
When the bootloader has been created, restart your computer and it should just boot to your Windows OS and Ubuntu will be removed.
Hope this helps :)

---

### Post by Cheesemill on 2013-02-05
Or you can boot from a Ubuntu Secure Remix CD and use the included OS Uninstaller application to remove Ubuntu with the click of a mouse.

[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by cap10Ibraim on 2013-02-05
[http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-US/windows7/Create-a-system-repair-disc)
It has an interface that will help you detect errors and fix them automatically 
also it has a cmd type there 
bootrec.exe /FIXMBR

To Delete Ubuntu type in windows search disk management 
use this tool to delete windows partition 
Boot windows go to the control panel and make something called rescue disk 
you can use this rescue disk to boot 

I do this on a weekly basis ):P

---

### Post by Mark Phelps on 2013-02-05
> **Perad1 said:**
> Hello.

I have a dual-boot system with Windows 8 / Ubuntu. I no longer need Ubuntu. How do I uninstall it without breaking my computer?

Is there a simple uninstall disc? Can I do it from the Ubuntu install disc?

I read somewhere I may need a Windows disc. I downloaded Windows 8 and only have a Windows 7 disc. Do I need one? Is this a problem?

You want to create a Recovery Drive -- which is different in Win8 than it was in Win7.  Details below:

[http://winsupersite.com/article/windows8/windows-8-tip-create-recovery-media-144098]("http://winsupersite.com/article/windows8/windows-8-tip-create-recovery-media-144098")

---

