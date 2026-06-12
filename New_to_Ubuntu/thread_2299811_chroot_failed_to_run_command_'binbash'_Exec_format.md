---
title: "chroot: failed to run command '/bin/bash': Exec format error"
date: 2015-10-21
forum: New to Ubuntu
---

### Post by micahpage on 2015-10-21
I started up my computer today to notice that its not going to grub. Its dual boot with windows and ubuntu. It fails to find OS, isntead of goijng to grub. It just stats
> [COLOR=#373E4D][FONT=helvetica]loading operating system....boot error[/FONT][/COLOR]
I am not sure why because it worked last night, but i didnt do anything change wise. 

So i got a live cd to reinstall grub
the error i get when i try to chroot into my os from the live cd is
[COLOR=#373E4D][FONT=helvetica]chroot: failed to run command '/bin/bash': Exec format error

[/FONT][/COLOR]the commands to chroot i am using are
```

[COLOR=#183691][FONT=Consolas]sudo mount /dev/sda[/FONT][/COLOR][FONT=Consolas][COLOR=#0086b3]5[/COLOR][/FONT][COLOR=#183691][FONT=Consolas] /mnt
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -t proc none /mnt/proc
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -o bind /dev /mnt/dev
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -o bind /sys /mnt/sys
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo chroot /mnt[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]
[/FONT][/COLOR]
```
sda5 is my linux partition

This has always worked for me before. I am not sure why it cannot find bash?

EDIT:
i searched online and found someone else said that it was a result of 32/62 bit conflict. The live cd is a 64 bit, so then i tried a 32 bit live cd, and got the same thing. So its not that.

EDIT2
I am actually selling this computer. The person that wants it only wants windows, but does not care if linux is installed. So another question is there a way to remove the partition of linux and have windows boot as normal without grub? What would be hte process. I would not want to remove linux and then not be able to have a linux os on to fix grub, etc. and not be able to boot even windows. However i cant get into windows to fix windows boot loader, because grub is messed up.

---

### Post by sandyd on 2015-10-21
> **micahpage said:**
> I started up my computer today to notice that its not going to grub. Its dual boot with windows and ubuntu. It fails to find OS, isntead of goijng to grub. It just stats

I am not sure why because it worked last night, but i didnt do anything change wise. 

So i got a live cd to reinstall grub
the error i get when i try to chroot into my os from the live cd is
[COLOR=#373E4D][FONT=helvetica]chroot: failed to run command '/bin/bash': Exec format error

[/FONT][/COLOR]the commands to chroot i am using are
```

[COLOR=#183691][FONT=Consolas]sudo mount /dev/sda[/FONT][/COLOR][FONT=Consolas][COLOR=#0086b3]5[/COLOR][/FONT][COLOR=#183691][FONT=Consolas] /mnt
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -t proc none /mnt/proc
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -o bind /dev /mnt/dev
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo mount -o bind /sys /mnt/sys
[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]sudo chroot /mnt[/FONT][/COLOR][COLOR=#183691][FONT=Consolas]
[/FONT][/COLOR]
```
sda5 is my linux partition

This has always worked for me before. I am not sure why it cannot find bash?

EDIT:
i searched online and found someone else said that it was a result of 32/62 bit conflict. The live cd is a 64 bit, so then i tried a 32 bit live cd, and got the same thing. So its not that.

EDIT2
I am actually selling this computer. The person that wants it only wants windows, but does not care if linux is installed. So another question is there a way to remove the partition of linux and have windows boot as normal without grub? What would be hte process. I would not want to remove linux and then not be able to have a linux os on to fix grub, etc. and not be able to boot even windows. However i cant get into windows to fix windows boot loader, because grub is messed up.

If you want to just have Windows, then it is easy.
Boot up using a Windows Installation disk, choose repair computer, troubleshoot, then to the command prompt.
Run
```

bootrec /fixmbr
```

Reboot and go back into Windows, and then go to control panel -> administrative tools -> computer management -> disk management.
Delete the Linux partitions, extend the Windows partition, and you should be good to go.

Does not work with EFI

---

### Post by micahpage on 2015-10-21
I figured the problem. On a whim i took out the SATA and power from the HDD, blew the dust, and reinserted and it worked.

---

