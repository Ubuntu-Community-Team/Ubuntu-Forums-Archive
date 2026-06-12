---
title: "mini inspiron dell 1012   ,,,,,,,, ubuntu 11.1"
date: 2011-12-25
forum: New to Ubuntu
---

### Post by Ax3 on 2011-12-25
when i look to system information  , i found that  graphic card  unknown . I'm still  searching for driver but useless  , so any one can help plz

dell inspiron mini 1012  ___> ubuntu 11.1

graphic card  integrated intel

---

### Post by BC59 on 2011-12-25
Check here:
[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by waynefoutz on 2011-12-25
there are no third party drivers for intel video cards. If you are seeing a graphical user interface, you're done.

---

### Post by Ax3 on 2011-12-26
thank u  ,,,,,,,,,,,,,,,,,,, but there is no drivers in this link for dell the graphic card

---

### Post by BC59 on 2011-12-26
@waynefoutz replied that there are no special graphic drivers for Intel cards. The page I posted is about Ubuntu integration problems. Looks like there is no Graphics card issue.

---

### Post by mikewhatever on 2011-12-26
There were several models of Dell mini 12 with different hardware inside. For example, the first model was released with the infamous GMA500 chip, for which Intel does not provide decent driver support. Can you post the output of **lspci** to verify what you have.

PS: AFYI, Ubuntu 11.1 doesn't exist.

---

### Post by Ax3 on 2011-12-26
ok dell inspiron mini 1012
atom N450
display 10.1 wid screen WsvGA withe true - life
graphic integrated intel

M11A45CH91D72KSA
Metra 
   
hany@hany-Inspiron-1012:~$ lspci 
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
07:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

thank u for ur help ^_^

---

### Post by mikewhatever on 2011-12-26
So, you have an N450, which is usually coupled with GMA3150. As you can see in the output, it's not unknown, it uses an open source driver from Intel and should work out of the box with any contemporary Linux distro. Can you explain why you've been searching for the driver?

---

### Post by Ax3 on 2011-12-26
when i look to system information  .  i saw this

 Graphics (unknown)

---

### Post by mikewhatever on 2011-12-26
Well, perhaps the system information doesn't know how to fetch the info. How about the output of 
**sudo lshw -C display** ?
Are there other reasons?

---

### Post by Ax3 on 2012-01-02
> **mikewhatever said:**
> Well, perhaps the system information doesn't know how to fetch the info. How about the output of 
**sudo lshw -C display** ?
Are there other reasons?


*-display:0             
       description: VGA compatible controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f0200000-f027ffff ioport:18d0(size=8) memory:d0000000-dfffffff memory:f0000000-f00fffff
  *-display:1 UNCLAIMED
       description: Display controller
       product: N10 Family Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:f0280000-f02fffff

---

### Post by treyberry on 2012-02-26
Hello, I am trying to install ubuntu 11.10 to my daughter's dell 1012 netbook. I am having issues getting the wireless to work. Just wondering if this is the right version for this netbook?

---

