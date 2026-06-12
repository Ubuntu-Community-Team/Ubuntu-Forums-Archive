---
title: "[SOLVED] Compiz- PC almost stopped-"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by Dutch70 on 2008-06-12
Hi, First of all I am very new to Linux, just got it set up.  I added too many settings, and it just about stopped my PC.

All I could find is this...(metacity --replace) to disable it, But would like a fresh start on the settings, should I uninstall and reinstall using synaptic or what? Please advise of any other possibility's.  

Just in case...output of lspci...Thanx

```
david@david-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:04.0 Communication controller: Conexant HSF 56k Data/Fax Modem
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
david@david-desktop:~$ 

```

---

### Post by sam_delta on 2008-06-12
go into system>preferences>advanced desktop effects settings, and then click on "preferences" located on the bottom-left, just above the 'close' button, and then under the 'profile' section, click 'reset to defaults'

sam

---

### Post by Dutch70 on 2008-06-12
Thanks Sam, knew I could count on you.:)


 After resetting defaults and enabling it again I got this message, and I dont know what it means or how to remove that value. (at the bottom), but I'm thinking that may have caused the problem in the first place. that would be nice info to have. Thanks again! 

```
david@david-desktop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


```

---

### Post by sam_delta on 2008-06-12
i duno exacly whats that config value, but it looks as if its not an error, just a warning, 

is compiz working right now, even with that warning, or it will just stop the operatioin and wont enable compiz?

also, try enabling compiz by going into system>preferences>appearence , then click on the 'visual effects' tab and select 'normal' or 'extra effects', see if you get any type of warning/error poping up in a new window, if nothing pops up, you should be good.


sam

---

### Post by Dutch70 on 2008-06-12
Seems to be working wonderfully. I enabled the cube and rotate. Also selected "extra effects" to push it a little and it seems to be good. No warnings or anything. 

 So, I'll just take it slow when adding things, and see where that leads. At least I know how to get it straightened out now.:biggrin:
 

 So thanks again Sam!

 I hope one day I can make a difference in this community too!

---

### Post by sam_delta on 2008-06-12
no problem man, and im sure you will make a difference, and itll be anytime soon.

thats a good thing to do, go slow on the effects, and keep track on which effects actually eat up your memory and keep them turned off.

good luck bro, enjoy ubuntu, :)
ill be around 
sam

---

