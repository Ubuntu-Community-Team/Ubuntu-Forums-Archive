---
title: "Problems with GRUB"
date: 2017-04-11
forum: New to Ubuntu
---

### Post by vrrodovalho on 2017-04-11
Hello

Can someone help me with grub-repair? I installed Ubuntu 16, but got a grub error. Then I followed the steps in [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) , but now only Windows 10 boots and Ubuntu is not recognized. Any ideias?

BootInfo URL: [http://paste2.org/L8DYBPXY](http://paste2.org/L8DYBPXY)

---

### Post by vrrodovalho on 2017-04-11
I tried to change boot order, but only 2 options were available and it dindn`t work.

---

### Post by oldfred on 2017-04-12
Boot-Repair shows signed kernels & Secure boot on. But it still should work.
Have you tried with Secure boot off as Boot-Repair suggests and then re-running Boot-Repair?

You are not showing an Ubuntu entry in UEFI. So does not seem that system fully installed.
sudo efibootmgr -v

What brand/model system?
What video card/chip?

Did you change hard drive settings from RAID to AHCI?
Grub will not install correctly with RAID setting on.
 [https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/](https://samnicholls.net/2016/01/14/how-to-switch-sata-raid-to-ahci-windows-10-xps-13/) 

        Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 

XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/)

---

