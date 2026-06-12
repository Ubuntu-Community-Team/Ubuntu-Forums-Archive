---
title: "Nvidia Graphics not working."
date: 2016-12-30
forum: New to Ubuntu
---

### Post by soorajmp on 2016-12-30
Hi Frieds,

I have Ubuntu MATE installed in Laptop , I have Nvidia Graphics card. But I have few doubts regarding if the graphics card being installed correctly or not.
I have few questions which I listed below.

1) If I install Nvidia drivers , will my card running always and will my Desktop environment uses my Nvidia graphics card ? or My graphics card will be used only when I play games ?
2) I pasted the output of 'lspci" command output at the end of this post. Please tell me if the Nvidia is properly installed or not. How can I verify the Nvidia installation ?
3) Does Desktop Env uses Nvidia support for displaying or is it uses only onboard intel graphics ? if it does not uses Nvidia, is it possible to configure my DE uses Nvidia instead of Intel ?



LSPCI output
--------------------

00:00.0 Host bridge: Intel Corporation Haswell-ULT DRAM Controller (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 0b)
00:03.0 Audio device: Intel Corporation Haswell-ULT HD Audio Controller (rev 0b)
00:14.0 USB controller: Intel Corporation 8 Series USB xHCI HC (rev 04)
00:16.0 Communication controller: Intel Corporation 8 Series HECI #0 (rev 04)
00:1b.0 Audio device: Intel Corporation 8 Series HD Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 1 (rev e4)
00:1c.2 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 3 (rev e4)
00:1c.3 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 4 (rev e4)
00:1c.4 PCI bridge: Intel Corporation 8 Series PCI Express Root Port 5 (rev e4)
00:1d.0 USB controller: Intel Corporation 8 Series USB EHCI #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation 8 Series LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 8 Series SATA Controller 1 [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 8 Series SMBus Controller (rev 04)
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0c)
08:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/810M/820M / GT 620M/625M/630M/720M] (rev a1)

---

### Post by Autodave on 2016-12-30
Have you searched the software center or synaptic package manager for the newest driver? You are much safer to use a driver from either of these sources than you are from d-ling from Nvidia.

---

### Post by SeijiSensei on 2016-12-30
If you always want to use the NVIDIA card, see if you can turn off the Intel adapter in the system's BIOS.  Otherwise you have to use nvidia-prime for these annoying hybrid laptops.  Take a look at [http://askubuntu.com/questions/758972/does-ubuntu-16-04-support-hybrid-graphics-cards-bumblebee](http://askubuntu.com/questions/758972/does-ubuntu-16-04-support-hybrid-graphics-cards-bumblebee)

Don't use bumblebee; it has been deprecated in favor of nvidia-prime as that article documents.

---

