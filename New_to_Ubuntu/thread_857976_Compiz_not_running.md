---
title: "Compiz not running"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by jamil_1 on 2008-07-13
Whenever I try run compiz i get an error:

jamil@jamil-desktop:~/compiz-0.6.2$ compiz --replace
/usr/bin/compiz.real: symbol lookup error: /usr/lib/compiz/libdecoration.so: undefined symbol: decor_apply_gravity
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

lspci out put:

jamil@jamil-desktop:~/compiz-0.6.2$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
03:01.0 Communication controller: Agere Systems 56k WinModem (rev 01)

---

### Post by ChameleonDave on 2008-07-13
Please run the "compiz-check" script to diagnose possible problems.

Do the following at the terminal:

```

cd
wget http://blogage.de/files/4359/download -O compiz-check
chmod +x compiz-check
bash compiz-check

```

(For people looking at this at a later date, use the guide at [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check) rather than the commands given above.)

---

