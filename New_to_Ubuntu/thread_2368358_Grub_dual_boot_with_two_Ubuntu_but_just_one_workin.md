---
title: "Grub dual boot with two Ubuntu but just one working"
date: 2017-08-09
forum: New to Ubuntu
---

### Post by michel.mds1983 on 2017-08-09
HEllo all!

     I am very new with ubuntu and after installing Ubuntu Studio I decided to change to the normal Ubuntu without modifications.
     But when I got the grub Dual boot screem where usually there is an option for windows and Ubuntu, there are two options for Ubuntu, just one is working of course, because it belongs to the old one.

     Is there any way to delete this option and let just one ubuntu on it?

thanks!
Michel

---

### Post by oldfred on 2017-08-09
Is this an UEFI system?

If you do this in your current install, does that then show both Ubuntu's?
sudo update-grub

UEFI only has one entry for all Ubuntu installs. You can do a reinstall of grub from any install to get it to be the default grub/Ubuntu. And then boot other installs from that one grub menu which should be the one you use the most.

Often easier to modify grub to boot partition, so you do not have to boot every install and run sudo update-grub in every one of them.

       How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by shridhar-kapshikar on 2017-08-10
You may try to update-grub using a boot-repair simple tool. 
Please refer below URL :
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by michel.mds1983 on 2017-08-10
Thank you guy, I will try it and com back to tell you what happened
I am using UEFI

---

