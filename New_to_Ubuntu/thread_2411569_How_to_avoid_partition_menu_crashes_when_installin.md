---
title: "How to avoid partition menu crashes when installing via USB?"
date: 2019-01-31
forum: New to Ubuntu
---

### Post by nreid2946 on 2019-01-31
I'm installing on my laptop, a lenovo 720s, and it doesn't have a disk drive.

Sad times.

But this means that I have to install Ubuntu via USB, but I'm unable to get past the partition creation screen right before installation begins. This is due to the fact that the program times out / crashes when pressing any of the "change" or add / minus buttons.

The window is also not showing any partitions at all, when they have for the most part already been created in Windows.

This laptop is going to be dual-booted.

Any solutions?

I apologize is this is a common issue.

Regards,

Nick.

---

### Post by Autodave on 2019-01-31
Have you disabled *fast boot* in the BIOS?  That needs to be done first.  After disabling it, proceed to let Win boot and then shut it down.  Now try your install.

---

### Post by yancek on 2019-01-31
You neglected to mention which version of windows you are using.  If it happens to be windows 10, I would suggest you read the official Ubuntu documentation at the link below on dual booting it with Ubuntu.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by ghostbacon on 2019-02-01
I'm not too sure of what you mean but if i were you i would load up a live Linux distro and start gparted. then format the hard drives from there. You could also use "YUMI" to put the installation tool straight onto the USB

---

### Post by ajgreeny on 2019-02-01
Don't create partitions which are to be used by Linux (of any distro) in Windows as it is possible that those partitions will be Windows dynamic partitions; these are not usable by Ubuntu or any other Linux as far as I'm aware.

Using gparted in the live system from the USB I suggest you delete the partitions you created for Ubuntu, leaving unallocated space.  That space should then be seen by the installer running from USB and allow you to install Ubuntu.

If gparted can not see those partitions it may be that you are running the USB live system using MBR instead of UEFI, or vice-versa, so see the link above from yancek regarding Ubuntu and UEFI, [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

