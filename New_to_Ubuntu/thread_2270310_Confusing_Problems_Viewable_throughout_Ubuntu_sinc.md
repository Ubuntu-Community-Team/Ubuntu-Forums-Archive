---
title: "Confusing Problems Viewable throughout Ubuntu since install"
date: 2015-03-22
forum: New to Ubuntu
---

### Post by ruedi2 on 2015-03-22
I have been having an aray of problems with ubuntu on my laptop. The laptop Is an asus with a Core i3 processor and 4 gb of ram. Acording to ubuntu's website it was recomended that if I had 4 gb of ram that I should install the 64 bit version. With the 64 bit version installed I can only use the pre installed packages. I cannot even use packages from ubuntu software center. Also I have a problem with terminal not allowing me to input my acount pasword unless I press enter and type the password before the terminal finishes displaying the fals entry text. I am new to ubuntu and linux so I realise I could be missing something. Any help is appreciated and thanks in advance.

---

### Post by kerry_s on 2015-03-22
password entry is invisible, you just type & hit enter.

what do you mean you can't install from the software center ? what does it do ?

---

### Post by carl4926 on 2015-03-22
Could be useful if you said which version of Ubuntu
And in a terminal get us the result of this

```
lspci -nnk
```Use your mouse to copy and paste in the terminal
Then paste it here in code tags (see the # symbol above in advanced reply)

---

### Post by ruedi2 on 2015-03-22
00:00.0 Host bridge [0600]: Intel Corporation 2nd Generation Core Processor Family DRAM Controller [8086:0104] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: i915
00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:1c33]
    Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4)
    Kernel driver in use: pcieport
00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4)
    Kernel driver in use: pcieport
00:1c.3 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 [8086:1e16] (rev c4)
    Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
    Subsystem: AzureWave Device [1a3b:1186]
    Kernel driver in use: ath9k
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device [1043:14c7]
    Kernel driver in use: alx

---

### Post by carl4926 on 2015-03-22
Please lets try something

```
sudo apt-get install chromium-browser
```

Either tell us what happens or show us the feedback from the terminal

---

### Post by kerry_s on 2015-03-22
> **carl4926 said:**
> Please lets try something

```
sudo apt-get install chromium-browser
```

Either tell us what happens or show us the feedback from the terminal

maybe "sudo apt-get update" first ?

---

