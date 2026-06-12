---
title: "Windows can't see a partition after i installed ubuntu"
date: 2015-08-27
forum: New to Ubuntu
---

### Post by ali52 on 2015-08-27
this is my first time installing linux, i'm completely new here. I installed ubuntu on top of Windows 10. I partitioned the drives as i  installed ubuntu. Ubuntu can see and access all of them. But windows  can't access one of the partitions. It's not the partition which ubuntu  was installed, i didn't install any os in there. And it is in ntfs  format. But still windows can't see it.

[ATTACH=CONFIG]264081[/ATTACH]

The partition i'm talking about is /sda3/ which is labeled "downrams". This partition was first mounted when i installed ubuntu, since i'm new i  don't know what that means but i unmounted it thinking that may be the  problem. But it didn't change anything.

---

### Post by sotiris2 on 2015-08-27
Are you certain that Windows can't see the partition? Maybe for some reason it doesn't automatically assign a letter to it? Check [here](http://windows.microsoft.com/en-us/windows/change-add-remove-drive-letter#1TC=windows-7) for how to assign a letter manually to partitions that don't have a letter. You could show us a picture from Windows' Disk Management utility which will show if the partition is really undetectable. 

I doubt this is an Ubuntu issue since it takes a very handoff-ish and careful approach to ntfs filesystems (it will not mount them if they are hibernated for example). On the contrary Windows will happily tell you your Linux partitions are unformatted and ask you to format them, so take special care.

---

### Post by kagashe on 2015-08-27
There is no EFI partition. Is it MBR system? (and not GPT).

Kamalakar

---

### Post by ajgreeny on 2015-08-27
You do not say so but I am assuming that both OSs will boot if you choose them from the grub menu, if grub is what you are using to boot the machine.

Did you shrink the Windows 10 partition during installation or did you shrink it with the windows own disk management, and then make the Ubuntu partitions from the free space?

---

### Post by grahammechanical on 2015-08-27
Do you want my guess? The partition that you think windows cannot see is the partition that windows is installed into.

sda5 is labelled "windows.os" but it is inside the sda2 extended partition. So it is a logical partition and I do not think that Windows likes to be installed in logical partitons. I may be wrong. sda3 is a primary partition and it has the boot flag. If we add the size of sda2 to the size of sda3 we get a sum equal to the size of sda itself. There is no sda1. There once was but it is now gone. And there is no sda4. Perhaps there never was. I think logical partitions start being numbered from sda5 to allow for 4 primary partitions.

sda6; sda7; & sda5 are all logical paritions inside sda2, an extended partition. And their sizes total the size of sda2. So, guess what ...

Regards.

---

### Post by Mark Phelps on 2015-08-27
You said you installed Ubuntu on top of Win10, but you also say that Windows can't access the NTFS partition.  So, what version of Windows are you using at present?

---

### Post by Mike_Walsh on 2015-08-30
Oh, gawd.

That's a **mess. **And no mistake about it. Got to be 'tidied up', **that's** for sure.

IMHO, the best course of action would be to copy over to an external source (eg. an external HDD) anything you wish to keep, and then:-

1) Wipe the disk clean.
2) Reinstall Win 10.
3) Use the Windows disk management tools to shrink it down to, say, 50-100 GB.
4) In the now unallocated space, create a new partition (sda2) and install Ubuntu to that. Ubuntu will ask if you want to install alongside Windows 10, but you would be better off choosing the 'Something else' option, and manually installing Ubuntu to sda2. The 'Install alongside' option used to have problems; I'm not certain whether these have yet been fixed.
5) Create a new partiton (sda3) for your 'Downrams' (?) stuff. You can then copy this back afterwards, once you get your OS's set up and running.
6) You will, in all likelihood, get initial boot problems. This is quite normal, actually! If you do, download, burn to CD, and then run the 'Boot Repair' program, and post back. Make sure to give us the 'pastebin' output from Boot Repair, please. Others here are more experienced with this than I am.


Regards,

Mike. ;)

---

