---
title: "No Bootable Deivce on Acer Aspire Es 11"
date: 2021-05-28
forum: New to Ubuntu
---

### Post by eoin-d on 2021-05-28
My family has had an Aspire Es 11 running windows for a few years. It was always running very slowly and I decided that I should install Ubuntu as the laptop seemed underpowered to run windows. After a while of troubleshooting different issues, I was able to get an install USB to work. However, when I restarted the laptop it said that there was no bootable device. I used the "Try Ubuntu" feature of the install USB to run boot repair. My results are here: [http://paste.ubuntu.com/p/Qy4KNVgqMk/](http://paste.ubuntu.com/p/Qy4KNVgqMk/) 
I believe that my issue may lie with the "Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (mmcblk0p1/EFI/ubuntu/-shimx64.efi file) !" text at the the end of the boot repair window. I am not sure how to do this, all I know is that the option to "Select a UEFI file as trusted for executing" is missing from my BIOS. 
I am not sure where I go from here.

---

### Post by oldfred on 2021-05-28
You are showing two unknown devices & one does have Ubuntu description. Those are the UEFI file for booting.
If you have Secure boot on, you may want to try to turn it off.

Acers have required users in UEFI to manually change 'unknown' to ubuntu and set "trust" so it is a valid boot file.
Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:class 3
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

Acer ES1-331 laptops Strange differences at new installations
[https://ubuntuforums.org/showthread.php?t=2362511](https://ubuntuforums.org/showthread.php?t=2362511)

That looks more like a lightweight system, full Ubuntu may be slow.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, xubuntu, Ubuntu MATE, Budgie

---

### Post by eoin-d on 2021-05-29
As I stated, there is no option to "Select a UEFI file as trusted for executing" in my BIOS.

---

### Post by oldfred on 2021-05-29
Have you updated to latest available. There were some versions of UEFI from Acer that were missing that setting.
You do have to have UEFI Secure boot on.

A user posted screen shots.
[https://ubuntuforums.org/showthread.php?t=2348269Acer](https://ubuntuforums.org/showthread.php?t=2348269Acer) Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

