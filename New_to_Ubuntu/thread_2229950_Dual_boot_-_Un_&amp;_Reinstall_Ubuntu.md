---
title: "Dual boot - Un &amp; Reinstall Ubuntu"
date: 2014-06-16
forum: New to Ubuntu
---

### Post by gordon99 on 2014-06-16
I installed Ubuntu 14.04, which dual boots with Windows 7, about 4 weeks ago. In trying to load programs onto Ubuntu I have effectively made Ubuntu unusable. I therefore wish to uninstall and reinstall Ubuntu, without damaging Windows 7 obviously.
I would be very pleased if someone could set out for me, step by step, what I need to do to achieve the objective. I have the USB drive which I used to install Ubuntu. I had to create an extended partition for Ubuntu in which I set up a root partition, a swap partition, a home partition and an NTFS data partition. I wish to do the same for the reinstall. Thank you.

---

### Post by grahammechanical on 2014-06-16
Basically, you choose the Something Else option and then tell the installer what partition you want Ubuntu installed into and what partitions you want to be the /home and swap partitions.

[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

Look at the fourth image in this link. The image labelled Installation type.

[http://ubuntuhandbook.org/index.php/how-to-install-ubuntu/](http://ubuntuhandbook.org/index.php/how-to-install-ubuntu/)

1) select the partition that you want to be /root (where Ubuntu will be installed and where, in your case, Ubuntu should already be installed) and click Change 
2) in the dialog box in the Use As panel select Ext4
3) tick the box Format the partition. Or not as you choose
4) select the mount point to be /
5) click OK

Now repeat for the partition that is /home only this time do NOT tick to format the partition but make sure the mount point is /home. The installer should make use of the existing swap partition.

Now double check that the bootloader is going to be installed where you want it to be. Most essential when we have more than one hard disk because the installer defaults to sda which may not be what we want. You should be at the Installation Type page and you can click Install Now. And keep your fingers crossed. :)

Oh, just in case it enters your head, you must keep the same user name for your existing /home folder to be own by you. Otherwise you will be another user with a different /home folder.

Regards.

---

### Post by gordon99 on 2014-06-16
Thanks gm. Just so that I am clear (a) I do not need to format the Ubuntu partitions in, say, Windows before I begin the re-install? (b) If I do not format partitions during the re-installation is there a risk that the files/directories I have wrecked since the original install will still be there to damage the new installation?

---

### Post by stalkingwolf on 2014-06-16
try using the recovery option in the boot menu with the fix broken packages choice first. might save a reinstall

---

### Post by gordon99 on 2014-06-16
Hello sw, I have tried the recovery options but with no success. 
Regards.

---

### Post by yancek on 2014-06-16
> Thanks gm. Just so that I am clear (a) I do not need to format the  Ubuntu partitions in, say, Windows before I begin the re-install?

A standard windows system can't even read a Linux filesystem so I don't see how you could format it from windows.  If you use the 'Something Else' manual option in Ubuntu, you will have the opportunity to create and/or format partitions you want to use which I would suggest you do during the install, especially since you will be installing over a previous installation.

---

### Post by gordon99 on 2014-06-16
Thanks y. I suppose I may have been misled when looking at partitions in Windows where all partitions on the hard disk appear. It maybe you can delete Ubuntu partitions (delete volume) but I have no intention of doing that of course.

---

### Post by gordon99 on 2014-06-16
Have now re-installed ubuntu.Thanks to all for your help and suggestions. Had one or two concerns but it seems to have gone OK. This partition business is a trap for the unwary however.

---

