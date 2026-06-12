---
title: "Problems after installing Nvidia FX5500"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by iamaperson on 2008-11-15
I installed a new graphics card into my computer and now when I boot with the card installed I get a text login and then it stays in text. When I take the graphics card out and boot using the on board graphics card it starts no problem.  I am a beginner with linux so have no idea what is going on. I have tried typing startx and it then tells me no screens. I searched this and tried a couple things and it has gotten me nowhere. I am hoping that someone can help me.

---

### Post by Mardoct909 on 2008-11-15
Did *you* put it in, or some guy at a store? If you did it, did you ensure you were grounded?

---

### Post by taurus on 2008-11-15
Try reconfiguring your X server again with

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by iamaperson on 2008-11-15
Yes I put it in. And I am a beginner with linux but not computers. I made sure I was grounded. The problem is not the card since my computer is a dual boot and the card works no problem on windows.

---

### Post by Elfy on 2008-11-15
You could also try the xfix from the recovery menu - boot from the recovery mode to reach the small menu - choose xfix - then resume from the same menu.

Not sure of the state of play with that card currently but there have been a few problems I think.

---

### Post by iamaperson on 2008-11-15
I tried your advice. Neither of the two suggestions helped. The screen it gives me is still a text login and after I login it stays text so I typed startx and it says
 (==) Using config file: "/etc/X11/xorg.conf"
Primary device is not PCI 
(EE) NO devices detected.

Fatal server error:
no screens found
giving up.
xinit: connection refused (errno 111): unable to connect to x server
xinit: NO such process (errno 3) Server error. 

Any suggestions?

---

### Post by taurus on 2008-11-15
Make sure you go into the BIOS and disable the onboard graphic card.  Then, boot into Ubuntu and run those commands again.  If it still doesn't work, no X, then post the output of this command from a prompt.

```
lspci
```

---

### Post by iamaperson on 2008-11-15
So now all I get is a blank screen after I try to boot. It gives me the ubuntu start goes about 1/8 of the way and then gives me a blank screen. :/ hmmmmmm. Is it a problem with the config file?

---

### Post by taurus on 2008-11-15
It's probably using the wrong video driver (onboard graphic card) for your new nVidia card.  Can you boot into recovery mode?

---

### Post by iamaperson on 2008-11-15
When I try to boot into recovery on the new graphics card it seems to hang up. But if I change me video card to the onboard with my card in the computer I can. I am not sure if that will help but maybe.

---

### Post by iamaperson on 2008-11-16
bump

---

### Post by Elfy on 2008-11-16
taurus asked for the result of lspci - can we have that please. You could also check that xorh is using the basic driver - boot the recovery mode - when you reach the menu choose root prompt - be very careful now.

Run these commands

```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.1605
```

Now open file to edit - using nano - Ctrl+O, Enter, Ctrl+X to save and exit

```
nano /etc/X11/xorg.conf
```

Use arrow keys - look for wher it _might_ say nvidia against Driver similar to 

> Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"

If you find such change to vesa, save and close - then 

```
reboot
```

If you don't know how or are worried - boot the livecd and post the result of

```
sudo fdisk -l
lspci
```

---

### Post by iamaperson on 2008-11-16
sorry I forgot to post the results of lspci.

00:1d.1 USB Controller: Intel Corporation 92901FB/FBM/FR/FRW (ICH6 Family) USB UHCI #2 (rev 03)


00:1d.2 USB Controller: Intel Corporation 92901FB/FBM/FR/FRW (ICH6 Family) USB UHCI #3 (rev 03)


00:1d.3 USB Controller: Intel Corporation 92901FB/FBM/FR/FRW (ICH6 Family) USB UHCI #4 (rev 03)


00:1d.7 USB Controller: Intel Corporation 92901FB/FBM/FR/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82081 PCI Bridge (rev d3)

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (Rev 03)

00:1f.2 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)

00:1f.2 IDE interface: INtel Corporation 82801FB/FW (ICH6/ICH6W) SATA COntroller (rev 03)

00:1f.3 SMBus: INtel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE1394 OHCI Link Layer Controller (rev 80)

02.02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139 C+ (rev 10)

02:04.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1)

02:05.0 Communication controller: Agere Systems V.92 56k WinModem (rev 03)

---

### Post by Elfy on 2008-11-16
mmm - yes - so have you done any of the above or not?

---

