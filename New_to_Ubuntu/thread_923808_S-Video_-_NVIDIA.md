---
title: "S-Video - NVIDIA"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by btp1095 on 2008-09-18
Hi all,

I am new to the forum and ubuntu, but love the system so far.  I am trying to connect my s-video cable from my laptop (Dell Inspiron 1420) to my LCD 32" Olevia.  I currently have Unbuntu 8.04 (hardy).  I did multipple searches to try and solve the problem on my own but nothing seemed to work.  I have an NVIDIA GeForceTM Go 8400M GS.

I need step by step instructions on how to fix this.  Please let me know if anyone can help.  Thank you!

---

### Post by overdrank on 2008-09-18
> **btp1095 said:**
> Hi all,

I am new to the forum and ubuntu, but love the system so far.  I am trying to connect my s-video cable from my laptop (Dell Inspiron 1420) to my LCD 32" Olevia.  I currently have Unbuntu 8.04 (hardy).  I did multipple searches to try and solve the problem on my own but nothing seemed to work.  I have an NVIDIA GeForceTM Go 8400M GS.

I need step by step instructions on how to fix this.  Please let me know if anyone can help.  Thank you!

Hi and welcome, if you have the nvidia driver and nvidia-settings installed then you can use the command ```
gksu nvidia-settings
``` or under system, administration, nvidia-settings and setup your external screen there.

---

### Post by btp1095 on 2008-09-18
> **overdrank said:**
> Hi and welcome, if you have the nvidia driver and nvidia-settings installed then you can use the command ```
gksu nvidia-settings
``` or under system, administration, nvidia-settings and setup your external screen there.

Thank you very much for the response.  I don't believe I have done anything in Ubuntu concerning nvidia drivers or settings.  How do I go about that? 

After that is complete do I simply enter the command you stated and I will be able to see my computer screen on my tv or is there another step?

Sorry, I am sure these are very beginner questions, but I obviously do not know much about Ubuntu.

Thank you again

---

### Post by mc4100 on 2008-09-18
> **btp1095 said:**
> I don't believe I have done anything in Ubuntu concerning nvidia drivers or settings.
I believe that was exactly what overdrank was referring to:
The way to go about changing the settings, is to look under System -> Administration -> Nvidia Settings,
where you should be able to set up another display.
If this menu entry is not there:
Open a terminal, via Applications -> Accessories, and type:
```
sudo apt-get install nvidia-settings
```
It will ask you for your password, but will not show you any feedback in "****"'s, like when you log in.

---

### Post by 73ckn797 on 2008-09-18
I have a Nvidia card but do not see a choice under administration for the video card settings, specifically.

EDIT:
OPPS!! the laptop does not use Nvidia, my desktop does so I will look into that there.

---

### Post by overdrank on 2008-09-18
Hi and as mc4100 stated you may have to install nvidia-settings. To the OP if you have not installed the nvidia drivers then you may look under system administration, hardware drivers.

---

### Post by 73ckn797 on 2008-09-18
> **mc4100 said:**
> I believe that was exactly what overdrank was referring to:
The way to go about changing the settings, is to look under System -> Administration -> Nvidia Settings,
where you should be able to set up another display.
If this menu entry is not there:
Open a terminal, via Applications -> Accessories, and type:
```
sudo apt-get install nvidia-settings
```It will ask you for your password, but will not show you any feedback in "****"'s, like when you log in.


Thanks, I was wanting to be able to have the video control that this gives.

---

### Post by btp1095 on 2008-09-18
> **overdrank said:**
> Hi and as mc4100 stated you may have to install nvidia-settings. To the OP if you have not installed the nvidia drivers then you may look under system administration, hardware drivers.

Ok great I did that and then when I went to System > Administration > NVIDIA X Server Settings I get the following message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

So I thought the next step would be to enter nvidia-xconfig in the terminal...but after I did that I got the following:

The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>

So what's next?

Thank you all for your help!

---

### Post by overdrank on 2008-09-18
> **btp1095 said:**
> Ok great I did that and then when I went to System > Administration > NVIDIA X Server Settings I get the following message:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

So I thought the next step would be to enter nvidia-xconfig in the terminal...but after I did that I got the following:

The program 'nvidia-xconfig' can be found in the following packages:
 * nvidia-xconfig
 * nvidia-glx
 * nvidia-glx-new
Try: sudo apt-get install <selected package>

So what's next?

Thank you all for your help!

Ok have you installed the nvidia drivers from system, administration, hardware drivers? If not please do so then you should be able to use the nvidia-settings.

---

### Post by btp1095 on 2008-09-18
> **overdrank said:**
> Ok have you installed the nvidia drivers from system, administration, hardware drivers? If not please do so then you should be able to use the nvidia-settings.

Ok I went to system, administration, hardware drivers and got this (see attachment)

Does that mean Ubuntu is not detecting my NVIDIA card?

---

### Post by overdrank on 2008-09-18
> **btp1095 said:**
> Ok I went to system, administration, hardware drivers and got this (see attachment)

Does that mean Ubuntu is not detecting my NVIDIA card?

Hi and yes it appears so. How did you install ubuntu? Did you use the live cd or another method?
Could you post the output of the command ```
lspci
``` in the terminal located under applications, accessories. You can copy and paste the command to the terminal and the same on the output of the command.

---

### Post by btp1095 on 2008-09-18
> **overdrank said:**
> Hi and yes it appears so. How did you install ubuntu? Did you use the live cd or another method?
Could you post the output of the command ```
lspci
``` in the terminal located under applications, accessories. You can copy and paste the command to the terminal and the same on the output of the command.

I installed via a live cd.  Below is the result of the command lspci:

ward@ward-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by mc4100 on 2008-09-18
> **btp1095 said:**
> I installed via a live cd.  Below is the result of the command lspci:

ward@ward-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)

Well, that was unexpected ...

---

### Post by jbrown96 on 2008-09-18
> 00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) It does not appear as though you have a Nvidia graphics card in your system. Do you have onboard and discrete cards?? Is your monitor connected to the onboard card?

---

### Post by mc4100 on 2008-09-18
> **jbrown96 said:**
> It does not appear as though you have a Nvidia graphics card in your system. Do you have onboard and discrete cards?? Is your monitor connected to the onboard card?
Just googled the Inspiron 1420, and it appears they're sold with Intel GMA, which would confirm the lspci:
[http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420](http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420)

Edit: Hmmm, they *can* be upgraded to theNVIDIA GeForceTM Go 8400M GS

---

### Post by overdrank on 2008-09-18
> **btp1095 said:**
> I installed via a live cd.  Below is the result of the command lspci:
```

ward@ward-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
```

As stated by others you do not show the nvidia graphics card so you have the intel graphics. You may try the command ```
gksu displayconfig-gtk
``` and setup your external monitor there. I have not used the intel graphics with dual monitors but other have.

---

### Post by btp1095 on 2008-09-18
Ok so if I don't have an NVIDIA card but instead an Intel GMA, what do I have to do in order to use my S-Video cable properly?

Thanks everyone

---

### Post by btp1095 on 2008-09-18
> **overdrank said:**
> As stated by others you do not show the nvidia graphics card so you have the intel graphics. You may try the command ```
gksu displayconfig-gtk
``` and setup your external monitor there. I have not used the intel graphics with dual monitors but other have.

Ok I tried that command and got the following:

ward@ward-laptop:~$ gksu displayconfig-gtk
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 189, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 394, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 404, in _finalizeInit
    gfxcard._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1123, in _finalizeInit
    screen._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1588, in _finalizeInit
    (cw,ch,x,x) = self.x_live_screen.getSize()
  File "/var/lib/python-support/python2.5/xf86misc.py", line 77, in getSize
    return self.sizes[self.currentsizeid]
IndexError: list index out of range

---

### Post by mc4100 on 2008-09-18
> **btp1095 said:**
> Ok so if I don't have an NVIDIA card but instead an Intel GMA, what do I have to do in order to use my S-Video cable properly?

Thanks everyone
BTW, do you have a function key on the keyboard that enables S-Video out (Fn+F3 for example)?
If so, what happens when you press it?

---

### Post by btp1095 on 2008-09-18
> **mc4100 said:**
> BTW, do you have a function key on the keyboard that enables S-Video out (Fn+F3 for example)?
If so, what happens when you press it?

Yea I tried Fn+F8 and that didn't do a thing

---

### Post by btp1095 on 2008-09-20
bump..

Does anyone think they can help?

Thanks again

---

