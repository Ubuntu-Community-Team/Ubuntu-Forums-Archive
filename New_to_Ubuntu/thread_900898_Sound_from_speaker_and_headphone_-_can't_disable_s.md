---
title: "Sound from speaker and headphone - can't disable speaker"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by stevenba on 2008-08-25
Sorry for the blast....
Card identified as ICH5
Chipset SigmaTel STAC9758.59

Cannot seem to disable labtop speaker, so sound plays simultaneously from speaker and headphone.  Tried ALSA Mixer and PCM, but can't seem to find the magic incantation to disable the speakers.  Off-hook option not visible in ALSA Mixer. :confused:

Laptop is uncertified Gateway M675, which seems to defy all the rules thus far.  
Thanks in advance for any suggestions.

---

### Post by pyromanic123boom on 2008-08-25
Try going to the terminal (if you didn't already) and type 

alsamixer

It should bring up alsamixer within the terminal. Scroll to the right and the left, and up and down to toggle percentage. You will be able to turn the speaker (possibly INTERNAL speaker?? not pc speaker) to 0, and front speaker up. try experimenting with the different vaules in alsamixer.

---

### Post by stevenba on 2008-08-26
Thank you, Pyromanic123boom.  This did the trick.  The answer was to turn PCM down all the way, and Front up all the way.

---

### Post by m-p{3} on 2008-12-08
If you need another alternative, go see my post [_here_](http://ubuntuforums.org/showthread.php?t=1004978).

---

### Post by jinjonBoo on 2010-01-16
Thank you [pyromanic123boom]("http://ubuntuforums.org/member.php?u=643195"), it worked well for me too! I'm using an HP laptop, with:
Card: ATI IXP
Chip: Analog Devices AD1981B
Ubuntu FTW!
Peace out

---

### Post by manojendu on 2010-05-12
Hi
I am using Dell Vostro 1014.
Ubunto 10.04
This problem persisted with all the various version of Ubuntu through  8.04 to present 10.04, and the solution provided doesn't work for me  (unfortunately so) because the 'preferences' in my volume control have  only the options Master and PCM, it doesn't have any control for  Headphone jack or any such thing. I've tried Kmix but still the  situation is the same. I've tried Alsamix and that has absolutely no  effect on the sound system for my notebook.

Please help.

---

### Post by lidex on 2010-05-12
> **manojendu said:**
> Hi
I am using Dell Vostro 1014.
Ubunto 10.04
This problem persisted with all the various version of Ubuntu through  8.04 to present 10.04, and the solution provided doesn't work for me  (unfortunately so) because the 'preferences' in my volume control have  only the options Master and PCM, it doesn't have any control for  Headphone jack or any such thing. I've tried Kmix but still the  situation is the same. I've tried Alsamix and that has absolutely no  effect on the sound system for my notebook.

Please help.

Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

---

### Post by princess9987 on 2010-05-29
I have a similar problem. I have given the outputs of the commands suggested. Could anyone help me? Also I do not see the volume control applet on the panel. 

I am using HP Pavillion DV6 and Ubuntu 10.04.

```
uname -a
Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: IDT 92HD75B3X5

==> /proc/asound/card0/codec#3 <==
Codec: Intel G45 DEVIBX
```

---

### Post by lidex on 2010-05-29
***princess9987 for HP DV6***
OK then. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel

```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

---

### Post by elena85 on 2010-05-30
Hi, I have the same problem, sound came from speakers and headphone, I'm using an ASUA X52Jr

#uname -a

Linux elena-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

#aplay -l

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: HDA Generic [HDA Generic]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Generic [HD-Audio Generic], dispositivo 3: ATI HDMI [ATI HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

#cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).

#head -n 1 /proc/asound/card*/codec#*


==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI


can you help me???!!!

---

### Post by princess9987 on 2010-05-30
> **lidex said:**
> ***princess9987 for HP DV6***
OK then. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel

```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default.

Thank you so much. 

I appended all the lines as you suggested in the alsa-base.conf file.
```
options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel

```
 But there was a problem, when I rebooted, my sound card wasnt recognised at all. Therefore I kept only the following line at the end of the alsa-base.conf file:

```
options snd-hda-intel model=hp-dv5

```

It seems to work now, putting headphones mutes the speaker. 

Thank you once again.. :)

---

### Post by lidex on 2010-05-31
> **princess9987 said:**
> Thank you so much. 

I appended all the lines as you suggested in the alsa-base.conf file.
```
options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel

```
 But there was a problem, when I rebooted, my sound card wasnt recognised at all. Therefore I kept only the following line at the end of the alsa-base.conf file:

```
options snd-hda-intel model=hp-dv5

```

It seems to work now, putting headphones mutes the speaker. 

Thank you once again.. :)

Funny, that's the line normally recommended for the Dv series and what I normally suggest. A recent posting on another web site said the multi-line entry would make everything work specifically on  a Dv6. I'll have to check him on that. How old is the laptop? Does everything work, including mic? Thanks.

---

### Post by princess9987 on 2010-05-31
Yeah, everything seems to work, mic, headphones and speakers... and the laptop is pretty new, around 2 months old... Its DV6-2150us model.

---

### Post by lidex on 2010-05-31
> **princess9987 said:**
> Yeah, everything seems to work, mic, headphones and speakers... and the laptop is pretty new, around 2 months old... Its DV6-2150us model.

Thanks for the follow-up!!

---

### Post by lidex on 2010-05-31
> **elena85 said:**
> Hi, I have the same problem, sound came from speakers and headphone, I'm using an ASUA X52Jr

#uname -a

Linux elena-laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux

#aplay -l

**** Lista di PLAYBACK dispositivi hardware ****
scheda 0: Intel [HDA Intel], dispositivo 0: HDA Generic [HDA Generic]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0
scheda 1: Generic [HD-Audio Generic], dispositivo 3: ATI HDMI [ATI HDMI]
  Sottoperiferiche: 1/1
  Sottoperiferica #0: subdevice #0

#cat /proc/asound/version

Advanced Linux Sound Architecture Driver Version 1.0.22.1.
Compiled on Feb  8 2010 for kernel 2.6.31-20-generic (SMP).

#head -n 1 /proc/asound/card*/codec#*


==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI


can you help me???!!!

First update your kernel:
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
Now **reboot** into your latest kernel and follow the alsa-upgrade link in my sig to update your alsa install.

---

### Post by elena85 on 2010-06-01
Hi, 
I have done as you say me, but doesn't work...

---

### Post by Drenriza on 2010-06-01
> **m-p{3} said:**
> If you need another alternative, go see my post [_here_](http://ubuntuforums.org/showthread.php?t=1004978).

Thanks mate. This solved my problem with exactly the same problem. Just on different hardware.

Thumps up ;)!

---

### Post by chandrav23 on 2010-06-11
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```Insert these lines at the bottom:
```

[B]options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel[/B]

```
Save. Close. Reboot. Check your levels in alsamixer.
```
 
**alsamixer **

```Press <F6> to select the correct soundcard.



Hi could you plese exlpain the above code.
Thanks

---

### Post by NightwishFan on 2010-06-11
This issue happens to me on the newer/backported alsa drivers. I will try your fix next time I test them. (I would like to have the issues ironed before Maverick. Reason is, I support Ubuntu for several people on this same laptop.)

Thanks in advance!

---

### Post by chandrav23 on 2010-06-15
hi,
please explain.................
 
 
[B]options snd-hda-intel model=hp-dv5
options snd slots=snd-hda-intel, snd-hda-intel
alias snd-card-0 snd-hda-intel
alias snd-card-1 snd-hda-intel[/B]
 
I need to know becoz while updating the aboe after restart my system system audio is going disable.
 
I can do it fine  if some one can give advise..
 
thanks

---

### Post by Forcecommander4 on 2010-09-27
OK - heres what did it for me. I always had sound coming out both speaker and headphones on Ubuntu 10.04 on my laptop. If you go into the sound preferences --> Output tab, theres a little box that says Analog Speakers or something like that. I always tried to change it to Analog Headphones, and then sound wouldn't come out of my speakers OR the headphones.

I figured out that the "Front" volume is at 0 by default when you select the analog headphones. In the sound preferences you can't change the Front volume, so I used the "alsamixer" command in the terminal. Simply use your arrows to select Front, then move the volume up and you should be good.

Hopefully this will work!

-Forcecommander

---

### Post by sabaripillai on 2010-11-25
> **lidex said:**
> Need some info. Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
cat /proc/asound/version
head -n 1 /proc/asound/card*/codec#* 
```Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.

Mine is a Toshiba Satellite L640 and I hear sound from both Speaker and Headphone. I tried out a lot of workarounds but nothing helped. The required information is here;

```
uname -a
Linux toshu-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI


lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

---

### Post by lidex on 2010-11-25
> **sabaripillai said:**
> Mine is a Toshiba Satellite L640 and I hear sound from both Speaker and Headphone. I tried out a lot of workarounds but nothing helped. The required information is here;

```
uname -a
Linux toshu-laptop 2.6.32-25-generic #45-Ubuntu SMP Sat Oct 16 19:52:42 UTC 2010 x86_64 GNU/Linux

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

head -n 1 /proc/asound/card*/codec#*
==> /proc/asound/card0/codec#0 <==
Codec: Conexant ID 5069

==> /proc/asound/card1/codec#0 <==
Codec: ATI R6xx HDMI


lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
03:00.0 Network controller: Broadcom Corporation Device 4727 (rev 01)
04:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

You would likely benefit from alsa update. Rather than a complete upgrade, try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by sabaripillai on 2010-11-27
> **lidex said:**
> You would likely benefit from alsa update. Rather than a complete upgrade, try updating your alsa-driver-modules.
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

thanks; i tryed this way before making the post; after installing alsa from the dev repo, the headphone would not work at all. just laptop speakers even if I plug-in the headphone. So i uninstalled the dev library and driver.

---

### Post by lidex on 2010-11-27
> **sabaripillai said:**
> thanks; i tryed this way before making the post; after installing alsa from the dev repo, the headphone would not work at all. just laptop speakers even if I plug-in the headphone. So i uninstalled the dev library and driver.

Alsa is not recognizing your codec correctly:
```
Codec: Conexant ID 5069
```
It's using the generic parser. You need later alsa to get recognition, probably just requires a model quirk added to alsa-base.conf. Have you tried the full upgrade? How about linuxant driver?
[http://www.linuxant.com/alsa-driver/](http://www.linuxant.com/alsa-driver/)

---

### Post by sabaripillai on 2010-11-28
thanks lidex; will try it out and will get back.

---

### Post by 130s on 2011-03-01
Hi, I'm having the same problem on my Netbook: Starling Star3 on Ubuntu 10.04 Netbook edition. Hope someone could help me out.

> 
% uname -a
Linux 130s-cranberry 2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux
n% aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
n% cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
n% head -n 1 /proc/asound/card*/codec#*
Codec: VIA ID 448


Thanks!

---

### Post by lidex on 2011-03-01
@130s
When you see something like this:
```
Codec: VIA ID 448 
```
it generally means alsa is not fully recognizing your codec and is using the generic parser. Your alsa version is 1.0.21, the current version is 1.0.24, so updating alsa in some way is a probable fix. So you can upgrade your OS, upgrade alsa, or upgrade your alsa modules. The latter the the least intrusive. 
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```
Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```
**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.

---

### Post by 130s on 2011-03-08
Thanks lidex. Today I tried to follow the steps you've sent and even though I've done all of them except for the one thing I describe below, I'm still seeing the same phenomenon.

I realized the result of uname -a has become different from the last time I saw (which is in my 1st post), and I couldn't find the corresponding version of linux-alsa-driver-modules-$(uname -r).

Updated info.
> 
$ uname -a
Linux 130s-cranberry 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 19:00:09 UTC 2011 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.21.

$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA ID 448
Thanks a lot.

---

### Post by lidex on 2011-03-08
You can follow the alsa-upgrade link in my sig for a script and instructions to bring you up to newer version in a fairly painless manner.

---

### Post by LifeTheHound on 2011-03-21
Problem persists on 10.10 (latest updates, Kubuntu, KDE4.6.1) for dv6 and on 11.04 (tested 2 days ago with latest updates) on a dv8. Different pairs of headphones were tried, both run Kubuntu and KDE4.6.1. 

Seriously, hp laptops are pretty common, and lots of people use headphones with them. Both laptops are of differing ages (the dv6 is over a year old, and the dv8 is almost a year now).

---

### Post by lidex on 2011-03-21
> **LifeTheHound said:**
> Problem persists on 10.10 (latest updates, Kubuntu, KDE4.6.1) for dv6 and on 11.04 (tested 2 days ago with latest updates) on a dv8. Different pairs of headphones were tried, both run Kubuntu and KDE4.6.1. 

Seriously, hp laptops are pretty common, and lots of people use headphones with them. Both laptops are of differing ages (the dv6 is over a year old, and the dv8 is almost a year now).

[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

---

### Post by LifeTheHound on 2011-03-21
> **lidex said:**
> [http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html/8#audio)

Thanks. ;) 

Really, why doesn't Ubuntu detect the model (or ask for it) during installation, and direct users to the appropriate wiki?

Would make troubleshooting a looooooooooooot easier. 

Also, why hasn't a fix made it to 11.04 yet?

---

### Post by 130s on 2011-03-29
> **lidex said:**
> You can follow the alsa-upgrade link in my sig for a script and instructions to bring you up to newer version in a fairly painless manner.


Thanks lidex, the AlsaUpgrade script in the link solved the problem!

# Now I have another problem which is tiny compared to the previous one, but my PC makes tick sound out from the speaker (though while headphones are plugged) whenever I slide 1 scale on the volume bar.

Environment: Ubuntu 10.04 Netbook edition
Current output of some commands:
> 
$ uname -a
Linux 130s-cranberry 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:21 UTC 2011 i686 GNU/Linux

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1812 Analog [VT1812 Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1

$ cat /proc/asound/version
Advanced Linux Sound Architecture Driver Version 1.0.24.
Compiled on Mar 29 2011 for kernel 2.6.32-30-generic (SMP).

$ head -n 1 /proc/asound/card*/codec#*
Codec: VIA VT1812


---

### Post by lidex on 2011-04-05
> **130s said:**
> Thanks lidex, the AlsaUpgrade script in the link solved the problem!

# Now I have another problem which is tiny compared to the previous one, but my PC makes tick sound out from the speaker (though while headphones are plugged) whenever I slide 1 scale on the volume bar.

Environment: Ubuntu 10.04 Netbook edition
Current output of some commands:

I've not seen that before but I do know choosing the wrong profile can cause weird noises/effects. Maybe have a look here:
[http://www.sabi.co.uk/Notes/linuxSoundALSA.html#chips](http://www.sabi.co.uk/Notes/linuxSoundALSA.html#chips)

---

### Post by kurogogyou on 2011-06-08
> **lidex said:**
> @130s
When you see something like this:
```
Codec: VIA ID 448 
```it generally means alsa is not fully recognizing your codec and is using the generic parser. Your alsa version is 1.0.21, the current version is 1.0.24, so updating alsa in some way is a probable fix. So you can upgrade your OS, upgrade alsa, or upgrade your alsa modules. The latter the the least intrusive. 
Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
```
sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
```Now install:
```
sudo apt-get install linux-alsa-driver-modules-$(uname -r)
```**Reboot**
Check your levels in alsamixer.
```
 alsamixer 
```Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab. 
On the output tab choose the correct device.


Thank you very much lidex! I had this very same problem and the first 3 commands solved it for me. 

Btw, I'm running Lucid Lynx on my Dell vostro 1015. =D

---

### Post by 130s on 2011-06-08
Thanks again lidex. 
# Now that I've upgraded to Ubuntu 11.04, I don't see the same problem anymore before I try looking at the link you provided.

---

### Post by arvinraj on 2011-08-08
Hi, I need some help too regarding the same problem:

```
**uname -a**
Linux ubuntu 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

[B]aplay -l
[/B]**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: VT1702 Analog [VT1702 Analog]
  Subdevices: 1/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1702 Digital [VT1702 Digital]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

**cat /proc/asound/version**
Advanced Linux Sound Architecture Driver Version 1.0.23.

**head -n 1 /proc/asound/card*/codec#***
==> /proc/asound/card0/codec#0 <==
Codec: VIA VT1702

==> /proc/asound/card0/codec#1 <==
Codec: Conexant ID 2c06

==> /proc/asound/card0/codec#2 <==
Codec: Nvidia MCP77/78 HDMI

```

Have been facing problem especially in my working area where i am required to keep noise to minimum level. But i cant do that if my laptop speakers dont mute when the headphones are plugged in.

I would really appreciate any help that i can get... thanks alot :)

---

### Post by lidex on 2011-08-16
> **arvinraj said:**
> Hi, I need some help too regarding the same problem:


Have been facing problem especially in my working area where i am required to keep noise to minimum level. But i cant do that if my laptop speakers dont mute when the headphones are plugged in.

I would really appreciate any help that i can get... thanks alot :)

Try setting your model name to auto:
```
echo "options snd-hda-intel model=auto" | sudo tee -a /etc/modprobe.d/alsa-base.conf
``` **Reboot**

---

### Post by SunnySan on 2011-09-09
Thanks all 
I have an Asus a52f with ubuntu 64 10.04
did the following and it is now working.

Using a Terminal="Applications->Accessories->Terminal"
Add the ubuntu-audio-dev ppa:
Code:
> sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update

Now install:
Code:
> sudo apt-get install linux-alsa-driver-modules-$(uname -r)
**Reboot**

Don't forget to restart your PC.
Thanks

---

### Post by SunnySan on 2011-09-12
hoops forget what I just wrote before, as I lost my microphone.
gain headphone without speaker but lost microphone...

Now how do I go back to my previous setting.....??

---

### Post by lidex on 2011-09-14
> **SunnySan said:**
> hoops forget what I just wrote before, as I lost my microphone.
gain headphone without speaker but lost microphone...

Now how do I go back to my previous setting.....??

Post your amixer output:
```
amixer
```

---

