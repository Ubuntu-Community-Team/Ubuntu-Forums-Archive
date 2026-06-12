---
title: "fresh installed latest version of ubuntu (14.04) very slow"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Dusan_Malic on 2014-05-21
I have just installed 14.04 Ubuntu on my laptop as second OS ( I have windows 8.1 installed on one disk and now Ubuntu on another). After installation Ubuntu is really slow, opening apps (mozila for example) takes 5-6 sec, in mozilla cant load video on youtube, ordinary google search also take too much...  Speed of internet is 100/80 mbps. 
So to cut long story short in Windows I got 10 times better performances. I have i7 and 8gb of RAM.
I know this what I am writing is all in general but did anyone have similar problems like me?

---

### Post by Harsh_Parikh on 2014-05-21
Did you use wubi for installing 14.04...??if not you should download wubi.exe file from google and then install 14.04....but if you don't want to do it...use gparted to dual boot with win8.1.....

---

### Post by LastDino on 2014-05-21
Do not use Wubi as it has been discontinued, with your specs you could run any Linux distro out there better than that. I'm not sure about the problem itself, but can you check few things like info on your video card, what kind of disk you used to install ubuntu on and how did you install ubuntu on it etc etc.
I'm sure someone more knowledgeable will come with more technical input by the time you post that.

---

### Post by coffeecat on 2014-05-21
> **Harsh_Parikh said:**
> if not you should download wubi.exe file from google and then install 14.04

The OP is using Windows 8.1. Wubi does not work with Windows 8 and UEFI.

---

### Post by Dusan_Malic on 2014-05-21
I used *Universal-USB-Installer-1.9.5.2 *and installed ubuntu via USB on my 2nd disk partition. Here are full specs

> Time of this report: 5/21/2014, 11:12:55       Machine name: DUSAN
   Operating System: Windows 8.1 Enterprise 64-bit (6.3, Build 9600) (9600.winblue_gdr.130913-2141)
           Language: English (Regional Setting: English)
System Manufacturer: Dell Inc.
       System Model: Inspiron 5521
               BIOS: InsydeH2O Version 03.72.24A08
          Processor: Intel(R) Core(TM) i7-3537U CPU @ 2.00GHz (4 CPUs), ~2.5GHz
             Memory: 8192MB RAM
Available OS Memory: 8068MB RAM
          Page File: 2891MB used, 6455MB available
        Windows Dir: C:\Windows
    DirectX Version: DirectX 11
DX Setup Parameters: Not found
   User DPI Setting: 132 DPI (137 percent)
 System DPI Setting: 120 DPI (125 percent)
    DWM DPI Scaling: Enabled
     DxDiag Version: 6.03.9600.16384 64bit Unicode

> Card name: Intel(R) HD Graphics 4000       Manufacturer: Intel Corporation
          Chip type: Intel(R) HD Graphics Family
           DAC type: Internal
        Device Type: Full Device
         Device Key: Enum\PCI\VEN_8086&DEV_0166&SUBSYS_05B81028&REV_09
     Display Memory: 6096 MB
   Dedicated Memory: 2063 MB
      Shared Memory: 4033 MB
       Current Mode: 1920 x 1080 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: unknown
         Monitor Id: AUO21ED
        Native Mode: 1920 x 1080(p) (60.060Hz)
        Output Type: Internal
        Driver Name: igdumdim64.dll,igd10iumd64.dll,igd10iumd64.dll,igdumdim32,igd10iumd32,igd10iumd32
Driver File Version: 10.18.0010.3379 (English)
     Driver Version: 10.18.10.3379
        DDI Version: 11
     Feature Levels: 11.0,10.1,10.0,9.3,9.2,9.1
       Driver Model: WDDM 1.2
Graphics Preemption: DMA
 Compute Preemption: Thread group
           Miracast: Not Supported
Hybrid Graphics GPU: Not Applicable
     Power P-states: Not Applicable
  Driver Attributes: Final Retail
   Driver Date/Size: 12/21/2013 10:02:46, 10591744 bytes
        WHQL Logo'd: Yes
    WHQL Date Stamp: 
  Device Identifier: {D7B78E66-4226-11CF-4777-B225B7C2C535}
          Vendor ID: 0x8086
          Device ID: 0x0166
          SubSys ID: 0x05B81028
        Revision ID: 0x0009
 Driver Strong Name: oem4.inf:5f63e5341859ec8c:iIVBM_w81:10.18.10.3379:pci\ven_8086&dev_0166
     Rank Of Driver: 00DA2001
        Video Accel: ModeMPEG2_A ModeMPEG2_C ModeWMV9_C ModeVC1_C 

I am not sure if that can help you...

I will try re-installing it now and I will get back to you when I finish

---

### Post by LastDino on 2014-05-21
Nothing is jumping out at the moment from that.
Try using different ISO, as in re-download it and make it bootable from the usb tool included in your Ubuntu OS, which you've already installed. Universal generally works, I used to use it quite often too, so I don't think it is problem relate to Universal itself, but worth a try. It is either that or ISO you downloaded itself might be corrupted.

---

### Post by Harsh_Parikh on 2014-05-22
You can get iso from here..[http://www.itsfoss.com](http://www.itsfoss.com)

---

### Post by hyperreal on 2014-05-22
> **Harsh_Parikh said:**
> You can get iso from here..[http://www.itsfoss.com](http://www.itsfoss.com)

To the OP:  Do not get the ISO file from the site above.  It's always best to download from the official source and to verify the checksum.

---

### Post by Harsh_Parikh on 2014-05-22
> **hyperreal said:**
> To the OP:  Do not get the ISO file from the site above.  It's always best to download from the official source and to verify the checksum.

This site redirects the user to the official website....but in such a manner that new one can know everything about installation guide of any distribution of ubuntu....
therefore i suggest this site....

---

### Post by mastablasta on 2014-05-22
with that config it should work fast and snappy.

hard to say what is keeping it back (where the bottleneck is). you should check the system processes and see if anything is taking the CPU.
i also think there are some intel drivers now available. generaly they are included in kernel, but if the CPU/GPU is new then installing latest version might help.

---

