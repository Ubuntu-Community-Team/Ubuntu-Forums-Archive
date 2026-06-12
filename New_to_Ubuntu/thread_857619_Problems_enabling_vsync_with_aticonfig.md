---
title: "Problems enabling vsync with aticonfig"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by erans on 2008-07-12
When I try the 

sudo aticonfig --sync-vsync=on

command, I get this error: 
```
No protocol specified
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option
to generate a new configuration file.
```

I tried doing "sudo aticonfig -f" and I got this error: ```
No protocol specified
Data incomplete in file /etc/X11/xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault

```

Any ideas?

---

### Post by peakshysteria on 2008-07-12
This might be lame but are you sure you have a working ATI driver? What do you get from:
```
fglrxinfo
```

And what card do you have?

---

### Post by erans on 2008-07-13
I don't think so. Just whatever was installed by default.

```
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 8x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

```

---

### Post by peakshysteria on 2008-07-13
You are not running the ATI driver. This a classic problem with ATI cards. Check what card you have by running:
```
lspci
```

An have a look at     [* BinaryDriverHowto * ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"). But your best bet to make it is [Method 2: Manual Method (installing Catalyst 8.6)]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method_.28installing_Catalyst_8.6.29") if your card aren't to old.

The easiest way if you want it easy is to install Envy from synaptic. It will install the driver for you as long as you have a card still supported by ATI.

---

### Post by erans on 2008-07-13
Damn, my card is too old. :(

It says it uses the legacy driver but that it isn't compatible/available to me. Is there any way to enable vsync?

---

### Post by peakshysteria on 2008-07-14
Aren't you in the ATI 9xxx range at all? Please post the output of:
```
lspci
```

---

### Post by nitrogoldfish on 2008-07-14
I'm having the same problem, running ```
aticonfig --initial=dual-head
``` spits back
> Data incomplete in file xorg.conf
	Device section "Configured Video Device" must have a Driver line.
aticonfig: Parsing the configuration file failed.
The above error messages are reported from XFree86 and may assist you in
diagnosing the problem with your configuration input file. Try use -f option to generate a new configuration file.
and adding the -f option returns a similar error and segfaults.

the relevant bits of /etc/X11/xorg.conf are:
> Section "Device"
        Identifier      "Configured Video Device"
        Driver          "fglrx"
EndSection


when I run ```
fglrxinfo
``` it says:
> display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY RADEON X700
OpenGL version string: 2.1.7412 Release
so it seems to be running with ATI graphics drivers...

do i need a different driver line in xorg.conf or am i just missing something completely?

thanks in advance for any help.

running xubuntu 8.04

---

### Post by markbuntu on 2008-07-14
Did you try using the Catalyst Control Center to set up your dual displays?
changing your xorg.conf should not be necessary if you are using flgrx.

---

### Post by nitrogoldfish on 2008-07-16
thanks mark: er... no. actually, i didn't know such an app existed outside of windows. is it available in the repos? come with ati drivers? how do i access it?

---

### Post by tramir on 2008-07-16
It's in the package fglrx-control, so you need to
```
sudo apt-get install fglrx-control
```
ATI control center is a QT application that won't show up in the menus, because it gets installed in the "Other" section that's hidden by default. So you either go to System - Preferences - Main menu and enable the "Other" submenu, or you can run it from the command line (or with ALT-F2) as 
```
amdcccle
``` 
(no need to run it with gksu/sudo)

---

### Post by nitrogoldfish on 2008-07-18
amdcccle segfaults...giving me the same error i was originally getting with aticonfig: > Data incomplete in file xorg.conf
	Device section "Configured Video Device" must have a Driver line.
Segmentation fault


...starting to think it might be easier to just edit xorg.conf by hand. lots of google results on how to do that

---

### Post by markbuntu on 2008-07-19
In the "... Video Device" Section of your xorg.conf just add this line:

	Driver      "fglrx"

This line should be automatically added to your xorg.conf when you click on "in use" in  Hardware Manager. If not, you can add it by hand.

If you want more info on adjusting your ati driver through xorg.conf, you can get it here:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

The directions for tweaking it are here:

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

---

### Post by sirHC88 on 2008-08-19
Hi,

I think I've got quite the same problem. I have got an IBM System x3650 server with Ubuntu Hardy. I have already opened a new [thread]("http://ubuntuforums.org/showthread.php?t=889470") for my problem some days ago.

Also tried to add "Driver "fglrx"" in the xorg.conf, rebooted afterwards, but with no success. When I enter "fglrxinfo" I get "Error: unable to open display (null)".

Any ideas how to solve this issue?

---

### Post by tramir on 2008-08-19
If you open Restricted drivers, does "ATI..." show as both enabled and in use?

---

