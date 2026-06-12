---
title: "Updating grub - twice?"
date: 2013-06-09
forum: New to Ubuntu
---

### Post by OllieGab on 2013-06-09
I've got the boot loader loaded with grub from Ubuntu and any changes I do on my other three Linux ditros I always update grub from within Ubuntu.
Question is: if i do a change to the grub file in another distro; do I need to update grub in THAT distro AND grub in Ubuntu?
Or is it enough to only change the 'local' grub? Ie, does the Ubuntu grub notices any changes without being updated itself?

Hope that was clear!?

Ciao!

---

### Post by Isamu715 on 2013-06-09
It's only necessary to update the GRUB and change GRUB settings in the distro that manages the GRUB. If you have GRUB from Ubuntu you only need to change settings and update grub from Ubuntu.

---

### Post by OllieGab on 2013-06-09
OK, but the problem I have is that, due to various problems with screen resolution on one distro (that isn't Ubuntu), it's been recommended that I add 'i915.modeset=0' to the grub file. If I add it in the grub file of the 'problematic' distro nothing happens at all but if I add it to the grub file controlled by Ubuntu it seems to cause problem of ALL the other distros (they didn't boot up without lots of 'recovery work').
I sort of imagined that the Ubuntu grub file starts up the desired distro, which in turn starts up according it its OWN grub details. I assume that is wrong, then?

---

### Post by oldfred on 2013-06-09
Your current grub looks for and finds the grub.cfg in other systems and copies the entries into your current grub menu. If you need custom settings you need to modify grub in that version and then update both systems.

I prefer to manage my own grub entries using a 40_custom and add my own parameters if need be.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Ubuntu adds links in root to current kernel. So you can make a standard boot stanza that always boot the current kernel and you then can add any added settings you need to the linux line.

      
 I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

---

