---
title: "Brightness HotKey not working after 13.10 Update"
date: 2013-10-18
forum: New to Ubuntu
---

### Post by oceanic2 on 2013-10-18
Device: Lenovo B570
Ubuntu: 13.10 (64bit)

Changing the brightness with the hotkeys shows the osd but the brightness does not change and it only has 5 steps previouly it hat more than 10.
Changing the brightness from the brightness & lock application does nothing.
Changing the brightness from the brightness applet does nothing.

Changing the brightness with the hotkeys in the grub bootmenu works!

Edited etc/default/grub with GRUB_CMDLINE_LINUX="acpi_backlight=vendor" but it did not work, osd did not show up with that line.

Executing ```
sudo su
"echo 200 > /sys/class/backlight/intel_backlight/brightness"
```

changes the brightness.

Any Help appreciated!
Thank you!

---

### Post by Toz on 2013-10-18
Hello and welcome to the forums.

Was this an upgrade from 13.04?

And can you post back some more info:
1. Your current kernel boot line:
```
cat /proc/cmdline
```
2. Info about your video cards:
```
lspci -k | grep -A3 VGA
```
3. Your current backlight interfaces and values:
```
for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
```
4. A copy of your /var/log/Xorg.0.log file:
```
pastebinit /var/log/Xorg.0.log
```
...and post back the link that is generated.

---

### Post by oceanic2 on 2013-10-18
hi thank you for your reply!

yes it was an update from 13.04

here is the output of the commands:
#1)
```
oceanic@Red-Queen:~$ cat /proc/cmdline
BOOT_IMAGE=/boot/vmlinuz-3.11.0-12-generic root=UUID=f7201446-c80f-4f85-a469-c6845ccd4443 ro quiet splash vt.handoff=7

```

#2)
```
oceanic@Red-Queen:~$ lspci -k | grep -A3 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: Lenovo Device 3975
	Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
```

#3) as i mentioned in the op, *echo "value" > /sys/class/backlight/intel_backlight *works, so the 200 vales are mine 

```
oceanic@Red-Queen:~$ for i in /sys/class/backlight/*; do echo $i; cat $i/brightness; cat $i/actual_brightness; cat $i/max_brightness; done
/sys/class/backlight/acpi_video0
0
0
10
/sys/class/backlight/intel_backlight
200
200
976

```

#4) [http://pastebin.com/Vy8SJmJc](http://pastebin.com/Vy8SJmJc)

again thank you for your help!

---

### Post by Toz on 2013-10-18
From your Xorg log file:
> [    26.163] (--) intel(0): found backlight control interface acpi_video0 (type 'firmware')
...yet as per your initial post, intel_backlight is the active backlight interface. The kernel parameter **acpi_backlight=vendor** should solve this but you also state that it didn't work. Can you try that kernel parameter again (make sure you run "sudo update-grub") and post back the results of the same commands from post #2 again for comparision purposes?


If it doesn't work again, can you try the **acpi_osi="!Windows 2012"** kernel parameter instead? The relevant line in /etc/default/grub should look like this:
```
GRUB_CMDLINE_LINUX="acpi_osi=\"!Windows 2012\""
```
...(note the escaped quotes).


One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

---

### Post by oceanic2 on 2013-10-18
this one worked:

> **Toz said:**
> 
...
One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

You are a very kind and smart person and i really thank you for help!

---

### Post by Toz on 2013-10-18
Glad to hear. For my own curiosity, are you using any extra kernel parameters in addition to 20-intel.conf?

And if you don't mind, can you please mark this thread as "Solved" via the "Thread Tools" link above your first post? Thanks.

---

### Post by oceanic2 on 2013-10-18
Just "quiet splash" but i as far as i know that was already there.

Before the update i had this issue about once a month but a restart always fixed the issue.

Again i really appreciate you help!

----
Was wondering where i could change the tag, i already started to edit my op ;)

---

### Post by Toz on 2013-10-18
> **oceanic2 said:**
> 
Was wondering where i could change the tag, i already started to edit my op ;)
To change post tags, look for the "Add/Edit Tags" button towards the bottom right of this page.

---

### Post by cailean99 on 2013-10-20
I did a fresh install of Ubuntu 13.10 yesterday on a Lenovo Z570.  I then spent ages trying every possible solution anyone suggested to this problem and eventually had to give up when none of them worked.  They mainly involved editing etc/default/grub.  I thought I'd try again today and came across this thread, which worked perfectly first time.  All I've done is added the /usr/share/X11/xorg.conf.d/20-intel.conf file given here, and changed the etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT back to "quiet splash" and the GRUB_CMDLINE_LINUX= back to "".  Thanks so much for your help!

---

### Post by BlaXpirit on 2013-10-21
Toz saves the day again!

> **Toz said:**
> create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again

This worked without any other tweaks on Lenovo B570. Thanks.

---

### Post by angelous2 on 2013-10-22
Thank you Toz, This works very well for me! 
I have a lenovo V570, ubuntu 13.10 (upgrade from 13.04) x64 
Linux 3.11.0-12-generic #19-Ubuntu SMP Wed Oct 9 16:20:46 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux



> **Toz said:**
> From your Xorg log file:

One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

good job!

---

### Post by nidhi18tomer on 2013-10-30
> **Toz said:**
> From your Xorg log file:

One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

This fixed my brightness but it screwed up my bumblebee, I cannot run optirun now.

Without this, optirun runs fine.

---

### Post by Toz on 2013-10-30
> **nidhi18tomer said:**
> This fixed my brightness but it screwed up my bumblebee, I cannot run optirun now.

Without this, optirun runs fine.

Hello and welcome to the forums.
I've only read about this fix working on intel-only graphics systems.
I don't have any experience with bumblebee, but I'm curious. What does your xorg.conf file look like with this addition (that makes bumblee work)? And what are your video card settings:
```
lspci -k | grep -iA3 VGA
```

---

### Post by Alessandro_Cellini on 2013-10-31
Excellent ! 

> **Toz said:**
> From your Xorg log file:

One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

SAMSUNG NP-R510 :: I've follow these instructions and after reboot, all the brightness controls works fine !! ... Fn+Arrow keys, brightness reduction on battery mode and widget brightness control, everythig works fine !

Thank you !

---

### Post by nidhi18tomer on 2013-10-31
**nidhi@nidhi-Ideapad-Z570:~$ ****lspci -k | grep -iA3 VGA**
```
nidhi@nidhi-Ideapad-Z570:~$ lspci -k | grep -iA3 VGA
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
    Subsystem: Lenovo Device 397d
    Kernel driver in use: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
--
01:00.0 VGA compatible controller: NVIDIA Corporation GF108M [GeForce GT 540M] (rev ff)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev ff)
    Kernel driver in use: snd_hda_intel
03:00.0 Network controller: Qualcomm Atheros AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```

**nidhi@nidhi-Ideapad-Z570:~$ optirun -vvv vlc**

```

                                               [ 4271.703330] [DEBUG]Reading file: /etc/bumblebee/bumblebee.conf
[ 4271.704562] [DEBUG]optirun version 3.2.1 starting...
[ 4271.704634] [DEBUG]Active configuration:
[ 4271.704691] [DEBUG] bumblebeed config file: /etc/bumblebee/bumblebee.conf
[ 4271.704721] [DEBUG] X display: :8
[ 4271.704786] [DEBUG] LD_LIBRARY_PATH: /usr/lib/nvidia-304:/usr/lib32/nvidia-304
[ 4271.704816] [DEBUG] Socket path: /var/run/bumblebee.socket
[ 4271.704846] [DEBUG] Accel/display bridge: auto
[ 4271.704889] [DEBUG] VGL Compression: proxy
[ 4271.704923] [DEBUG] VGLrun extra options: 
[ 4271.704961] [DEBUG] Primus LD Path: /usr/lib/x86_64-linux-gnu/primus:/usr/lib/i386-linux-gnu/primus
[ 4271.720113] [DEBUG]Using auto-detected bridge primus
[ 4275.465173] [INFO]Response: Yes. X is active.

[ 4275.465187] [INFO]Running application using primus.
[ 4275.465442] [DEBUG]Process vlc started, PID 3642.
VLC media player 2.0.8 Twoflower (revision 2.0.8a-0-g68cf50b)


```
**nidhi@nidhi-Ideapad-Z570:~$ ls /usr/share/X11/xorg.conf.d/**
```
10-evdev.conf         11-evdev-trackpoint.conf  50-vmmouse.conf  51-synaptics-quirks.conf
11-evdev-quirks.conf  50-synaptics.conf         50-wacom.conf    glamor.conf
```

**nidhi@nidhi-Ideapad-Z570:/usr/share/X11/xorg.conf.d$ cat glamor.conf **
```
Section "Module"
    Load  "dri2"
    Load  "glamoregl"
EndSection
```

---

### Post by fabiom2 on 2013-11-01
> **Toz said:**
> 

(...)


One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.


The Solution above works like a charm on **Xubuntu 13.10 64 Bits** / Netbook Asus 1015BX.

---

### Post by nidhi18tomer on 2013-11-02
Solved it by editing **glamor.conf** and removing **20-intel.conf  **from** [B]/usr/share/X11/xorg.conf.d/**[/B]

My **glamor.conf **looks like this now
```
Section "Module"
    Load  "dri2"
    Load  "glamoregl"
EndSection
Section "Device"
        Identifier  "intel"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
EndSection
```

---

### Post by Toz on 2013-11-02
> **nidhi18tomer said:**
> Solved it by editing **glamor.conf** and removing **20-intel.conf  **from** [B]/usr/share/X11/xorg.conf.d/**[/B]

My **glamor.conf **looks like this now
```
Section "Module"
    Load  "dri2"
    Load  "glamoregl"
EndSection
Section "Device"
        Identifier  "intel"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
EndSection
```
Interesting. You've removed the Bus ID number and changed the Identifier parameter. Thanks for posting back the solution - I'm sure others with bumblebee graphics will find this helpful.

---

### Post by f-jack on 2013-11-22
Good Job works great

---

### Post by blacksnow67 on 2013-11-22
Working on HP Elitebook 840G1 and finally did it for me. I cannot thank you enough!

---

### Post by drjkonline on 2013-12-24
> [COLOR=#000000]*create the file *[/COLOR][B]/usr/share/X11/xorg.conf.d/20-intel.conf with the following content:
Code:
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
...and log out and back in again[/B]

This worked for me on Lenovo s210 T running ubuntu 13.10. Thanks.

---

### Post by ubh on 2014-01-01
As in here---> [http://ubuntuforums.org/showthread.php?t=2181534&p=12819813#post12819813](http://ubuntuforums.org/showthread.php?t=2181534&p=12819813#post12819813)
This solution worked for me```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```

No other tweaks needed on a fresh install of 13.10 amd64 on Lenovo B570e.

Really thanks to **Toz**! :D

---

### Post by Mr.Pytagoras on 2014-01-06
Just to add my experience with this kind of a problem (for future readers)

If you'are having troble getting the brightness controll to work on an Acer laptop, then the real problem might be in the module acer-wmi.

If you can control brightness using terminal or power-manager app then try this command in terminal:
```
xev
```
and press the FN+BrightnessUP/DOWN -> if it wont show anything then you have problem with the acer-wmi. You have to blacklist it, that's simple, just add the following line to /etc/modprobe/blacklist.conf
```
blacklist acer_wmi
```

If you can not control brightness from terminal or any other apps then you might wanna add this to file /etc/default/grub :
```
acpi_backlight=vendor
``` or
```
acpi_osi='!Windows 2012'
```

or in my case I needed both

you could try also:
```
acpi_osi=Linux
```
but from what I can tell it might work for brightness however it might affect other areas (for example on my acer 5750G laptop i wasn't able to get my cpu temperature under 60C and the fan was on all the time) 

Hope it helps

---

### Post by Toz on 2014-01-06
Thanks for sharing, Mr.Pytagoras. 
You had a typo in the blacklist command (you misspelled blacklist). I've corrected it.

---

### Post by geoaraujo on 2014-01-07
> **Toz said:**
>  One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

Thank you!!!

---

### Post by ileopoldes on 2014-01-10
I did have the same problem. The second option above works for me.
My pc is a Dell Latitude 3540

Below I put some informations about my system. Perhaps it can help someone.

1. Current kernel boot line:
          ```
BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=f253cbe7-d82f-4bb4-aaad-0eaed406d45a ro "acpi_osi=!Windows 2012"
```


2. Info about video cards:
     

     ```

00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09)
        Subsystem: Dell Device 0609
        Kernel driver in use: i915
00:14.0 USB controller: Intel Corporation Lynx Point-LP USB xHCI HC (rev 04)

03:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Venus PRO [Radeon HD 8850M]
    Subsystem: Dell Device 0609
    Kernel driver in use: radeon


```

---

### Post by yoyo_58 on 2014-02-12
> **Toz said:**
> 

One other thing to try would be to create the file **/usr/share/X11/xorg.conf.d/20-intel.conf** with the following content:
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
...and log out and back in again to see if it works. Try it without any additional kernel parameters.

You rock!

Thank you.

---

### Post by burgesszachary1 on 2014-02-19
> **yoyo_58 said:**
> You rock!
```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection
```
Thank you.


Working for my Lenovo s210 IdeaPad Touch -- Running Ubuntu 13.10 Thanks!!!!!!!!!!!!!

---

### Post by nick97 on 2014-05-25
>  	Code:
 	Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"

EndSection 


you saved my eyes and my Lenovo's Z570 LCD
ubuntu 13.10
BOOT_IMAGE=/boot/vmlinuz-3.11.0-88-mptcp root=UUID=6fff3a3d-fe84-4d55-a3ea-8096a58c42a9 ro quiet splash vt.handoff=7

---

### Post by eyad-salah on 2014-10-28
I tried the xev and it's showing the following:
> KeyPress event, serial 37, synthetic NO, window 0x4200001,    root 0x90, subw 0x0, time 2727082, (185,286), root:(972,338),
    state 0x10, keycode 126 (keysym 0xb1, plusminus), same_screen YES,
    XLookupString gives 2 bytes: (c2 b1) "±"
    XmbLookupString gives 2 bytes: (c2 b1) "±"
    XFilterEvent returns: False


KeyRelease event, serial 37, synthetic NO, window 0x4200001,
    root 0x90, subw 0x0, time 2727088, (185,286), root:(972,338),
    state 0x10, keycode 126 (keysym 0xb1, plusminus), same_screen YES,
    XLookupString gives 2 bytes: (c2 b1) "±"
    XFilterEvent returns: False




I did everything else. I can control my brightness using the "intel_backlight" command but not using the keyboard keys.

---

### Post by Bloodcage on 2014-10-28
[COLOR=#333333][FONT=Lucida Grande]For all of you running a Laptop with NVIDIA Card and who are still not able to get the f* function keys for brightness to work, just follow the steps below. It worked very well for my system (Samsung q45, Intel Dualcore T7100 @ 1,8Ghz , Nvidia Geforce 8400M G 512) running Linux Mint 17.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]In command line, type in:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]sudo gedit /etc/X11/xorg.conf[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]You will have to enter your root password.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now, you should see:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]___________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Section "Device"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Identifier "Device0"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Driver "nvidia"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]VendorName "NVIDIA Corporation"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]EndSection[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]___________________________________________________[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]If you see nothing, just enter all the lines above and follow up with the next step below[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Under the VendorName Line, add the following:[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]______________________________________________________[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]Option "RegistryDwords" "EnableBrightnessControl=1"[/FONT][/COLOR]
[COLOR=#333333][FONT=Lucida Grande]______________________________________________________[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Now, save and reboot. Check your brightness controls, and hopefully this fixed things.[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]I've tried so many solutions out of the net and nothing had helped me until I came to this solution. But be aware that these steps only working for NVIDIA Grafics and you must have chosen the NVIDIA Driver in your system in "Administration -> Driver Manager"[/FONT][/COLOR]

---

