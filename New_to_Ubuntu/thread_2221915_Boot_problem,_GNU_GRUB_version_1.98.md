---
title: "Boot problem, GNU GRUB version 1.98"
date: 2014-05-04
forum: New to Ubuntu
---

### Post by mike185 on 2014-05-04
[COLOR=#000000]Hello,[/COLOR]

[COLOR=#000000]I'm new enough to linux. I istalled ubuntu 12.04 LTS on my external hard disk, so i can use Ubuntu when the hd is connected to the notebook, instead if the hd isn't connected[/COLOR] i use Win 8.1.

[COLOR=#000000]Anyhow, when I turn my computer on,[/COLOR][COLOR=#000000]I get this message:[/COLOR]

[COLOR=#000000]Code:
 GNU GRUB version 1.98

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub>[/COLOR]
[COLOR=#000000]So i have to write "exit" ( 2 times) and now the boot goes on, and i can choose the operating system.[/COLOR][COLOR=#000000]

[/COLOR][COLOR=#000000]Can i disable the Gnu Grub screen?

[/COLOR][COLOR=#000000]Thank you[/COLOR][COLOR=#000000]



[/COLOR]

---

### Post by oldfred on 2014-05-04
That looks like an old copy of grub somewhere that BIOS/UEFI is booting first, then you move on to a correct one?
What is boot order in BIOS.

You can post link to BootInfo report so we can see details of what is where, but will not show BIOS settings:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mike185 on 2014-05-05
I've never installed an other Ubuntu version on my computer, but i installed one on the same exsternal hard disk before.
The boot order in BIOS is     [ubuntu (PO ST1000L...]
                                          [Windows Boot Manage...]
                                          [ubuntu (PO ST1000L...]

 mentre il Boot Overrise        [Windows Boot Manage...]
                                          [ubuntu (PO ST1000L...]   
                                           [ubuntu (PO ST1000L...]   
I done the BootRepair and this is the link to BootInfo [http://paste.ubuntu.com/7397159/](http://paste.ubuntu.com/7397159/)

BootRepair told me to disable SecureBoot in the BIOS, so i disabled it and then i run BootRepair.

This is the later BootInfo  [http://paste.ubuntu.com/7397269/](http://paste.ubuntu.com/7397269/)

---

### Post by oldfred on 2014-05-05
This says you ran the 'buggy' fix from Boot-Repair.
>  /EFI/Microsoft/Boot/bkpbootmgfw.efi 



I would undo that if you can boot the ubuntu entry in UEFI menu.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

Does it boot ok with secure boot off?
Only secure boot systems boot with secure boot on.
The rename is only required for those systems that modify UEFI to only boot Windows.
And with rename you can only boot Windows from grub menu, but some have had issues booting Windows from grub menu when secure boot is on.

I prefer to have an efi partition on every hard drive with an install. Or you should consider an efi partition on your external drive. Then drive would work with another UEFI system. Or you can with a bit of effort make it to boot in both UEFI or BIOS mode. This was flash drive, but could be done to any external drive.
      
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by sandyd on 2014-05-05
Moved to absolute beginners

---

