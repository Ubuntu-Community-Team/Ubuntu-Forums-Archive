---
title: "No restore cd, only bootable USB with Xubuntu. Stuck in grub rescue&gt;"
date: 2012-09-04
forum: New to Ubuntu
---

### Post by AndyOpie150 on 2012-09-04
2003 Sony VAIO PVC V200G with Windows XP service pack 3.
First partition is 5GB. Second is 57GB XP OS. Third is 48GB wiped and ext.4 formated. Fourth is 990MB swap partition.

I had tried Lubuntu then Kubuntu. Decided to try Xubuntu so I wiped and mergeged the two partitions. Formated to ext.4. Already had Xubuntu on USB drive using Pendrivelinux utility program.
When I went to reboot (so I could eventualy boot into plop boot manager for the "boot into USB" option), I booted into 
error: no such partition.
grub rescue>

Need to fix so I can A. Boot into XP and B. Boot into USB and install Xubuntu.

Moderators: Please move to proper forum if this is not it.

---

### Post by oldfred on 2012-09-04
This is one of the easiest ways. And if for some reason it does not work, you can post the link from running BootInfo for details.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

If you have to manually boot.
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

Manual boot:
See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

# this exampe is sda2 or hd0,2 as location of install.
set prefix=(hd0,2)/boot/grub
set root=(hd0,2)
linux (hd0,2)/vmlinuz root=/dev/sda2 ro
initrd (hd0,2)/initrd.img
boot

---

### Post by AndyOpie150 on 2012-09-04
Will have to do manually. Output of ls:
(hd0)
(hd0, msdos5)
(hd0, msdos2)
(hd0, msdos1)

This looks different from the outputs in the links. I'm I correct in assuming that (hd0) is the 5GB partition, (md0, msdos1) is the Windows partition, (hd0, msdos2) is the wiped and merged partition, and (hd, msdos5) is the swap partition?

---

### Post by oldfred on 2012-09-04
hd0 is just the drive or sda.

Then you have three partitions sda1 (hd0,1), sda2 (hd0,2) and sda5 (hd0,5). Often one is swap and will have no files at all.

Try this for all three partitions  1, 2, & 5

ls (hd0,5)/  # Do you see 'vmlinuz' and 'initrd.img' ?
ls (hd0,5)/boot # Do you see the kernel and initrd image files ?
ls (hd0,5)/boot/grub # Do you see lots of *.mod files and grub.cfg ?

---

### Post by AndyOpie150 on 2012-09-04
Tried:
ls (hd0,5)/ and ls (hd0, msdos5)/. Output of both were: no such file system.

Tried:
The same thing with msdos1 and msdos 2 and got: no such disk.

---

### Post by oldfred on 2012-09-04
If you are sure sda2 is Windows this may boot you into it. It sounds like you delete the install with all the grub files.

grub > chainloader (hd0,2)+1
grub > boot

---

### Post by AndyOpie150 on 2012-09-04
Typed: chainloader (hd0,2)+1
Unknown command 'chainloader'
I don't see: grub> 
I see: grub rescue>

Note: Typed grub > chainloader (hd0,2)+1 as well, got: Unkown command 'grub'

---

### Post by oldfred on 2012-09-04
The chainloader is a valid command in grub, but the rescue mode must not support it?? 

The grub> is another error separate from rescue, you would not type the grub>.

If you cannot manually boot and have no CD or USB support the only choice is to remove drive and connect drive to another computer with CD or USB support or an install of Ubuntu to allow you to work on the drive.

---

### Post by AndyOpie150 on 2012-09-04
As mentioned in first post, I do have a bootable USB drive with Zubuntu installed.

 My cd drive works, just don't have a restore set of cd's
will have to buy cd and get someone to put the first item you linked to on it.
Manual method most not be an option in grub rescue.

EDIT: Found someone who can make cd. Will post in a few days when I have everything straightened out.

---

### Post by AndyOpie150 on 2012-09-06
Found someone that allowed me to download and burn the boot repair iso img from the first link in oldfred's first post. Worked great. This is the only way to get out of grub rescue. 
 
Apparently when I wiped the two partitions containing Lubuntu and Kubuntu I had wiped not only the boot.img but the grub as well.
 
Thanks oldfred, this thread can now be prefixed as "Solved"

---

### Post by oldfred on 2012-09-06
Glad you found a way to solve it.

You can change to solved.

---

### Post by AndyOpie150 on 2012-09-08
> **oldfred said:**
> Glad you found a way to solve it.

You can change to solved. Thanks for the help, sorry I have a tendency to try to solve things the hard way right at first.

---

