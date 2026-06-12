---
title: "Guide EMU1212m in (k)ubuntu 9.10"
date: 2009-11-01
forum: Outdated Tutorials &amp; Tips
---

### Post by CyberRat on 2009-11-01
EMU 1212m in 9.10

Card does work but it is missing a firmware file after a clean in stall.

```

[    8.550442] EMU10K1_Audigy 0000:05:01.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    8.550520] emu1010: Special config.
[    8.550608] emu1010: EMU_HANA_ID = 0x3f
[    8.550609] emu1010: filename emu/emu1010b.fw testing
[    8.550612] EMU10K1_Audigy 0000:05:01.0: firmware: requesting emu/emu1010b.fw

[    8.873483] firmware: emu/emu1010b.fw not found. Err = -2
[    8.873486] emu1010: Loading Firmware file emu/emu1010b.fw failed
[    8.874115] EMU10K1_Audigy 0000:05:01.0: PCI INT A disabled
[    8.874147] EMU10K1_Audigy: probe of 0000:05:01.0 failed with error -2

```Thats simple to solve:

```
cd ~
mkdir Download
cd Download
sudo apt-get install build-essential

```Ubuntu 9.10 uses version 1.0.20 of Alsa, we just need to add the firmware package.

```

wget ftp://ftp.alsa-project.org/pub/firmware/alsa-firmware-1.0.20.tar.bz2
tar -xfv alsa-firmware-1.0.20.tar.bz2
cd alsa-firmware-1.0.20
./configure --with-cards=emu10k1
make
sudo make install
sudo reboot

```Open up the Alsa Mixing tool (alsamixer). 
Tune the volumes to your liking, and keep moving to the right with the arrow keys, until you reach Internal Rate Clock.
[s]Change that from 48000 to 44100.[/s]

If you wish to contribute to this guide, please do so.

edit:
On my PC I set the internal clock back to 48000 to keep whole system consequent due to how pulse manage my card in combination with Audacity.

To enable inputs in alsamixer, select the Capture settings with TAB (see Capture highlight at top left of your screen). Here I routed DSP 0 to 0202 ADC left, and DSP 1 to 0202 ADC right. Then scroll all the way to the right and slide the EMU volume all the way up (or as far it sounds best for you)

---

### Post by cpolymeris on 2010-08-29
Hello,
After thinking for years about it I finally started writing a  mixer app for the Emu 1212m, try it out here:
[http://emutrix.googlecode.com]("http://emutrix.googlecode.com/")

I appreciate feedback/bug reports or any other comment.

---

