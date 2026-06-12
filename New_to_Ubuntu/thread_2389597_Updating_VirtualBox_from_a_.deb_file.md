---
title: "Updating VirtualBox from a .deb file"
date: 2018-04-18
forum: New to Ubuntu
---

### Post by waltd on 2018-04-18
Hello, I installed VirtualBox from a .deb file.  I just got a message in VirtualBox that an update to VirtualBox is available in a .deb file. I downloaded the new .deb file. What is the best way up update Virtualbox with this new .deb file.  Can I just execute the .deb file and the updates will overwrite the existing application? Or do I need to uninstall the old version first before executing the new .deb file? If I must first uninstall, what is the best Terminal commands to uninstall VirtualBox that was installed from a .deb file?  Thank you.

---

### Post by PaulW2U on 2018-04-19
> **waltd said:**
> Can I just execute the .deb file and the updates will overwrite the existing application? Or do I need to uninstall the old version first before executing the new .deb file?You can install the new version over the old one. There is no need to uninstall first. I used to install Sublime Text and Atom that way. If at any time you uninstall then whatever is there at the time will be uninstalled.

VirtualBox is in the software repositories, May be you're downloading .debs as Ubuntu's version is not the most current?

Did you know that you can configure your system to download updates as they become available? No need to download and install .debs each time a new version is released. The instructions can be found at [https://www.virtualbox.org/wiki/Linux_Downloads](https://www.virtualbox.org/wiki/Linux_Downloads) although it's not very obvious. The instructions start at "Debian-based Linux distributions". If you're not happy carrying out those instructions then you can continue installing a new .deb each time. 

Obviously there is a certain amount of risk involved by installing software from outside of the official Ubuntu repositories but you should be fine if you're downloading from the Virtualbox site.

---

### Post by kerry_s on 2018-04-19
yeah, i wouldn't use that.
all the virtualbox pieces need to be the same version. installing just the app it self with out the matching kernel patch might give you a broken install.

---

### Post by SeijiSensei on 2018-04-19
Just follow the instructions that PaulW2U cited to configure your system to use the Oracle repositories.  Then VB will be updated in conjunction with the rest of the software on your machine.  It will also make sure you have the right support files to use it with new kernels.

[https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions](https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions)

---

