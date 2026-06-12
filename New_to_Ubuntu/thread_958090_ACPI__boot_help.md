---
title: "ACPI / boot help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by Phoenix CMXIV on 2008-10-25
When i tried out the Live CD, i had altered my BIOS to boot to Cd, then HD. i encountered an error (Busy Box 1.1.3 on boot), and that error was fixed by enableling ACPI in my BIOS. I installed Kubuntu fine, but now, it doesnt boot to a CD, so i have to boot from HD. when i boot from HD i get an error (when "Verrifying DMI pool data") i get 

```
NTLDR is missing
Press CTRL + ALT + DEL to restart
```

If i disable the ACPI, i can get to grub and choose my OS, but kubuntu wont boot, because ACPI isnt enabled.

Two Problems, only one needs to be fixed either:

- Let Grub boot with ACPI on
- Get Kubuntu to boot without ACPI on.

---

### Post by caljohnsmith on 2008-10-25
Just to clarify, you're saying that when you enable ACPI, and when you boot your HDD, you get that ntldr error; but when you disable ACPI, you get the Grub menu on start up but can't boot Kubuntu? 

If that is the case, it sounds like when you have ACPI enabled, your BIOS skips over Grub in the MBR (Master Boot Record), and instead BIOS simply tries to boot the active partition on your HDD (which would most likely be Windows, and that would explain the ntldr error). From your Live CD, open a terminal (applications > accessories > terminal) and please post the output of:
```
sudo fdisk -lu
```
Next, figure which is your Kubuntu partition in the form sdXY (like sda2 or similar) by noticing which partition is "linux" under the "system" category, and then do:
```
sudo fdisk /dev/sda
```
Type "a" to change the bootable flag, type the partition number for the Kubuntu partition ("2" for sda2 for example), then type "w" to write the change to the HDD. Next do:
```
sudo grub
grub> find /boot/grub/stage1
```
The above command should return your main Kubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd0,1), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX,Y)
grub> quit
```
Post the results of that, reboot, and let me know exactly what happens when you have ACPI enabled and disabled. :)

---

### Post by Phoenix CMXIV on 2008-10-26
When I Type the first Command I get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22df22de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   292977404   146488671    7  HPFS/NTFS
/dev/sda2       292977405   976768064   341895330    5  Extended
/dev/sda5       292977468   308608649     7815591   82  Linux swap / Solaris
/dev/sda6       308608713   976768064   334079676   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1aac5444

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156264254    78132096    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e205c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001    7  HPFS/NTFS

```

i continued with the commands and will edit my post in A few Minutes when i reboot.

---

### Post by Phoenix CMXIV on 2008-10-26
Now when i boot i get the NTLDR error if i boot with AND withought ACPI on.

i redid the " sudo fdisk -lu " command and got:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22df22de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   292977404   146488671    7  HPFS/NTFS
/dev/sda2       292977405   976768064   341895330    5  Extended
/dev/sda5       292977468   308608649     7815591   82  Linux swap / Solaris
/dev/sda6   *   308608713   976768064   334079676   83  Linux

*continued listing my other, irrelevant drives.*

```

I can tell you that it still tries to boot from /dev/sda1 (my win partition)

How do i remove the boot tag from it??

I also redid the codes and with replies:

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> find /boot/grub/stage2
find /boot/grub/stage2
 (hd0,5)
```

---

### Post by Phoenix CMXIV on 2008-10-26
I rebooted with the live CD, and when i do the " sudo fdisk -lu " command i get:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x22df22de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   292977404   146488671    7  HPFS/NTFS
/dev/sda2       292977405   976768064   341895330    5  Extended
/dev/sda5       292977468   308608649     7815591   82  Linux swap / Solaris
/dev/sda6   *   308608713   976768064   334079676   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1aac5444

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   156264254    78132096    7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2e205c4d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   488392064   244196001    7  HPFS/NTFS

```

The boot on sda1 (windows) is no longer there. but look at the second HD, there is a boot on the one and only partition. Could this be affecting anything?

i will remove the boot flag on it and see what happens.

will edit in a few minutes

_______________

I am glad to say that i am typing on Konqueror and looking at my only live CD in my hand. Thank you caljohnsmith. I wouldn't have done it without you. The world need more people like you. Peace out!!!

THANKS!!!

---

### Post by caljohnsmith on 2008-10-26
OK, well after seeing your fdisk output, I think I have a better idea of what your original problem was since you have multiple drives present (you didn't happen to mention that in your first post :)). That means you probably have a Windows MBR in your sda drive instead of Grub, and now that the Linux partition is marked as the "bootable" or active partition instead of the Windows partition, that's why it works. Just one last word of caution: make sure your Windows entry in your Grub's menu.lst does not have a "makeactive" line, because if it does, you will either boot directly into Windows from then on, or most likely you may not be able to boot at all if two partitions are both marked as active. So one last check would be:
```
gksudo gedit /boot/grub/menu.lst
```
And your Windows entry should be:
```
title Windows
root (hd0,0)
chainloader +1
```
So make sure it doesn't have a "makeactive" line. Then you should be all set. Anyway, cheers and have fun. :)

---

