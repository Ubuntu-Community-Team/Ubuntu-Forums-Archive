---
title: "Report - AMD Trinity APU and ubuntu"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by paker on 2013-01-01
When I was buying parts for a new desktop, I wasn't 100% sure if AMD Trinity APU would work well in ubuntu. I am reporting it is.

A10-5800K 100W 
MSI FM2-A75MA-E35 microATX board
Samsung PC1600 30nm low voltage, 2x4GB @ 2133
ubuntu 12.10 64 bit
analog monitor connected to D-sub
Samsung SCX-4623F multifunction printer

I installed 12.10 from USB thumb drive. Installation was without a glitch. One thing minor, installation didn't prompt to remove thumb drive before restart. 

I wansn't prompted to install any special driver. Ubuntu recognized the printer. 

One foot note. Stock cooler is aluminum with 70mm fan. It was noisy. I replaced it with a 120 mm cooler. Default cooler fan speed was 100% always. Adjustment in BIOS.

---

### Post by grahammechanical on 2013-01-01
Have you run System Testing? Then your information will get into official places.

[https://friendly.ubuntu.com/]("https://friendly.ubuntu.com/")

Regards.

---

### Post by nortexoid on 2013-02-23
I'm running a similar setup:

AMD A10-5800K APU
Asrock FM2A75 Pro4-M mATX motherboard
Corsair Vengeance LP 2x4GB 2133Mhz DDR3
1TB Hitachi 7200 RPM SATA
Asus PCE-N53 dual band N600 network card
Asus Bluetooth dongle
Internal flash card reader
MS Sculpt Mobile keyboard (bluetooth)

Most seems to be working fine, but suspend/sleep is problematic. Sometimes it works, most of the time it doesn't. There appears to be two sleep states, the second a deep sleep from which the computer often doesn't resume. Sometimes it will, but apparently only after I've disconnected my bluetooth keyboard. At least, I've had more success then. I'm running Kubuntu 12.10, KDE 4.10, so perhaps the problem doesn't arise in Ubuntu. I'd be surprised.

I almost forgot to mention that HDMI audio also doesn't work after resuming from suspend. (Video is fine though.)

On the stock cooler: I have one 120mm intake, the PSU fan, and the stock cooler/fan all set to their lowest RPM setting. It's very quiet. It idles at 27C, normal working conditions are at 33C, and loading it is from 42-50+C. I have my fans set to spin up once it hits 45C. Works great, though I wouldn't overclock much with it. (It is loud at full speed.)

---

