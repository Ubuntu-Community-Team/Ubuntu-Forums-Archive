---
title: "Grub to grub2"
date: 2011-11-18
forum: New to Ubuntu
---

### Post by mijdrawoh on 2011-11-18
(11.10)  I am attempting to move from grub legacy to grub2.  I found the grub2 documentation (help.ubuntu.com/community/Grub2) which shows how to make the change but I'm unable to get the screen shown with the links used to make the change.  Grub-pc is installed as required. I want to use this method as opposed to grub-update because I have entries in menu.lst that I don't want to lose.  Thanks in advance for your help.

---

### Post by oldfred on 2011-11-18
You can manually convert your custom menu entries to grub2 style without too much difficulty. You add the new entries to 40_custom. Note that partition numbering has also changed where hd0,0 in grub legacy is now hd0,1.

General menuentry Construction Rules:

    * The first line must start with menuentry and end with {
    * The area between the quotation symbols is what will appear on the GRUB 2 menu. Edit as desired.
    * The last line of the menuentry must be }
    * Do not leave empty spaces at the end of lines
    * The set root= line should point to the GRUB 2 /boot location ( sdXY )
    * The root reference in in the linux line should point to the system partition.
          o If GRUB 2 cannot find the referenced kernel, try replacing the UUID with the device name (example: /dev/sda6 ).

gksudo gedit /etc/grub.d/40_custom
#then update grub2's menu with the new entries
sudo update-grub


This is a typical entry to boot another partition with a Ubuntu install.

I first saw this from Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

```
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

```

---

### Post by mijdrawoh on 2011-11-19
As a real newbie, I am hesitant to add a Grub2 bootloader and then modify it.  Reading the description of grub-pc actions, that seems like a safer course to follow.  But, I'm stuck.  Grub-pc is installed on my system and I can't figure out how to run it.  I assume a CLI has to used, however I keep getting not a valid command.  What command is required?  Thanks.

---

### Post by oldfred on 2011-11-19
When you say is it installed, do you just mean you have downloaded the package?

Can you boot with old grub and just have to install grub2 to MBR? Or will you have to chroot into your system from a liveCD.

This has several ways:
chroot & grub uninstall & reinstall -drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

This also installs grub2 which is grub-pc.
Reinstall:
sudo dpkg-reconfigure grub-pc

You can uninstall grub and install grub2.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

and just incase:
Uninstall grub2
[https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Uninstalling%20GRUB%202)

---

### Post by lolpenguin on 2011-11-20
HOLD IT!!!!!!!!!!!!!!
If you are running Ubuntu inside a Windows partition (ie using Wubi, you selected Run Alongside Windows from the Ubuntu website) then DO NOT UPGRADE TO GRUB2 OR YOU WILL BREAK YOU INSTALLATION.

If you installed Ubuntu to a separate partition using a LiveCD, LiveUSB, DVD, or Alternate Installer (ie you wiped a partition) then go ahead.

Happy upgrade!

---

