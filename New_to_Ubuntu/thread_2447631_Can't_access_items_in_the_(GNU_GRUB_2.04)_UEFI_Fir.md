---
title: "Can't access items in the (GNU GRUB 2.04) UEFI Firmware Settings (Ubuntu 20.04)"
date: 2020-07-22
forum: New to Ubuntu
---

### Post by kveldman on 2020-07-22
Trying to re-enable my front camera on my Surface Pro 3 running Ubuntu 20.04 (GNU GRUB v2.04) but am unable to select the option. The GRUB menu opens, I select UEFI Firmware Settings, I am prompted for a password (I've never set one). I can get past the password by hitting enter while it's blank, but I am unable to select certain options, specifically  "Secure Boot Control", "Administrator Password", or any of the menu items within "Advanced Device Security"

Images here: [http://imgur.com/a/FtSKjSU](http://imgur.com/a/FtSKjSU)

I have tried passwords "root" and "password", and I cannot enter my root user password because only lowercase letters are allowed in the password screen (see image above). 

Any ideas how I can edit those menu entries? My front camera is disabled and I would like to be able to use it for web-meetings. 

Some extra information that might be important: Ubuntu20.04 and Windows 10 are both loaded. I suspect there is some kind of default password that I would need to enter to have access, but my Google-Fu is not strong enough to find it if that is the case.

---

### Post by oldfred on 2020-07-22
The grub menu item should just take you into UEFI, just like using Windows or using direct keys.
This is not a grub issue & you should change title to refer to a Surface Pro UEFI issue, so those who may know about that system will see your post.

But if you ever set a password, you typically need that to open additional UEFI settings. Do not know your system specifically.

Surface Pro Ubuntu install:
[https://ubuntuforums.org/showthread.php?t=2365819](https://ubuntuforums.org/showthread.php?t=2365819)
Surface Pro 3 - USB/MicroSD Only Install 
[http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)
[http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu](http://askubuntu.com/questions/265644/dual-boot-surface-pro-with-ubuntu)
Surface Pro2 mega thread:
[http://ubuntuforums.org/showthread.php?t=2183946](http://ubuntuforums.org/showthread.php?t=2183946)
[http://ubuntuforums.org/showthread.php?t=2209247](http://ubuntuforums.org/showthread.php?t=2209247)

---

### Post by grahammechanical on 2020-07-23
some years ago I heard of a case where the supplier set a password for what was in those days called the BIOS and refused to tell the customer what the password was. Has this happened to you?

From the little searching I have done it seems that you can only change a UEFI password on a Surface Pro by using the present password to access the UEFI at the correct security access level.

Microsoft says this

> 
[LIST]
[*]**Administrator Password**     This option lets you create a password to prevent others from  changing the UEFI settings. Organizations that need to protect sensitive  information typically use an administrator password. 
[/LIST]


Are you able to use Windows 10 to enable and disable certain items of hardware? Is this camera disabled in Windows 10?

[https://support.microsoft.com/en-gb/help/4023531/surface-how-to-use-surface-uefi](https://support.microsoft.com/en-gb/help/4023531/surface-how-to-use-surface-uefi)

> You can also load the UEFI firmware settings menu through Windows. To do this:  
[LIST]
[*]Select **Start  **> **Settings ** > **Update & security**  > **Recovery**.
[*]Under **Advanced startup**, select **Restart Now**.
[*]Under **Choose an option**, select **Troubleshoot** > **Advanced Options** > **UEFI Firmware Settings**, and then select **Restart**.
[/LIST]


Regards.

---

