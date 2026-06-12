---
title: "Failed to boot after 1st installation"
date: 2017-09-03
forum: New to Ubuntu
---

### Post by benz37 on 2017-09-03
Hello all,
Ubuntu 16.04 failed to boot after the 1st installation, on dell XPS 8920 desktop alongside with Win10, with two errors
1) nouveau 0000:01:00.0: DRM: failed to create kernel channel, -22
Gave up waiting for root device
2) ALERT! UUID=xxxx does not exist. Dropping to a shell

ps:
I have the Dell XPS 8920 with Core i7 7700K, 16 GB DDR4, with NVIDIA GeForce GTX 1060, HDD 1TB, PCI 250GB, Windows 10 pre-installed
I installed ubuntu on the HDD
Any clue ?

---

### Post by Autodave on 2017-09-03
Did you install and driver for your Nvidia card?

---

### Post by yancek on 2017-09-03
With windows 10 pre-installed, it was almost certainly UEFI so did you also install Ubuntu UEFI?  Explained at the Ubuntu site below.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

The ALERT message you posted indicates it is trying to find a partition by its UUID and it doesn't exist.  Open a terminal and run the command:  sudo blkid
Take a look at the output and compare that to the UUID you see in the error message and the contents of the grub.cfg file and it's UUIDs.  Or post that info here.

---

### Post by Quarkrad on 2017-09-03
Also,  make sure you configure Windows 10 to shut down completely when you tell it to *shut down* rather than it's default state of 'hibernating' (thus enabling it to have a speedier boot up).  Not doing this causes all sorts of issues with Ubuntu dual booting. (There are lot's of instructions on the web how to do this - it is very easy to do).

---

### Post by benz37 on 2017-09-03
No, I did not install NVIDIA, this happened at the first start, just after the installation

---

### Post by benz37 on 2017-09-03
I added a boot option (pci=nomsi) that allowed me to have command line, it was the only way to have command line.
After a look on journalctl, here is a list of all errors I got:

tpm_crb MSFT0101:00: can't request region for ressource
iwlwifi 0000:03:00.0: pci_enable_msi failed - -22
dev-disk-by\x2dpartlabel-xxxxxxxx\x5cx20patition-device: Dev. xxxxx    appeared twice with different sysfs path
Timed out waiting for device dev-disk-by\x2duuid-ECEB\x2d2C96.device


Total of four error in red

---

### Post by mastablasta on 2017-09-05
> **benz37 said:**
> No, I did not install NVIDIA, this happened at the first start, just after the installation

regarding nvidia - you need to boot with nomodeset to use VGA mode, then install nvidia drivers using additional drivers application or using nvidia PPA (if you want the latest).

---

### Post by oldfred on 2017-09-05
Did you change to AHCI? Not sure if nvme_load=YES still required or not?
You have to install Windows AHCI drivers before you change.
 Dell XPS 8920 & Nvidia GTX 1060 & PCIe M2 drive Raid change to AHCI
[https://ubuntuforums.org/showthread.php?t=2360929](https://ubuntuforums.org/showthread.php?t=2360929) 

      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)
[https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en](https://www.dell.com/support/article/us/en/19/sln142679/how-to-enable-boot-from-dvd-option-with-uefi-boot-mode-enabled--windows-8--81--10-?lang=en)
Dell with NVMe needs AHCI & boot option nvme_load=YES
[https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en](https://www.dell.com/support/article/us/en/19/sln299303/loading-ubuntu-on-systems-using-pcie-m2-drives?lang=en)

---

### Post by benz37 on 2018-02-15
Solved after a BIOS update released on Dec 08 2017 V 1.0.11

---

