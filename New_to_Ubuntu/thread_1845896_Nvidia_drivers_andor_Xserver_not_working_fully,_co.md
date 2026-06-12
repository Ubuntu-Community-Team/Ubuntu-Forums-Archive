---
title: "Nvidia drivers and/or Xserver not working fully, complete beginner"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by Akiyatsu on 2011-09-17
I am completely new to ubuntu and struggling with simple things 
still, so apologies if I sy anything daft.  

Installed Ubuntu 11.04 for the first time, put it on a usb stick to test it.  Worked and looked great.  So I installed it, but the first thing that happened when I loaded up was the message:

It seems you do not have the hardware required to run unity. Please choose Ubuntu classic at the login screen and you will be using the traditional environment.  

Ok so I figured this isn't the end of the world and carried on. 
Although the laptop is quite new and I was suprised it was not 
considered good enough for unity (didnt know what unity was until I looked it up).  

Now I didn't think any more of it until I clicked the Nvidia X 
Server Settings in System > Administration on the bar at the top.  I got the message:

You do not appear to be using the Nvidia X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.  

So I tried to do as it suggested but nothing seemed to happen, and the message poped up each time I opened Nvidia X Server Settings.  

Then I figure maybe I just dont have the right  drivers.  So I go to System > Administration and open Aditional Drivers.  It tells me that it has the latest drivers('This driver is activated but not in use') for Nvidia, but it is not using them. 
 
So I know (read as 'am guessing') that something is wrong with Nvidia X server and/or the drivers I have, but no idea what exactly, what to do about it, or how to start working out what needs fixing. 

Any advice will have to be solid gold fool proof, and will be 
greatly appreciated.  

I have tried many solutions to what might be my problem from 
numerous forums, each time it has not worked, or caused Ubuntu to 
stop working, and I have had to reinstall Ubuntu twice.  

How do I get Unity to work?  And therby know that my video drivers are installed and working as they should be?  

Thank you

---

### Post by papibe on 2011-09-18
Welcome to the forums!

There's a bug on the program 'Additional Drivers' that doesn't report correctly the use of the driver (even though you may be using it).

In order to make sure you are running the Nvidia driver:

Backup your X config file first:
```
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then run the Nvidia X Server Setings:
```
$ gksudo nvidia-settings
```
Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.

To make 100% sure you are using the driver, the result of these command:
```
$ grep -i nvidia /var/log/Xorg.0.log
```
Should be something similar to this:
```
(--) PCI:*(0:1:0:0) 10de:0640:3842:c959 nVidia Corporation G96 [GeForce 9500 GT] rev 161, Mem @ 0xde000000/16777216, 0xc0000000/268435456, 0xdc000000/33554432, I/O @ 0x0000dc80/128, BIOS @ 0x????????/524288
(II) Module glx: vendor="NVIDIA Corporation"
(II) NVIDIA GLX Module  195.36.24  Thu Apr 22 10:38:29 PDT 2010
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/extra-modules/nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
(II) NVIDIA dlloader X Driver  195.36.24  Thu Apr 22 09:34:29 PDT 2010
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "TwinView" "0"
(**) NVIDIA(0): Option "MetaModes" "DFP-0: nvidia-auto-select +0+0"
(**) NVIDIA(0): Option "CustomEDID" "DFP-1:/home/pablo/xfiles/newedid.bin"
(**) Sep 15 09:08:17 NVIDIA(0): Enabling RENDER acceleration
(II) Sep 15 09:08:17 NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) Sep 15 09:08:17 NVIDIA(0):     enabled.
(II) Sep 15 09:08:19 NVIDIA(0): NVIDIA GPU GeForce 9500 GT (G96) at PCI:1:0:0 (GPU-0)
(--) Sep 15 09:08:19 NVIDIA(0): Memory: 1048576 kBytes
...

```
With no errors (indicated by EE)

Once that's up and working, when can check how ready your system is for Unity.

Tell us how it goes,
Regadards.

---

### Post by sandyd on 2011-09-18
> **Akiyatsu said:**
> I am completely new to ubuntu and struggling with simple things 
still, so apologies if I sy anything daft.  

Installed Ubuntu 11.04 for the first time, put it on a usb stick to test it.  Worked and looked great.  So I installed it, but the first thing that happened when I loaded up was the message:

It seems you do not have the hardware required to run unity. Please choose Ubuntu classic at the login screen and you will be using the traditional environment.  

Ok so I figured this isn't the end of the world and carried on. 
Although the laptop is quite new and I was suprised it was not 
considered good enough for unity (didnt know what unity was until I looked it up).  

Now I didn't think any more of it until I clicked the Nvidia X 
Server Settings in System > Administration on the bar at the top.  I got the message:

You do not appear to be using the Nvidia X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.  

So I tried to do as it suggested but nothing seemed to happen, and the message poped up each time I opened Nvidia X Server Settings.  

Then I figure maybe I just dont have the right  drivers.  So I go to System > Administration and open Aditional Drivers.  It tells me that it has the latest drivers('This driver is activated but not in use') for Nvidia, but it is not using them. 
 
So I know (read as 'am guessing') that something is wrong with Nvidia X server and/or the drivers I have, but no idea what exactly, what to do about it, or how to start working out what needs fixing. 

Any advice will have to be solid gold fool proof, and will be 
greatly appreciated.  

I have tried many solutions to what might be my problem from 
numerous forums, each time it has not worked, or caused Ubuntu to 
stop working, and I have had to reinstall Ubuntu twice.  

How do I get Unity to work?  And therby know that my video drivers are installed and working as they should be?  

Thank you

post output of
```

lsmod
```

---

### Post by wildmanne39 on 2011-09-18
Hi, welcome to the forum! also if you installed a nvidia driver from another source besides additional drivers then you will have two drivers installed and you will need to open synaptic and uninstall one of them.

Please post the results of this command here, it will tell us if you can run unity.
```
/usr/lib/nux/unity_support_test -p
```
Thank you

---

### Post by Akiyatsu on 2011-09-18
Thanks very much for the replies.  


I have  done a clean install of Ubuntu 11.04, as it was not booting after my  attempts to fix/find out what was going on.  Update Manager popped up on  first boot up, I allowed it to do the recommended updates.  Still  getting the same Xserver/Unity behavior.  If helpful I am using a Dell  Inspiron N5110-2997.  
 

In response to papibe:


Backup your X config file first:
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old


This fails with the message cp cannot stat ... No such file or directory.  
 

Then run the Nvidia X Server Setings:
$ gksudo nvidia-settings


Select X Server Display Configuration (left). In the right press 'Save to X Configuration File'. Restart your machine.
 

So this opens the nvidia X server settings.  On the  left there is only 'nvidia-settings Configuration' and it appears  selected already.  There is no button 'Save to X Configuration File' but  there is a similar one 'Save Current Configuration' just above the quit  and help button, I assume this is the same thing.  I saved the file and  restarted.  
 

To make 100% sure you are using the driver, the result of these command:
$ grep -i nvidia /var/log/Xorg.0.log

This gives me the message

[    14.033] (II) Module glx: vendor="NVIDIA Corporation"
[    14.033] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    14.106] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Sorry I follow instructions to the letter but I'm none the wiser still.  

Response to sandyd:

lsmod gives this read out:

Module                  Size  Used by
rfcomm                 38125  8 
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
snd_hda_codec_hdmi     27535  4 
snd_hda_codec_idt      60537  1 
nvidia               9766978  0 
arc4                   12473  2 
usb_storage            43946  0 
snd_hda_intel          28209  2 
iwlagn                284777  0 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
iwlcore               148964  1 iwlagn
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
uas                    17676  0 
uvcvideo               66851  0 
i915                  451068  2 
mac80211              257001  2 iwlagn,iwlcore
dell_wmi               12601  0 
snd_seq_midi           13132  0 
cfg80211              156212  3 iwlagn,iwlcore,mac80211
btusb                  18160  2 
snd_rawmidi            25269  1 snd_seq_midi
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
dell_laptop            13515  0 
snd_seq_midi_event     14475  1 snd_seq_midi
sparse_keymap          13666  1 dell_wmi
dcdbas                 14054  1 dell_laptop
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
videodev               75143  1 uvcvideo
drm_kms_helper         40745  1 i915
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                59039  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   184164  3 i915,drm_kms_helper
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
xhci_hcd               72190  0 
libahci                25548  1 ahci
r8169                  46630  0 

Response to wildmanne39

I have not knowingly installed anything, just a clean install, and allowed Ubuntu update to run.  Result of your request is:

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context


Thank you again for your replies.

---

### Post by wildmanne39 on 2011-09-18
Hi, post the results of this command please:
```
lspci | grep VGA
```
Thank you

---

### Post by Akiyatsu on 2011-09-18
The result of 

lspci | grep VGA

is as follows

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)

Thank you.

---

### Post by wildmanne39 on 2011-09-18
Hi, it looks like you have two video cards one intel and one nvidia, do you know if one is optimus? if so here is a link for it.
[https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)
Thank you

---

### Post by realzippy on 2011-09-18
Optimus...
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by wildmanne39 on 2011-09-18
Hi realzippy, thank you for that great link, you are always full of useful information.

---

### Post by owiknowi on 2011-09-18
the switchable graphics thingy is still a bit of a hassle under open source os.
by default the -often- intel chipset is used, no matter if nvidia or ati drivers are installed.

installed several ubuntu flavors on a hp dv6-3185ed (intel + ati hd5600) and they all crashed in an awful way: everything froze completely so i had to power down the hard way and ruined my hdd that way in the bargain...

btw. i've never got an answer on the same problem posted here:
[http://ubuntuforums.org/showthread.php?t=1786836&goto=newpost](http://ubuntuforums.org/showthread.php?t=1786836&goto=newpost)
(so i had to leave my beloved ubuntu 10.04.2 lts)

---

### Post by Akiyatsu on 2011-09-18
How do I find out if one is Optimus?  

I'm also not sure what that means exactly, although having looked at the links it is some form of driver for systems with two graphics processing units?

What should my next move be?  I am reluctant to try anything off my own initiative again, as I have had to reinstall Ubuntu enough times in the past 24hours for my liking :)

Thank you all again.

edit: reading in more detail, I am less concerned about power saving as I never use the laptop on battery, but would like to be able to feel that I am able to use all the features of Ubuntu Unity, and I wouldnt mind being able to install EVE either at some point in the future.

---

### Post by wildmanne39 on 2011-09-18
Hi, I just wanted to let you know that I have not forgotten about you, I am researching the issue to see if I can find a solution.
Thank you

---

### Post by Akiyatsu on 2011-09-18
Hey no worries.  I'm amazed and very grateful to have had so many replies and helpful links (well they would be if I understood them all, but that's not the posters fault) in less than a day.  

Thanks.

---

### Post by wildmanne39 on 2011-09-18
Hi, in additional drivers is there another nvidia driver for your card? 

Post the results of this command please:
```
dmesg | egrep 'nvi|firm|i915'
```
Thank you

---

### Post by Akiyatsu on 2011-09-18
[   12.726043] nvidia: module license 'NVIDIA' taints kernel.
[   12.875417] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   12.875422] i915 0000:00:02.0: setting latency timer to 64
[   12.898662] i915 0000:00:02.0: irq 56 for MSI/MSI-X
[   12.993270] iwlagn 0000:09:00.0: loaded firmware version 17.168.5.2 build 35905
[   13.217826] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.217831] nvidia 0000:01:00.0: power state changed by ACPI to D0
[   13.217836] nvidia 0000:01:00.0: enabling device (0004 -> 0007)
[   13.217843] nvidia 0000:01:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   13.217850] nvidia 0000:01:00.0: setting latency timer to 64
[   13.247920] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[ 1289.424536] i915 0000:00:02.0: restoring config space at offset 0x1 (was 0x900007, writing 0x900407)
[ 1289.425045] nvidia 0000:01:00.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100007)
[ 1289.459336] i915 0000:00:02.0: setting latency timer to 64
[ 1289.662053] PM: restore of drv:i915 dev:0000:00:02.0 complete after 202.773 msecs

---

### Post by wildmanne39 on 2011-09-18
Hi, that output shows a bug in that nvidia driver.

Did you install it from additional drivers? 

Open synaptic and type in nvidia and make sure you do not have two drivers in use.

Also is there another driver in additional drivers for your nvidia card?
Thank you

---

### Post by Akiyatsu on 2011-09-18
No I have made no attempt to install drivers.  The only things I have done since the fresh install was the suggestions posted in this thread.  

In synaptic, there are the following installed items under a search for nvidia:

xserver-xorg-video-nouveau
nvidia-current
nvidia-settings
jockey-common
jockey-gtk
nvidia-common

In the additional drivers it says 'No proprietary Drivers are in use on this system'.  In the white selection box, there is one driver 'NVIDIA accelerated graphics driver' that has a green light next to it.  Says that this driver is activated but not in use.  Then it just gives some blurb about needing the driver to run unity, and that I need to install the driver to use unity.  

There are no options here other than Remove, Help and Close.  

Thank you.

---

### Post by wildmanne39 on 2011-09-18
Hi, that is just a bug, it is in use.

When you move your mouse all the way to the left of the screen do you see a launcher on the desktop? Or if you hit the super key also known as the windows key does the launcher come out?
Thank you

---

### Post by Akiyatsu on 2011-09-18
No nothing happens when I move the cursor to the left of the screen or when I hit the 'windows' key.  

The desktop I have currently looks different to the one that was there when I tried out Ubuntu, running it from the usb stick.  The bar to the left was there when running from the usb stick.  

Thank you.

---

### Post by wildmanne39 on 2011-09-18
Hi, that is what I thought but I wanted to make sure. The only suggestion I have is to go to the nvidia website and download and install the newest driver from there, make sure you deactivate the one you are using know first.

---

### Post by Akiyatsu on 2011-09-18
Ok. So to deactivate the current ones I'm guessing I will use that Synaptic to remove the 3 starting with nvidia?  

And, if possible, can you explain what exactly the problem is?  (I feel so stupid saying that seeing as I started the thread)  I mean is the nvidia card working at all?  Is it simply a case that the hardware I have is not supported on Ubuntu, and I might be better off trying a different distribution? 

If these forums support it and I can find the button I shall have to up-rate you, give you karma or whatever it might be called.  Thanks very much for your time.

---

### Post by wildmanne39 on 2011-09-18
Hi, you can go into additional drivers and deactivate it there.

I suspect that you have the optimus nvidia card that is not well supported, just what is mentioned in the bumbulbee link I gave you.

I would look up your documentation for your computer and and see if it is optimus.

If it is not you may be able to get it to work by installing from the nvidia website, usually the driver in additional drivers works best.

Also you could disable your intel graphics and see if it is conflicting with the nvidia driver but if you do that and the nvidia driver is not working correctly then you may not be able to load the desktop.

According to the information you have posted it looks like the nvidia driver is loading but there may still be a problem with it.

I myself have an older nvidia card and it recommended the new driver but it caused my system to crash and I have to use the old one.

If you want to do something nice for me you can click on the red link in my signature and show your support for me becoming an ubuntu member.
Thank you

---

### Post by wildmanne39 on 2011-09-18
Hi, you might also try this with the nvidia driver installed.
```
sudo nvidia-xconfig --add-argb-glx-visuals --no-logo --force-generate
```
That should make a new config file for nvidia.
Thank you

---

### Post by anewguy on 2011-09-19
Since the i915 will be the on-board GPU, has the OP tried just disabling the on-board GPU in the BIOS?

Dave ;)

---

### Post by realzippy on 2011-09-19
Unity:

Your laptop should indeed be able to run Unity,also on the Intel graphics (which are pretty fast btw)...
To make sure you have the latest kernel,mesa,libdrm and xserver-xorg-video-intel packages on your system,
run
```
gksudo software-properties-gtk
```
mark the checkbox:
natty-updates and natty-proposed,and backports if you want in *Updates* tab.
Once being here,you might want to add Canonical Partners in
*Other Software*,restricted extras in *Ubuntu SW*
Then open a terminal,update your system:
```
sudo apt-get update
sudo apt-get upgrade
```

Reboot.You should be now able to run Unity 3D...
...........................................................................
Nvidiadriver:

Yes,check your BIOS for graphics options as *anewguy* suggested.
If you have an option for nvidia only,choose it.After booting you should be able to install the nvidia driver.
If you don't have any (most optimus laptops don't),read on:

If you do not care about your battery capacity since your laptop
is always plugged to power supply,I suggest to install
the "fork" of bumblebee:bumblebee_stable, which also installs a "patched" nvidia-driver.
You cannot install any "normal" nvidia driver on an "Optimus" laptop without BIOS graphics switch;
the nvidia driver will always cry for a screen,which is dedicated to the
intel card.
Bumblebee runs 2 Xservers via VirtualGL, one for each card...

To install bumblebee_stable,nvidia driver:

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:mj-casalogic/bumblebee
wget https://raw.github.com/Bumblebee-Project/Bumblebee/master/cleanup
chmod +x cleanup
sudo ./cleanup --force
```
This is only needed if you formerly used/tried to install an old version of bumblebee,running it anyway does no harm..
If you get an error when running the cleanup script,reboot and run the script again...

Then:
```
sudo apt-get purge nvidia-current
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install bumblebee
sudo usermod -a -G bumblebee YOURUSERNAMEHERE
```
..replace YOURUSERNAMEHERE with your user's name.If you have more users on your machine,repeat this step for every user...
**Reboot**
Your system now runs on the Intel integrated graphics card,run:
```
glxspheres

```
for a few seconds,note the FPS rate..
Then run: (can take a few seconds when running 1rst time)
```
optirun glxspheres

```
..the prefix "optirun" before an application "tells" system to run the app on the more powerful nvidia-card.
Compare the FPS,it should have increased drastically.
So whenever you need more graphics power,eg. googleearth or a game,
start this app with "optirun" in front of to use nvidia-card.
You can create launchers for this purpose,no need to run the terminal.

source:
[https://launchpad.net/~bumblebee/+archive/stable](https://launchpad.net/~bumblebee/+archive/stable)

...............................................................
If you want to change the nvidia graphics settings,you had to start nvidia-settings (the GUI for your nvidia-driver) with:
```
nvidia-settings -c :8
```
..if you prefer editing xorg.conf manually (not very likely ;-) ),note that you would have to edit:
/etc/X11/**xorg.conf.nvidia**
since there is no normal "xorg.conf" in a bumblebee setup,which would "confuse" the intel card.

Note that -as mentioned in the beginning- your nvidia card always
sucks power in this bumblebee_stable configuration,whether you use it or not.They are working on switching nvidia off for the future.

The other bumblebee version tries to shut down the card with ACPI_Calls.
On some laptops this works,but on some it causes trouble.
The bb_stable developer calls it:
[I]Cleaning a dirty window with a stone...
[/I]
..which is kinda ugly workaround.

---

### Post by Akiyatsu on 2011-09-22
Hi, thanks for the further suggestions.  

Ill get back to you about the results when I can.  Been busy and not had time to continue to learn about ubuntu.  

Cheers.

---

