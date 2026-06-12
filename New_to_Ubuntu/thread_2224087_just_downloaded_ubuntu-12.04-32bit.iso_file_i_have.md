---
title: "just downloaded ubuntu-12.04-32bit.iso file i have a win8 64bit how to dualboot??"
date: 2014-05-14
forum: New to Ubuntu
---

### Post by kr4k3n2 on 2014-05-14
i just downloaded "ubuntu 12.04 32bit .iso" and burned it on a pendrive, i already have a "windows 8.1 pro 64bit" i want to dualboot without any loss or after-install recovering ;)

---

### Post by simplychrislike on 2014-05-14
You can start the installation of Ubuntu and look if the installer asks you to install the Ubuntu next to Windows. This is shown at the part where you can choose the partitions. Until this point, nothing will happen to your Windows installation.
But why don't you get the newest Ubuntu 14.04?

---

### Post by kr4k3n2 on 2014-05-14
MY BAD :( is there any way to upgrade it to 14.04 from 12.04 ?? :)

---

### Post by kr4k3n2 on 2014-05-14
and also post some links on dualbooting :)

---

### Post by olliemonster on 2014-05-14
To upgrade from 12.04 to 14.04 without changing anything you will have to wait till canonical release 14.4.1 on july 24th. To upgrade earlier open a terminal with ctrl alt t and type
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
```
sudo do-release-upgrade -d
```
For dual booting when you boot ubuntu from your usb stick and click install you can shrink the size of your windows install but make sure you defragment you disk first and make sure you install grub when it ask's on the install ubuntu instructions.

---

### Post by simplychrislike on 2014-05-14
You should not install Ubuntu 12.04 and try to update to version 14.04!
If that already happened, maybe those links help you to get up-to-date: [https://help.ubuntu.com/community/SaucyUpgrades](https://help.ubuntu.com/community/SaucyUpgrades) and [https://help.ubuntu.com/community/TrustyUpgrades](https://help.ubuntu.com/community/TrustyUpgrades)
Get the newest Ubuntu [here]("http://www.ubuntu.com/download/desktop").

---

### Post by grahammechanical on 2014-05-14
There is something missing here
> 
[COLOR=#333333][FONT=Ubuntu]Having a PC with EFI firmware does not mean that you need to install Ubuntu in EFI mode. What is important is below: [/FONT][/COLOR]

[LIST]
[*=left]if the other systems (Windows Vista/7/8, GNU/Linux...) of your computer are installed in EFI mode, then you must install Ubuntu in EFI mode too.
[/LIST]

> 
[COLOR=#333333][FONT=Ubuntu]To install Ubuntu in EFI mode:[/FONT][/COLOR]

[LIST]
[*=left][FONT=inherit]Use a 64bit disk of Ubuntu ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))[/FONT]
[/LIST]


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With Windows 8 64 bit on the machine it is bound to be installed in EFI mode. You need Ubuntu 64 bit. Just download and burn another ISO image. This time of 14.04 64 bit.

I also strongly advise not to tick "Install Third Party Software." That will install a proprietary video driver and if there is going to be a problem with the first re-boot after installing it will be because of the proprietary video driver.

After installation we can install the third party software through the Ubuntu software centre by searching for Ubuntu Restricted Extras. And we can experiment with proprietary video drivers by going to System Settings>software and Updates>Additional Drivers tab.

Regards.

---

