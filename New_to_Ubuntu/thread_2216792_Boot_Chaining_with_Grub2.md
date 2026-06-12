---
title: "Boot Chaining with Grub2"
date: 2014-04-13
forum: New to Ubuntu
---

### Post by KAWill70 on 2014-04-13
I recently installed a Linux distribution and had the boot loader written to the boot sector of the disk drive itself.  Later I installed another Linux distribution to a different partition and had the boot loader written to that specific partition.

As expected, the second distribution did not show up in the Grub2 boot menu on the next boot.  I booted into the recovery option for the primary distribution and did an update-grub.  Boot was then resumed and I later shut down and rebooted.  Now the second installation appeared in the boot menu.

Is this pretty much the standard procedure when associating boot loaders with their respective distribution?  I assume I could have done a normal update-grub with the same results if I had fully booted into the first distribution first.

What actually happened to make all this work?  I believe update-grub does some OS Probing and updates grub.cfg.  Is that really all that happens?  Does the contents of the primary grub.cfg then determine what is on the boot menu for each subsequent boot?

Any other tips appreciated.

---

### Post by oldfred on 2014-04-13
You can do that.

Grub2's os-prober looks for grub.cfg or other distributions files to copy a boot stanza. But with multiple installs you have to run the update in the second install which may occur automatically on a new kernel. But then have to boot into the install with its grub in the MBR that controls booting and run sudo update-grub so it can find the new entry in the second install. 
Once you get several installs it can be a lot of work and difficult to keep track of. 
I use bootinfoscript and/or BootInfo report from Boot-Repair to keep track of installs.
I also turn off os-prober and manually update 40_custom with boot entries. Some I copy from grub.cfg or create my own.

       Using 40_custom & Custom menu
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus) 

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
[https://help.ubuntu.com/community/Grub2/Displays](https://help.ubuntu.com/community/Grub2/Displays)

Debian based installs put a link to the most current kernel in / (root) and you can just create one boot stanza to the link that does not need updating. 

      
 I first saw this from Ranch hand, he helped Cavsfan who created more details in link above.
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition. example based on sda13 change all 13's to your partition number.
At least for Ubuntu family OS's, they all place symlinks in /, called vmlinuz and initrd.img These point to the most recent versions of the kernel in the /boot folder.
More info:
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

   gksudo gedit /etc/grub.d/40_custom
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}
menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

---

### Post by NikTh on 2014-04-14
You understand it correctly. The script 30_os-prober scans for other operating systems and add them to grub configuration file grub.cfg. You can find (and read) the script inside /etc/grub.d/ directory. This script has executable permissions and the update-grub command reads it when execute. 

What I've done in my multi-boot system (5 distributions) is: 

I have a primary grub installed in /dev/sda MBR. I've removed the execution bit from 30_os-prober. I've installed grub of each other distribution on its own partition. (e.g. Arch Linux is installed on /dev/sda3 and Arch Linux grub is installed in /dev/sda3). I've edited the primary grub 40_custom and added chainloading to each other distribution grub. 

So, when I boot I have a menu with Ubuntu first and then my entries. When I click on Arch Linux for instance, grub will "jump" to the other grub (Arch Linux grub) ...etc. 

It's a good practice when you have a multi-boot system, there is no need to reboot into the primary distribution , when a kernel update comes. Well, Arch Linux here is not a good example because it has not multiple kernel versions, but other distributions have. 

Chainloading is quite easy like this

```

menuentry 'Arch Linux (rolling)' --class gnu-linux --class gnu --class os {
        insmod part_msdos 
        insmod ext2
        set root='hd0,msdos3'
    chainloader +1
}

```
The most important entry is: set root='hd0,msdos3' , where it should point to the correct partition. Translating to : /dev/sda3 (where Arch Linux grub is installed).

---

### Post by KAWill70 on 2014-04-14
Thanks very much oldfred and NikTh.  Your replies are really appreciated and a great help.  This entire forum is a terrific resource while makes getting help very easy.

You both have given me much to study and understand.  I now see the problem with multiple kernel updates over time.  If I understand boot chaining, the chain is really only a maximum of two for any given boot which would add to the boot delay.

I have opened and viewed grub.cfg in etc/grub.d and will now see what is needed to define 40_custom for my case.

---

