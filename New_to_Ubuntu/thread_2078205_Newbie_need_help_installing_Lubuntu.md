---
title: "Newbie need help installing Lubuntu"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by solanoa27 on 2012-10-30
Hi guys,

First of all, I´m a newbie.   Installed Lubuntu 12.10 but when i try to boot i get a system prompt and that´s all.  My computer configuration is:

Operating System: Windows 7 Starter 32-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.120830-0333)
           Language: Spanish (Regional Setting: Spanish)
System Manufacturer: SAMSUNG ELECTRONICS CO., LTD.
       System Model: N102SP/N100SP/N101SP
               BIOS: AMIBIOS Version 04QQ.M041.20120406.TXJ
          Processor: Intel(R) Atom(TM) CPU N2100   @ 1.60GHz (2 CPUs), ~1.6GHz
             Memory: 2048MB RAM
Available OS Memory: 2036MB RAM
          Page File: 1059MB used, 3012MB available
       
-----------------
Display Devices
-----------------
          Card name: Intel(R) Graphics Media Accelerator 3600 Series
       Manufacturer: Intel Corporation
          Chip type: Intel(R) GMA 3600 Series (Atom N2100)
           DAC type: Internal
         Device Key: Enum\PCI\VEN_8086&DEV_0BE1&SUBSYS_C629144D&REV_09
     Display Memory: 762 MB
   Dedicated Memory: 0 MB
      Shared Memory: 762 MB
       Current Mode: 1024 x 600 (32 bit) (60Hz)
       Monitor Name: Generic PnP Monitor
      Monitor Model: unknown
       
------------------
Sound Devices
------------------
            Description: Speakers (Realtek High Definition Audio)
 Default Sound Playback: Yes
 Default Voice Playback: Yes
            Hardware ID: HDAUDIO\FUNC_01&VEN_10EC&DEV_0269&SUBSYS_144DC629&REV_1002
        Manufacturer ID: 1
             Product ID: 100
                   Type: WDM
            Driver Name: RTKVHDA.sys
         Driver Version: 6.00.0001.6499 (English)
     
Please help!

---

### Post by NikTh on 2012-10-30
Hi , 
Welcome !! 

How you installed Lubuntu? via wubi (from within Windows) or regular dual-boot ? 

What guide you followed ? 

Thanks

---

### Post by solanoa27 on 2012-10-30
I installed as regular dual boot using a usb flash memory.  In download the iso and used LILI USB CREATOR.  Then boot from usb and followed the instructions.

---

### Post by NikTh on 2012-10-30
> **solanoa27 said:**
> I installed as regular dual boot using a usb flash memory.  In download the iso and used LILI USB CREATOR.  Then boot from usb and followed the instructions.

OK. So maybe this is a Intel GMA problem. 

Try something , when you see this prompt press CTRL+ALT+F2 and login from there, can you? 

IF yes , then give these 2 commands 

```
sudo service lightdm stop 
sudo service lightdm start
``` 

Is the login screen comes out ? 

Thanks

---

### Post by ciphoenix on 2012-10-30
No message displayed?

---

### Post by solanoa27 on 2012-10-30
> **NikTh said:**
> OK. So maybe this is a Intel GMA problem. 

Try something , when you see this prompt press CTRL+ALT+F2 and login from there, can you? 

IF yes , then give these 2 commands 

```
sudo service lightdm stop 
sudo service lightdm start
```Is the login screen comes out ? 

Thanks

After the first command the response is "Stop: uknown instance"

after the second command its showing like a list and stop in "stopping save udev log and update rules"

---

### Post by NikTh on 2012-10-30
Unfortunately the problem is located at the graphics card. Intel GMA 3600. 

I just found this thread 
[http://ubuntuforums.org/showthread.php?t=1953734&page=8](http://ubuntuforums.org/showthread.php?t=1953734&page=8)

I don't know how to help but see the last post from @bodhi.zazen, it may help you. 

Thanks

---

### Post by amjjawad on 2012-10-30
Hello and Welcome to Ubuntu Forum :)

Thanks for choosing and using Lubuntu and I'm sorry to know you are having some issues but I'm here to help and will do my best. I'm one of Lubuntu Team Members. 

Let's make this as simple as possible.

Before you have installed Lubuntu 12.10 32bit on your machine, have you tried to test it without installation from the LiveUSB? if you haven't done that, could you please do it now?

This will not touch your installation and will do absolutely nothing to your machine.

If there is something wrong with 12.10, sometimes, using an older/previous release is not bad idea and yes, I'm referring to 12.04 but let's see what will happen.

If the problem is indeed with the Graphics Card/Driver, then that is different story.


Edit:
Ok, I have checked this: [http://ubuntuforums.org/showthread.php?t=1953734&page=15](http://ubuntuforums.org/showthread.php?t=1953734&page=15)

I second what the other poster suggested. [Please check and see if you can run Linux on your machine]("http://ubuntuforums.org/showpost.php?p=12060642&postcount=147").

---

