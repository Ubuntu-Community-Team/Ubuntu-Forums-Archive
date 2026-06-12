---
title: "No sound on Racing P1 mini-pc"
date: 2018-03-20
forum: New to Ubuntu
---

### Post by hokroeger on 2018-03-20
Buyed a Racing P1 mini-pc, a pretty little machine, but there is no way to make the sound work. Work's only on 64 bits. Started with Linux Mint - to unstable to use. Lubuntu works fine, but there is no sound output, and internal wifi is not working too. Is there any way to make at last the sound working?

Run Setup.exe to: 
 
1. Install drivers 
2. View the documents 
3. Install software and utilities 
 
========================================================================================================================================================= 
Driver 
=================================================================================== 
 
Intel(R) HD Graphics                        Chipset\Drivers\Graphics            11/18/2015     20.19.15.4331 
Intel(R) Sideband Fabric Device                    Chipset\Drivers\MBI                05/26/2015     604.10146.2655.573 
Intel(R) Power Management IC Device                Chipset\Drivers\PMIC                09/30/2015     604.10146.2656.7129 
Intel(R) Serial IO I2C ES Controller                Chipset\Drivers\I2C                10/12/2015     604.10146.2654.7394 
Intel Serial IO GPIO Controller                    Chipset\Drivers\GPIO                07/15/2015     604.10146.2652.3930 
Intel(R) Integrated Sensor Solution                Chipset\Drivers\ISH    \HECI_ISH        11/01/2015     2.0.20.3157 
ISS Dynamic Bus Enumerator                    Chipset\Drivers\ISH    \Bus            11/08/2015     2.0.20.3159 
Intel(R) HID Event Filter                    Chipset\Drivers\ISH    \HidEventFilter        04/25/2015     604.10146.2708.64268 
Intel(R) Battery Management Device                Chipset\Drivers\BM                11/10/2015     604.10146.2444.8539 
Intel(R) Dynamic Platform and Thermal Framework            Chipset\Drivers\DPTF                07/24/2015     8.1.10900.175 
Intel(R) Trusted Execution Engine Interface            Chipset\Drivers\TXEI                06/16/2015     2.0.0.1067 
Intel(R) Serial IO UART Controller                Chipset\Drivers\UART                05/21/2015     604.10146.2653.391 
Intel(R) Serial IO SPI Controller                Chipset\Drivers\SPI                06/01/2015     604.10146.2657.947 
Intel SST Audio Device (WDM)                    Chipset\Drivers\Audio\AudioRealtek\isstrtc    08/09/2015     604.10135.2747.5232 
Realtek I2S Audio Codec                        Chipset\Drivers\Audio\AudioRealtek\rtii2sac    05/10/2016     10.0.10586.4426 
Intel(R) AVStream Camera                    Chipset\Drivers\Camera    \iacamera64        10/29/2015     21.10154.6044.496 
Intel(R) Imaging Signal Processor 2401                Chipset\Drivers\Camera    \iaisp64        10/29/2015     21.10154.6044.496 
Camera Sensor OV2680                        Chipset\Drivers\Camera    \ov2680            09/03/2015     604.10146.2443.6099 
Camera Sensor OV8858                        Chipset\Drivers\Camera    \ov8858            09/09/2015     21.10154.6023.441 
Broadcom bcmfn2 Device (WIFI)                    Chipset\Drivers\AP6255                03/31/2016     1.517.0.0 
Broadcom Serial Bus Driver over UART Bus Enumerator (BT)    Chipset\Drivers\BT    \BCM_770        03/04/2016     12.0.1.810 
NEXT Biometrics NB-2020-U                    Chipset\Drivers\NB2020                10/27/2015    11.54.38.763

---

### Post by taranrampersad on 2018-03-20
Yeah - same problem, haven't found a workaround yet [bump!] with Lubuntu 14.04.5 - I opted for this since there's presently a bug with Artful and UEFI packages that I'm not confident is fixed. ([https://phab.lubuntu.me/T4](https://phab.lubuntu.me/T4) ). 

I've fiddled, but it's just not happy with the Wifi (AP6255) and since I am not running a hard line, I need to get the Wifi running first to worry about other things. And of course the Racing P1 comes with a CD when it doesn't have a CD drive. <eyeroll>

---

### Post by hokroeger on 2018-03-21
Got you the sound working? 
Hawe you tested another distro? I tested Linux Mint mate - is unstable - freezes totally, and the same problems: no sound, no wifi (but works fine with either system whit wifi stick). So my guess is, it will neither work with Ubuntu.

---

### Post by hokroeger on 2018-03-21
I found THIS, but not tried it yet. [http://linuxiumcomau.blogspot.com/](http://linuxiumcomau.blogspot.com/)

---

