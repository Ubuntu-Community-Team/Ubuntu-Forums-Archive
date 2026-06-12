---
title: "Advanced Desktop Effects wont start"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by DyBurke on 2008-10-05
I've tried random assorted things around the forums as well as fiddled with some stuff myself, but I cannot seem to get Compiz to work.  Here are some readouts:

compiz-check
```
:~$ ./compiz-check 

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia) 

```

sudo lspci
```
:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
```

glxinfo
```
:~$ glxinfo
name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x21 24 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x22 24 dc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
0x4b 32 tc  1  0  0 c  .  .  0  0  0  0  0  0  0  0  0  0  0  0 0 None
dburke@lappy:~$ who
dburke   tty7         2008-10-05 00:21 (:0)
dburke   pts/0        2008-10-05 12:24 (:0.0)
```

If you need anything else, please, just ask.  I'd love to get this working so I can focus on some other things I want to do with ubuntu.

---

### Post by nowshining on 2008-10-05
i'd suggest that with the intel internal card that it can't handle the effects and the OS is stopping it from coming up... did you install all updates?? Other may as well suggest getting a Nvidia/Ati external graphics card... :)

---

### Post by DyBurke on 2008-10-05
> **nowshining said:**
> i'd suggest that with the intel internal card that it can't handle the effects and the OS is stopping it from coming up... did you install all updates?? Other may as well suggest getting a Nvidia/Ati external graphics card... :)

My computer is a laptop so getting another graphics card isn't really an option.  Other people have said they got most the effects to work fine on this card and at one point, it was working.  For some reason it has stopped letting me turn on effects since I turned them off.

---

### Post by nowshining on 2008-10-05
oh srry then, then by posting this answer/rebuttel ur post will get bumped :) and hopefully someone witht more info. can help u...

---

### Post by k3lt01 on 2008-10-05
Have you got restricted drivers installed/updated? Sometimes if the video card needs a restricted driver, or updated driver, desktop effects wont work.

---

### Post by Landara on 2008-10-05
I had problems with my driver, i used the program called Envy which you can get repo, it worked, now i have compiz :)

---

### Post by DyBurke on 2008-10-05
> **k3lt01 said:**
> Have you got restricted drivers installed/updated? Sometimes if the video card needs a restricted driver, or updated driver, desktop effects wont work.

I don't need restricted drivers.  I have an intel card.  There is a native driver for it.  It works well.  Used to run compiz fine.  I don't understand how to change the rendering method.  If I could just figure that out I think I'd be okay.

---

### Post by rybaxs on 2008-10-05
Did u activate the Visual Effects at the Appearances Preferences?

right click at the desktop -> change desktop background -> Visual Effects

:D

---

### Post by DyBurke on 2008-10-05
> **rybaxs said:**
> Did u activate the Visual Effects at the Appearances Preferences?

right click at the desktop -> change desktop background -> Visual Effects

:D


They wont enable.  Hence the subject line of my post.

---

### Post by rybaxs on 2008-10-05
is your Motherboard? Second Edition? 

I've encountered that problem, ASUS motherboard SE. Visual effects wont work. it just pop an error, until now i can't solve the problem after testing and reading some forums and tutorials.. :(

sorry, that's all i have.

---

### Post by rybaxs on 2008-10-05
sudo lspci
```
:~$ sudo lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```

This is mine that visual effects work.
```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```

Your specs is higher than me. Did u install the drivers updates? or restricted drivers? it will automatically pop up? Sometimes sources are down.. try to run updates later.

---

### Post by DyBurke on 2008-10-05
> **rybaxs said:**
> sudo lspci
```
:~$ sudo lspci
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

```This is mine that visual effects work.
```

00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)

```Your specs is higher than me. Did u install the drivers updates? or restricted drivers? it will automatically pop up? Sometimes sources are down.. try to run updates later.

The Update Manager says that my computer is fully up-to-date.

---

### Post by wgrant on 2008-10-05
You haven't by any chance got another user logged in, do you? Are you a member of the 'video' group?

---

### Post by DyBurke on 2008-10-06
> **wgrant said:**
> You haven't by any chance got another user logged in, do you? Are you a member of the 'video' group?

No one else is logged in and there is no video group. :(

---

### Post by eternalnewbee on 2008-10-06
If it worked for others with the same system hardware as yours, then you should be able to enable it too.
I'd try uninstalling, and reinstalling compiz, and see what happens...
Trial & Error: That's how we learn, or achieve what we want.

---

### Post by Blackwolf_Oz on 2008-10-06
Simply do the following:
Code:

sudo echo "SKIP_CHECKS=yes" >>/etc/compizconfig/config

Then check in the /etc/X11/xorg.conf file, that the driver for your graphic card is the intel one.

The entry should look similar to this example:
Code:

Section "Identifier"
Identifier "A name for the card
Driver "intel"
...
EndSection

and then try to enable compiz.
The biggest thing with the xorg file is having the "intel" part. This lets it use the intel drivers. I dont know a ton about the intel drivers specifically, but I have had some experience with ATI and nVidia's.

See what doing those two things do.

---

### Post by lazyart on 2008-10-06
> **rybaxs said:**
> Your specs is higher than me. Did u install the drivers updates? or restricted drivers? it will automatically pop up? Sometimes sources are down.. try to run updates later.

There are no restricted drivers for Intel.  Intel produces open-source drivers.

---

### Post by DyBurke on 2008-10-06
> **legend1264 said:**
> Simply do the following:
Code:

sudo echo "SKIP_CHECKS=yes" >>/etc/compizconfig/config

Then check in the /etc/X11/xorg.conf file, that the driver for your graphic card is the intel one.

The entry should look similar to this example:
Code:

Section "Identifier"
Identifier "A name for the card
Driver "intel"
...
EndSection

and then try to enable compiz.
The biggest thing with the xorg file is having the "intel" part. This lets it use the intel drivers. I dont know a ton about the intel drivers specifically, but I have had some experience with ATI and nVidia's.

See what doing those two things do.

This is the returned output:
```

:~$ sudo echo "SKIP_CHECKS=yes">>/etc/compizconfig/config
bash: /etc/compizconfig/config: Permission denied

```

My xorg.conf file already has intel specified as the driver.  Tried that. :(

---

### Post by anewguy on 2008-10-06
I'd have to do some searching to find out the exact syntax and where it all goes, but have you tried adding:

load "xgl"   or   load "aiglx" to xorg.conf

I think you also have to have the section at the end that enables composite if I remember right.  I had to do that once, but have since changed video cards and it's been a while.

Dave :)

Found part of what I was looking for.  I think the error message is saying since you don't use the nvidia driver, you need aiglx or xgl enabled.  I *think* (ouch!!) the following will do that:

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "AIGLX" "off"
EndSection

These go before the device section for the video card.

At the end, I think you also need this:

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

---

### Post by DyBurke on 2008-10-06
> **anewguy said:**
> I'd have to do some searching to find out the exact syntax and where it all goes, but have you tried adding:

load "xgl"   or   load "aiglx" to xorg.conf

I think you also have to have the section at the end that enables composite if I remember right.  I had to do that once, but have since changed video cards and it's been a while.

Dave :)

I have not tried that, but was thinking about doing something similar.  Any information you could scrounge up on the subject would be super helpful.  It's back to Google for me. :)

---

### Post by anewguy on 2008-10-06
You might also want to look at /var/log/Xorg.0.log - it will tell you how the xserver started up for you, including the driver it's using, if glx, etc., are enabled, etc..

Dave:)

---

