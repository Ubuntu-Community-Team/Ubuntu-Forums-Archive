---
title: "Ubuntu wont boot after Installation"
date: 2018-04-24
forum: New to Ubuntu
---

### Post by jimhaines on 2018-04-24
After installation of v. 16.04 from usb, it won't boot from hard drive. I turned off secure boot and successfully set up root, home, and swap partitions for install. No error messages during install. Using pre-installed Win 10 on new hp envy x360 with AMD fx 9800 chip. Anyone having a simular problem or knows an answer for my problem?  Also what is the difference between OEM install and normal installation?

---

### Post by yancek on 2018-04-24
Windows 10 pre-installed, almost certainly using UEFI.  Did you install Ubuntu UEFI?  The Ubuntu documentation at the site below tells you how you can be sure you are booting Ubuntu UEFI and installing it UEFI.  That is one of the most common reasons for the result you have, do a Legacy install of Ubuntu with an EFI install of windows.  You might still be able to boot Ubuntu but it will involve making changes in the BIOS and then you would have to change back to boot windows.  If you can boot the Ubuntu install media, do that and from a terminal run this command and post the output here.  THis will tell if you have an EFI partition.  You should be able to mount that partition and see if you have an Ubuntu folder there, if not re-insall UEFI per instructions at the link below. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Brief explanation of OEM at the link below.

---

### Post by jimhaines on 2018-04-24
Thanks for the reply.  I will try that.

---

### Post by jimhaines on 2018-04-25
Thank you, Yancek.  The UEFI issue was definitely one of my problems.  I'm still having problems though.   Here is a question:
The Ubuntu installation program allows me to select the EFI partition but not set the mount point.  I'm assuming UEFI doesn't need the mount point specified.  I then select install.  At this point, I am told that the root is not set and to go back to the partition menu.  I'm confused because it won't let me set the root. I think my brain hurts.   What am i doing wrong? Thanks in advance.

---

### Post by yancek on 2018-04-25
You need to select free space or a specific partition to format for Ubuntu and you need to select the mount point.  You need to use the manual install method, referred to as Something Else in Ubuntu.  Go to the link below which is a tutorial on installing Ubuntu.  If you scroll about half way down the page, it explains how to edit the partition to select it for install and set the mount point as /.  Ignore the part about creating a separate boot partition, you don't need that and it needlessly complicates things.  Did you review the UEFI documentation at the link I posted earlier, particular attention to General Principles.

 [https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html](https://www.itzgeek.com/how-tos/linux/ubuntu-how-tos/install-ubuntu-16-04-with-screenshots.html)

---

### Post by jimhaines on 2018-04-27
I was successful in getting Ubuntu to boot from the hard drive. However I got the following messages.

Ubuntu login: [1040.663994] SQUASHFS error: unable to read fragment cache entry [e6763ee]


[1040. 664069] SQUASHFS error: unable to read page, block [e6763e], size df54


[1040.663608] SQUASHFS error: unable to read fragment cache entry [e6763ee]

Question what does squash do? Where would I look to repair this?

---

### Post by oldfred on 2018-04-27
See this:
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

This user added another boot parameter. acpi=off
[https://askubuntu.com/questions/528036/ubuntu-installation-over-usb-and-dvd-fails?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa](https://askubuntu.com/questions/528036/ubuntu-installation-over-usb-and-dvd-fails?utm_medium=organic&utm_source=google_rich_qa&utm_campaign=google_rich_qa)

---

### Post by jimhaines on 2018-04-28
Thanks OldFred.  Best info yet.

---

### Post by jimhaines on 2018-05-06
Problem solved. I chose to make a persistent usb drive with mkusb. Works great with ubuntu 18.04

---

### Post by sdeflabofficial on 2018-05-09
Hi,
We have installed Ubuntu 16.04LTS sucessfully,able to boot it  from the hard disk.While trying to setup root login ,
via the below command 
sudo sh -c ' echo "greater-show-manual-login=true">>/etc/lightdm/lightdm.conf

After that our DELL Precision T7610 Workstation started restarting, it says :" Your system is running in  low-graphics mode, Your screen, graphics card, and input device settings  could not be detected correctly.".


Can anybody help us to solve this issue.....

Thanks in Advance

---

### Post by oldfred on 2018-05-09
If not newest nVidia, you have to check which driver is correct.
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

If you install incorrect one you have to totally purge before installing correct one.
Only install from Ubuntu repository, not directly from nVidia.

       # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended  


 #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display 

While recommended one should be correct, always best to check nVidia site on which driver is recommended. At various times, older cards get a older driver frozen version (legacy driver) with only security updates. Newest drivers then have features an older card may not support.

---

