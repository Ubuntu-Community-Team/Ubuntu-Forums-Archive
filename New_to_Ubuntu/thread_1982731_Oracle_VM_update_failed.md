---
title: "Oracle VM update failed"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by sgshah on 2012-05-19
Hi,

In my Ubuntu 10.04LTS, Oracle VM version 3.2.8 is installed and running fine.

I am willing to update Oracle VM (VirtualBox) to latest version.
But while running debian pkg, following error is displayed:-
"Error: Conflicts with the installed package 'virtualbox-3.2'"
Screenshot is attached for reference.

Any help to overcome error is greatly appreciated.

--
Shirish

---

### Post by wildmanne39 on 2012-05-22
Hi, you need to uninstall the old version then you can install the new version and you will not lose your vm's as long as you do not uninstall the configuration files.
Thanks

---

### Post by sgshah on 2012-05-23
Thanks wildmanne39.

But next question comes to me is : how to uninstall only Virtual Box without uninstalling configuration files ?

-
Shirish

---

### Post by plucky on 2012-05-23
> **sgshah said:**
> Thanks wildmanne39.

But next question comes to me is : how to uninstall only Virtual Box without uninstalling configuration files ?

-
Shirish

Use **Synaptic Package Manager** and search for Virtualbox.You can then select it and mark to un-install.
The configuration files will stay in you /home folder.

Good Luck

---

### Post by wildmanne39 on 2012-05-23
Hi +1 on plucky's answer but I would like to add just do not choose to remove completely and it will leave the configuration files.
Thanks

---

### Post by sgshah on 2012-05-24
Thanks again wildmanne39 and plucky,

With your support I have updated VirtualBox thanks, but while running guest OS from Virtual box, below error pop up and I am unable to use the USB ports???

"Failed to open a session for the virtual machine Windows Xp.  Implementation of the USB 2.0 controller not found!  Because the USB 2.0 controller state is part of the saved VM state, the VM cannot be started. To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND). 
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Console Interface: IConsole {1968b7d3-e3bf-4ceb-99e0-cb7c913317bb}  
"
Any help on this, how to get USB ports working with VietualBox version4.1 ? ? ?

---

### Post by plucky on 2012-05-24
> To fix this problem, either install the 'Oracle VM VirtualBox Extension Pack' or disable USB 2.0 support in the VM settings (VERR_NOT_FOUND).

Go [Here](https://www.virtualbox.org/wiki/Downloads) and download the extension pack for your installation.

I am surprised it didn't offer to install it for you after you installed the updated package.

Good Luck

---

### Post by sgshah on 2012-05-24
Thanks plucky,

problem solved completely. Thanks a ton for all your help.

I downloaded debian pkg, & installed VB.......after that no pop up for extension package.

Thanks
--
Shirish

---

### Post by wildmanne39 on 2012-05-24
Hi, I am glad you got it working, please use thread tools at the top of the page to mark the thread solved.
Thanks

---

