---
title: "Graphics Card &amp; Drivers"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by Shadius on 2012-04-14
Hello all,
I'm a new Ubuntu Linux user and I'm trying to do a these things:

1) I'd like to check what graphics card I have because there's no name on the card itself other than ATI.

2) If I have the latest drivers for it, and if not, how to go about updating my graphics card's drivers. 

Any help is appreciated!

---

### Post by grahammechanical on 2012-04-14
To sort out the second question

Open the Dash and search for Additional Drivers. Launch that utility. It may offer you a proprietary driver for you machine. You need to be connected to the Internet, then when you click Activate the driver will be downloaded and installed.

If it (or when it) says that the driver is already activated, then open the Dash and search for ATI, you should get access to an ATI video card Settings utility. Launch that and see what information it gives you about the card.

Regards.

---

### Post by anewguy on 2012-04-14
Or click on system settings on the menu (looks like a gear with a wrench over it), then click system info.  It should show your video card there.

Dave ;)

---

### Post by 23dornot23d on 2012-04-14
Also if you do this in a console or teminal ..... and post back the results ....
[B]
lspci -v | grep VGA[/B]

This should show the graphic card installed in the computer.

---

### Post by Shadius on 2012-04-14
> **grahammechanical said:**
> To sort out the second question

Open the Dash and search for Additional Drivers. Launch that utility. It may offer you a proprietary driver for you machine. You need to be connected to the Internet, then when you click Activate the driver will be downloaded and installed.

If it (or when it) says that the driver is already activated, then open the Dash and search for ATI, you should get access to an ATI video card Settings utility. Launch that and see what information it gives you about the card.

Regards.

I launched the Additional Drivers utility and it shows nothing there. It says, "No proprietary drivers are in use on this system."

---

### Post by Shadius on 2012-04-14
> **anewguy said:**
> Or click on system settings on the menu (looks like a gear with a wrench over it), then click system info.  It should show your video card there.

Dave ;)

I opened up the System Settings and with "Overview" highlighted it shows:

"Graphics  Unknown"

And with Graphics highlighted, it shows:

"Driver  Unknown"

---

### Post by Shadius on 2012-04-14
> **23dornot23d said:**
> Also if you do this in a console or teminal ..... and post back the results ....
[B]
lspci -v | grep VGA[/B]

This should show the graphic card installed in the computer.

This is my output:

```
shadius@shadius-5410US:~$ lspci -v | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 If [Radeon 9000] (rev 01) (prog-if 00 [VGA controller])
shadius@shadius-5410US:~$ 


```

---

### Post by 23dornot23d on 2012-04-14
It is on the Ubuntu list for 11.04 ..... needs something extra for 11.10

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is part of the Quote from there .....

> 
**Require Oneric/11.10**

 These cards should work with Ubuntu Oneric/11.10: 

PALM        Radeon HD 6310/6250 BARTS       Radeon HD 6850/6870 TURKS       Radeon HD 6570/6670 CAICOS      Radeon HD 6450 CAYMAN      Radeon HD 6950/6970/6990Full list is in the  [Oneric radeon man page.]("http://manpages.ubuntu.com/manpages/oneiric/man4/radeon.4.html") 
 
**Require Natty/11.04 and Modesetting Only**

 [COLOR=Red]**These  cards should work with Ubuntu Natty/11.04, however you will need a more  recent version of Mesa (7.11.x) than Natty's default (7.10.x) to get 3D  acceleration. **[/COLOR]

PALM        RadeonHD 6310/6250 TURKS       RadeonHD 6570/6670 CAICOS      RadeonHD 6450 
**Accelerated 3D support**

 All these Radeon(HD) cards and derivatives have good 3D acceleration support 

R100                        Radeon 7200 RV100                       Radeon 7000(VE), M6, RN50/ES1000 RS100                       Radeon IGP320(M) RV200                       Radeon 7500, M7, FireGL 7800 RS200                       Radeon IGP330(M)/IGP340(M) RS250                       Radeon Mobility 7000 IGP R200                        Radeon 8500, 9100, FireGL 8800/8700 [COLOR=Red]**RV250                       Radeon 9000PRO/9000, M9**[/COLOR] RV280                       Radeon 9200PRO/9200/9200SE/9250, M9+ RS300                       Radeon 9100 IGP RS350                       Radeon 9200 IGP RS400/RS480                 Radeon XPRESS 200(M)/1100 IGP R300                        Radeon 9700PRO/9700/9500PRO/9500/9600TX, FireGL X1/Z1 R350                        Radeon 9800PRO/9800SE/9800, FireGL X2 R360                        Radeon 9800XT RV350                       Radeon 9600PRO/9600SE/9600/9550, M10/M11, FireGL T2 RV360                       Radeon 9600XT RV370                       Radeon X300, M22 RV380                       Radeon X600, M24 RV410                       Radeon X700, M26 PCIE R420                        Radeon X800 AGP R423/R430                   Radeon X800, M28 PCIE R480/R481                   Radeon X850 PCIE/AGP RV505/RV515/RV516/RV550     Radeon X1300/X1400/X1500/X2300 R520                        Radeon X1800 RV530/RV560                 Radeon X1600/X1650/X1700 RV570/R580                  Radeon X1900/X1950 RS600/RS690/RS740           Radeon X1200/X1250/X2100 R600                        RadeonHD 2900 RV610/RV630                 RadeonHD 2400/2600 RV620/RV635                 RadeonHD 3450/3470 RV670                       RadeonHD 3850/3870 RS780                       RadeonHD 3100/3200/3300 RS880                       RadeonHD 4100/4200/4290 RV710                       RadeonHD 4350/4550 RV730                       RadeonHD 4650/4670 RV770                       RadeonHD 4850/4870 REDWOOD     RadeonHD 5550/5570/5670 JUNIPER     RadeonHD 5750/5770 CYPRESS     RadeonHD 5850/5870 HEMLOCK     RadeonHD 5970
do these in a terminal ..... please ..... will give someone some more information to work with - as ATI cards are not my thing though -  was just helping get more infomation to help solve the problem

**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**

 **lsb_release -a**

---

### Post by Shadius on 2012-04-14
> **23dornot23d said:**
> It is on the Ubuntu list for 11.04 ..... needs something extra for 11.10

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is part of the Quote from there .....

do these in a terminal ..... please ..... will give someone some more information to work with - as ATI cards are not my thing though -  was just helping get more infomation to help solve the problem

**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**

 **lsb_release -a**

Thank you for helping! At least, I can start to figure out what's going on here. Would you mind explaining that code to me? I'd like to be able to understand some of these codes that I'm running.

---

### Post by 23dornot23d on 2012-04-14
Sorry cannot blame you for asking 

lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'

ls pci basically means list all the pci attachments on the system ......
The rest looks to see which modules are used by the kernel .... eg

> [B]keith@keith-Aspire-7730ZG:~$ lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'
01:00.0 VGA compatible controller: NVIDIA Corporation G98 [GeForce 9300M GS] (rev a1) (prog-if 00 [VGA controller])
        Kernel driver in use: nouveau
        Kernel modules: nouveau, nvidiafb
keith@keith-Aspire-7730ZG:~$ [/B]

The other is just to see which system you are using ....

> [B]keith@keith-K53SV:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 11.04
Release:    11.04
Codename:    natty
keith@keith-K53SV:~$ [/B]

---

### Post by Shadius on 2012-04-14
Oh okay. Thank you very much for the breakdown. I just didn't want to be in the dark about what I'm running. Trying to get more familiar with the Unix-like codes (if that's the correct terminology).

---

### Post by mörgæs on 2012-04-14
Why do you want to leave the open-source driver (that is, the one installed by default)?

---

### Post by Shadius on 2012-05-01
> **mörgæs said:**
> Why do you want to leave the open-source driver (that is, the one installed by default)?

I just wanted to find out what my card was and if I had the right drivers for it, and if the card can run Ubuntu 3D. That's my goal.

---

### Post by NikTh on 2012-05-01
> **Shadius said:**
> I just wanted to find out what my card was and if I had the right drivers for it, and if the card can run Ubuntu 3D. That's my goal.
You can check it out by running this test in unity 3D environment*
```

/usr/lib/nux/unity_support_test -p
```

*you are in 3D environment when you login in Ubuntu section (from login-screen). There is another Ubuntu 2D section also. Check the gear at up right of login box.

---

### Post by Shadius on 2012-05-06
> **23dornot23d said:**
> It is on the Ubuntu list for 11.04 ..... needs something extra for 11.10

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

This is part of the Quote from there .....

do these in a terminal ..... please ..... will give someone some more information to work with - as ATI cards are not my thing though -  was just helping get more infomation to help solve the problem

**lspci -v | perl -ne '/VGA/../^$/ and /VGA|Kern/ and print'**

 **lsb_release -a**

Here's my output: 

```
shadius@shadius-5410US:~$ lspci -v | perl -ne '/VGA/.../^$/ and /VGA|Kern/ and print'
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI R250 If [Radeon 9000] (rev 01) (prog-if 00 [VGA controller])
	Kernel driver in use: radeon
	Kernel modules: radeon, radeonfb
shadius@shadius-5410US:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise
shadius@shadius-5410US:~$
```

---

### Post by Shadius on 2012-05-06
> **NikTh said:**
> You can check it out by running this test in unity 3D environment*
```

/usr/lib/nux/unity_support_test -p
```

*you are in 3D environment when you login in Ubuntu section (from login-screen). There is another Ubuntu 2D section also. Check the gear at up right of login box.

```
shadius@shadius-5410US:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 (RV250 4966) x86/MMX/SSE TCL DRI2
OpenGL version string:  1.3 Mesa 8.0.2

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      no
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       no

Unity 3D supported:       no
shadius@shadius-5410US:~$ 

```

So I guess that means I can't run Ubuntu in 3D and get all the fancy effects like making my Gnome Panel (if that's the correct name for it) transparent? :(

---

