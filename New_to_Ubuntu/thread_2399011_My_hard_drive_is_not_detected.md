---
title: "My hard drive is not detected"
date: 2018-08-20
forum: New to Ubuntu
---

### Post by michew on 2018-08-20
I tried to dual boot Ubuntu 18.04 on my XPS 13 (9360, i7, pre-installed Windows 10) but failed. Reason is that none of the partitions showed up on gparted (**except** my USB drive), and therefore I cannot proceed with the installation. I used Rufus and tried both GPT and MBR to burn the ISO onto the USB, still failed. I have already disabled fast start up and secureboot. Two strange things:

1. USB drive is **sometimes** not detected when I tried to boot ubuntu after I hit F12 at the Dell screen.
2. The time always shifts to few hours ahead whenever I log back into Windows 10.

Sorry I am new and cannot figure out why these are happening and while I realized some people have the same issue as I do, I still haven't found a solution. Thanks in advance.

---

### Post by oldfred on 2018-08-20
Dell requires several UEFI settings changes. You also need to update UEFI from Dell and if SSD update firmware for SSD.
And Windows needs settings changed also.
With latest versions of Ubuntu, more of the proprietary drivers are already included.

With Dell you need to change UEFI setting for drives from RAID or Intel SRT to AHCI, but first install AHCI drivers into Windows.
Also turn off fast boot and usually better to turn off UEFI Secure Boot. 
You should have two USB flash drive boot settings in UEFI boot menu, f12. But you only want to use the UEFI one.

In Windows make sure Windows fast start up is off. Note that Windows with updates will turn it back on, and you need to keep it off. Best to also make a Windows repair disk. And did not Dell and Windows suggest backups, you really need to do that first.

More details on general UEFI installs in link in my signature below

Issues are common across many similar models by brand. Bigger differences if AMD or Intel.
       Dell XPS 13 9360 
[https://ubuntuforums.org/showthread.php?t=2353288](https://ubuntuforums.org/showthread.php?t=2353288)
Dell XPS 13 9560 install without issues
[https://ubuntuforums.org/showthread.php?t=2357321](https://ubuntuforums.org/showthread.php?t=2357321)
[https://wiki.archlinux.org/index.php/Dell_XPS_15_9560](https://wiki.archlinux.org/index.php/Dell_XPS_15_9560)
Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 
            Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

### Post by michew on 2018-08-20
Thanks for the reply. I heard that switching to AHCI might cause problems with Windows?

---

### Post by oldfred on 2018-08-20
You just have to install the AHCI driver.
Or everytime you reboot switch from RAID to AHCI or vice-versa.

---

### Post by owenll on 2018-08-21
No it worked on my XPS 13 which now dual boots fine - but I needed my windows when I messed up, so remember to back up

---

