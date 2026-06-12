---
title: "Ubuntu don't boot"
date: 2021-01-12
forum: New to Ubuntu
---

### Post by poncho2808 on 2021-01-12
After turning on a computer i see only dark screen. I tried boot-repair but the result is the same. Link to pastebin from boot-repair: [https://paste.ubuntu.com/p/N8wZHY6KzY/](https://paste.ubuntu.com/p/N8wZHY6KzY/) 
I would appreciate some help.

---

### Post by grahammechanical on 2021-01-12
> After turning on a computer i see only dark screen.

Do you not see the manufacturer's splash screen with its option to load into the UEFI settings utility? Note this advice from Boot Repair

>  Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.1 LTS entry 

Have you done that? The Grub boot loader will give you an option to load either Ubuntu or Windows. The Microsoft boot loader will only allow you to load Windows. So if UEFI firmware is set to boot Windows then you will not have an option to load Ubuntu.

It is important to know exactly when that black screen occurs. Is it before either the boot loader of Windows or Ubuntu starts to load or after one of them starts to load?

Regards

---

### Post by VMC on 2021-01-12
The second line of summary:
```
[COLOR=#666666]=[/COLOR][COLOR=#000000]> No boot loader is installed in the MBR of /dev/sdb.[/COLOR]
```[COLOR=#000000]
Grub is not installed. Use live dvd to install grub:
[/COLOR][repair-grub]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")

---

### Post by poncho2808 on 2021-01-12
It Is happening exactly after manufacturer Splash screen. I do not have Windows installed, i have only Ubuntu for a couple of months. To be honest i do not really understand what firmware boot means

---

### Post by poncho2808 on 2021-01-12
> **VMC said:**
> The second line of summary:
```
[COLOR=#666666]=[/COLOR][COLOR=#000000]> No boot loader is installed in the MBR of /dev/sdb.[/COLOR]
```[COLOR=#000000]
Grub is not installed. Use live dvd to install grub:
[/COLOR][repair-grub]("https://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd")
 

After 'grub-install /dev/sdb' i received 'error:cannot find EFI directory'

---

### Post by oldfred on 2021-01-12
You should not have grub installed in MBR of sdb, since you have UEFI system with UEFI version of grub.
Did UEFI get updated and then you may need to redo some settings in UEFI that you changed previously?

What brand/model system?
What video card/chip?

Since only one install it may be booting thru grub & having video or other issue.
Can you press escape key when booting? It should be after UEFI/BIOS & before grub menu would appear. You may have to try several time to get it correct.
Then see if recovery mode boots.

If not using Windows best not to use NTFS.
NTFS requires chkdsk or defrag periodically and you cannot do those from Linux.

---

### Post by poncho2808 on 2021-01-12
Video card : Nvidia GTX 1060
I didn't update anything lately, the problem occured without changes to the system. 
After pressing escape i see command line with "grub>". What should i type here to boot a Recovery mode?

---

### Post by oldfred on 2021-01-12
First just try enter.
Then try this
configfile (hd0,2)/boot/grub/grub.cfg
or 
configfile (hd1,2)/boot/grub/grub.cfg
Your install is in sdb2, but boot drive normally seen in grub as hd0, but if system booting from hd0, then install is in hd1. I typically have to experiment.
You can confirm which it sees with 
ls
ls (hd0,2)/  # Do you see 'vmlinuz' and 'initrd.img' ?
or 
ls (hd0,2)/boot  # Do you see 'vmlinuz' and 'initrd.img' ?

Update may not have added nVidia driver like it should have.

---

### Post by poncho2808 on 2021-01-13
Yes, in (hd0, 2)/boot i see those things.

---

### Post by yancek on 2021-01-13
> Yes, in (hd0, 2)/boot i see those things. 		 

According to what you posted in your last post, you should be able to boot from the Grub prompt with the entry posted by oldfred in the post just above:

> configfile (hd0,2)/boot/grub/grub.cfg 

In your initial post, you indicate that when you boot, you only see a black screen.  If that were the case, how did you get the output from boot repair?  You must have booted something.

There were a number of questions asked that would have probably helped which you did not answer.  When you boot the computer, the first thing one usually sees is the manufacturer logo and there should be a message (usually at the bottom of the screen) showing for a few seconds telling you which key to press to access the BIOS firmware.  You have an EFI install of Ubuntu because you have an EFI partition showing in the boot repair output beginning at line 40.  If you scroll further down in the boot repair file to line 88 you will see the entry Boot0002 which is Ubuntu.  It appears to be first in boot order (line 85) so verify that.  

If the suggested entry above does not boot, post back with the results/messages you see and answer the other questions asked by members.

---

### Post by oldfred on 2021-01-13
If you have the nVidia card, you need nVidia driver or nomodeset.
You used to always use nomodeset to boot live installer & first boot or until you installed proprietary nVidia driver.

If installed press escape to get grub menu and add nomodeset.
The recovery mode also has the nomodeset parameter.

Safe Graphics Boot option on installer adds nomodeset.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by poncho2808 on 2021-01-14
Booting with nomodest parameter helped. Thank you very much

---

