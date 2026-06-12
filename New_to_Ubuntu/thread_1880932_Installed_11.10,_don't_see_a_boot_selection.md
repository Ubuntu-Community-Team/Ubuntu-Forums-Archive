---
title: "Installed 11.10, don't see a boot selection"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by Gord12 on 2011-11-14
I just installed 11.10 to a new sata drive in a working windows 7 system, and when I rebooted the system booted directly to win7. I expected to see a boot selection screen?

 I'm not sure about the selections I made when partioning....

First Linux experience

---

### Post by grahammechanical on 2011-11-14
Ubuntu installs a boot loader called Grub into the Master Boot Record of the hard disk.

If Ubuntu is sharing the hard disk with Windows then the boot loader is in the MBR of the hard disk that has both Windows and Ubuntu then you get a menu.

If Ubuntu is the only operating system on the disk then we do not get a menu.

Can you change the boot options in the BIOS so that the machine boots from the Ubuntu hard disk before it tries to boot from the Windows hard disk? You might then see a menu that lets you choose to boot either Ubuntu or Windows. Provided that the Windows hard disk was in the machine at the time that Ubuntu was installed.

Regards.

---

### Post by Gord12 on 2011-11-14
I did go back and shut down and changed the boot sequence after I posted my question, and linux did boot properly.

Is there not a way to create a boot menu short of changing the bios each time?

---

### Post by Cyclane on 2011-11-14
Boot to ubuntu, open a terminal and issue the following command:
```
sudo update-grub
```
This should be enough. Next time you boot to the same HD you will again boot to grub but this time it will contain a option 'Windows 7 loader'

---

### Post by Mark Phelps on 2011-11-15
IF you have the two OSs on two different disks, in my experience, the better long-run solution is to have each disk be bootable on its own.  That makes boot repairs and updates a lot easier.

I'm guessing that you installed GRUB to your Windows drive, so the first thing to do would be to remove that.  Download the CD image from the link below, burn that to CD:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

Then, disconnect the Ubuntu drive, leave the Windows drive connected, boot from the CD -- and use that to repair the Windows boot.  Reboot from the Windows drive to confirm that works now.

Then, disconnect the Windows drive, connect the Ubuntu drive, and see if it boots -- might not. IF not, boot from the Ubuntu desktop CD and use it to restore GRUB to the Ubuntu drive.  Instructions are in the link below:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

Then, when Ubuntu boots OK, shut down, reconnect the Windows drive -- but continue to boot from the Ubuntu drive.  Boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the GRUB menu.

When you next reboot, you should get a GRUB menu with choices for both OSs.

---

