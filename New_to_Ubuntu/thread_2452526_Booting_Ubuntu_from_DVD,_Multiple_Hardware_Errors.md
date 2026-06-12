---
title: "Booting Ubuntu from DVD, Multiple Hardware Errors"
date: 2020-10-23
forum: New to Ubuntu
---

### Post by kuhnie on 2020-10-23
0.162497] mce: [Hardware Error] : CPU O: Machine Check: 0 Bank 5: ae00000000

40110a

0.162501] mce: [Hardware Error]: TSC O ADDR fef87340 MISC 178a0000086 [ 0.162505) mce: [Hardware Error]: PROCESSOR 0:306c3 TIME 1603475051 SOCKET O

[

APIC O microcode 28

[ 0.515139] Initramfs unpacking failed: Decoding failed 1.061360] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 022554

[

[

IBUS)

1.066179] ACPI BIOS Error (bug): Could not resolve symbol [_SB.PCIO.GFX0.D D02. BCL], AE_NOT FOUND (20190816/psargs-330)

[ 1.066189) ACPI Error: Aborting method \_SB.PCIO.PEGO.PEGP.DDO2. BCL due to

previous error (AE_NOT_FOUND) (20190816/psparse-529) [ 1.072342] nouveau 0000:01:00.0: bus: MMIO read of 00000000 FAULT at 10ac08 [ IBUS ]


Could only take a picture. Logs from google lens

---

### Post by kuhnie on 2020-10-23
[https://photos.google.com/share/AF1QipM6h3fUNeBF3EmAj6nJ-aqVFFhQQcPVQ9WeHK0rPe__Lh6Hwyi6sPMvmMOPF81VPQ?key=UTVHQVlvMTVMTFVtRTQtcUVGT0t1ZTVYLTVmUjRB](https://photos.google.com/share/AF1QipM6h3fUNeBF3EmAj6nJ-aqVFFhQQcPVQ9WeHK0rPe__Lh6Hwyi6sPMvmMOPF81VPQ?key=UTVHQVlvMTVMTFVtRTQtcUVGT0t1ZTVYLTVmUjRB)

---

### Post by grahammechanical on 2020-10-23
If you tell me the hardware you are trying to run the Ubuntu live session on I will tell you the answer. No. I am joking. I have no idea what is causing this.

But we do need to know the version of Ubuntu and the hardware of your machine. And that will be just the start of the information we need.

Regards

---

### Post by Enigma12 on 2020-10-24
Also, are you certain that you have a good download? Did you validate the md5sum? I found I get more reliable downloads with Transmission than just a regular download. And, since I haven't done a new installation for a while, but I have looked at other distros recently, I know that at least some check the install media for every file being correct before it actually starts the live test. If that testing starts when booting, let it run, and you'll find out if what you have is correct.

---

### Post by ActionParsnip on 2020-10-24
Verify download and make sure you have the latest BIOS

---

