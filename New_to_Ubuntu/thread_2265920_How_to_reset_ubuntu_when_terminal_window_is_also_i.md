---
title: "How to reset ubuntu when terminal window is also inaccessable"
date: 2015-02-18
forum: New to Ubuntu
---

### Post by vishal_ on 2015-02-18
I have recently dual booted my laptop which was pre installed with Windows 8.1 to Ubuntu.
Everything was working fine but i had allotted only 8gb to ubuntu root folder. After installing few softwares in ubuntu there was memory overflow and since then ubuntu doesnt work properly. I will be able to login into ubuntu and see the desktop icon shortcuts but not even able to open a terminal window. or any application. I am not able to remove any software to clear the roots memory . The windows OS is working fine. Please help me as i want to use Ubuntu only, and i will be clearing some memory and alloting more space with GParted in ubuntu. but i have to remove or RESET Ubuntu back to its basic files and i dont have any risk of data loss. I would be happy to delete all files if needed. Please help me to RESET ubuntu to its basic file set after which i can increase the memory alloted for it.

---

### Post by Impavidus on 2015-02-18
If you don't care about losing all files on Ubuntu, then the easy solution is first shrinking the Windows partition (from within Windows) to get some space. The resize will only be completed on a reboot, so reboot Windows a couple of times. Then boot from a live disk and delete the Ubuntu partitions, then create new ones and reinstall. Deleting partitions and creating new ones is faster and safer than resizing partitions. Especially if the system is already broken.

---

### Post by grahammechanical on 2015-02-18
We cannot reset Ubuntu in the manner that you request. But we do have a Recovery Mode that is useful in some situations. You will find Recovery Mode in the Advanced Options for Ubuntu sub-menu of the Grub boot menu. At the Recovery menu

Select Clean - try to make free space. That might get you somewhere. You might be able to load a working desktop.

Select Root - drop to a root shell prompt. That will let you remove applications if you know the correct commands. To get back to the Recovery Menu type exit and then select Resume. That will load the desktop using a fall back open source video driver. Restart to load Ubuntu with the usual video driver.

Remember, to use Windows utilities to resize Windows partitions but run a Windows defag utility more than once before resizing and check each time that Windows still loads. Then use Gparted to expand the Ubuntu partition into the unallocated space that you have created.

Regards.

---

