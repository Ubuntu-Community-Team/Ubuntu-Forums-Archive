---
title: "ubuntu 8.04 - bluetooth"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by moftah on 2008-07-23
dears,
i am still beginner of ubuntu , i have labtop LG R400 with vista installed.

i moved to ubuntu 8.04 (dual boot)  i disable my wireless network and bluetooth from inside
vista by pressing FN+F6( wireless and bluetooth key)

when i am inside ubuntu i can not access wireless or bluetooth ( i pressed FN+F6) and installed all pakages related to bluetooth and changes as per

[http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu](http://www.linuxquestions.org/linux/answers/Hardware/Bluetooth_Transferring_and_receiving_files_under_Ubuntu)

but still i can not initiate wireless network card or bluetooth.


your help is appriciated

thanx

---

### Post by Joeb454 on 2008-07-23
Can you open a terminal from Applications &#8594; Accessories &#8594; Terminal and post the output of ```
lscpi
```

---

### Post by moftah on 2008-07-23
> **Joeb454 said:**
> Can you open a terminal from Applications &#8594; Accessories &#8594; Terminal and post the output of ```
lscpi
```

thank you the following are my output

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon X2300
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 15)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

### Post by Joeb454 on 2008-07-23
Hmm, so Ubuntu does recognise your Wireless card is there (it's at the bottom of the output).

Is there some hardware switch for turning it on and off?

Also try enabling it in Windows, then rebooting into Ubuntu (I doubt it's related, but worth a try)

---

### Post by moftah on 2008-07-24
> **Joeb454 said:**
> Hmm, so Ubuntu does recognise your Wireless card is there (it's at the bottom of the output).

Is there some hardware switch for turning it on and off?

Also try enabling it in Windows, then rebooting into Ubuntu (I doubt it's related, but worth a try)


thank you for follow up.

yes it is now initiate and can discover oter bluetooth after i logged in windows and pressed Fn+F6  (combintion key to activate wireless and bluetooth at my keyboard)


but if i don't have windows how i can initiate this hardware part or other specially this is soft key and not button at side of computer.


thank you.


note: when i try to reply using Firefox from inside Ubuntu i recive message to down load or open file  how to solve this since now i reply from windos..

---

### Post by Joeb454 on 2008-07-24
Do you use the big new reply button or the little reply button (the big one is on the left)

---

### Post by moftah on 2008-07-24
> **Joeb454 said:**
> Do you use the big new reply button or the little reply button (the big one is on the left)


i used (quote) button under your reply and then pressed  Submit Reply
as now

---

