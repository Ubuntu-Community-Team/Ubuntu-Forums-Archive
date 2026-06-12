---
title: "problem installing"
date: 2008-10-30
forum: New to Ubuntu
---

### Post by Sequences on 2008-10-30
I get goofy errors

Buffer I/O error on device sr0, logical block ...
end request: I/O error, dev sr0, sector ...

i get tons of these and it does seem as if i can get past it. memory check does not come up with anything and i have burned the CD twice, once on slowest speed. what can i do?

---

### Post by randy78 on 2008-10-30
> **Sequences said:**
> I get goofy errors

Buffer I/O error on device sr0, logical block ...
end request: I/O error, dev sr0, sector ...

i get tons of these and it does seem as if i can get past it. memory check does not come up with anything and i have burned the CD twice, once on slowest speed. what can i do?


Did you download the right distribution for your computer (32bit or 64bit)?

What kind of computer do you have (RAM, video card, processor, etc...)

---

### Post by Sequences on 2008-10-30
i get that when i boot from live cd
when i check cd for correctness, i get that
when i use install i get that.

my normal OS runs fine.

---

### Post by pirattrev on 2008-10-30
can you possibly boot into an alt cd? and out of curiosity which device is sr0? that could be your problem. Is it an external or sd card that's plugged into your computer?

---

### Post by randy78 on 2008-10-30
I figured that and edited my post above to reflect that... one thing I have experienced personally is that DVDs seem to be more reliable that CD images...
I've downloaded and burnt to cd several times, only to throw the cd away and re-burn to DVD, because the cd wasn't working.

If your pc can burn DVDs, try that and let us know.

---

### Post by cariboo on 2008-10-30
I've getting that with every release, it prints the error out about 10-15 times and then gets on with the install, I beleive it comes from burning the cd to fast. I usually burn at 12X, I plan on burning the intrepid final at 4X to see if that makes a difference.

Jim

---

### Post by Sequences on 2008-10-30
it seems as if burning it onto a dvd worked. when i burned the cd, it was at 4x, but still didnt work.. why is this so?

---

### Post by randy78 on 2008-10-30
No clue... I'd like to know myself!

---

### Post by MeanEYE on 2008-10-31
Confirmed here too. I've tried burning to a CD and got this error. With DVD, smooth as silk. :)

---

### Post by combuster on 2008-10-31
I'll tell u why! Its because of a new kernel module for pata drives, it turns out that since 2.6.25-16 a new pata driver was released and it gives a lot of trouble to everyone regardless of mainboard chipset used. If anybody reads this from ubuntu developement team since hardy i can't successfully burn data cd regardless of application i use (brasero, gnomebaker), it burns the cd but cant mount it later and booting from burned instalation iso's cause initramfs bysybox error for live desktop and i/o error for alternate installation cd's (iso's are downloaded from official torrent so md5 is ok). Here is dmesg and lspci:

```

[    5.081347] Driver 'sr' needs updating - please use bus_type methods
[    5.112724] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda caddy
[    5.119174] sr 3:0:0:0: Attached scsi CD-ROM sr0

```

```

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

```

I forgot to mention, since i couldn't burn the installation cd from hardy i remembered that i had a puppy linux on usb drive somewhere and i've booted it and burned the iso from puppy which is on 2.6.25-16 kernel and all went ok, cd was successfully burned and md5 was checked it was ok, and then i chose check cd for defects upon reboot and it all went ok. Installation went smoothly. I still can not burn cd's without errors on intrepid. HELP DEV's !

---

