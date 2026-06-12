---
title: "xubuntu does not recognize usb"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by kurishiiu on 2008-07-20
Hi,

i installed Xubuntu 8.04 about a month ago. I had ubuntu before and it was fine. Now i was trying to move some music to my brother usb but this xcfe won't recognize it. I made the tests suggested in other threads but i cannot get to access the mp4 and it makes me crazy. I'm not liking this xubuntu that much

Please help!!!

**lspci shows:**

lspci
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 730 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge)
00:01.1 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 82)
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.3 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 07)
00:01.4 Multimedia audio controller: Silicon Integrated Systems [SiS] SiS PCI Audio Accelerator (rev 02)
00:01.6 Modem: Silicon Integrated Systems [SiS] AC'97 Modem Controller (rev a0)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 630/730 PCI/AGP VGA Display Adapter (rev 31)


**lsusb shows **
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

** sudo fdisk -l showsonly one disk**

Disco /dev/sda: 20.4 GB, 20490559488 bytes
255 cabezas, 63 sectores/pista, 2491 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x89fa89fa

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        2382    19133383+  83  Linux
/dev/sda2            2383        2491      875542+   5  Extendida
/dev/sda5            2383        2491      875511   82  Linux swap / Solaris

---

### Post by dhughes on 2008-07-20
Did you try **lsusb**

---

### Post by kurishiiu on 2008-07-20
> **dhughes said:**
> Did you try **lsusb**

as i explained on my post i tried it and this is the result

**lsusb shows**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

---

### Post by dhughes on 2008-07-20
> **kurishiiu said:**
> as i explained on my post i tried it and this is the result

**lsusb shows**
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

 Oops missed that, I saw lspci.

---

