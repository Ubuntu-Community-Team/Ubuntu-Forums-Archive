---
title: "HOWTO: Install Hardy (8.04.1) on HP tx2500"
date: 2008-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by thegnark on 2008-07-28
I spent a long time configuring everything, and I thought I'd compile a quick writeup. I decided to re-install to meticulously document each step. This guide assume that you have at least basic working knowledge of using Ubuntu. If this is your first time using Linux, I'm recommending that you do not attempt to install Hardy Heron on the tx2500 at this time.

**This is based on [Ubuntu 8.04.1]("http://cdimage.ubuntu.com/releases/hardy/release/") x64 (Hardy Heron LTS)**. It probably works for 32-bit, but I haven't tested and don't see a specific reason to go with 32-bit over 64-bit.

Known issues:

[LIST]
[*]Digitizer *mostly* works (but not 100%)
[*]CPU scaling is NOT supported by current kernel
[*]Suspend/sleep is a bit flaky
[/LIST]
  [[SIZE=4]Installation[/SIZE]]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")

[LIST=1]
[*]Boot installation disc
[*]Highlight your language and press [Enter]
[*]Highlight"Install Ubuntu"
[*]Press F6
[*]Press F6 (again)
[*]Highlight "acpi=off" and press [Enter].  small "x" should appear to the left of this option
[*]Press [Esc]
[*]Press [Enter]
[*]This should boot to a graphical installer
[*]*Install as normal*
[*]After installation is complete, reboot as instructed
[/LIST]
 [[SIZE=4]First boot[/SIZE]]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")

[LIST=1]
[*]Highlight the first boot option (Ubuntu 8.04.1, kernel 2.6.24-19-generic)
[*]Press 'e' to edit the boot options
[*]Scroll down to the line that starts with "kernel"
[*]Press 'e' to edit this command
[*]Scroll to the end of the line and add the following option (no quotes): "acpi=off". The boot options should have the following options listed: "ro quiet splash acpi=off"
[*]Press '[Enter]' to confirm you are done editing the line
[*]Press 'b' to boot
[*]This should boot you to a graphical display prompt.
[/LIST]
[SIZE=4]Configuring Ubuntu[/SIZE]
This *should* get your Wireless working with an update to wl; also, a slightly newer kernel version is here. 

[LIST=1]
[*][Blacklist thermal]("http://ubuntuforums.org/showpost.php?p=5426140&postcount=80")
[LIST=1]
[*]Open a terminal
[*]Run "sudo gedit /etc/modprobe.d/blacklist"
[*]Add this text on its own line at the bottom of the file:
blacklist thermal
[*]Save and close
[/LIST]
 
[*][Enable sound]("http://ubuntuforums.org/showthread.php?p=5402251#post5402251")
[LIST=1]
[*]Open a terminal
[*]Run "sudo gedit /etc/modprobe.d/alsa-base"
[*]Add the following line to the bottom of the file:
options snd-hda-intel index=0 model=toshiba position_fix=1
[*]Save
[*]Close
[/LIST]
 
[*][Update]("http://ubuntuforums.org/showpost.php?p=5408040&postcount=53") (Fixes wireless and updates to kernel 2.6.24-20)
***Note:** Once these updates are moved from proposed to the standard repository, enabling "proposed" may not be required. In this case, skip this step.*
[LIST=1]
[*]Plug in to an ethernet port
[*]Verify that you have internet access
[*]Open up Synaptic
[LIST=1]
[*]System
[*]Administration
[*]Synaptic Package Manager
[/LIST]
 
[*]**SKIP THIS STEP FOR NOW. It looks like the necessary updates may be part of the standard repositories. If your wireless does not work after rebooting, come back and perform this step.**
Enable Hardy Proposed to your repositories
[LIST=1]
[*]Settings
[*]Repositories
[*]Updates
[*]Check "Pre-released updates (hardy-proposed)
[*]Click the "Close" button
[*]Confirm the message box that pops up warning you to reload
[/LIST]
 
[*]Click "Reload"
[*]Click "Mark All Upgrades"
[LIST=1]
[*]Click "Mark"
[/LIST]
 
[*]Click "Apply"
[LIST=1]
[*]Click "Apply"
[/LIST]
 
[*]After updates are complete, click "Close"
[/LIST]
 
[*][Enable the digitizer]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447"). Instructions are somewhat complicated, so I'm just providing a link to the thread instead of replicating here.
[*]Install ATI restricted driver
[LIST=1]
[*]Go to your restricted drivers manager
[LIST=1]
[*]System
[*]Administration
[*]Hardware Drivers
[/LIST]
 
[*]Check "ATI restricted driver
[LIST=1]
[*]Click "Enable"
[/LIST]
 
[/LIST]
 
[*]**Reboot as normal**
[/LIST]
 If there's anything you would like to add or correct, post and I'll try to update as appropriate. Also, feel free to check out [**HP Pavilion tx2000 series laptop runnign (sic) Ubuntu 8.04 - My Howto**]("http://mirosol.kapsi.fi/tx2020/tx2000howto.htm"). The [original thread]("http://ubuntuforums.org/showthread.php?t=845911") contains a lot of testing/discovery information.

---

### Post by gali98 on 2008-07-30
For the Wacom Digitalizer(with touch):
My tutorial (linux wacom .0.8.1-1 better protocol, but pressure is a bit wacky should be updated soon...):
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

TomTheWombat's Tutorial (linux wacom .0.7.9-11 you have to patch the source.. more of a hack then a good protocol, however it works, and pressure works good as far as I know....)
[http://ubuntuforums.org/showthread.php?p=4715731#post4715731](http://ubuntuforums.org/showthread.php?p=4715731#post4715731)

Now keep in mind both these post are for the tx2000 series, however as far as I know the wacom part of the lappy's are the same and should work. 
I have seen one report of my tutorial working on a tx2500 series.
I wrote it sunday (July 27, 2008 ) so it is pretty new.

I am also looking through the source to see if I can fix the pressure issue. I'm no coder, but I never give up :)
Kory

---

### Post by TreeFallComplete on 2008-07-30
Hey,

I followed the install steps above exactly for my tx2500 laptop, and it loads the kernel and then immediately cuts to a DOS screen, the last entry of which is "Kernel panic - not syncing: Attempted to kill init!"

From there it doesn't do anything.

---

### Post by pluckster on 2008-08-01
Are you installing 32bit or 64 bit? I was only get 64bit to work at all.

---

### Post by thegnark on 2008-08-01
> **thegnark said:**
> **This is based on [Ubuntu 8.04.1]("http://cdimage.ubuntu.com/releases/hardy/release/") x64 (Hardy Heron LTS)**

Bolded line at the top :roll:

---

### Post by ownaginatious on 2008-08-04
Umm... what's with the ACPI of this computer, and why is is pissing off Ubuntu? This is pretty annoying, considering that I have no battery meter and that the fan likes to stay at, if not close to, full blast all the time.

---

### Post by thegnark on 2008-08-04
> **ownaginatious said:**
> Umm... what's with the ACPI of this computer, and why is is pissing off Ubuntu?

If you watch the startup messages, you'll see that there is a problem with the temperatures being reported by the laptop and/or read by the OS. Therefore, Ubuntu thinks temps are too high and proactively shuts down to prevent damage to your computer.

The chipsets in these laptops are quite new, so it's possible that the code to deal with them simply needs to be added. This HOWTO spawned from a [much longer thread]("http://ubuntuforums.org/showthread.php?t=845911") with lots of discovery/testing info.

---

### Post by gali98 on 2008-08-04
My previous tutorial has been updated and pressure is fixed :)
You might want to check it out...
Kory

---

### Post by nxd on 2008-08-06
Just a quick question, did anyone have a chance to test Linux Mint with the 2500z?  Does it also give thermal problems at boot?  Since it's based off ubuntu would this guide work for it?

---

### Post by ownaginatious on 2008-08-06
For the time being, it appears that all variations of Linux are affected by the ACPI bug in the tx2500. I tried Arch Linux, and it had the same problem. I've heard from others that Fedora is also experiencing the same problem. Hopefully, the next Kernel update will fix all this. Lets hope it comes out soon :p

---

### Post by gali98 on 2008-08-07
That is expected as the kernel is the same overall kernel on all distros, where each distro adds a few of its own modules...
Kory

---

### Post by Gustavo Morales on 2008-08-10
Hi I have a tx 2510 us but after of many hours that i can't install ubuntu 8.04.1, finally i got it install but it shut down my laptop before start to run normally, what can i do? please i hope can install ubuntu with all of it functions.
thank's

PDT: Sorry for my english, I'm from colobia and I don't speak english very well

---

### Post by kevincop on 2008-08-23
I have just followed your HOWTO and it worked like a charm. All I needed to do is modify the file names for the touch, stylus and eraser (the usb file names). 

***I have a tx2500z and both the touchscreen and the stylus/eraser are behaving normally.*** Sound is good too. The only thing is ... it's running too hot, but that certainly has nothing to do with your howto. =)

So thanks a lot thegnark, gali98 and everyone else who worked on this tx2500 thing ;) 

[SIZE="4"]You all[/SIZE] :guitar:!

---

### Post by gali98 on 2008-08-24
Well you are welcome. I know the laptop in all of the reviews I saw online said it ran a bit hot. (I have the tx2000 but it probably applies....) even on Windows.
It does heat up my legs a bit.
Kory

---

### Post by dexterchief on 2008-08-24
Just wondering what the battery life is like with Ubuntu. I know that the battery life is not great but could be extended by tweaking some of the power options in Vista. Not sure what kind of controls you have under Ubuntu for that sort of thing.
I am also wondering about the screen orientation button (and the other buttons like the DVD button and the touch pad toggle) and whether or not they work under Ubuntu.

Thanks for the info so far!

---

### Post by thegnark on 2008-08-25
Right now, the battery life is abysmal... This is due to the lack of CPU support in the current kernel. When Intrepid Ibex comes out in October, things should improve greatly; however, even with the updated kernel, battery life in linux seems to consistently fall short of Vista and XP due to the state of ACPI support

---

### Post by marranzano on 2008-08-29
hello and thanx for all the help i found in this 3d...

i have a tx2510us and this is my current situation:
**kernel**: ubuntu with kernel 2.6.24-21-generic generic
**thermal**: after kernel upgrade I'm using the fix: *options thermal nocrt=1* in /etc/modprobe.d/options
**sound**: used the options *snd-hda-intel index=0 model=toshiba position_fix=1* fix in /etc/modprobe.d/alsa-base
**digitizer**: used the [_suggested guide_]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447") and everything seems to work (still needs further testing)
**wireless**: works fine once update kernel... to have it automatically connect after reboot (static ip and wpa) added *sudo /etc/init.d/networking restart* to /etc/rc.local
**cpu scaling**: added *sudo modprobe powernow-k8* and *sudo powernowd* to /etc/rc.local -> cpu does scaling but only to a minimum of 500 when it should go down to 12% ... :confused:

now the things I still can't get to work:
**xrandr**: no rotation at all... I get an error!!! :( (I have a ati hd3200 with fglrx driver... any ideas??)
**synaptics**: all works but i can't make it do the multifinger tapping :confused:
**keys**: there are 3 keys on the monitor that still need to be mapped (i hope) still have to work on this... ;)

if you have suggestions for the last three i would appreciate...

thanx again

ps. I'll put my xorg.conf in attachment for those who have the tx2510us

---

### Post by gali98 on 2008-08-29
A few of those buttons require a driver (one that is not written to my knowledge) to work. A few are. The touchpad does not support multitouch :(

I am going to try that cpu scaling thing thanks:)
and glad you got my tutorial to work
Kory

---

### Post by Ununtu on 2008-08-30
Hi everyone.

I've just tried to install Ubuntu on my TX2520ef following this tutorial, but I could'nt get it to work correctly (especialy for the digitizer). I tried twice reintsalling, but there's still the same mess. As I start looking around, I'm finding more and more bugs:
- digitzer doesn't work (already posted the bug on the Tablet-PC thread)
- [FIXED]batteries not recognised (they work, but it always tells me I'm on AC, even when I've booted on the battery)
- [FIXED] no wifi detection (the update with the preposed repositories made the wifi appear on the Networkmanager, but i don't detect the network). this might have to do with the fact that the wifi button (on the front of the computer) doesn't respond and is always orange (=off)
- [FIXED] computer doesn't correctly shut down : it stop at "Will now halt", but just stays on. and and not have the "Suspend to RAM" button/option
- Vista can't be booted, even if it appears in Grub (I get this error: the winload.exe file is either missing or damaged) I've pt Grub on the MBR, it's problably the orgin of this problem. I'll deal with this later

I'm wondering if this could come from the fact that I tried keeping Vista (only for some time, don't worry), so the dual-boot might have caused some problems...?? I'm a bit too new in the Linux world to understand all this:( Maybe all this is just one mistake I made at the beggining, but I paid attention to what I was doing and didn't see a glich...

If any of you has dual-boot and a fonctionnal PC, let me know, so I can find out if the problem is there or if I have to look elsewhere. (If you have any ideas or tips, don't hesitate!)

Thanks a lot.

EDIT: I fixed some of the bug: looking at the updates in the tutorial, I realised I had a bad translation of the end of the tutorial, so I had left the "acpi=off" mode at each boot. My bad.

---

### Post by gali98 on 2008-08-30
Hey Ununtu...


Did you follow this whole guide before doing my tutorial?

Kory

---

### Post by Ununtu on 2008-08-31
Yeah, I did. Put acpi off, blacklisted thermal, enabled sound, update to the 2.6.24.21 kernel, set the ATI driver, all this under a 8.04.1 64bits version of Ubuntu.
Only thing is that I kept Vista for the time being (but by mistake, I've put Grub on the MBR, so it isn't able to load for the moment, I'll fix this later, my goal is to have Ubuntu fully working so that I can get rid of Vista).

I read the tutorials carefully, and I translated them in french too (for the french wiki), so I don't think I forgot something... I don'tn get where the problem is...

PS: I just saw that small changes have been made to this tutorial, I'm going to check everything

EDIT: that's it, found the translation error, corrected thing, tried again, and it's working

---

### Post by rylangrayston on 2008-09-04
I am about to purchase the tablet found at this link
[http://h20386.www2.hp.com/CanadaStore/Product.aspx?pdetail=P65857]("http://h20386.www2.hp.com/CanadaStore/Product.aspx?pdetail=P65857")

this is what the cpu specs are 

Processor
	AMD Turion&#8482; X2 RM-70 Dual-Core Mobile Processor
&#8226; 2.00 GHz, 1MB L2 Cache, Up to 4000 MT/s system bus running at AC/DC mode 35 watt
Processor type
	AMD Turion&#8482; X2 RM-70 Dual-Core Mobile Processor
&#8226; 2.00 GHz, 1MB L2 Cache, Up to 4000 MT/s system bus running at AC/DC mode 35 watt 

my question... is this a 64 bit  or 32 bit CPU 
I even found this processor on the amd site and im still not sure 
What do X2 and RM-70 mean?

Thanks I know its a little of topic but i figured you guys would know
off the top of your head!

also I dont want to pay for vista is there a retailer that i can opt out with?, im in canada.

---

### Post by thegnark on 2008-09-06
They're 64-bit processors

---

### Post by gali98 on 2008-09-07
[http://www.system76.com/](http://www.system76.com/)

They preinstall ubuntu.

But this really isn't the place to post about this. Let's try to stay on topic.
:)

Kory

---

### Post by laurentp on 2008-09-07
Hi,

I know it's kind offtopic, but I'm really considering buying this laptop (the tx2524 version is on sale at 899$ at futureshop) and considering trying to get vista refund. So, I'm wondering if those problems will be fixed... I'm kind of a old-timer linux user but I don't think I can help fix the more technical stuff (like ACPI). Sorry again for offtopic,

Laurent

---

### Post by marranzano on 2008-09-08
hi again...
little update on my system:
**xrandr** - still not working (perhaps will wait for the radeonhd driver...)
**special keys** - the two lower keys on the monitor are still dead... wasn't able to map them...

**fingerprint recognition** using fprint works....
followed instructions from [_here_]("http://ubuntuforums.org/showthread.php?t=760018"), and also had to update sudo as mentioned in [_this_]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/254599") bug

has anyone been able to get **lirc** working??

---

### Post by alexpwalsh on 2008-09-11
Yes, buy the exact laptop(HP tx2524ca) from Futureshop for $899, I bought it a month ago(and paid $1099) and I LOVE IT.... this forum works fine. (Or did)...

The only problems I have with it are that vista is on it... which made it impossible to get everything working nicely at first, but thats not for this forum. Other than that, its wonderful. Vista is a little buggy though (surprised?)...

Here's my current problem, I'm still kind of new to Ubuntu (and linux in general at that...) but The first time I loaded ubuntu on it, it worked exactly as this forum described (minus the digitizer)... but now, I ran into some problems and have to re-install ubuntu and my kernel is only updating to x.19 and not the x.20 that the instructions are saying, and subsequently my wireless isin't working, the funny thing is it did yesterday before all of my troubles... now I'm just frustrated.... Its a joint problem as well, because it doesnt detect the Bluetooth either, the light that indicates them working or not never turns blue(on) it stays amber(off).....

Anyone have any thoughts?

---

### Post by alexpwalsh on 2008-09-11
ok, so to update my situation, I upgraded with the proposed repositories and now have kernel x.21 , and still doesn't work. I believe I had .20 before, is there any way I can revert to THAT kernel now?

---

### Post by rammsdell on 2008-09-12
Hello, I have a HP tx2510us, I was able to boot linux with the acpi=off and nolapic boot options, just having acpi=off alone doesn't work. I was able to get everything else to work except for the initial network.  
I cannot get it to have any network connections.  I've tried the install and live dvd, neither one will work with a wired connection.  The network icon shows that there is a connection even when the cable is disconnected.  When connected the lights glow on the port but the os doesn't respond to it.  I do not know ubuntu enough to troubleshoot the problem, ubuntu 7.04 seems to recognize the ethernet fine.  Does anyone have any suggestions?

---

### Post by alexpwalsh on 2008-09-13
OK, to start, I solved my problem, I added the noapci option to the live CD on initial boot(pre-install) and it solved ALL of my problems. It worked fine...


> **rammsdell said:**
> Hello, I have a HP tx2510us, I was able to boot linux with the acpi=off and nolapic boot options, just having acpi=off alone doesn't work. I was able to get everything else to work except for the initial network.  
I cannot get it to have any network connections.  I've tried the install and live dvd, neither one will work with a wired connection.  The network icon shows that there is a connection even when the cable is disconnected.  When connected the lights glow on the port but the os doesn't respond to it.  I do not know ubuntu enough to troubleshoot the problem, ubuntu 7.04 seems to recognize the ethernet fine.  Does anyone have any suggestions?

Try turning off apci with the noapci option when you press F6 twice when highlighting the boot option, it seemed to make everything work for me(except the digitizer, which I havent tried yet)... it then sees that its a laptop and not a desktop computer, this I believe is what solved my problem...BUT then again I'm running the 2524ca model too.. so.. 

NOTE: This also solved my issues with my Bluetooth drivers as well.

Best of luck

---

### Post by rammsdell on 2008-09-13
well I tried it once more with just acpi=off and it worked, I don't know what nolapic is but I wasn't able to boot without it earlier.  Thanks:KS

---

### Post by marranzano on 2008-09-20
anyone managed to get the front mic working?? works really poorely... crackle and pops... :(

---

### Post by gali98 on 2008-09-20
That is a bug with the audio driver. I have a bug submitted here:
[https://bugs.launchpad.net/alsa-driver/+bug/271560](https://bugs.launchpad.net/alsa-driver/+bug/271560)
But I'm not sure if it will get any attention.
Kory

---

### Post by marranzano on 2008-09-20
same situation you described in the bug, but different device:
```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
```
$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xd2400000 irq 16
```
```
$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.18rc3.
Compiled on Sep 19 2008 for kernel 2.6.24-21-generic (SMP).
```

:mad:

---

### Post by wolfdude96 on 2008-09-20
Hello - I am using a tx2510us running Hardy.

After I upgraded my kernel to 2.6.26.5-ultimate in order to get CPU scaling and ACPI to work my sound died...

If I click on the volume control icon in the upper right I get the following error: "No volume control GStreamer plugins and/or devices found."

Here is /etc/modprobe.d/alsa-base:
```

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe --quiet snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm && { /sbin/modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer && { /sbin/modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq && { /sbin/modprobe --quiet snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi && { /sbin/modprobe --quiet snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel index=0 model=toshiba position_fix=1

```

In addition I can no longer edit touchpad settings as the system treats my touchpad as a mouse.

It would also be great if someone could figure out how to enable screen rotation.

Here is my xorg.conf:
```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Synaptics Pad"
	Inputdevice "stylus"	"SendCoreEvents"
	Inputdevice "touch"	"SendCoreEvents"
	Inputdevice "eraser"	"SendCoreEvents"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
EndSection

Section "InputDevice"
	Identifier  "Synaptics Pad"
	Driver      "synaptics"
	Option	    "SendCoreEvents" "true"
	Option	    "Device" "/dev/psaux"
	Option	    "Protocol" "auto-dev"
	Option	    "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "Button2" "3" # make side-switch a right button
Option "TopX" "225"
Option "TopY" "225"
Option "BottomX" "26300"
Option "BottomY" "16375"
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.1-event-"
Option "TopX" "200"
Option "TopY" "225"
Option "BottomX" "4000"
Option "BottomY" "3875"
EndSection

Section "InputDevice"
Identifier "eraser"
Driver "wacom"
Option "Type" "eraser"
Option "Device" "/dev/input/by-path/pci-0000:00:14.5-usb-0:2:1.0-event-mouse"
Option "USB" "on"
EndSection

Section "Monitor"
	Identifier   "Configured Monitor"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "Configured Video Device"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Option "RandRRotation"  "on"
	Driver      "fglrx"
	BusID       "PCI:1:5:0"
EndSection



Section "Screen"
	Identifier "Default Screen"
	Device     "Configured Video Device"
	Monitor    "Configured Monitor"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "Extensions"
        Option        "Composite"        "Disable"
EndSection

Section "ServerFlags"
       Option  "AIGLX" "off" 
EndSection


```

If I could just figure out the sound, touchpad, and rotation issues I would never have to boot into Vista again.

Thanks for your time.

---

### Post by marranzano on 2008-09-20
sound (no mic), cpu scaling and touchscreen/touchpad work with 2.6.24-21-generic...

so far no luck with _rotation_ (i guess it has to do with fglrx :mad: ), _microphone_, _two buttons_ on the bottom of the screen and _suspend_...

---

### Post by wolfdude96 on 2008-09-20
The new kernel allows the use of ACPI functionality and suspend. If only sound, rotation, and the touchpad worked well with it.

---

### Post by Dual Cortex on 2008-09-22
Oh god finally. Will try.

EDIT: Doesn't work if I don't disable ACPI, with 2.6.24-21 Generic. Why?
Blacklisting thermal doesn't seem to do anything either.

---

### Post by marranzano on 2008-09-22
> **marranzano said:**
> anyone managed to get the front mic working?? works really poorely... crackle and pops... :(
mic has improved...
not sure what i changed... could be this:
```
$ cat /etc/modprobe.d/sound 
alias snd-card-0 snd-hda-intel
alias sound-slot-0 snd-hda-intel

```
or the latest catalist 8-9 which fix an audio bug for the hd3200 :confused:

anyhow it was a good surprise... :)

---

### Post by jubej on 2008-09-22
marranzano how did you edit the /etc/modprobe.d/sound

i tryed the command you posted: $ cat /etc/modprobe.d/sound 

but it says:
            cat: /etc/modprobe.d/sound: No such file or directory
so how will i edit it then?


by the way i have ubuntu 8.10 alpha5 and it works wonderfull with the new kernel 2.6.27-3 no more acpi=off and wlan working ootb everything exept hibernation or the touchscreen/digitizer i dont know how to make it work,  Maybe there should be a forum about the tx2000 series in ubuntu 8.10?

---

### Post by Dual Cortex on 2008-09-22
I can confirm it boots up nicely with II Alpha 6, 2.6.27-4

---

### Post by Donny5 on 2008-09-23
That's good news, was that 32 or 64 bit? I only have one cd-r left...

Dónal

---

### Post by Dual Cortex on 2008-09-23
64 Bit

---

### Post by toobaz on 2008-10-03
Hello everybody, and thanks to everyone, in particular thegnark, for help.

It's now been some days I'm using my new tx2510 with 64 bit intrepid (updated daily) and it's pratically perfect. Everything works out of the box except:
- wireless: but you just have to unload ssb and wl modules, and then reload wl (LP bug 263184)
- touchscreen: the howto for Hardy doesn't apply. The 2.6.27 kernel is still not supported by wacom project (LP bug 260675), however I saw in some other post that the module for the 2.6.26 works well with it. But it seems like the intrepid default xorg.conf is less complete that the hardy default, so for instance there is no section "ServerLayout" and I can't follow the howto. I tried in several different ways to edit xorg.conf, but always got a "no screen found" at X startup
- without the ATI proprietary drivers, still no 3D and VGA/S-video. But I think that in the final version, intrepid's restricted modules manager will propose to install them (it still doesn't)
- ekiga doesn't recognize the webcam, but cheese does, so maybe it's just an ekiga problem
- suspend-to-ram needs fixing: the computer correctly goes to sleep and wakes, but then mouse and keyboard don't work no more. (I'd say LP bug 23497, the fix in [http://ubuntuforums.org/showpost.php?p=5220536&postcount=19](http://ubuntuforums.org/showpost.php?p=5220536&postcount=19) solves the problem)
- hibernation often doesn't work: approx. one time out of 2, in the resume process the pc freezes
- sometimes, the pc will freeze also in a normal startup boot, while saying something about powernowd
- the battery detection almost works, but not perfectly. I can see battery discharging, but a certain point, the computer just dies unexpectly, showing low charge indeed but without popping up "battery critical" or even "battery critical" messages

Pietro

---

### Post by gali98 on 2008-10-03
Hmmm.. I know people have gotten the wacom tablet to work. You just have to build it from source then use the module built for th 2.6.26 kernel.
And on the suspend problem. When you come back from suspend, you have to hit ctrl alt f1 then ctlr alt f7. That always works for me.
Kory

---

### Post by toobaz on 2008-10-05
> **gali98 said:**
> Hmmm.. I know people have gotten the wacom tablet to work. You just have to build it from source then use the module built for th 2.6.26 kernel.

Kory, that's what I just wrote. I'm just not able to configure xorg.conf because it's different from Hardy's one, but this is probably a trivial point, I just don't have time now for experimenting.

> **gali98 said:**
> And on the suspend problem. When you come back from suspend, you have to hit ctrl alt f1 then ctlr alt f7. That always works for me.
Kory

It doesn't for me. I just put the PC in standby, and now I'm using a USB mouse and a USB keyboard untile I reboot.

Pietro

---

### Post by Ang on 2008-10-05
I have an tx2590 and Hardy 8.04 installed with the 2.6.21 kernel and:

What works
-Sound works "out of the box"
-3D acceleration "works out of the box"
-Mic not tested
-Touchpad works, but only for the left button. (no "multitapping")
-CPU scaling works

and what does not work
-Touchscreen! The configure part from the guide doesn't work!
-Suspend works one out of three times!
-Part wise the wireless. Works like a charm when I'm close the router, but when the signal drops a bit so does the connection not work at all! (I'm using WPA2 security)

---

### Post by gali98 on 2008-10-05
> **toobaz said:**
> Kory, that's what I just wrote. I'm just not able to configure xorg.conf because it's different from Hardy's one, but this is probably a trivial point, I just don't have time now for experimenting.


Ahhh read it wrong. If you upload your xorg, I can fix it for you...

> -Touchscreen! The configure part from the guide doesn't work!
What do you mean? If you will upload your xorg also, I will fix it too.

Also if by multitapping you mean using more than one finger to do other functions, then it will not ever work. That is a hardware feature not present. That is mainly for apples but probably a few other vendors that add it.
Kory

---

### Post by fy3 on 2008-10-05
hi all,

Am using a Tx2510us.
Ran into a dead end in teh following sections of this instruction:

1. _INSTALLATION_
Starting from installing the **ubuntu-8.04.1-dvd-amd64.iso**,  i get: **Kernel panic - not syncing: VFS unable to mount (8,1)**.

It seems the only other way i can install ubuntu is to download the 699mb installers in the main website. I downloaded both of them and proceed to install the same way as instructed. 

To cut short, the link supplied in this 

2. _DIGITIZER_
Doesn't work. Can't Install. Can't download driver. Can't Extract Drivers. 

Followed the instruction as detailed in: [http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)

Hit the brick wall when attempting to install build-essential:
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

3. _ROTATING SCREEN_
After adding **Option "RandRRotation" "on"**, nothing seems to happen when i type the command **xrandr -o <whatever>**.

All i'm really confused about is the Boot Disk.
The one i downloaded from the supplied link in this thread doesn't work to begin with. That dominoed to a series of failed attempts on nearly every step along the way.

Please, if there is a Ubuntu God out there, PM me to the rescue.
Thanks

---

### Post by alromh87 on 2008-10-05
fy3
I'm not an Ubuntu God but might be abble to help you.

1. INSTALLATION
Try the intrepid beta cd [http://www.ubuntu.com/testing/intrepid/beta](http://www.ubuntu.com/testing/intrepid/beta)

2. DIGITIZER
if running Intrepid just run in a terminal 
sudo apt-get install fprint-demo libpam-fprint
sudo fprint_demo
register your finger and enable pam module by editing nano /etc/pam.d/common-auth to something like

auth    sufficient      pam_fprint.so
auth    required        pam_unix.so nullok_secure
#auth   requisite       pam_unix.so nullok_secure
auth    optional        pam_smbpass.so migrate

3. ROTATING SCREEN
I read this but I can't remember where it works for tx1000 runnning hardy and gentoo, you can create a file like /usr/bin/auto-rotate.sh  make it executable and run (it will rotate your screen 90° every time run), you could also map it to some button to act as in vista.

#!/bin/bash
orient=$(xrandr -q --verbose | awk 'NR==2{print $4}');
if [ "$orient" = "normal" ]; then
        xrandr -o right
elif [ "$orient" = "right" ]; then
        xrandr -o inverted
elif [ "$orient" = "inverted" ]; then
        xrandr -o left
elif [ "$orient" = "left" ]; then
        xrandr -o normal
fi


I hope this helps, let me know if it works or you need something else.

---

### Post by marranzano on 2008-10-06
> **fy3 said:**
> 1. _INSTALLATION_
...
It seems the only other way i can install ubuntu is to download the 699mb installers in the main website. I downloaded both of them and proceed to install the same way as instructed. 

i guess this is solved
> 2. _DIGITIZER_
Doesn't work. Can't Install. Can't download driver. Can't Extract Drivers. 
Followed the instruction as detailed in: [http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Hit the brick wall when attempting to install build-essential:
sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
can you tell us a little more? what is the response to the above command? did you enable the online repositories?
> 3. _ROTATING SCREEN_
After adding **Option "RandRRotation" "on"**, nothing seems to happen when i type the command **xrandr -o <whatever>**.

i have the same machine and we have an ati card (not nvidia)... as far as i know rotation is not supported (actually it should work with the latest fglrx but i was never able to make it work... :confused:)
> All i'm really confused about is the Boot Disk.
The one i downloaded from the supplied link in this thread doesn't work to begin with. That dominoed to a series of failed attempts on nearly every step along the way.
which boot disk? are you installing ubuntu or just using a live version?

---

### Post by fy3 on 2008-10-06
Thanks for all the suggestions.

There is a god!

This is what happened:

1. Sick of Kernel 2.6.24.19, updated and installed Kernel 2.6.24.19 (wasn't able to find Kernel 2.6.24.20 for some unknown reason).

2. Tried Wacom configuration in Kernel 2.6.21. Worked but Uncalibrated. after much tweaking, it went off again. Deleted driver and installation folder in Desktop. Reboot 

3. Switched to Kernel 2.6.24.19. Tried to config again. Soldiered on for 3 hours. Got Stylus to work but not Touch. Got sick of this again. Reboot

4. Switched to Kernel 2.6.24.21 again. MIRACLE HAPPENED! THERE IS A GOD! TOUCH & STYLUS WORKS!!!!!!!!!!!

5. No luck on Rotation as *marranzano* pointed, our devices uses ATI video cards. Any help on this, gali98? the_gnark?

Thanks

p/s: i have 3 boot disks. 2 downloaded from Ubuntu.org and one from this thread. the one in this thread does not work!

---

### Post by gali98 on 2008-10-06
I have the tx2000z which has nVidia graphics. As far as I know, from what I've read, rotation using xrandr does not work. I will look into it when I get home...
Kory

---

### Post by Ang on 2008-10-06
> **gali98 said:**
> 
What do you mean? If you will upload your xorg also, I will fix it too.

Also if by multitapping you mean using more than one finger to do other functions, then it will not ever work. That is a hardware feature not present. That is mainly for apples but probably a few other vendors that add it.
Kory

No, you don't have to put down energy to look in to it. ;) But thanks anyway. I will wait for an awesome script after the Intrepid release! ;)

When I say "multitapping" so do I mean to "tapp" with more than one finger. I think most touchpads supports it, it's only Windows which is the problem. 
For an example so will a tapp whith one finger mean "left click, two fingers will mean middle click while three fingers will mean right click.
This comes very handy since you will have a middle button support and you will get rid of the annoyance of "clicking" buttons! (and it goes smoother and faster)

It worked out of the box for my old laptop, so I really think it should  work for this one too. Maybe it works in Intrepid? Can someone comment this?

---

### Post by gali98 on 2008-10-06
Hmmm... I tried it once and it just didn't work. I pinned it to lack of hardware support. I will definately look into it because it would be a very useful feature.

On the rotation, here is a post that may help.
[http://ubuntuforums.org/showthread.php?p=5865999#post5865999](http://ubuntuforums.org/showthread.php?p=5865999#post5865999)
Kory

---

### Post by toobaz on 2008-10-07
> **gali98 said:**
> Ahhh read it wrong. If you upload your xorg, I can fix it for you...

Wow, it would be really nice. You can find the bare intrepid default xorg.conf (which is very minimal) at [http://paste.ubuntu.com/55058/](http://paste.ubuntu.com/55058/) .

My (few) tentatives all brought to X not starting, so they are quite useless...

thanks

Pietro

---

### Post by redneckProgrammer on 2008-10-07
thegnark,   
  I would really like to thank you for your detailed walk through.  I was able to get 8.04 running on my new tx2510 with your post.  Now that I found someone else's post on connecting a bluetooth mouse, I am one happy dual-booter (unfortunately need Windoze for some work/school).   Thanks, Brian
[http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)

---

### Post by gali98 on 2008-10-08
Hey Toobaz... I will gladly help. 
But first I need a little info.
First what model lappy do you own?
Second please run this command and paste the output.

ls -Rl /dev/input

Thanks, Kory

---

### Post by toobaz on 2008-10-08
> **gali98 said:**
> Hey Toobaz... I will gladly help. 
But first I need a little info.
First what model lappy do you own?

A tx2510

> **gali98 said:**
> Second please run this command and paste the output.

ls -Rl /dev/input

Thanks, Kory

Here it is... in fact, I recognize all the infos needed for the howto are there, but I had no chance in inserting them in the minimalist xorg.conf.


```

/dev/input:
totale 0
drwxr-xr-x 2 root root    120 2008-10-08 21:30 by-path
crw-rw---- 1 root root 13, 64 2008-10-08 21:30 event0
crw-rw---- 1 root root 13, 65 2008-10-08 21:30 event1
crw-rw---- 1 root root 13, 66 2008-10-08 21:30 event2
crw-rw---- 1 root root 13, 67 2008-10-08 21:30 event3
crw-rw---- 1 root root 13, 68 2008-10-08 21:30 event4
crw-rw---- 1 root root 13, 69 2008-10-08 21:30 event5
crw-rw---- 1 root root 13, 70 2008-10-08 21:30 event6
crw-rw---- 1 root root 13, 71 2008-10-08 21:30 event7
crw-rw---- 1 root root 13, 72 2008-10-08 21:30 event8
crw-rw---- 1 root root 13, 73 2008-10-08 21:30 event9
crw-rw---- 1 root root 13, 63 2008-10-08 23:30 mice
crw-rw---- 1 root root 13, 32 2008-10-08 23:30 mouse0
crw-rw---- 1 root root 13, 33 2008-10-08 21:30 mouse1

/dev/input/by-path:
totale 0
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 pci-0000:00:13.2-usb-0:2:1.0-event- -> ../event8
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-1-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-1-mouse -> ../mouse1
```

Thank you

Pietro (Toobaz)

---

### Post by gali98 on 2008-10-11
toobaz...

I'm really sorry it has taken this long for me to post back. I have not had a lot of time lately, and I just installed Intrepid (it's great!) But I am back.
First of all the problem is that the wacom driver is not installed properly.
I will pm you a package. Just look in your messages for more info. I will explain there.
Kory

---

### Post by george_a on 2008-10-12
Hello,
Thanks for the information about the live cd and getting the sound work.


It's been a week now that i am trying to get my wireless working...

I tried several HOWTOs but none of them worked.

Currently I have installed a fresh copy of Ubuntu with 2.6.24-21-generic and according to other users this should make the wireless work but still nothing...


Does any1 knows how to troubleshoot the wireless problem? Is the most important for me.... I don't care that much about the rest now...

Thank you,
George




P.S My laptop next to the "power" light it has tx2000 printed but on the service tag and in the system properties of vista is tx2500.  I am in the correct thread right ?

---

### Post by Alathald on 2008-10-16
@george_a

If you have the type N wireless card you'll have to use the proprietary drivers 
[available from Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php")...this took me quite awhile to figure out myself :-k

Now let's just hope that the rotation and xvideo issues are fixed in the new fglrx drivers...

---

### Post by Alathald on 2008-10-16
Actually, I just noticed that Broadcom drivers are now available from the repos. Just check your Restricted Hardware Drivers and they should be there under Broadcom STA Wireless Driver. 

Hopefully this will work better than the old drivers and I won't get kicked from my campuses VPN as often :shock:

---

### Post by gali98 on 2008-10-16
@Alathald
Are you on Intrepid?
The new network manager works awesome with vpn and everything.
I am on the tx2000... When I installed it the wireless work right away (There must be some free driver that also works, after that I installed the driver you mentioned and it is different.. I don't know exactly what the deal is..)
If you are having problems you might try switching (if you have not already made the leap).
Kory

---

### Post by george_a on 2008-10-17
Thanks for the reply, 
I tried that but still nothing...

In the System > Administration > Hardware Drivers it says Broadcom STA wireless driver enabled and in use but it can't find any network. I tried to use "Connect to other Network.." (left click on the two pcs icon) but after i submit the details remains at the "Attempting to join the wireless network...."

here is the  lshw -C Network if it helps..
```
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth1
       version: 01
       serial: 00:21:00:4a:a5:6c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11

```

---

### Post by Alathald on 2008-10-17
I'm still on Hardy, I had been using the old Broadcom drivers and I don't think they liked VPNs but the new STA drivers in the repos are a godsend, it's working great.

I haven't tried Intrepid yet, though the only issue I'm really having is flickering video :-k

---

### Post by gali98 on 2008-10-17
@george

first I would make sure you are entirely up to date. (If a newer kernel is added you will need to restart)
Then go back to hardware drivers and disable the Broadcom driver. Then reenable it.
If it still doesn't work, you could try  disabling it, restarting, enabling it, then restarting one more time.
Kory

---

### Post by vibhor goyal on 2008-10-21
Hi!!

I have the N type wireless, I tried the way you have mentioned, but when I try to compile it, I get stuck, as the it says that its not able to make ubuntu_headers. Please please help me on this.

Thanks


> **Alathald said:**
> @george_a

If you have the type N wireless card you'll have to use the proprietary drivers 
[available from Broadcom]("http://www.broadcom.com/support/802.11/linux_sta.php")...this took me quite awhile to figure out myself :-k

Now let's just hope that the rotation and xvideo issues are fixed in the new fglrx drivers...

---

### Post by fy3 on 2008-10-21
Hey, its me again.
Been busy with work and moving so haven't had time to update on installation.

Just wanna know, is there anyone with a TX2510US who has everything working from touch, rotate, wireless, sound, etc ?

If so, could you PM me so we could discuss this between us instead coz i really wanna trash vista for good. its been hell for me with vista and i hope its inventors burn in a stake for even thinking it up.

The forums are helpful but there are too many model with different chipsets and parts for the tx 2xxx series.

Thanks.

---

### Post by odbyt on 2008-10-22
Hi. I tried to play Guild Wars but he are freez :/ Then im tried to play Tibia and it freez too.

Im install EnvyNG drivers. What i can do?


I apologize for my english.

---

### Post by george_a on 2008-10-25
> **gali98 said:**
> @george

first I would make sure you are entirely up to date. (If a newer kernel is added you will need to restart)
Then go back to hardware drivers and disable the Broadcom driver. Then reenable it.
If it still doesn't work, you could try  disabling it, restarting, enabling it, then restarting one more time.
Kory

Thank you for your reply, however nothing changed...

I ve installed the new beta version of ubuntu and it worked from the first time!!

---

### Post by gali98 on 2008-10-25
Well... I guess that works too. :)
Glad to here it. I love intrepid....
Kory

---

### Post by vibhor goyal on 2008-10-29
Hi!!

I have hp tx2500 with Wireless N card (broadcom BCM4322), I have been trying a lot to get the wireless but to no positives as of now. Please help me out!

P.S. : I have already tried the native broadcom's drivers and ndiswrapper, and my kernel version is 21 and OS is ubuntu 8.04 64 bit edition.

Thanks in Advance!

---

### Post by vibhor goyal on 2008-10-29
> **Ununtu said:**
> Hi everyone.

I've just tried to install Ubuntu on my TX2520ef following this tutorial, but I could'nt get it to work correctly (especialy for the digitizer). I tried twice reintsalling, but there's still the same mess. As I start looking around, I'm finding more and more bugs:
- digitzer doesn't work (already posted the bug on the Tablet-PC thread)
- [FIXED]batteries not recognised (they work, but it always tells me I'm on AC, even when I've booted on the battery)
- [FIXED] no wifi detection (the update with the preposed repositories made the wifi appear on the Networkmanager, but i don't detect the network). this might have to do with the fact that the wifi button (on the front of the computer) doesn't respond and is always orange (=off)
- [FIXED] computer doesn't correctly shut down : it stop at "Will now halt", but just stays on. and and not have the "Suspend to RAM" button/option
- Vista can't be booted, even if it appears in Grub (I get this error: the winload.exe file is either missing or damaged) I've pt Grub on the MBR, it's problably the orgin of this problem. I'll deal with this later

I'm wondering if this could come from the fact that I tried keeping Vista (only for some time, don't worry), so the dual-boot might have caused some problems...?? I'm a bit too new in the Linux world to understand all this:( Maybe all this is just one mistake I made at the beggining, but I paid attention to what I was doing and didn't see a glich...

If any of you has dual-boot and a fonctionnal PC, let me know, so I can find out if the problem is there or if I have to look elsewhere. (If you have any ideas or tips, don't hesitate!)

Thanks a lot.

EDIT: I fixed some of the bug: looking at the updates in the tutorial, I realised I had a bad translation of the end of the tutorial, so I had left the "acpi=off" mode at each boot. My bad.

hey!! I have the same problem with my wireless as you have, please give me directions on how u fixed this.

---

### Post by gali98 on 2008-10-29
I suggest waiting one day, and installing Intrepid. (it comes out tomorrow!)
It has much better support in most areas of hardware.
Kory

---

### Post by vibhor goyal on 2008-10-29
I just tried 8.10 RC and it worked with wonders... amazing.. I didn't even turn off the acpi... kudos to ubuntu developers.

---

### Post by alexpwalsh on 2008-10-30
Hey All, how about Intrepid Ibex wireless and WPA2 Enterprise???? I'm lost and my campus only has WPA2 Enterprise......

---

### Post by TheBernok on 2008-11-01
Hi, I have a few questions for those who already upgraded their TX2500 to 8.10. 

Did it fix some (or all of the issues) in the first post?

> Known issues:

    * Digitizer mostly works (but not 100%)
    * CPU scaling is NOT supported by current kernel
    * Suspend/sleep is a bit flaky

Is "acpi=off" still needed?

If I follow the guide (first post) would it run smooth in 8.10? If not, which are the current issues you are experiencing?

---

### Post by gali98 on 2008-11-01
I said the same in my pm, but for both places, no you should not have to do the acpi=off
Kory

---

### Post by marranzano on 2008-11-01
this is my current situation with tx2510us:
intrepid ibex fresh install...

ubuntu boots fine without any kernel options!
Thermal was giving me trouble (/proc/acpi/thermal_zone/ was empty) -> solved with a bios update 
cpu scaling works with powernowd

wacom works fine -> had to change xorg.conf as in attachment
ati hd3200 rotates!!! -> i guess it's either the radeon or the radeonhd driver (no 3d) but i'm so pleased of the rotation. anyone know if fglrx rotate?
audio -> had to add "options snd-hda-intel model=toshiba" to /etc/modprobe.d/alsa-base
wireless works fine (wpa...).
suspend to ram worked with [_this workaround_]("http://ubuntuforums.org/showpost.php?p=5220536&postcount=19")

webcam works once after boot and then goes dead!!?

still have to check microphone, remote...

---

### Post by gali98 on 2008-11-01
The webcam is still a little weird.... What program are you using?
I think rotate does work with fglrx. I just saw today somewhere in one of the tx2500 threads that it should work. The forums are messing up right now so I can't find it.
Kory

---

### Post by marranzano on 2008-11-02
> **gali98 said:**
> The webcam is still a little weird.... What program are you using?
using cheese... works after a fresh boot, then if i restart cheese it doesnt work anymore...
> I think rotate does work with fglrx. I just saw today somewhere in one of the tx2500 threads that it should work. The forums are messing up right now so I can't find it.
Koryi'd love to read that post if you find it... just changed to fglrx 8.10, got 3d but no rotation```
~$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 800
default connected 1280x800+0+0 0mm x 0mm
   1280x800       60.0* 
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x432        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
```:(

any advice for the remote?

---

### Post by toobaz on 2008-11-02
Kory: I'm very sorry I didn't answer to your PMs. I did check daily, but... well, apparently I did not know **where** one's PMs are, and only now I discovered...

Anyway: I'm posting you again the result of "ls -Rl /dev/input":

```
/dev/input:
totale 0
drwxr-xr-x 2 root root    120 2008-10-08 21:30 by-path
crw-rw---- 1 root root 13, 64 2008-10-08 21:30 event0
crw-rw---- 1 root root 13, 65 2008-10-08 21:30 event1
crw-rw---- 1 root root 13, 66 2008-10-08 21:30 event2
crw-rw---- 1 root root 13, 67 2008-10-08 21:30 event3
crw-rw---- 1 root root 13, 68 2008-10-08 21:30 event4
crw-rw---- 1 root root 13, 69 2008-10-08 21:30 event5
crw-rw---- 1 root root 13, 70 2008-10-08 21:30 event6
crw-rw---- 1 root root 13, 71 2008-10-08 21:30 event7
crw-rw---- 1 root root 13, 72 2008-10-08 21:30 event8
crw-rw---- 1 root root 13, 73 2008-10-08 21:30 event9
crw-rw---- 1 root root 13, 63 2008-10-08 23:30 mice
crw-rw---- 1 root root 13, 32 2008-10-08 23:30 mouse0
crw-rw---- 1 root root 13, 33 2008-10-08 21:30 mouse1

/dev/input/by-path:
totale 0
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 pci-0000:00:13.2-usb-0:2:1.0-event- -> ../event8
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-1-event-mouse -> ../event9
lrwxrwxrwx 1 root root 9 2008-10-08 21:30 platform-i8042-serio-1-mouse -> ../mouse1
```

I see everyone is talking about fixing xorg.conf... but wouldn't now adding a .fdi file to hal configuration the right way to fix things? (but is there anywhere some documentation about fdi's?!)

P.S: you can forget my PM at this point

---

### Post by toobaz on 2008-11-02
Just one more thing: is using the upstream wacom module now useless? The deb package in the archives is OK?

---

### Post by marranzano on 2008-11-02
> **toobaz said:**
> ...I see everyone is talking about fixing xorg.conf... but wouldn't now adding a .fdi file to hal configuration the right way to fix things? (but is there anywhere some documentation about fdi's?!)...
perhaps you're right... but my xorg.conf works...
you can find it here:
[http://ubuntuforums.org/showpost.php?p=6083093&postcount=80](http://ubuntuforums.org/showpost.php?p=6083093&postcount=80)
it seems the crucial part is
```
Section "ServerFlags"
        Option "AutoAddDevices" "False"
EndSection
```

---

### Post by harak on 2008-11-02
> **gali98 said:**
> The webcam is still a little weird.... What program are you using?
I think rotate does work with fglrx. I just saw today somewhere in one of the tx2500 threads that it should work. The forums are messing up right now so I can't find it.
Kory


Gali and Marranzano

Here's the site which talks about rotation in 8.9... intrepid has 8.10 I guess.
[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1)


But looks like the address keeps chaging... Anyway, all one (with tx2500) needs to do is run the following
sudo  aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"

---

### Post by gali98 on 2008-11-02
Okay.. 
This is that article about the xrandr (rotation)
[http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_89_linux&num=1)
I think you have to enable xrandr in xorg.conf....

Edit: Harak beat me to it... Thanks...
On the HAL and fdi files and alll of that..... I have no idea what it is. I know the basics of HAL and basically an fdi file just tells HAL how to detect devices and what to do with them.....
But there isn't much info out there on them..... and not using them works also (how we've always done it)

As far as I have tested, the deb wacom packages in Intrepid do not work. I have not signigicantly tested it though. I think it puts in fdi files and stuff, and with those packages, you may not need to configure the xorg.conf at all.

But I don't have time to mess with it now.. and the old way works for me...

I didn't need that flag in the xorg.conf... I just purged all the config files from the wacom packages...

sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom

If I missed anything please post back and remind me....
Kory

---

### Post by marranzano on 2008-11-02
> **harak said:**
> ... But looks like the address keeps chaging... Anyway, all one (with tx2500) needs to do is run the following
sudo  aticonfig --set-pcs-str="DDX,EnableRandr12,TRUE"
YEAHHHHHH!!!!!!!!!!!!!  it works!!!!!!

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
LCD connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x432        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
```


U made my day :guitar:

tnx...

---

### Post by BaronVonJimmy on 2008-11-03
Firstly, thanks very much for your help here, Kori and Thegnark! It's been a great help.

Here are my experiences installing 8.10 on my new tx2500.

[INDENT]1) Installation was smooth out of the box. Wireless drivers and fglrx, which have been a pain on older machines/distro's seem to install smoothly. I did need the one line workaround to get sound. Everything else not listed below seems to work fine (Webcam, CPU Scaling, etc).

2) The wacom. I'm not sure if the repository driver works or not, I don't think I gave it a working xorg.conf. Kory's tutorial worked nicely however. My only quibble is that after the compilation step, the wacom didn't respond to screen touching where the instructions said it would. After providing a working xorg.conf though, the wacom works.

3) So far, I've got rotation to work, but only reliably with the 'radeon' driver. See 4a for my problems.

4) Things that I'm still looking into...
[INDENT]a) Rotation works with the aticonfig line (see earlier posts) while using the 'fglrx' driver, however it doesn't play nice with compiz (no refreshing), and when the rotation isn't 'normal' the mouse cursor is badly offset and not rotated with the screen.
b) Suspend and Hibernate. Suspend hangs on resume under fglrx for me, while under radeon my touchpad and keyboard cease to function. I've not tried hibernating with fglrx, but with radeon it works ok, however non-X screens are corrupted until reboot.
c) Fingerprint reader and Multimedia buttons. I've not tried anything here yet.[/INDENT][/INDENT]

I'll get there soon though. Thanks again. My Ubuntu installation is very much usable on this tablet!

---

### Post by gali98 on 2008-11-03
Glad you got it working... I fixed my tutorial to tell people to restart.
You didn't have to do this in Hardy, but you do in Intrepid for whatever reason...
Thanks for the feedback!
Kory

---

### Post by alexpwalsh on 2008-11-04
Could someone please start this thread again with 8.10, 9 pages is too much to read through. I'm having problems with WPA2 at my University, and only with my model... it seems that others are not having any problems..... thoughts?

---

### Post by gali98 on 2008-11-04
Trust me, there are plenty of threads out there on this model of laptop....
Just search the thread for specific things...
on your issue, I already posted on the other thread, but I will duplicate it here for you:

This is a post about it:
[http://ubuntuforums.org/showthread.php?t=970236](http://ubuntuforums.org/showthread.php?t=970236)

also, as that post says, WICD may help.
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Kory

---

### Post by harak on 2008-11-04
> **marranzano said:**
> YEAHHHHHH!!!!!!!!!!!!!  it works!!!!!!

```
$ xrandr -q
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 1280 x 1280
LCD connected 1280x800+0+0 (normal left inverted right x axis y axis) 261mm x 163mm
   1280x800       60.0*+
   1280x768       60.0  
   1280x720       60.0  
   1024x768       60.0  
   800x600        60.0  
   720x480        60.0  
   640x480        60.0  
   640x432        60.0  
   640x400        60.0  
   512x384        60.0  
   400x300        60.0  
   320x240        60.0  
   320x200        60.0  
CRT1 disconnected (normal left inverted right x axis y axis)
TV disconnected (normal left inverted right x axis y axis)
```


U made my day :guitar:

tnx...

Always there to help!. 

But does it work always? Sometimes my screen would go all black. I retained the open source radeon driver... doesn't seem to conflict with fglrx! and stopped having those black screens.

---

### Post by BaronVonJimmy on 2008-11-05
> **harak said:**
> Always there to help!. 

But does it work always? Sometimes my screen would go all black. I retained the open source radeon driver... doesn't seem to conflict with fglrx! and stopped having those black screens.

Hi there.

My problem with fglrx is that it wouldn't play nice with Compiz. The screen would stop refreshing if rotated to any orientation other than 'normal'. Turning Compiz Effects off fixed this, and I believe the problem is also fixed in the git version of Compiz Fusion. 

However rotation under fglrx and general tablet use is still unusable(IMO) because of the mouse cursor problems, where it is often inverted and in the wrong place on screen. Back to the radeon driver for me.

---

### Post by harak on 2008-11-05
> **gali98 said:**
> Okay.. 

Edit: Harak beat me to it... Thanks...
On the HAL and fdi files and alll of that..... I have no idea what it is. I know the basics of HAL and basically an fdi file just tells HAL how to detect devices and what to do with them.....
But there isn't much info out there on them..... and not using them works also (how we've always done it)

As far as I have tested, the deb wacom packages in Intrepid do not work. I have not signigicantly tested it though. I think it puts in fdi files and stuff, and with those packages, you may not need to configure the xorg.conf at all.

But I don't have time to mess with it now.. and the old way works for me...

I didn't need that flag in the xorg.conf... I just purged all the config files from the wacom packages...

sudo apt-get install wacom-tools xserver-xorg-input-wacom
sudo apt-get purge wacom-tools xserver-xorg-input-wacom

If I missed anything please post back and remind me....
Kory


Thanks for the suggestion. As you said its to much work done. Right now my system works ok... I have seen some of your tutorials on using the multimedia buttons on panel. Bad news with tx2500 is that "xev" command doesn't show any keykodes for any of those panel buttons. If you find something please let me know!

Thanks in advance

---

### Post by harak on 2008-11-05
> **BaronVonJimmy said:**
> Hi there.

My problem with fglrx is that it wouldn't play nice with Compiz. The screen would stop refreshing if rotated to any orientation other than 'normal'. Turning Compiz Effects off fixed this, and I believe the problem is also fixed in the git version of Compiz Fusion. 

However rotation under fglrx and general tablet use is still unusable(IMO) because of the mouse cursor problems, where it is often inverted and in the wrong place on screen. Back to the radeon driver for me.

have you tried this to get rotate screen and also change mouse position. The mouse position is not handled by fglrx. wacom is the right one.
xrandr -o left 
xsetwacom set stylus ROTATE "CCW"
xsetwacom set eraser ROTATE "CCW"
xsetwacom set Touch ROTATE "CCW"

To get everything back to normal:

xrandr -o  normal
xsetwacom set stylus ROTATE "NONE"
xsetwacom set eraser ROTATE "NONE"
xsetwacom set Touch ROTATE "NONE"

---

### Post by harak on 2008-11-05
@BaronVonJimmy

Also I haven't uninstalled the open source radeon driver. Doesn't seem to conflict fglrx. rotation with compiz works fine. May be I should try using git version. I have problems with compiz when I use graphics from remote servers.
Thanks for the tip!

---

### Post by gali98 on 2008-11-05
Harak, see here for help on the keycodes:
[http://ubuntuforums.org/showpost.php?p=6090433&postcount=336](http://ubuntuforums.org/showpost.php?p=6090433&postcount=336)
Kory

---

### Post by harak on 2008-11-05
> **gali98 said:**
> Harak, see here for help on the keycodes:
[http://ubuntuforums.org/showpost.php?p=6090433&postcount=336](http://ubuntuforums.org/showpost.php?p=6090433&postcount=336)
Kory

Kory,
   i could reproduce the results of that site... But the buttons seem respond only in the console(ctr+alt+f1-6) and not when my desktop(ctr-alt-f7) is on. I have mapped  the keys to some other applications to check if they are working.. but could not launch them. 

I am at my wits end

---

### Post by gali98 on 2008-11-05
Okay do this:

sudo service hotkey-setup restart

note: this does the same exact thing as
sudo /etc/init.d/hotkey-setup restart
in Intrepid they added the command service bascially so you don't have to type so long :)
This worked on my lappy.
Try that for now... and then test it with xev. Then let me remember how to make it start on reboot, as right now you will lose the settings if you reboot. I got it to work on Hardy. will post back soon.
Kory

---

### Post by gali98 on 2008-11-05
Okay got it!

run these two commands and you should be set (as long as running that command works, and it should!)
  
  sudo update-rc.d -f hotkey-setup remove 
  
  sudo update-rc.d hotkey-setup start 99  6 5 4 3 2 1 .

(don't forget the period at the end!)
It worked for me after restarting...
Hope it works for you!
Kory

---

### Post by harak on 2008-11-05
It works. the DVD button starts totem. xev recognizes the refresh button!

You are great!

---

### Post by gali98 on 2008-11-05
Well I try! :)
Glad to hear it...
I found that after hours of searching. I had killed my keyboard, and all the keys were messing up. I got lucky and ran the right command, then worked from there.
I guess thats how all the cool stuff is found, by breaking it first :)
Kory

---

### Post by BaronVonJimmy on 2008-11-06
> **harak said:**
> have you tried this to get rotate screen and also change mouse position. The mouse position is not handled by fglrx. wacom is the right one.
xrandr -o left
xsetwacom set stylus ROTATE "CCW"
xsetwacom set eraser ROTATE "CCW"
xsetwacom set Touch ROTATE "CCW"

To get everything back to normal:

xrandr -o normal
xsetwacom set stylus ROTATE "NONE"
xsetwacom set eraser ROTATE "NONE"
xsetwacom set Touch ROTATE "NONE"

> **harak said:**
> @BaronVonJimmy

Also I haven't uninstalled the open source radeon driver. Doesn't seem to conflict fglrx. rotation with compiz works fine. May be I should try using git version. I have problems with compiz when I use graphics from remote servers.
Thanks for the tip!

Yep. Those the commands I'm using.

Under 'radeon' everything seems to work fine, apart from the usual lack of 3D accelleration.

Under 'fglrx' without compiz, whenever my screen orientation is not 'normal', ie. after xrandr -o, my mouse cursor (not the position, but the actual pointer on screen) is not rotated. When I click, it's as though it's horribly uncalibrated. This happens with mice and the touchpad too, not just my tablet, so I'm presuming it's something to do with the display driver.

And Under 'fglrx' with compiz, I get the same problem, but additionally the screen completely stops refreshing, except for the mouse pointer, after a rotate.

These last two may be down to my xorg.conf file, which is rather minimal apart from the Wacom entries and 'fglrx' or 'radeon' as necessary. I'll look into the 3D drivers again at some point, though today I'll have a go with the screen media buttons.

---

### Post by marranzano on 2008-11-06
> **gali98 said:**
> ...
run these two commands and you should be set (as long as running that command works, and it should!)
  
  sudo update-rc.d -f hotkey-setup remove 
  
  sudo update-rc.d hotkey-setup start 99  6 5 4 3 2 1 .
...
thanx Kory, worked for me too...

any idea for the other two keys on the monitor?

how do i get the remote to work?

thanx

---

### Post by harak on 2008-11-06
BaronVonJimmy,
  I remember i had similar problem but not with the mice. I will have to check it after I uninstall readeon (soon).

The screen refresh problem was there but it was random. So I installed radeon along with fglrx. The problem seems solved. Though now I dont know which driver is actually working or if both are working.

You may want to try it!

*EDIT*
I do have 3d working alond with xrandr.

---

### Post by harak on 2008-11-06
BaronVonJimmy

I checked even without radeon. It works ok for me. There must be someway to debug your case (I am no expert!).

I am attaching my xorg.conf for you to compare to start with.

---

### Post by harak on 2008-11-06
*EDIT*

My bad! 

It does not work under compiz without radeon! I did not realize i was working with Metacity. The mice doesn't even respond for me!

---

### Post by harak on 2008-11-06
BaronVonJimmy
If you still want to run fglrx and donot mind using metacity when you have your screen rotated the following will work

        xrandr -o left
	metacity --replace&
	xsetwacom set stylus ROTATE "CCW"
	xsetwacom set eraser ROTATE "CCW"
	xsetwacom set Touch ROTATE "CCW"

        xrandr -o normal
	compiz --replace&
	xsetwacom set stylus ROTATE "NONE"
	xsetwacom set eraser ROTATE "NONE"
	xsetwacom set Touch ROTATE "NONE"

This doesn't solve the real problem. but you can use the compositing when you are in normal mode and no compositing when rotated. I never found any use for compositing in the rotated mode. 

Have you installed the git version, by the way?

---

### Post by laurentp on 2008-11-07
Hi everyone,

first of all I'm so happy to be freed from Vista that came preloaded with this machine, you couln'd imagine... So thank you all. But right now I'm having some problems with my tx2524ca... The laptop randomly and completely freezes ( can't hit ctrl-alt-backspace, ctrl-alt-delete and have to remove power). Sometimes the caps-lock key flash when it's frozen. I think I've tracen down the problem but I'm not sure. My wireless disconnect/reconnect several times before the crash so it may be related to some issues that were reported before. It's difficult to isolate the crash because it happens kind of rarely... Here is some maybe pertinent output that I could find :
in my kernel log
```
Nov  6 17:07:48 larrylaptop-Intrepid kernel: [ 3556.247495] hda-intel: IRQ timing workaround is activated for card #0. Suggest a bigger bdl_pos_adj.
Nov  6 17:08:15 larrylaptop-Intrepid kernel: [ 3582.924901] usb 4-1: reset low speed USB device using ohci_hcd and address 3 
```

the second line is repeated a lot of times. My usb mouse was repeatedly flashing also. And in the syslog :

```
ov  6 22:15:07 larrylaptop-Intrepid avahi-daemon[4961]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.1.101.
Nov  6 22:15:07 larrylaptop-Intrepid avahi-daemon[4961]: New relevant interface eth1.IPv4 for mDNS.
Nov  6 22:15:07 larrylaptop-Intrepid avahi-daemon[4961]: Registering new address record for 192.168.1.101 on eth1.IPv4.
Nov  6 22:15:08 larrylaptop-Intrepid NetworkManager: <info>  (eth1): device state change: 7 -> 8 
Nov  6 22:15:08 larrylaptop-Intrepid NetworkManager: <debug> [1226027708.130412] periodic_update(): Roamed from BSSID 00:0F:66:BF:16:C1 (johnny) to (none) ((none)) 
Nov  6 22:15:08 larrylaptop-Intrepid NetworkManager: <info>  Policy set 'Auto johnny' (eth1) as default for routing and DNS. 
Nov  6 22:15:08 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) successful, device activated. 
Nov  6 22:15:08 larrylaptop-Intrepid NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete. 
Nov  6 22:15:10 larrylaptop-Intrepid ntpdate[11403]: adjust time server 91.189.94.4 offset -0.030000 sec
Nov  6 22:16:38 larrylaptop-Intrepid NetworkManager: <debug> [1226027798.195557] periodic_update(): Roamed from BSSID (none) ((none)) to 00:0F:66:BF:16:C1 (johnny) 
Nov  6 22:16:39 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 7 -> 3 
Nov  6 22:16:39 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 3 -> 0 
Nov  6 22:16:44 larrylaptop-Intrepid NetworkManager: <debug> [1226027804.198870] periodic_update(): Roamed from BSSID 00:0F:66:BF:16:C1 (johnny) to (none) ((none)) 
Nov  6 22:16:44 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
Nov  6 22:16:46 larrylaptop-Intrepid kernel: [22094.784647] usb 4-1: reset low speed USB device using ohci_hcd and address 3
Nov  6 22:16:48 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 2 -> 0 
Nov  6 22:16:50 larrylaptop-Intrepid NetworkManager: <info>  (eth1): supplicant connection state change: 0 -> 2 
```

with a lot of things before that I won't put to expand uselessly. Hopefully it can be fixed and I will try to make work my touchscreen that for some reasons just don't work with all that have been said in this thread. I can put more detailed logs if you want. Maybe I sould fill a bug report but I would like to know the problem more before. Sorry for the big message,

Laurent

---

### Post by BaronVonJimmy on 2008-11-07
> **harak said:**
> BaronVonJimmy
If you still want to run fglrx and donot mind using metacity when you have your screen rotated the following will work

        xrandr -o left
	metacity --replace&
	xsetwacom set stylus ROTATE "CCW"
	xsetwacom set eraser ROTATE "CCW"
	xsetwacom set Touch ROTATE "CCW"

        xrandr -o normal
	compiz --replace&
	xsetwacom set stylus ROTATE "NONE"
	xsetwacom set eraser ROTATE "NONE"
	xsetwacom set Touch ROTATE "NONE"

This doesn't solve the real problem. but you can use the compositing when you are in normal mode and no compositing when rotated. I never found any use for compositing in the rotated mode. 

Have you installed the git version, by the way?

At least, it's solved my cursor problem! For some reason reloading metacity or compiz corrects the orientation and position of the mouse pointer.

I'm going to try git tonight and work on the front panel buttons over the weekend. I'll report back when I'm done.

---

### Post by harak on 2008-11-07
> **BaronVonJimmy said:**
>  For some reason reloading metacity or compiz corrects the orientation and position of the mouse pointer.


You got orientation correction on reloading compiz?
Doesn't work that way for me!

---

### Post by harak on 2008-11-07
> **laurentp said:**
> Hi everyone,

first of all I'm so happy to be freed from Vista that came preloaded with this machine, you couln'd imagine... So thank you all. But right now I'm having some problems with my tx2524ca... The laptop randomly and completely freezes ( can't hit ctrl-alt-backspace, ctrl-alt-delete and have to remove power). Sometimes the caps-lock key flash when it's frozen. I think I've tracen down the problem but I'm not sure. My wireless disconnect/reconnect several times before the crash so it may be related to some issues that were reported before. It's difficult to isolate the crash because it happens kind of rarely... Here is some maybe pertinent output that I could find :
with a lot of things before that I won't put to expand uselessly. Hopefully it can be fixed and I will try to make work my touchscreen that for some reasons just don't work with all that have been said in this thread. I can put more detailed logs if you want. Maybe I sould fill a bug report but I would like to know the problem more before. Sorry for the big message,

Laurent

Are you running compiz? If so what are your power settings?

---

### Post by laurentp on 2008-11-07
> **harak said:**
> Are you running compiz? If so what are your power settings?

I was not running compiz at the time my computer crashed. I had the problem of connect/disconnect of the wireless today, I disabled my wireless and my computer didn't crash so I'm really starting to suspect the wireless. What do you mean by power settings? I haven't touch them so they should be default. Thanks for your time,

Laurent

---

### Post by harak on 2008-11-07
@laurentp
Well I asked that because I have this problem (keyboard freezing) when running compiz... So I have set my power and screen saver settings not to stop display or start screensaver when Idle. I thought you might have a related problem. I do not remember what the default power settings were.

---

### Post by BaronVonJimmy on 2008-11-07
> **harak said:**
> You got orientation correction on reloading compiz?
Doesn't work that way for me!

The mouse pointer problem I mentioned seems to disappear when the window manager is reloaded.

Therefore my only problem now is the lack of screen refreshing in compiz, after rotating using xrandr. I've sucessfully installed the git version using [http://forum.compiz-fusion.org/showthread.php?t=7744](http://forum.compiz-fusion.org/showthread.php?t=7744), but it seems no different (apart from the extra compiz effects). Problem after rotating is still there.

---

### Post by harak on 2008-11-07
Hey baronvonjimmy 
I found something... 
When I have compiz on and when the screen is in normal mode. fgl_glxgears reports around 33fps (my lcd sactually has a refresh rate of 60fps). You see that compiz has its limitations. 

without compiz I get 60 fps as it should be

when I have the screen rotated and without compiz, fgl_glxgears reports just 20 fps. No doubt then that when compiz is on the refresh rate is far lesser and thats why we have the problem. 


The problem in part is with compiz... But its more with fglrx.  But this is only the second version (with randr) which is out. So we gotta wait and probably put a bug report.

So installing any version of compiz wont help. A compositing software is, I think, something that should consume resources.

---

### Post by gali98 on 2008-11-07
@marranzano

Those two keys will not work. Somehow, a driver needs to be written for them, as I don't guess they come through with the rest of the keyboard input.

On the remote, I'm not quite sure, as mine works by default.
My guess would be to start with xev, and see if you can get input. From there, you can map the keycodes to keys.

@laurent
Did you do step 1 of this tutorial (blacklist thermal)
As far as I know (and correct me if I'm wrong :))
in Intrepid this is not necessary. Also, are you using the restricted wireless driver?
Kory

---

### Post by BaronVonJimmy on 2008-11-08
> **harak said:**
> Hey baronvonjimmy 
I found something... 
When I have compiz on and when the screen is in normal mode. fgl_glxgears reports around 33fps (my lcd sactually has a refresh rate of 60fps). You see that compiz has its limitations. 

without compiz I get 60 fps as it should be

when I have the screen rotated and without compiz, fgl_glxgears reports just 20 fps. No doubt then that when compiz is on the refresh rate is far lesser and thats why we have the problem. 


The problem in part is with compiz... But its more with fglrx.  But this is only the second version (with randr) which is out. So we gotta wait and probably put a bug report.

So installing any version of compiz wont help. A compositing software is, I think, something that should consume resources.

Yep, similar results.
fgl_glxgears, compiz: 19FPS + Flickering
fgl_glxgears, metacity: ~500FPS
fgl_glxgears, metacity, xrandr -o inverted: 42FPS

I had thought the git version might be a fix since there's a bug report similar to my problem marked as fixed. Although it was for an intel card.


On a different note I got my keycodes from ./getkeycodes as detailed earlier. Additionally that button that enables/disables the touchpad is mapped to code 216(on) and 217(off), and the lid(screen down) is mapped to 227. Added the values to my .Xmodmap and they seem to be bindable, but for some reason don't take the names I actually set them in my .Xmodmap file.

---

### Post by laurentp on 2008-11-08
> **gali98 said:**
> @marranzano

@laurent
Did you do step 1 of this tutorial (blacklist thermal)
As far as I know (and correct me if I'm wrong :))
in Intrepid this is not necessary. Also, are you using the restricted wireless driver?
Kory

Hi,
I've not blacklisted thermal as I saw that it wasn't necessary. I'm using the free driver for wireless but I will try the restricted to see if it does the same thing. Maybe I should do a bug report for the driver as it seems to be driver-related.

Laurent

---

### Post by gali98 on 2008-11-08
Okay.. that is probably it. Post back if you will and give the results :)
thanks,
Kory

---

### Post by tutonien on 2008-11-09
Hello all,

First, I would like to thank you for all the support you provide here, especially thegnark and kory whose howtos got me started.

That said, I eventually managed to make a call with Skype. I'm on Interpid and everything does not work like a charm but I really wanted Skype, so hopefully this will be useful to someone here.

See my screenshot in attachment for the details. I think everything you need is there but I may be wrong because I can't remember all the settings I have played with. On the screenshot are:
[LIST]
[*]/home/your_username/.asoundrc : this file is suggested by the [pulseaudio perfect setup guide]("http://www.pulseaudio.org/wiki/PerfectSetup#Skype"). In my case, I did not modify /etc/pulse/daemon.conf as suggested in the first step of the tutorial (because I'm a noob and I was scared :frown:). The "pcm.copy" paragraph may be useless for Skype but it was necessary to make [FONT="Lucida Console"]arecord[/FONT] work like in the man page. This file is necessary before the next step.
[*]Skype's audio settings ("son entrant" is the French for "input sound", "son sortant" means "output sound" and "sonnerie" stands for "ring")
[*][FONT="Lucida Console"]gnome-volume-control[/FONT]: here, you might want to tick all the boxes after clicking the "Preferences" button, then you'll be able to switch from "Mic" (which seems to be the mic you plug) to "Front mic" (which the one embedded in the screen). Also check the mic boosts here and there
[/LIST]

With all of this, I was able to make a call while playing music with Exaile or watching a Youtube video which means that Skype can ring while you do other things.

So far, I still cannot record anything using [FONT="Lucida Console"]gnome-sound-recorder[/FONT] (it freezes after clicking on stop).

Note: I have the TX2520EF and Skype is the version 2.0.0.72 from the medibuntu repository. All of this may apply to Hardy but I did not test

---

### Post by laurentp on 2008-11-09
I've tried the restricted driver and the same problem happened. My computer froze 2 times yesterday while I was doing a lab report in LaTeX... Nothing in dmesg, some things that looks inoffensive in syslog, it's really a strange and annoying problem. Maybe it's the network manager... I'll try WICD when I have some time. I've saved my syslog from the time of connection to the time of crash : [http://pastebin.com/m7f915a7b](http://pastebin.com/m7f915a7b) . If your want more logs, just ask me... I don't know how I could make them more verbose... 

By the way, how did you guys made work the touch screen? I've tried the 2 options here ([https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)) and I've absolutely nothing... Thanks for your help,

Laurent

---

### Post by gali98 on 2008-11-09
That will not work Laurentp... thats for normal wacom tablets (and it doesn't work that great either :))
Here is my tutorial:
[http://ubuntuforums.org/showthread.php?p=5469447#post5469447](http://ubuntuforums.org/showthread.php?p=5469447#post5469447)
Kory

---

### Post by harak on 2008-11-10
> **BaronVonJimmy said:**
> Yep, similar results.
fgl_glxgears, compiz: 19FPS + Flickering
fgl_glxgears, metacity: ~500FPS
fgl_glxgears, metacity, xrandr -o inverted: 42FPS

I had thought the git version might be a fix since there's a bug report similar to my problem marked as fixed. Although it was for an intel card.


On a different note I got my keycodes from ./getkeycodes as detailed earlier. Additionally that button that enables/disables the touchpad is mapped to code 216(on) and 217(off), and the lid(screen down) is mapped to 227. Added the values to my .Xmodmap and they seem to be bindable, but for some reason don't take the names I actually set them in my .Xmodmap file.


Try this:

[http://wiki.cchtml.com/index.php/Performance_Issues](http://wiki.cchtml.com/index.php/Performance_Issues)

After that I had significant improvement. Also it is clearly written that the driver is still not good enough for compiz.

500 FPS! what card is it? I am sure its not hd 3200 that I have. Else I will have a lot of questions

---

### Post by BaronVonJimmy on 2008-11-10
> **harak said:**
> Try this:

[http://wiki.cchtml.com/index.php/Performance_Issues](http://wiki.cchtml.com/index.php/Performance_Issues)

After that I had significant improvement. Also it is clearly written that the driver is still not good enough for compiz.

500 FPS! what card is it? I am sure its not hd 3200 that I have. Else I will have a lot of questions

Output of a quick fgl_glxgears
```
Using GLX_SGIX_pbuffer
1595 frames in 5.0 seconds = 319.000FPS
1742 frames in 5.0 seconds = 348.400FPS
```
Note quite 500.
Output of fglrxinfo
```
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD3200 Graphics
OpenGL version string: 2.1.8087 Release
```

I can't think of anything unusual I've done, 3D wise. Just installed the restricted drivers is about all!

I've also added the two lines from that link you gave, (Thanks for that too!). I now get 40FPS while the screen is inverted, which is a bit better than 20. In compiz, fgl_glxgears flickers something awful still, only at around 10FPS

---

### Post by harak on 2008-11-10
BaronVonJimmy   
Same here too!

---

### Post by chrono144 on 2008-11-11
I have an audio related question,
I edited my alsa-base with 
options snd-hda-intel index=0 model=toshiba position_fix=1
and it works, I have sound and everything, but when there is an alert sound or error sound, the sound is still the on board speaker (the one that makes a very loud beep before you are in an OS)
I was wondering if anyone was familiar with this, and if I could reassign that sound to alsa (I have already looked under system>preferences>sound)
but basically I want the ability to mute my computer completely when I'm in class, but even when alsa is muted, the alert sound still sounds because it is not going through the sound card...
anyway, thanks!

---

### Post by tutonien on 2008-11-11
Hi chrono144,

Add 
[FONT=Lucida Console]
blacklist pcspkr[/FONT]

on a new line at the end of

[FONT=Lucida Console]/etc/modprobe.d/blacklist

And I don't know if it's necessary but I also went to gnome-volume-control and if you click on prefences and check the "Beep" device, then its channel is displayed with others, so you can mute it.
[/FONT]

---

### Post by gali98 on 2008-11-11
You probably only need to blacklist the module.. That will surely suffice. Though actually, the beep in the mixer is probably referring to alsa's beep...
Kory

---

### Post by chrono144 on 2008-11-11
blacklisting pcspkr worked like a charm! thanks!

---

### Post by dharmabummed on 2008-11-13
Speaking of making the machine silent in class, is there anyone experiencing a clicking sound coming from the hard drive, down on the far right corner of the computer. I've heard this is normal, but is there any way to turn it off?
see also [http://forum.tabletpcreview.com/showthread.php?t=19655](http://forum.tabletpcreview.com/showthread.php?t=19655) and [http://forum.tabletpcreview.com/showthread.php?t=21687](http://forum.tabletpcreview.com/showthread.php?t=21687)

apparently it could have something to do with file indexing on the HDD

Also, is the flickering while running fgl_grxgears dependant on compiz? I'm dual booting vista and video playback on the HD3200 hasn't been the most stable there either, though it doesn't flicker, there's a good lag in playback

looks like ATI has released a new driver today.. [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

anyone tried it?

---

### Post by laurentp on 2008-11-14
Has anyone tried to configure WICD for WPA ? I think network manager is the source of my crashes and I can't configure WICD correctly ( there is no Broadcom option in wpa_supplicant driver...)

---

### Post by TreeFallComplete on 2008-11-15
Okay, so awhile back I installed Hardy on my tx2500 using this tutorial. It worked great, and thanks so much.

Now, though, I upgraded to Intrepid and my computer doesn't work anymore. (kind of disappointing, since I was hoping the new version would *fix* problems, not create more)

Basically, the computer behaves the same way it did when I had installed hardy and was doing the first boot: it loads, then the kernel panics. I did the press escape-edit boot command-acpi=off thing, and instead of allowing it to boot, like it did with Hardy, it says

[    0.446780] IO APIC resources could not be allocated
[    0.448010] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I suspect the problem is that I wasn't given the option to do the acpi=off thing during the upgrade. Also, I may have done something mildly stupid when I allowed it to overwrite my special boot commands during the upgrade. Right now the only thing I can think to do is to get a disk and try installing intrepid/hardy from there, but I was hoping someone here could help?

---

### Post by harak on 2008-11-15
> **TreeFallComplete said:**
> Okay, so awhile back I installed Hardy on my tx2500 using this tutorial. It worked great, and thanks so much.

Now, though, I upgraded to Intrepid and my computer doesn't work anymore. (kind of disappointing, since I was hoping the new version would *fix* problems, not create more)

Basically, the computer behaves the same way it did when I had installed hardy and was doing the first boot: it loads, then the kernel panics. I did the press escape-edit boot command-acpi=off thing, and instead of allowing it to boot, like it did with Hardy, it says

[    0.446780] IO APIC resources could not be allocated
[    0.448010] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I suspect the problem is that I wasn't given the option to do the acpi=off thing during the upgrade. Also, I may have done something mildly stupid when I allowed it to overwrite my special boot commands during the upgrade. Right now the only thing I can think to do is to get a disk and try installing intrepid/hardy from there, but I was hoping someone here could help?

Hi I had this problem when I upgraded from hardy to intrepid... I would want you to check the following:

When you start your laptop what kernel version do you see in your boot options? If you do not see 2.6.27.* then your upgrade was not successful and you are still running the old kernel in hardy with all its acpi problems

The way out is to login with acpi=off in recovery mode and use the fix brocken packages option first. It would be good if you have a wired internet connection, while you are doing that. you might be asked to run dpkg-reconfigure -a. I am not sure about that. But you will know!

If you do not have a wired internet conection. you can get an intrepid cdrom. then drop to root shell and run "apt-cdrom add"; exit and then select fix brocken packages.

Good luck

---

### Post by TreeFallComplete on 2008-11-16
Nope, I'm seeing 2.6.27 as my kernel number, and it's the one that's not working. It seems like my only option is to reinstall from disc...

---

### Post by harak on 2008-11-16
> **TreeFallComplete said:**
> Nope, I'm seeing 2.6.27 as my kernel number, and it's the one that's not working. It seems like my only option is to reinstall from disc...

Apart from the boot commands... did you allow change of the blacklist file as well? Also you should still have the 2.6.26* kernel visible... why not log in using that with acpi=off and then try to fix broken packages?

---

### Post by dharmabummed on 2008-11-16
For anyone who's having problems with the flickering on video playback, browsing the forums I found a temporary solution. If you turn visual effects off in appearance prefs the flickering dissapears, and my results from running glxgears shot up from around 200fps to 1000fps

Does anyone know how to configure the stylus/mouse/touch in xrandr?

---

### Post by harak on 2008-11-16
> **dharmabummed said:**
> For anyone who's having problems with the flickering on video playback, browsing the forums I found a temporary solution. If you turn visual effects off in appearance prefs the flickering dissapears, and my results from running glxgears shot up from around 200fps to 1000fps

Does anyone know how to configure the stylus/mouse/touch in xrandr?

We were concerned about flickering with compiz i.e. visual effects enabled. Infact i have seen that if i disable rand rotation the flickering disappears even if I have visual effects turned on.

If you have configured stylus/mouse in the normal mode then you just have to run the following code before or after rotating to the left. 

xsetwacom set stylus ROTATE "CCW"
xsetwacom set eraser ROTATE "CCW"
xsetwacom set Touch ROTATE "CCW"

for inverted replace CCW with HALF and for right replace "CCW" with CW

it should work fine

*EDIT*
I meant my earlier posts about fgl_glxgears. if fgl_glxgears works fine then any video will work fine.

---

### Post by dharmabummed on 2008-11-17
> **harak said:**
> Thats certainly not news(see my earlier posts). We were concerned about flickering with compiz i.e. visual effects enabled. Infact i have seen that if i disable rand rotation the flickering disappears even if I have visual effects turned on.

Alright, I saw that post and knew that it was compiz, but somehow it didn't clue in for me. I am still, as they apparently say, a 'ubuntu noob' :) And feel like refraining from opening my mouth from now on unless absolutely necessary :P

thanks for the info

---

### Post by harak on 2008-11-17
dharmabummed   

everyone is a noob to begin with. I apologize. It was my fault to say that "its not news".

---

### Post by dharmabummed on 2008-11-17
> **harak said:**
> dharmabummed   

everyone is a noob to begin with. I apologize. It was my fault to say that "its not news".

dude, no worries, it's november in sweden and the sun is dissapearing, thus i think i'm a little over sensitive right now :)

peace

---

### Post by toobaz on 2008-11-20
Hello,

in one of the last updates, my audio completely stopped working.

While just after (intrepid) installation it just didn't emit sounds (problem solved by just inserting the right string in /etc/modprobe.d/alsa-base), now alsa doesn't even see the soundcard; for example, if I run mplayer I get:
```

AO: [pulse] Failed to connect to server: Invalid argument
[AO_ALSA] alsa-lib: pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[AO_ALSA] Unable to set hw-parameters: Input/output error
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
[AO_ALSA] alsa-lib: pcm_pulse.c:625:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

[AO_ALSA] Unable to set hw-parameters: Input/output error
[AO ARTS] loading the aRts backend "/usr/lib/libartscbackend.la" failed
[AO ESD] latency: [server: 0.19s, net: 0.00s] (adjust 0.19s)
AO: [esd] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...


MPlayer interrupted by signal 13 in module: play_audio
- MPlayer crashed. This shouldn't happen.
  It can be a bug in the MPlayer code _or_ in your drivers _or_ in your
  gcc version. If you think it's MPlayer's fault, please read
  DOCS/HTML/en/bugreports.html and follow the instructions there. We can't and
  won't help unless you provide this information when reporting a possible bug.

```

Does someone have the same problem?

I'm a little afraid filing a bug would be nonsense, since the card is just officially not recognized...

Speaking of: I opened this bug on ALSA [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4234](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4234) , but maybe one must register to see it.

Isn't it possible do bring all the info we got so far in a wiki page (I mean: something more readable than hundreds of pages of forum)? I can offer the wiki, if there are no better solutions (I don't know if the official Ubuntu wiki appreciates collaborative, work-in-progress works...)

---

### Post by marranzano on 2008-11-21
having a strange problem with ibex:
everytime i reboot the router (to which i'm connected via wifi) the system hangs??? only thing to do is a hard reboot...
no problem if i turn the pc's wireless off and on during the router's reboot...

ideas?

ps. the wiki would be usefull!

---

### Post by TreeFallComplete on 2008-11-22
> **harak said:**
> Apart from the boot commands... did you allow change of the blacklist file as well? Also you should still have the 2.6.26* kernel visible... why not log in using that with acpi=off and then try to fix broken packages?

Nope. 2.6.26 not visible. I'm just going to install from scratch. Thanks for your help, though.

---

### Post by toobaz on 2008-12-06
Hello. 2 things:

- my audio finally works without (the "jack non recognized") problems. I'm still not able to say if I was only dumb in the past or updates solved the problem in the present, but it disappeared
- I created the wiki page I writing about some posts ago. It's at [http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500](http://www.pietrobattiston.it/wiki/doku.php?id=intrepid_on_hp_pavilion_tx2500) and whoever wants to add info will be given an account . If you know of some more "institutional" wiki to host it let me know.
- if someone can give me a hint for a good howto for fprint, gdm and PAM integration , I will appreciate it
bye

Pietro

---

### Post by Drklght on 2008-12-24
Hello,
I'm new to linux so I'm not too familiar with its errors. 
I got a TX2510us AMD Turion X2 2.1ghz Puma
3GB RAM  250GB HD
The problem is I can't even get it to install. If I try installing it with ACPI it will automatically shut down after I press ENTER(PLEASE EJECT CD BLABLA THEN PRESS ENTER). However if I press F6 and toggle acpi=off, it will not even start the installation. After it loads the linux kernel it will give me a black screen with errors, and the final line reads:
[   50.321939] Kernel panic - not syncing: Attempted to kill init!

I have no idea what this means... can someone please help me?
Thanks

---

### Post by networm1230 on 2008-12-24
I am using ubuntu 8.04 now. Im going to give you a suggestion of last resort wipe your in entire hard drive drive and star a clean installation of ubuntu 8.04 I know of a tool to wipe your drive completely [http://www.dban.org/](http://www.dban.org/) warning be careful save all data before using this

---

### Post by toobaz on 2008-12-25
> **networm1230 said:**
> I am using ubuntu 8.04 now. Im going to give you a suggestion of last resort wipe your in entire hard drive drive and star a clean installation of ubuntu 8.04 I know of a tool to wipe your drive completely [http://www.dban.org/](http://www.dban.org/) warning be careful save all data before using this

I really don't think wiping the hard drive can be a solution... at least not the first I'd suggest for a kernel panic...

Drklght, did you check the CD for integrity? And test memory (if the computer is new, I'd leave it at least a couple of hours testing)?
Both options are available from the first menu that comes out (after you've chosen the language).

Also, if both CD and memory test succeed, could you try just to boot (not install, if you prefer 8.04) an Intrepid (Ubuntu 8.10) CD and see if it works?

---

### Post by networm1230 on 2008-12-25
> **toobaz said:**
> I really don't think wiping the hard drive can be a solution... at least not the first I'd suggest for a kernel panic...

Drklght, did you check the CD for integrity? And test memory (if the computer is new, I'd leave it at least a couple of hours testing)?
Both options are available from the first menu that comes out (after you've chosen the language).

Also, if both CD and memory test succeed, could you try just to boot (not install, if you prefer 8.04) an Intrepid (Ubuntu 8.10) CD and see if it works?

yes! before I installed ubuntu 8.04 on my PC I did do all the testing that the ubuntu live CD had including memory testing. warning memory testing tacks a long time. you do not need to install ubuntu on your PC if you just wont to test ubuntu out run it off the live CD doing this will not touch you PC hardware. the live CD run off of Ram memory

---

### Post by toobaz on 2008-12-25
> **Drklght said:**
> Hello,
If I try installing it with ACPI it will automatically shut down after I press ENTER(PLEASE EJECT CD BLABLA THEN PRESS ENTER).

Just for your information: this is exactly what you should expect: Hardy thinks computer is too hot (because, as you can read in this thread, it wrongly reads some heating sensors values), so it immediately shuts down and, before really powering off, shows that screen, which is the ordinary screen shown at the shutdown of a live session.

> **Drklght said:**
> However if I press F6 and toggle acpi=off, it will not even start the installation. After it loads the linux kernel it will give me a black screen with errors, and the final line reads:
[   50.321939] Kernel panic - not syncing: Attempted to kill init!

I have no idea what this means... can someone please help me?
Thanks

The real (because as far as I know not previously reported) problem is this: a kernel panic is a grave important error which means linux just can't go on. However, this message by itself is not very informative...

Now that I think about it, if you could report some of the lines of errors preceding that one (lot of people do it by just taking a picture of the screen and posting it), we could maybe tell you something more useful.

---

### Post by Fallenou on 2009-01-03
> **dharmabummed said:**
> Speaking of making the machine silent in class, is there anyone experiencing a clicking sound coming from the hard drive, down on the far right corner of the computer. I've heard this is normal, but is there any way to turn it off?
see also [http://forum.tabletpcreview.com/showthread.php?t=19655](http://forum.tabletpcreview.com/showthread.php?t=19655) and [http://forum.tabletpcreview.com/showthread.php?t=21687](http://forum.tabletpcreview.com/showthread.php?t=21687)

apparently it could have something to do with file indexing on the HDD

Also, is the flickering while running fgl_grxgears dependant on compiz? I'm dual booting vista and video playback on the HD3200 hasn't been the most stable there either, though it doesn't flicker, there's a good lag in playback

looks like ATI has released a new driver today.. [http://ati.amd.com/support/drivers/linux64/linux64-radeon.html](http://ati.amd.com/support/drivers/linux64/linux64-radeon.html)

anyone tried it?

It may be the hard drive power management which does spin down to "park" the hard drive head. It can reduce your hard drive life expectancy, you really should disable hard drive power management with hdparm or other tool.

Here are some links which deal with this serious problem :

[http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/](http://ubuntudemon.wordpress.com/2007/10/26/laptop-hardrive-killer-bug/)
[http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/](http://ubuntudemon.wordpress.com/2007/10/28/laptop-hardrive-killer-bug-how-to-discover-whether-you-are-affected/)
[http://duopetalflower.blogspot.com/2008/04/harddrive-killer-bug-workaround-for.html](http://duopetalflower.blogspot.com/2008/04/harddrive-killer-bug-workaround-for.html)
[http://archive.atomicmpc.com.au/forums.asp?s=2&c=16&t=4658](http://archive.atomicmpc.com.au/forums.asp?s=2&c=16&t=4658)

don't get fooled by the fact that most people says "it's not ubuntu's fault, it's the default hard drive power management bios/firmware policy", whoever is responsible for this we don't care, anyway it can be really bad for your hard drive, so i really encourage you to disactivate it.

---

### Post by marranzano on 2009-01-19
hello,
I now have intrepid and still can't get the remote control to work...
please, for those who have it working, could you post or send me your lsmod?
also, is there the need to install lirc?

thanx

---

### Post by toobaz on 2009-01-20
> **marranzano said:**
> hello,
I now have intrepid and still can't get the remote control to work...
please, for those who have it working, could you post or send me your lsmod?
also, is there the need to install lirc?

thanx

Hello,
I really had to do _nothing_ to enable remote control in my intrepid (notice that not all buttons work, but all the most important do). For instance, rhythmbox works great.

Package "lirc" is not installed on my system.

Here is my lsmod output:

```
Module                  Size  Used by
nls_iso8859_1          13568  0 
nls_cp437              15232  0 
vfat                   21120  0 
fat                    64824  1 vfat
ppp_deflate            13696  0 
zlib_deflate           30744  1 ppp_deflate
bsd_comp               14336  0 
ppp_async              18688  1 
crc_ccitt              10496  1 ppp_async
ppp_generic            36776  7 ppp_deflate,bsd_comp,ppp_async
slhc                   14720  1 ppp_generic
michael_mic            11008  0 
arc4                   10368  0 
ecb                    11520  0 
crypto_blkcipher       27780  1 ecb
af_packet              29568  0 
binfmt_misc            18700  1 
rfcomm                 51104  23 
sco                    20612  2 
bridge                 64544  0 
stp                    11268  1 bridge
bnep                   23168  2 
l2cap                  33280  18 rfcomm,bnep
vboxdrv              1653120  0 
ppdev                  16904  0 
ipv6                  314312  29 
powernow_k8            23684  0 
cpufreq_userspace      12420  0 
cpufreq_ondemand       16400  2 
cpufreq_stats          14468  0 
cpufreq_conservative    16392  0 
freq_table             13568  3 powernow_k8,cpufreq_ondemand,cpufreq_stats
cpufreq_powersave      10368  0 
sbs                    22288  0 
sbshc                  14592  1 sbs
container              12288  0 
pci_slot               13704  0 
parport_pc             44200  0 
lp                     19588  0 
parport                50096  3 ppdev,parport_pc,lp
joydev                 20736  0 
snd_hda_intel         489264  3 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
snd_seq                67168  7 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
wacom                  31368  0 
serio_raw              14596  0 
uvcvideo               68616  0 
snd                    79432  16 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
evdev                  20512  15 
psmouse                51612  0 
compat_ioctl32         18176  1 uvcvideo
soundcore              16800  1 snd
videodev               46720  2 uvcvideo,compat_ioctl32
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
v4l1_compat            24580  2 uvcvideo,videodev
btusb                  21912  6 
bluetooth              70820  27 rfcomm,sco,bnep,l2cap,btusb
i2c_piix4              17936  0 
i2c_core               36128  1 i2c_piix4
ieee80211_crypt_tkip    18048  0 
video                  28948  0 
ieee80211_crypt        14596  1 ieee80211_crypt_tkip
output                 11776  1 video
battery                21128  0 
wmi                    15808  0 
ac                     13448  0 
button                 15904  0 
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
ext3                  150544  4 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
usbhid                 39776  0 
hid                    59072  1 usbhid
usb_storage            92864  0 
sr_mod                 24644  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  5 
crc_t10dif             10240  1 sd_mod
sg                     45408  0 
pata_acpi              13568  0 
ata_generic            14212  0 
libusual               31784  1 usb_storage
pata_atiixp            14208  0 
ahci                   43148  4 
r8169                  40196  0 
libata                200160  4 pata_acpi,ata_generic,pata_atiixp,ahci
scsi_mod              183160  5 usb_storage,sr_mod,sd_mod,sg,libata
dock                   18464  1 libata
ohci_hcd               34972  0 
ehci_hcd               48908  0 
usbcore               175376  9 wacom,uvcvideo,btusb,usbhid,usb_storage,libusual,ohci_hcd,ehci_hcd
thermal                27424  0 
processor              47800  2 powernow_k8,thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
fuse                   68288  3 
```

---

### Post by marranzano on 2009-01-21
> **toobaz said:**
> Hello,
I really had to do _nothing_ to enable remote control in my intrepid (notice that not all buttons work, but all the most important do). For instance, rhythmbox works great.

Package "lirc" is not installed on my system
wasn't able to find any relevant missing modules in my config so i just went through a fresh reinstall (formatting everything exept /home)...

result: still no remote control!! (it works fine in vista...)

if anyone is able to help me debug my issue I would be really thankful...

marranzano

EDIT:
ok, after going nuts i ubgraded the bios, installed lirc, removed lirc... don't know what did the magic (suppose the bios upgrade) but it now works... thnx anyhow...  :D

---

### Post by toobaz on 2009-01-22
> **marranzano said:**
> now works...

great!

---

### Post by marranzano on 2009-01-24
i'm now able to reproduce my problem with the receiver:

1) i have the receiver working with ubuntu
2) reboot into vista
3) suspend vista
4) wake vista
5) reboot into ubuntu --> remote doesn't work!!

the only way i found to "wake up the receiver" is to flash the bios, this is a very ugly solution... there must be a way to "wake it up" from linux!?!

any advice?

thnx

---

### Post by odd on 2009-04-22
@marranzano: to not repeat posts - I got it working again without flashing the bios - look [here]("http://ubuntuforums.org/showpost.php?p=7108170&postcount=3").

---

### Post by b33eazy on 2009-06-26
I'm a tx2500 owner. I have a few questions: I never used Linux, so how do I install Ubuntu on my partial (10gb) hard drive? How do I set-up those really cool backgrounds/themes? Thanks.

---

### Post by ed021990 on 2009-07-06
hey guys, on jaunty do you get ur ethernet and wireless cut after suspend/wake up?

---

### Post by toobaz on 2009-07-06
After suspend ethernet doesn't work, wile wireless does.

I've written slightly more here: [http://www.pietrobattiston.it/wiki/doku.php?id=jaunty_on_hp_pavilion_tx2500](http://www.pietrobattiston.it/wiki/doku.php?id=jaunty_on_hp_pavilion_tx2500)

Pietro

---

### Post by chadmerkert on 2009-07-25
Hey ed021990,

I was having a problem with the wireless and ehternet after resume on my tx2500z as well, but I was able to fix it rather easily!

[SIZE="4"]For the wireless:[/SIZE]

Open up a terminal and type:

```
sudo gedit /etc/default/acpi-support
```

In this file, find 

```
MODULES_WHITELIST=""
```

and change it to:

```
MODULES_WHITELIST="wl"
```

Save and close the file. That should get the wireless working after a suspend/resume.

[SIZE="4"]To fix the ethernet after resume:[/SIZE]

check to see what driver your ethernet card has:

```
lshw -C network
```

find your ethernet card, and see what it says for driver=
Mine is r8169

Type the following in a terminal:

```
sudo gedit /etc/pm/config.d/unload_modules
```

this should bring up a blank file,

add this line to the file with your driver name in the quotation marks and save/close the file:

```
SUSPEND_MODULES="r8169"
```

That should fix the ethernet.

Please let me know if this helped you.

---

### Post by auto123 on 2009-07-29
I don't get it, I followed your instructions on the first page and yet my wireless and sound still don't work :(

instead of using the ethernet port I used a wireless dongle, could this be effecting the wireless install or what?

I would really like to try ubuntu as I work and do everything computer related with ms and I just want to try something different

my tablet is still good on windows though,
-Tyler

---

### Post by auto123 on 2009-07-29
well I got sound to work but the wifi still does not work.

on a side note I tried booting with acpi=off and it hangs at an all text screen.

I would really enjoy this if my wireless was working,
-tyler

nevermind, I found a working driver under system>administration>hardware drivers

sorry for being a noob : P

---

### Post by valiantdust on 2009-09-11
> **auto123 said:**
> I don't get it, I followed your instructions on the first page and yet my wireless and sound still don't work :(

instead of using the ethernet port I used a wireless dongle, could this be effecting the wireless install or what?

I would really like to try ubuntu as I work and do everything computer related with ms and I just want to try something different

my tablet is still good on windows though,
-Tyler

Is your sound still non-functional? I followed the directions as given, and the sound still didn't work initially, but some tinkering in System > Preferences > Sound got me there ...

---

