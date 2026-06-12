---
title: "Bluetooth not working for TRUST 2.1 USB adapter"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by suomalainen on 2011-10-10
Ubunteros,

I have a Trust Bluetooth 2.1 USB adapter.

I'm trying to get it working in Ubuntu 10.04 to no avail. As I have a dual boot Ubuntu/XP machine I have also installed it into XP. Here it works w/o issue. However, during start-up when I press F2 to get into BIOS the BIOS says under "Devices" that "Bluetooth Device = {none}. Then when machine boots into XP my bluetooth does work.

I'm using a Dell Inspiron 2200 with BIOS version A07. In BIOS it is not possible to "TURN ON" bluetooth.

My Ubuntu is version 10.04.

lsusb say's:

Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0cf3:3000 Atheros Communications, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 001 Device 006: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 005: ID 046d:c527 Logitech, Inc. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

This is the Trust bluetooth device I'm using:

Bus 003 Device 003: ID 0cf3:3000 Atheros Communications, Inc.

I'd appreciate hearing how I can fix the issue.

Thank you,

Suomalainen

---

### Post by LowSky on 2011-10-10
```
sudo service bluetooth restart
```

it should then work

---

### Post by suomalainen on 2011-10-10
Thanks but nope that didn't do it. When I start bluetooth in system-->preferences--> bluetooth I get msg. "No bluetooth adapters present".

---

### Post by suomalainen on 2011-10-10
Ubunteros,

Is setting up Bluetooth really this difficult? I've been at it all day and haven't moved an inch forward. Everything is working fine under Win XP but as soon as I boot up Ubuntu I can't even connect. No Bluetooth adapters is the only message I see when I try to launch the Bluetooth application.

Assistance would be greatly appreciated!

Thanks!!!

---

### Post by suomalainen on 2011-10-11
Bump.......

---

### Post by JSchultheis on 2011-10-11
> **suomalainen said:**
> Ubunteros,

I have a [[COLOR="Blue"]***_[SIZE="3"]Trust Bluetooth 2.1 USB adapter[/SIZE]_***[/COLOR]]("http://www.trust.com/products/product.aspx?artnr=15542").

I'm trying to get it working in Ubuntu 10.04 to no avail. As I have a dual boot Ubuntu/XP machine I have also installed it into XP. Here it works w/o issue. However, during start-up when I press F2 to get into BIOS the BIOS says under "Devices" that "Bluetooth Device = {none}. Then when machine boots into XP my bluetooth does work.

I'm using a Dell Inspiron 2200 with BIOS version A07. In BIOS it is not possible to "TURN ON" bluetooth.

My Ubuntu is version 10.04.

[COLOR="Red"]_lsusb_[/COLOR] say's:

```
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[COLOR="Red"]Bus 003 Device 003: ID 0cf3:3000 Atheros Communications, Inc. 
[/COLOR]Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 12d1:14ac Huawei Technologies Co., Ltd. 
Bus 001 Device 006: ID 046d:c52f Logitech, Inc. 
Bus 001 Device 005: ID 046d:c527 Logitech, Inc. 
Bus 001 Device 003: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 001 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

This is the Trust bluetooth device I'm using:

```
[COLOR="red"]Bus 003 Device 003: ID 0cf3:3000 Atheros Communications, Inc.[/COLOR]
```

I'd appreciate hearing how I can fix the issue.

Thank you,

Suomalainen



This is a usb adapter, correct?
That being the case we can rule out any BIOS configuration.


Open a terminal and type in these commands:
```

sudo hcitool dev
sudo hcitool scan
sudo rfkill list
```

Enter your password when prompted.

Post the results back here in your next post

---

### Post by suomalainen on 2011-10-11
@JSchultheis

Thanks for coming to the rescue! Unfortunately, the commands you offered did not seem to work or do anything. 

Here is what I received in terminal:

paavo@paavo-laptop:~$ sudo hcitool dev
[sudo] password for paavo: 
Devices:
paavo@paavo-laptop:~$ sudo hcitool scan
Device is not available: No such device
paavo@paavo-laptop:~$ sudo rfkill list
paavo@paavo-laptop:~$ 


I've been reading a lot about how "Bluetooth" needs to be "turned on" in Windows XP. Indeed, when I boot-up XP my USB Bluetooth adapter functions flawlessly. However, in BIOS is says for blue tooth the following:

Bluetooth Device {none}

And this field is not able to be changed.

If you or someone else can assist further that would be great. Thanks for your support thus far.

Best,

Suomalainen

---

### Post by Johnb0y on 2011-10-11
seen [this]("https://help.ubuntu.com/community/BluetoothSetup"), might help you out...???

---

### Post by gandaran on 2011-10-11
check with
```
lsmod
```
if the ath3k driver is loaded

---

### Post by suomalainen on 2011-10-11
@Johnb0y - Thanks for the link. I saw that too and it got me no where.

@gandaran-Thanks for the suggestion you offered. Sorry that I don't know what I'm looking for but trust you can help me. Thanks again!

The lsmod command yielded:

paavo@paavo-laptop:~$ lsmod
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  29250  1 
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  1 
crc_ccitt               1339  1 ppp_async
option                 20198  1 
usbserial              33694  4 option
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
ppdev                   5259  0 
snd_intel8x0           25652  2 
snd_ac97_codec        100646  1 snd_intel8x0
ac97_bus                1002  1 snd_ac97_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
pcmcia                 30784  0 
dell_wmi                1793  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  288963  2 
dell_laptop             6888  0 
ipw2200               135216  0 
yenta_socket           20408  2 
dcdbas                  5422  1 dell_laptop
libipw                 39896  1 ipw2200
psmouse                63677  0 
drm_kms_helper         29329  1 i915
snd                    54244  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
rsrc_nonstatic         10015  1 yenta_socket
serio_raw               3978  0 
lib80211                5046  2 ipw2200,libipw
soundcore               6620  1 snd
intel_agp              24375  2 i915
lp                      7028  0 
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
drm                   163651  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
joydev                  8740  0 
video                  17375  1 i915
agpgart                31724  2 intel_agp,drm
snd_page_alloc          7076  2 snd_intel8x0,snd_pcm
output                  1871  1 video
parport                32635  2 ppdev,lp
usbhid                 36110  0 
hid                    67288  1 usbhid
usb_storage            39841  5 
e100                   28211  0 
mii                     4381  1 e100
paavo@paavo-laptop:~$

---

### Post by gandaran on 2011-10-11
no, I don't see any ath3k module.
I believe the Ubuntu 10.04 kernels don't have this driver built-in 
maybe I'm wrong but I think you'll have to install the driver
use the google search for "ubuntu ath3k" maybe you'll find something to help fix the problem.

---

### Post by JSchultheis on 2011-10-11
alrighty, what a mess of a thread :lolflag:

So just to be clear, many of the instructions given were to figure out what the system thinks is going on, and not to actually induce changes.

Next, you can make pretty boxes, especially around the 'code' that you use, as well as the 'feedback that it provides. That way we can review it all without going [[COLOR="Blue"][SIZE="3"][FONT="Times New Roman"]***_googly eyed_***[/FONT][/SIZE][/COLOR]]("http://www.youtube.com/watch?v=73a0h6h1IKQ")... <---(good link)

Putting stuff in boxes is easy on the 'go advanced' page using the litle pound sign (hash sign), just put the info in between. It will then provide scroll bars and all.
:)

---------------


So, please confirm that it is a stand alone usb adapter, not internal.

---

### Post by JSchultheis on 2011-10-11
Ok duh!! The first sentence you said USB adapter.
I am a bit unslept today, running only on caffeine...

Let's not talk about BIOS anymore, because USB addons have nothing to do with BIOS. Perhaps a USB port, but nothing beyond the port. That is what was throwing me for a loop :p

Next up:
Open Synaptic Package Manager. Search "pulse"

Scroll down and select:```
pulseaudio
pulseaudio-module-bluetooth
```When you select these```
Mark for Installation
```then click```
Apply
```then click```
Apply
```
Search "blue"
Scroll down and select:```
blueman
bluetooth
```When you select these```
Mark for Installation
Apply
Apply
```

Close Synaptic.
Open Terminal```
sudo apt-get install libasound2-plugins "pulseaudio-*" paman padevchooser paprefs pavucontrol pavumeter
sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
sudo apt-get update
sudo apt-get upgrade
```

----------Next: Adding Users to the PulseAudio groups
Next go to System -> Administration -> and click on ```
Users and Groups
Manage Groups
```Scroll all the way to the bottom of the list where you will find:```
pulse-access
pulse-rt
```(you prolly won't have pulse-rt)
Make sure to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound.
Do the same for```
Bluetooth
```

Reboot.

Do you see a bluetooth applet?

---

### Post by JSchultheis on 2011-10-11
Must...Not...Close...Eyes...


Ok, go to ```
System>Preferences>Bluetooth Manager
Adapter>Preferences>Always Visible
Adapter>Search
```Find and pair your headset.

Go to I think ```
Applications(?)>Sound&Video>PusleAudio Device Chooser
```Click, then```
Volume Control
Playback
Internal
```select your bluetooth headset.

Is this for phone, music, both?

---

### Post by JSchultheis on 2011-10-11
Check the 'hidden' volume level box, available through terminal:```
alsamixer -Dhw
```
Use the arrow keys to make sure that: 'Master' Headphones' and 'PCM' are all at max.

Created a file of:```
gksudo gedit /etc/asound.conf
```
then enter the following:

```
pcm.pulse {
    type pulse
}
ctl.pulse {
    type pulse
}
pcm.!default {
    type pulse
}
ctl.!default {
    type pulse
}
```

reboot.

Finally, finally, fire up PulseAudio Device Chooser.
Click bluetooth applet.
Highlight the device of choice.
Select Device>Audio Profile
Select A2DP (High Fidelity) etc.


Yes? and please answer the above questions.

---

### Post by suomalainen on 2011-10-11
@JSchultheis

Thank you very much for the detailed instructions. I've hit a stumbling block. Before going into detail, however, let me assure you that your instructions were written very clearly and followed to the "T".

```
Scroll all the way to the bottom of the list where you will find:
Code:

pulse-access
pulse-rt

(you prolly won't have pulse-rt)
Make sure to highlight each, one at a time, and click Properties. Just put a check next to each user that you want to be able to have access to sound.
Do the same for
Code:

Bluetooth

Reboot.

Do you see a bluetooth applet? 
```

The part regarding putting a tick mark into the box next to "Bluetooth" was not accomplished because Bluetooth was not on the list.

When I re-booted a Bluetooth applet did not appear.

When I went to System--> Preferences --> Bluetooth Manager the following error message was given. See attached pic for more details.

Hopefully this can be worked out whatever it is. Thank you very much for the personal time you dedicated to support me on this issue. I appreciate your help!

Suomalainen

---

### Post by JSchultheis on 2011-10-11
Are you able to find a 'pulseaudio device chooser'? if not, do you have any other pulseaudio options and what are they?

---

### Post by suomalainen on 2011-10-11
I have a pulse-access. Does this help?

---

### Post by gsocker on 2011-10-11
Looking at the USB device id, your adapter appears to be based on an Atheros AR3011 chipset. This appears to be on of the chipsets with no built in intelligence - **everything** is in the firmware. This means it requires runtime firmware loading. This appears to be the sole purpose of the ath3k driver. We need to get this driver installed on your system and get the firmware loaded. After that it should work with the standard bluetooth drivers.

Fortunately, the firmware is easily available.

Unfortunately, the necessary driver(ath3k) does appear to be part of 10.04 LTS.
I don't have a 10.04 install handy; does anyone know if this is included or where a package can be found if not?

---

### Post by suomalainen on 2011-10-11
I just found this:

```

The on-board bluetooth (appears in lsusb as 0cf3:3002 Atheros Communications, Inc.) needs the ath3k module which is not on the latest lucid kernel. However the module is coming on a kernel soon and you can grab the code to compile it yourself:
Code:

git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/ath3k.git
cd ath3k
make
sudo make install
sudo modprobe -v ath3k
echo ath3k | sudo tee -a /etc/modules


```

When I enter the commands in terminal I get

```
paavo@paavo-laptop:~$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/mcgrof/ath3k.git
The program 'git' is currently not installed.  You can install it by typing:
sudo apt-get install git-core
paavo@paavo-laptop:~$ sudo apt-get install git-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 libaccess-bridge-java-jni libaccess-bridge-java
  linux-headers-2.6.32-21-generic tzdata-java ca-certificates-java
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libdigest-sha1-perl liberror-perl patch
Suggested packages:
  git-doc git-arch git-cvs git-svn git-email git-daemon-run git-gui gitk
  gitweb diffutils-doc
The following NEW packages will be installed:
  git-core libdigest-sha1-perl liberror-perl patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 5,811kB of archives.
After this operation, 12.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  liberror-perl libdigest-sha1-perl git-core patch
Install these packages without verification [y/N]? y
Get:1 http://fi.archive.ubuntu.com/ubuntu/ lucid/main liberror-perl 0.17-1 [23.8kB]
Get:2 http://fi.archive.ubuntu.com/ubuntu/ lucid/main libdigest-sha1-perl 2.12-1build1 [26.2kB]
Get:3 http://fi.archive.ubuntu.com/ubuntu/ lucid-updates/main git-core 1:1.7.0.4-1ubuntu0.2 [5,638kB]
Get:4 http://fi.archive.ubuntu.com/ubuntu/ lucid/main patch 2.6-2ubuntu1 [123kB]                              
Fetched 5,811kB in 7s (790kB/s)                                                                               
Selecting previously deselected package liberror-perl.
(Reading database ... 192774 files and directories currently installed.)
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package libdigest-sha1-perl.
Unpacking libdigest-sha1-perl (from .../libdigest-sha1-perl_2.12-1build1_i386.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.0.4-1ubuntu0.2_i386.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.6-2ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up liberror-perl (0.17-1) ...
Setting up libdigest-sha1-perl (2.12-1build1) ...
Setting up git-core (1:1.7.0.4-1ubuntu0.2) ...
Setting up patch (2.6-2ubuntu1) ...
paavo@paavo-laptop:~$ cd ath3k
bash: cd: ath3k: No such file or directory
paavo@paavo-laptop:~$ 

```

The command "cd ath3k" returns No such file/directory.

Seems not to work or I'm doing something wrong

I found this info at:

[http://ubuntuforums.org/showpost.php?p=9253770&postcount=7](http://ubuntuforums.org/showpost.php?p=9253770&postcount=7)

---

### Post by gsocker on 2011-10-11
Ok, after some searching, it looks like the package is in one of the backport packages.  No need to compile it. Install linux-backports-modules-wireless-lucid-generic. It looks like this package contains the driver.

Then remove and reinsert the bluetooth adapter and see if you get anywhere. If it still doesn't find it, please post the results of running dmesg - the last 10 lines should do it.

Hope this helps.

---

### Post by suomalainen on 2011-10-11
@gsocker

THANK YOU VERY MUCH FOR YOUR SUPPORT! And for digging up where those files were that I needed to install. This all did the trick and now I got bluetooth working. Now I just need to fiddle around with the settings and see where I go. I'll mark this thread solved once all is well.

I also want to thank all the other people who offered valuable input to move me ahead in all this. I really appreciate your help as well....

Until next time,

Suomalainen

---

### Post by suomalainen on 2011-10-12
Good Morning Ubunteros,

Couple of questions:

1. Is there supppose to be two Bluetooth icons in the panel? See attached pic.. The icon on right say's "Indicator Applet 0.3.7" and the one on left says "Blueman applet 1.21".

2. System--->Preferences---> has both "Bluetooth" and "Bluetooth Manager" present. should one be removed? If so how?

3. I have my Samsung  Bluetooth mono headset model HM1100 paired w/o issue. However. it I attempt to listen to music or do a mp3 voice recording there is terrible static on the headset. How can I correct this?

Thank You!

---

### Post by gandaran on 2011-10-12
> Is there supppose to be two Bluetooth icons in the panel? See attached pic.. The icon on right say's "Indicator Applet 0.3.7" and the one on left says "Blueman applet 1.21".
if bluetooth works okay with gnome bluetooth manager then just remove blueman as there is no need for two managers installed.

---

### Post by suomalainen on 2011-10-12
@gandaran Thanks!

I still got the static problem on the headset

And now it appears that even know the handset is paired it will not connect and exchange files....

what to do.......

---

### Post by suomalainen on 2011-10-12
Bump.........

As per the static heard when listening to MP3 or making voice recordings, is it possible to load a "mono" something or other for the mono bluetooth headset so that all is heard better?

I did this for my Samsung Nexus S and downloaded from the "market# the app BTmono and now I can hear MP3 and other apps via my bluetooth headset because of installing this BTmonon app.

Thanks again.

---

### Post by gandaran on 2011-10-13
I don't know if this will help but try adjusting to a lower volume on the PC sound preferences.
doing this fixed the static on my microphone (not bluetooth)

---

### Post by suomalainen on 2011-10-14
What I need is a mono plug in so I can hear sound in "mono" over my bluetooth headset.

---

