---
title: "no wifi connection 10.04"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by briar rabbit on 2012-04-27
Hello all,

I would like to get a wifi going on my PC.

I have WiFiRadar which starts and shows available connections.  The 'automatic configure' option does not work.  Neither does the 'manual configure' option.  However, I may be doing it wrong because it ask questions.  I prefer not to be ask questions by my PC.

The PC is a Lenovo T61 laptop.
Release 10.04 (lucid)
Kernel Linux 2.6.32-33-generic
GNOME 2.30.2

  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:1c:bf:39:9f:c0
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:32 memory:df2ff000-df2fffff


03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945


There is a switch and a button that active the wlan/wifi, both are on.

I also have Connection Manager 0.5.  Could there be a conflict?

I have read several pages and found no answer.  One question does come to mind; if I put the 3.1 Kernel in will that mean I no longer have the 10.04 version of Ubuntu?

Any help is appreciated.

---

### Post by 3rdalbum on 2012-04-27
> **briar rabbit said:**
> Hello all,

I would like to get a wifi going on my PC.

I have WiFiRadar which starts and shows available connections.

I also have Connection Manager 0.5.  Could there be a conflict?

There could indeed. You see, Ubuntu ships with Network Manager, whose job it is to manage wifi network connections. If you've installed WifiRadar and ConnMan, then you've got three systems trying to compete for control.

Before messing around with new kernels, try simply removing WifiRadar and ConnMan and just use Network Manager's applet toward the right of the top panel. See if this can see the network and connect once these other systems are gone.

---

### Post by briar rabbit on 2012-04-27
Hi thanks for the advice, one problem - now I can not get online at all.  

I removed WiFiRadar and Connection Manager and now I can not get online.

I am at the neighbors on a MS (yuk) OS.

I NEED HELP

The Software Center list the Network Manager as installed but I can not find it anywhere.  There is no 'icon' where the Help Center tells me it 'is' so ... ... ... help

I do not do terminals very well so if it be in a terminal ... help

I am not panicking yet       just     getting   a       little   nervous   .  . .

---

### Post by briar rabbit on 2012-04-27
Hello,

So if I have the Network Manager but there is no icon in the system tray ... where is it?

I could sure use some help here.  Can someone tell me how/what to do - to get back on line.

Thanks in advance

---

### Post by wildmanne39 on 2012-04-27
Hi try this:
```
sudo apt-get install --reinstall network-manager network-manager-gnome
```
make sure you have removed the other applications you were using completely including the configuration files then reboot.
Thanks

---

### Post by briar rabbit on 2012-04-27
This is what I got:
```
ferg@ferg-laptop:~$ network manager
network: command not found
ferg@ferg-laptop:~$ la network manager
ls: cannot access network: No such file or directory
ls: cannot access manager: No such file or directory
ferg@ferg-laptop:~$ netman
netman: command not found
ferg@ferg-laptop:~$ sudo apt-get install --reinstall network-manager network-manager-gnome
[sudo] password for ferg: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-30
  linux-headers-2.6.32-21-generic linux-headers-2.6.32-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 144 not upgraded.
Need to get 790kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://archive.ubuntu.com/ubuntu/ lucid/main network-manager-gnome 0.8-0ubuntu3
  Could not resolve 'archive.ubuntu.com'
Err http://security.ubuntu.com/ubuntu/ lucid-security/main network-manager 0.8-0ubuntu3.2
  Could not resolve 'security.ubuntu.com'
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main network-manager 0.8-0ubuntu3.2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3.2_i386.deb  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8-0ubuntu3_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ferg@ferg-laptop:~$ --fix-missing
--fix-missing: command not found
ferg@ferg-laptop:~$ sudo apt-get install --fix-missing
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-30 linux-headers-2.6.32-21-generic linux-headers-2.6.32-30-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 144 not upgraded.
ferg@ferg-laptop:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic linux-headers-2.6.32-30 linux-headers-2.6.32-30-generic
0 upgraded, 0 newly installed, 4 to remove and 144 not upgraded.
After this operation, 171MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 304047 files and directories currently installed.)
Removing linux-headers-2.6.32-21-generic ...
Removing linux-headers-2.6.32-21 ...
Removing linux-headers-2.6.32-30-generic ...
Removing linux-headers-2.6.32-30 ...
ferg@ferg-laptop:~$ sudo apt-get install --reinstall network-manager network-manager-gnome
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 144 not upgraded.
Need to get 790kB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://archive.ubuntu.com/ubuntu/ lucid/main network-manager-gnome 0.8-0ubuntu3
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com/ubuntu/ lucid-updates/main network-manager 0.8-0ubuntu3.2
  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager/network-manager_0.8-0ubuntu3.2_i386.deb  Could not resolve 'archive.ubuntu.com'
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/n/network-manager-applet/network-manager-gnome_0.8-0ubuntu3_i386.deb  Could not resolve 'archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
ferg@ferg-laptop:~$ sudo apt-get network-manager --fix-missing
E: Invalid operation network-manager
ferg@ferg-laptop:~$  
```

How bad is it?

---

### Post by wildmanne39 on 2012-04-27
Hi, you may have a problem with your source list so you may not be able to install any applications.

You did have a wired connection that is working correct when you tried to install network manager? make sure you can load web pages, if so run this command and post the output here.
```
sudo apt-get update && sudo apt-get upgrade
```
Thanks

---

### Post by briar rabbit on 2012-04-27
Thanks for the help.

I have No internet connection.

I just tried to reinstall Connection Management, it came back:

E: Invalid operation reinstall

Well can I get the Network Manager from the CD I used to install Ubuntu the first time?

---

### Post by wildmanne39 on 2012-04-27
Hi, you can put the livecd in the cdrom then go to synaptic, settings, repositories, and put a check by install using cd then reload the repositores, then type network manager into the search window of synaptic and you should be able to install it that way.
Thanks

---

### Post by briar rabbit on 2012-04-27
The repositories told me to do the apt-cdrom in the terminal.  I got the following.

[HTML]ferg@ferg-laptop:~$ sudo apt-cdrom install --reinstall network-manager network-manager-gnome
[sudo] password for ferg: 
E: Command line option --reinstall is not understood
ferg@ferg-laptop:~$ sudo apt-cdrom install network-manager
E: Invalid operation install
ferg@ferg-laptop:~$ [/HTML]

And for just about a minute there I thought it was fixed.

Thanks for the efforts.

---

### Post by wildmanne39 on 2012-04-27
Hi can you not just click on network manager and network-manager-gnome in synaptic with the livecd in and install it that way?
Thanks

---

### Post by briar rabbit on 2012-04-27
I Just looked agian.  Network Manager and Network Manager gnome are installed.  Clicking on them does not give me the option to reinstall. I can only 'mark for removal' or 'mark for complete removal'.

The biggest problem is that the Network Manager does not come up on the system tray - at least that is what I am thinking.  Its installed but its like it is 'turned off'.  It can not be found to work on its properties.  I have tried restarting several times - no change.

---

### Post by wildmanne39 on 2012-04-27
Hi, if they are installed it should be in the panel but right click on the top panel and see if you can add it and run this command it will tell us if network manager is running:
```
ps aux | grep nm-apple
```
if it is I will have you post more information.
Thanks

---

### Post by briar rabbit on 2012-04-28
Hello wildmanne39, 
If your still there here are the results of your request:

[HTMLferg@ferg-laptop:~$ ps aux | grep nm-apple
ferg      4091  0.0  0.0   3324   812 pts/0    S+   05:26   0:00 grep --color=auto nm-apple
ferg@ferg-laptop:~$ 
][/HTML]

The 'nm-apple' appears in red in the original.

I do not remember when the last time was I saw the network manager icon in the system tray area.  It is not there now..
Everything I read says it is there - but says nothing about if it is not there.

I have check the 'as to panel' several time it is always the same - as in no network manager'.

I just tried to add a screen shot of the system tray but I don't see where it worked.

[IMG]http:///home/ferg/Desktop/systemtray.png[/IMG][IMG]http:///home/ferg/Desktop/system%20tray.png[/IMG]

---

### Post by briar rabbit on 2012-04-28
where did it go

---

### Post by wildmanne39 on 2012-04-28
Hi, network manager is running can you connect to the internet with a wired connection now at least? Did you right cliik on the top panel to try to add a network icon?
Thanks

---

### Post by wildmanne39 on 2012-04-28
Hi, since network manager is running in the back ground go ahead and post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
so we can troubleshoot your wireless.

Did you ever have wireless working in 10.04 on this computer?
Thanks

---

### Post by briar rabbit on 2012-04-28
Hi your still here - thanks

I have no internet connection.
I have never had internet connection on that laptop with wireless.
I have started preparing for losing it to a fresh install, the problem is it has a lot of things on it I have no idea how to duplicate; things that I spent hours on this forum reading about to get to work.
OK enough crying.  If it can be saved great.
Apparently I have had a long standing problem with that Network Manager - who'd have thought it would take me off-line completely.

Here are the results you ask for.

Thanks to you and to 3rdalbum, I'll bet he was even more surprised than me that I would loose all connection to the internet.


[HTML]
ferg@ferg-laptop:~$ sudo cat /etc/lsb-release; uname -a
[sudo] password for ferg: 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux ferg-laptop 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
ferg@ferg-laptop:~$ sudo lspci -nnk | grep -ia2 net
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:19.0 Ethernet controller [0200]: Intel Corporation 82566MM Gigabit Network Connection [8086:1049] (rev 03)
    Kernel driver in use: e1000e
    Kernel modules: e1000e
--
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau
03:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4227] (rev 02)
    Kernel driver in use: iwl3945
    Kernel modules: iwl3945
ferg@ferg-laptop:~$ sudo lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
ferg@ferg-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          
ferg@ferg-laptop:~$ sudo rfkill list all
0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes
ferg@ferg-laptop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8740  0 
snd_hda_codec_analog    58598  1 
snd_hda_intel          22069  2 
snd_hda_codec          74201  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
pcmcia                 30784  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
thinkpad_acpi          68083  0 
arc4                    1153  2 
iwl3945                68727  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               467048  2 
iwlcore               106149  1 iwl3945
ttm                    50103  1 nouveau
mac80211              205402  2 iwl3945,iwlcore
yenta_socket           20408  1 
rsrc_nonstatic         10015  1 yenta_socket
tpm_tis                 7488  0 
sdhci_pci               5470  0 
intel_agp              24375  0 
snd                    54244  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
psmouse                63677  0 
serio_raw               3978  0 
sdhci                  15494  1 sdhci_pci
nvram                   6203  1 thinkpad_acpi
led_class               2864  4 thinkpad_acpi,iwl3945,iwlcore,sdhci
pcmcia_core            32964  3 pcmcia,yenta_socket,rsrc_nonstatic
ricoh_mmc               2923  0 
tpm                    13936  1 tpm_tis
tpm_bios                5266  1 tpm
drm_kms_helper         29329  1 nouveau
drm                   162377  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            5028  1 nouveau
agpgart                31724  3 ttm,intel_agp,drm
cfg80211              126144  3 iwl3945,iwlcore,mac80211
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
video                  17375  0 
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39841  0 
ohci1394               26950  0 
ieee1394               81181  1 ohci1394
ahci                   32360  2 
e1000e                119888  0 
ferg@ferg-laptop:~$ 
[/HTML]

Thanks again wildmanne39.
I have not give up on it just trying to fix another pc at the same time - good thing I'm a pack-rat.

---

### Post by wildmanne39 on 2012-04-28
Hi, you have a soft and a hard block for the hard block it usually means the switch or button on the laptop is off try turning it on then use ```
rfkill list all
```
to see if the hard block is gone.

For soft block please post:
```
lsmod | grep wmi
```
Thanks

---

### Post by briar rabbit on 2012-04-28
here it hope it helps

[HTML]ferg@ferg-laptop:~$ sudo rfkill list all
[sudo] password for ferg: 
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ferg@ferg-laptop:~$ sudo lsmod | grep wmi
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54244  17 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,thinkpad_acpi,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ferg@ferg-laptop:~$ 
 [/HTML]

---

### Post by wildmanne39 on 2012-04-28
Hi, the blocks are gone, please post the output of:
```
nm-tool
sudo iwlist scan
```
Thanks

---

### Post by briar rabbit on 2012-04-28
here goes

[HTML] ferg@ferg-laptop:~$ sudo nm-tool
[sudo] password for ferg: 

NetworkManager Tool

State: disconnected


** (process:1766): WARNING **: error: failed to read connections from org.freedesktop.NetworkManagerUserSettings:
    The name org.freedesktop.NetworkManagerUserSettings was not provided by any .service files
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        00:1C:25:18:61:C4

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             disconnected
  Default:           no
  HW Address:        00:1C:BF:39:9F:C0

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    ATT5939:         Infra, 74:44:01:0C:BC:74, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA2


ferg@ferg-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Device or resource busy  [/HTML]

---

### Post by briar rabbit on 2012-04-28
Well something has happened.  I have tried several ... well ok a few times today to get on line and nothing happened BUT, I am on line, on The Machine right now.  GREAT Thanks a lot.  however - what the heck did you do?  All I thought we did was put in code to see what was what.  It works though and just like before I have no icon in the panel telling me whether I am connected or not.  I have in the past just when to a known website and when there ... well I knew I was on line.

OK you have spent a lot of time already wildmanne39 do you have the time to help me get an icon for the network manager?

Really you hanged in there when I was close to ... well  .. close to something far from the happy now. hurray hurray

this is good definitely good

PS:   in my excitement I forget to mention this is only the Ethernet connection, still I am on line ........

---

### Post by 3rdalbum on 2012-04-29
Yes, I was a bit surprised and felt bad when you said that you couldn't get any connection now.

However, not all is lost. If you have network-manager-gnome then there are two reasons you might not have the icon on your panel:

1. You haven't got the "notification area" applet on the panel, or
2. the nm-applet program just isn't running.

Right-click on your top panel and choose "Add to Panel" and then choose the Notification Area applet. If you get an error message saying that there's already a notification area running, then keep reading.

If you have a notification area but still no Network Manager icon, then you should try opening a terminal and typing:

```
nm-applet
```

which should start the Network Manager applet and make it appear on the panel. Note that it will disappear when you close the terminal, so don't close the terminal yet.

Now that we know we have a notification area, but need to manually start nm-applet, you can add the 'nm-applet' command to your Startup Applications. It's been a while since I've used 10.04 but it's under System > Preferences > Startup Applications or System > Preferences > Session or something like that.

---

### Post by wildmanne39 on 2012-04-29
Hi, I am glad you are online please do:
```
sudo apt-get update && sudo apt-get upgrade
```
Then reboot and unplug wired connection then
```
sudo rmmod -f iwl3945
sudo modprobe iwl3945 disable_hw_scan=1
```
see if wireless comes on but do not reboot if it works we will need to make it permanent.
Thanks

---

### Post by briar rabbit on 2012-04-29
Welcome back first responder,

I put the notification area in the panel, using the 'add to panel'.  Nothing happened; no error, no network manager. 

It should be by the clock and battery graph and while looking there I saw several almost clear lines. It was 5, yes FIVE notification areas. 

I deleted them all.  

I went to System > Preferences > Startup Applications as you said.  Removed 'connection management' which was not in the panel anyway.  Then a clicked on the Network Manager.  Badda bing badda bomb, rise and shine Network Manager its show-time.

So now the test.  Right now I have ethernet connection, I have the Network Manager icon telling all sorts of things; when I'm on-line and when I'm not and a dialog of such groovy things as 'Wireless Networks available". 

So I go to the neighbors house (they have wireless, I am wired).  I have a strong signal and I think what is the right password (they are not home and the password they gave me the other day was indeed wrong).

New Problem.  I am ask for the Login Keyring password which I give but it does not take (you'd think if it -the pc- is going to ask a question it would accept the answer given it).

I go to Help and it tells me to Edit the chosen connection and it will not ask for the password again. NOT SO.  That part of the wireless connection that says "Available to all users" is grayd out cain't chang dat.

The new question is. Why is the wireless connection asking me for my login password but not accepting the only password I have ever used? and Why is the 'available to all users' in the edit option grayed out?

OK thanks for hanging in there wildmanne39, I will hold up on the code action until I hear back about this new and thrilling development.

Thanks all

---

### Post by briar rabbit on 2012-04-29
done:
sudo apt-get update && sudo apt-get upgrade
done also:
sudo rmmod -f iwl3945 sudo modprobe iwl3945 disable_hw_scan=1 Unfortunately no good at all.

I read this post: [http://ubuntuforums.org/showthread.php?t=1929976&highlight=wireless+internet+10.04](http://ubuntuforums.org/showthread.php?t=1929976&highlight=wireless+internet+10.04)

and did everything there as well - because it is a 10.04 also.  But no good.

I read another post where someone mentioned it strange that so many people have trouble with their wireless internet.  It does seem odd, is it because so much out there is proprietary?

Thanks for helping

---

### Post by wildmanne39 on 2012-04-29
Hi, I am sorry I am replying slow I installed 12.04 and it is not working well.

That other thread does not have the same driver as you so when you do things like that from other posts you can create more trouble then you had before.

I will get back to you as soon as my system is have way usuable.
Thanks

---

### Post by briar rabbit on 2012-04-30
OH Rejoice rejoice.  I have been working on this internet connection for 2 years.  Every once in a while I would spend hours on it, get very frustrated and give up on it.  BUT NOW IT WORKS

Apparently the 'WiFiRadar' I had read about at one time was not the answer.  Neither was the 'Connection Management'.

Who says doing the same thing over and over expecting different results is the definition of insanity?  It may be the only way to get a PC to work.  Well, OK not 'exactly' the same thing over and over BUT CLOSE.

So, apparently I was not doing the last part right in the edit connection.  They're not the same thing a key and a key ring and a password and a ... well you get the picture.

Please don't get mad at me, I'm just trying to be honest with those trying to help me.

All the stuff wildmanne39 and 3rdalbum told me would have worked a little earlier if I had been better on my end.

Thanks a lot for the help.

I could not image myself doing what you and others do here (I will never know that much about computers) but, I would sure hate the thought of living in a world without you.

---

### Post by wildmanne39 on 2012-05-01
Hi, your welcome! I am glad your wireless is working.
Enjoy

---

