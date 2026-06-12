---
title: "Toshiba Sattelite Sound"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by Colin82 on 2008-05-31
I have a Toshiba Sattelite A135-S2247.  I am a total Linux/Ubuntu noob, so please bear with me.  I installed Hardy today, and everything worked beautifully right after install except the sound.  This problem is 2 fold:

1. I have to have all the sound almost all the way up to hear anything.  

2. When I connect headphones to the headphone jack, nothing happens.  The internal speakers don't mute, and no sound is output via the headphones.

I tried the reccomendations in this thread, short of compiling the driver.  Currently I do not have the ability to connect this computer to the inernet.  If I don't have it figured out in the next month, then I'll try to compile the driver and see if that fixes it.  Didn't know if anyone with this model laptop had any insight that could help me.

Other than these problems, I'm very happy with Hardy.  Much faster than Vista, and a nice, clean, simple layout.

Thank you in advance for any suggestions.

---

### Post by Colin82 on 2008-06-02
After doing some digging, and some trial and error, these are the solutions I have tried, and the results:

In the /etc/modprobe.d/alsa-base I have tried adding these lines

1. options snd-hda-intel model=lenova
   No change

2. options snd-hda-intel model=toshiba
   No change

3. options snd-hda-intel model=auto
   This allowed sound to be output via the headphones and added a "Switches" tab to the volume control where I could check/uncheck headphones.  However it did not mute the laptop speakers when I plugged in headphones.  Also when I would use the volume wheel on the front of the laptop, it would mute the front channel speakers (laptop speakers).

4. options snd-hda-intel model=3stack
   Same results as using model=auto

5. options snd-hda-intel model=laptop-micsense
   No change

The output of lspci in the terminal window is:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
06:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
06:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
06:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
06:04.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller

Sorry for such a long post, but I wanted to include as much info as I could so hopefully someone can help me.  Thank you.

---

### Post by coolacid217 on 2008-09-09
I have exactly the same problem (and the same soundcard)... is there any solution already?:confused::confused::confused:

---

### Post by sdcope on 2008-10-06
This is exactly the same thing I'm dealing with.  I've been through multiple setups I've found in the forum.  I've reinstall Alsa and OSS from source, and edited alsa-base more times then I care to count.  I'm getting crazy frustrated...

---

### Post by PRDS on 2008-10-31
How I got my headphones working on my Toshiba A135-S4527 notebook:

First, type the following command into the terminal:

gksudo gedit /etc/modprobe.d/alsa-bas

On the very bottom, add the following line.

options snd-hda-intel position_fix=1 model=lenovo

Reboot! Done!

This not only enabled my headphones, but made it so when I plug in my headphones, the computer speakers stop.

Hope it works!

---

