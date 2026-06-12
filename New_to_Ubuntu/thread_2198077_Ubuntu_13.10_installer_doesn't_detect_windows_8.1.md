---
title: "Ubuntu 13.10 installer doesn't detect windows 8.1"
date: 2014-01-06
forum: New to Ubuntu
---

### Post by bicycleracesjw on 2014-01-06
Brand new HP 2000 came pre-installed with Windows 8. I completed the upgrade to Windows 8.1 and then proceeded to attempt a side by side installation of 13.10. However, the installer doesn't detect windows and only gives me the options of deleting the entire disc or "something else". I don't really understand the menu in the something else option, so now I'm kind of stuck. Any help is greatly appreciated.

---

### Post by btrix2 on 2014-01-07
its weird that windows is not detected. how are you installing Ubuntu is it live cd or through exe file. something else is just custom install. you can change the way how ubuntu installs itself. if it doesnt detect windows you can install Ubuntu by using exe file or us live cd boot use something else option and just remember where windows is installed and install ubuntu on another partition.

---

### Post by westie457 on 2014-01-07
Hello bicycleracesjw[COLOR=#DD4814][COLOR=#000000] welcome to UF.
[/COLOR][/COLOR]

The easiest way to get started with your Ubuntu installation is read through this link. [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Next is to disable fastboot with this link. [http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

Also disable all forms of hibernation/sleep/suspend using this link. [http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/](http://www.techrepublic.com/blog/tr-dojo/delete-hiberfilsys-by-disabling-windows-hibernate-function/)

Let us know if you have any further problems.

When the installation has been successful Windows hibernation can be enabled by reversing the directions of the third link.

Do not switch on Windows 'Fastboot' because it overrides Grub.

---

