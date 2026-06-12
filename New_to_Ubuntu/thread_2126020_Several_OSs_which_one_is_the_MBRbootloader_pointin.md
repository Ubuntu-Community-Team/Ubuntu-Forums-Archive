---
title: "Several OSs: which one is the MBR/bootloader pointing to?"
date: 2013-03-15
forum: New to Ubuntu
---

### Post by OllieGab on 2013-03-15
I've got 5 OSs installed (including Windows). Question is; is it possible (with some commands perhaps) to see which OS has its bootloader installed in the MBR?
Or I suppose (?) it's more like: which OS is the MBR pointing to?

---

### Post by Bashing-om on 2013-03-15
OllieGab; Hi !
Several ways from the command line to look at grub/MBR and installed OSs:
```
sudo debconf-show grub-pc
sudo grub-probe -t device /boot/grub
sudo grub-probe -t fs_uuid /boot/grub
sudo grep menuentry /boot/grub/grub.cfg
```

These should get you a good idea of what you are looking at.[INDENT=2]
hth

[/INDENT]

---

### Post by oldfred on 2013-03-15
I use this, but I also run bootinfoscript which Boot_repair runs. I include bootinfoscript as part of my rsync backup so I know partitions,versions, boot loaders and lots of useful info not documented anywhere else.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)

      
 Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

