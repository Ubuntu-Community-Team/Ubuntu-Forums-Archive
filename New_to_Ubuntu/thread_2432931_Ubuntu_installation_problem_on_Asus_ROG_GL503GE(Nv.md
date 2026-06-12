---
title: "Ubuntu installation problem on Asus ROG GL503GE(Nvdia Drivers)"
date: 2019-12-11
forum: New to Ubuntu
---

### Post by terrarium on 2019-12-11
[COLOR=#1C1E29]Hi,[/COLOR]
[COLOR=#1C1E29]Recently I have been trying to install Ubuntu on my laptop, but things did not go so easy as I expected. I created a partition on my hard drive for Ubuntu, burned the 18.04.3 LTS version using Rufus, and then installed the OS. The installation went fine as expected, but after restarting the machine, the start screen froze. I waited for at least an hour to see if Ubuntu would finally boot up, but it did not. I formatted the drive partitioned for Ubuntu, removed the Ubuntu entry from the Boot priority list, and did the whole thing again. Nothing worked :(

[/COLOR]
[COLOR=#1C1E29]I looked up for the issue on google and found this: [https://medium.com/@nitinpatel_20236/fixing-the-problems-installing-ubuntu-on-asus-rog-laptop-asus-gl503ge-5b6f497201b8](https://medium.com/@nitinpatel_20236/fixing-the-problems-installing-ubuntu-on-asus-rog-laptop-asus-gl503ge-5b6f497201b8)[/COLOR]
[COLOR=#1C1E29]I think there is some compatibility issue installing Ubuntu on systems with nvidia drivers. The aforementioned link provided a solution, but I am not sure about the process, neither did I try that.(there's no screenshot attached with each step). Can anybody inform me about the correct procedure on how to install Ubuntu on laptops with nvidia graphics cards?[/COLOR]
[COLOR=#1C1E29]Thanks! :KS

My system specs:[ATTACH]284603[/ATTACH]

[/COLOR]

---

### Post by oldfred on 2019-12-11
Generally you have to use nomodeset boot parameter to install & first boot or until you install nVidia driver from Ubuntu repository. If very new card/chip, you may also need ppa for newest drivers.
Newest Ubuntu will now give option to install nVidia driver as part of proprietary drivers checkbox.

You should be installing in UEFI boot mode, so you have to manually edit grub.cfg as you boot.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) & 
[URL="https://help.ubuntu.com/community/Grub2"]https://help.ubuntu.com/community/Grub2

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
    [URL="https://help.ubuntu.com/community/Grub2"]
[/URL]        
 Acer Predator Helios 300 Boot into system, update, reboot then install drivers.
[https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace](https://askubuntu.com/questions/1194761/how-to-install-nvidia-geforce-gtx-1050-ti-drivers-for-ubuntu-18-04-03-lts-on-ace)

---

### Post by terrarium on 2019-12-12
Thanks a lot! Everything seems to work out fine except that I have to disable secure boot every time I boot into Ubuntu, otherwise nvidia drivers won't work. (nvidia-smi does not work if secure boot is disabled). How can I overcome this problem?

---

### Post by oldfred on 2019-12-12
At the current time I do not use Secure Boot. 

Do not know details, but in general:
But you have to install the drivers with Secure Boot on and then you should automatically get mmx64.efi which is the key manager. Ubuntu cannot provide UEFI secure boot key for proprietary software. But any user can provide his own key to his software or if he believes proprietary software is safe. You then you assign your own key to the nVidia driver.

You may have to uninstall (totally purge) the version that does not have a key & reinstall to assign the key.
[https://askubuntu.com/questions/1147165/after-installing-nvidia-driver-430-ubuntu-19-04-does-not-boot-and-stuck-on-boot](https://askubuntu.com/questions/1147165/after-installing-nvidia-driver-430-ubuntu-19-04-does-not-boot-and-stuck-on-boot)

---

