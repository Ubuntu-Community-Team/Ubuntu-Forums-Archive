---
title: "Losing boot twice (after installing Nvidia driver?)"
date: 2020-05-02
forum: New to Ubuntu
---

### Post by jandewit6 on 2020-05-02
Hope someone is willing to help me through the following boot-repair [report]("https://paste.ubuntu.com/p/mXQHkgsq22/").

System: Macbook air late 2010. Has been running without problem on Win7 since I bought it new in Nov 2010.
I do not want to upgrade to Win10 ever.

Installed Ubuntu 18.04.4 and everything running fine. Ony problem is freezing because of system overload.
Removed hardware acceleration in Fireforx and Chromium and system is more stable.
Switched to using Nvidia driver and system load was further reduced. System running fine until reboot into black screens.
Restarted with installation disk (try ubuntu) and ran boot-repair.
I tried following several online instructions including uninstalling Nvidia, but to no avail.
Cannot find my way into a grub menu and most instructions on manually reinstalling boot partitions are above level for me.

Any help in keeping me away from Win or Mac much appreciated.

---

### Post by CelticWarrior on 2020-05-02
Welcome.

Boot Repair is excellent to check details - and at first glance yours is fine - but if the system is booting, even in those cases where it boots to a black screen, there nothing else to do with Boot Repair. Or messing with boot partitions like you suggested or absolutely anything else boot related except, eventually, Secure Boot in UEFI settings (not anything OS related though) if applicable. I'm not sure it is applicable to Macs as I have zero experience with those.

Now the question is: How have you installed Nvidia drivers and which ones? For which Nvidia Graphics? And how are you trying to uninstall them?

---

### Post by jandewit6 on 2020-05-02
Thanks for your quick reply.

I installed via the Ubuntu software console and switched to the suggested driver  and under drivers started using the available nvidia drivers. It worked fine until restart.

In the terminal (start via installation disk) I did: $ ubuntu-drivers devices and got:
Model: MCP89 [GeForce 320M]
driver: nvidia-340 - distro non-fre recommended
driver: xserver-xorg-video-nouveau - distro free bulletin

GeForce 320M I recognise from my old days with Windows.

Uninstall instructions I found here: [http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux](http://www.linuxandubuntu.com/home/how-to-install-latest-nvidia-drivers-in-linux)

However, as I am not too familiar with messing around with the system yet, I thought it safer to ask first on the forum.

---

### Post by CelticWarrior on 2020-05-02
The linked tutorial is mostly correct. There's no need to add the graphics drivers PPA for installing an old driver (old but long term support and the last one you can use for that card). However, that alone shouldn't be a problem but better to proceed cautiously.

Suggestion (for now do not use installation media but make sure you have internet connection):
[LIST]
[*]Try booting normally. If you end up in a black screen again either then use CTRL+ALT+F3 to get a TTY (command line only)
[*]Login
[*]purge Nvidia drivers: ```
sudo apt-get purge nvidia*
```
[*]Install ppa-purge: ```
sudo apt install ppa-purge
```
[*]Run ppa-purge to remove the PPA and clean everything that was installed form there: ```
sudo ppa-purge ppa:graphics-drivers
```
[*]Fully update the system: ```
sudo apt update && sudo apt full-upgrade
```
[*]Install the proper Nvidia drivers: ```
sudo ubuntu-drivers autoinstall
```
[/LIST]

---

### Post by jandewit6 on 2020-05-02
Thanks man.
Via the grub menu that I finally got access to, I was able to get rid of the nvidia driver, using your commands.
Am in again, system still requesting much from processors, but running.
Will have a look around for a better driver and probably another way of installing.

Thanks even so much!

---

### Post by CelticWarrior on 2020-05-02
That is the one and only Nvidia drivers version you can use and only until Nvidia doesn't relegate that model to legacy and stop any support for it. At that point you will only be able to use the open-source nouveau.

---

### Post by jandewit6 on 2020-05-02
Update: the sudo ubuntu-drivers autoinstall command installed the same nvidia driver again.
Back to black.
So I repeated the purge procedure and am running now without nvidia.

Happy without nvidia then.

Thank you again, much appreciated.

---

