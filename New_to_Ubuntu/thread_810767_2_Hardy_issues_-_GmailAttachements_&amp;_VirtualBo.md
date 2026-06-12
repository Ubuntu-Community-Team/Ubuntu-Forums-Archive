---
title: "2 Hardy issues - GmailAttachements &amp; VirtualBox"
date: 2008-05-28
forum: New to Ubuntu
---

### Post by richard.e.morton on 2008-05-28
Hi,

I am newish to the world of Linux but I have finally done the deed and reinstalled my primary laptop and installed hardy as the only OS. I have the laptop working fine except for the occasional bump in the road. Most of these bumps I have overcome, but there are 2 outstanding ones I hope you can help:

1. When in Gmail (I have the new interface for gmail, but I have also tried the old interface and also basic html view) I cannot add an attachment to an email I am composing. When I click on attach then browse I get the file selector dialogue where I can browse to a file and select it. When I select a file and click open the dialogue disappears but the filepath is not completed in the email.

2. VirtualBox, when starting a VirtualServer it says;

VirtualBox kernel driver not installed. The vboxdrv kernel module was either not loaded or /dev/vboxdrv was not created for some reason. Please install the virtualbox-ose-modules package for your kernel, e.g. virtualbox-ose-modules-generic..
VBox status code: -1908 (VERR_VM_DRIVER_NOT_INSTALLED).


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

however the modules package indicated is indeed installed (I have re-installed it to be sure)

I hope you can help

thanks for looking

Richard

---

### Post by richard.e.morton on 2008-05-28
ok, so I have solved the issue with firefox and gmail using the following destructions to upgrade to firefox3rc1

[www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

I am not however, able to get virtualbox to work! anyone out there know the answer?

Thanks

R

---

### Post by Oldsoldier2003 on 2008-05-28
> **richard.e.morton said:**
> ok, so I have solved the issue with firefox and gmail using the following destructions to upgrade to firefox3rc1

[www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

I am not however, able to get virtualbox to work! anyone out there know the answer?

Thanks

R

you could either search synaptic and install the ose modules for virtualbox, or just remove virtualbox and get it directly from sun. the version there is better than the one in the repos.

[http://www.sun.com/software/products/virtualbox/index.jsp](http://www.sun.com/software/products/virtualbox/index.jsp)

---

