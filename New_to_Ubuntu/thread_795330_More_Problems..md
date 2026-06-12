---
title: "More Problems."
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Daagorath on 2008-05-15
ok, so Ubuntu doesnt know my wireless card is there, how do i change that, cuz the light that says my wireless is enabled is orange not blue, and it should be blue, and also, in Ubuntu, i go to System, then to Administrator, and to Drivers, and it shows my Nvidia card, and says its not active or somthing, so i go to prefrences and try to change the grapics leval and it says it was unable to change it. these things confuse me.. sorry if what i have said is unclear.

---

### Post by DMinard on 2008-05-15
well i dont know about the wireless thing but have u tried updating your NVIDA drivers?

---

### Post by Daagorath on 2008-05-15
ya, its called Nvidia gForce go 6150, i went into control panel on Vista, and when to the driver, and had it search for updates, i dunno if it helped tho, it didnt seem to.

---

### Post by sam_delta on 2008-05-15
more information please

go into application>accessories>terminal and post the output of the following command
```
lspci
```

sam

---

### Post by Daagorath on 2008-05-15
ok, if you want me to type that, im gonna have to restart my comp and get onto Ubunto, might be a min.

---

### Post by sam_delta on 2008-05-15
if you have a wired connection, would be easier if you could plug your pc into the internet with the cable and talk with us in ubuntu, its easier and faster



sam

---

### Post by Daagorath on 2008-05-15
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


well theres half of what it said, i saved it into 2 different documents and i cant get the other open, but thats it.

---

