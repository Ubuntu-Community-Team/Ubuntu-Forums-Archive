---
title: "How do I make my VB Ubuntu recognize my wireless adapter?"
date: 2013-01-20
forum: New to Ubuntu
---

### Post by aineshane on 2013-01-20
I am very new to Ubuntu and any linux based operating system though I have done a little reading on it.

I recently installed virtual box on my win7 32 bit and loaded Ubuntu 12.04 Precise as the guest OS.

The reason for this is so that I gain the ability to use reaver and aircrack. However, the pc doesn't see my wireless adapter. It only list ethernet

The lspci command gives me this
```
shane@shane-VirtualBox:~$ lspci
00:00.0 Host bridge: Intel Corporation 440FX - 82441FX PMC [Natoma] (rev 02)
00:01.0 ISA bridge: Intel Corporation 82371SB PIIX3 ISA [Natoma/Triton II]
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:02.0 VGA compatible controller: InnoTek Systemberatung GmbH VirtualBox Graphics Adapter
00:04.0 System peripheral: InnoTek Systemberatung GmbH VirtualBox Guest Service
00:05.0 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio Controller (rev 01)
00:06.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 08)
00:08.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)
00:0d.0 SATA controller: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] (rev 02)

```

I don't know what else to list

---

### Post by slickymaster on 2013-01-20
Did you try to set your VM to use NAT - it's in the ethernet section.
That will make a virtual ethernet card which picks up your hosts internet connection. You don't need to have your PC connected through ethernet, it just need to be connected to the internet.

---

### Post by aineshane on 2013-01-21
> **slickymaster said:**
> Did you try to set your VM to use NAT - it's in the ethernet section.
That will make a virtual ethernet card which picks up your hosts internet connection. You don't need to have your PC connected through ethernet, it just need to be connected to the internet.

It easily connects to the net if I use my host os' connection. What I want is to use Ubuntu to monitor wireless access points and then use reaver to hack the. Is that possible when Ubuntu is the guest OS?

---

### Post by lisati on 2013-01-21
Breaking into other people's networks is something we do not support here.

Thread closed.

---

