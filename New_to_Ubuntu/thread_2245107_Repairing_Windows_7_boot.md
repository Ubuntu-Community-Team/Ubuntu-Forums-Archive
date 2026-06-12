---
title: "Repairing Windows 7 boot"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by Sebastijan_Duman on 2014-09-21
Hello! 

I accidentaly delete wrong boot option with EasyBCD using Windows 7. I have tried to automatically repair with boot-repair-disk, but no luck. Here is my pastebin: 

[http://paste.ubuntu.com/8394852/](http://paste.ubuntu.com/8394852/)

Thanks for any help!

---

### Post by grahammechanical on 2014-09-21
What is the problem? Does the machine not load Windows? This is what Boot Repair did:

> [COLOR=#666666]===================[/COLOR] Recommended repair
Recommended-Repair
This setting will restore the [COLOR=#666666][([/COLOR]generic mbr[COLOR=#666666])][/COLOR] MBR in sda, and make it boot on sda1.
Additional repair will be performed: unhide-bootmenu-10s   fix-windows-boot

Quantity of real Windows: 1
Will restore the MBR_TO_RESTORE : sda [COLOR=#666666]([/COLOR]generic mbr[COLOR=#666666])[/COLOR] into sda
dd [COLOR=#AA22FF]**if**[/COLOR][COLOR=#666666]=[/COLOR]/usr/lib/syslinux/mbr.bin [COLOR=#B8860B]of[/COLOR][COLOR=#666666]=[/COLOR]/dev/sda
0+1 records in
0+1 records out
parted /dev/sda [COLOR=#AA22FF]set [/COLOR]1 boot on
                                                                          
Information: You may need to update /etc/fstab.

Boot successfully repaired.

What were you expecting to happen? 

> 
[COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain1 disks with OS, 1 OS : 0 Linux, 0 MacOS, 1 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.Windows not detected by os-prober on sda2.

If this is a Windows support question, then it should be in the Other Operating Systems and Projects section of this forum. 

Regards

---

### Post by westie457 on 2014-09-21
Windows is trying to boot from the wrong partition (sda2) it should be sda1.
Using the Live media start Gparted and make SDA1 the boot partition and remove the 'Boot' flag from SDA2. Click on the green tick to apply, agree to any other prompts. Shut down the system and remove the Live media. Boot and now you should be in Windows.

Let us know how it goes.

---

