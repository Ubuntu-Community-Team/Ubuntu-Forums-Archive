---
title: "No sound at all. Kubuntu 10.04"
date: 2012-01-24
forum: New to Ubuntu
---

### Post by zolkin on 2012-01-24
****Hi all!

I've just installed Kubuntu 10.04 on my new Sony laptop, and as I expected I have a lot of troubles with hardware (dear sony....).

I fixed several issues with Flash and Network Drivers, but now I'm stocked with sound.

Out of the box it was no sound at all (e.g. during the boot or on a browser). Then I updated my kernel and everything up to

me@lucid-vaio:~$ uname -r
2.6.32-38-generic

Then I tried to manipulate with installing/deliting pulseaudio using this thread (exactly - step by step)
[http://ubuntuforums.org/archive/index.php/t-1164323.html](http://ubuntuforums.org/archive/index.php/t-1164323.html)
but it didn't help.

Of course I checked the alsamixer and desktop settings to not be "mute".

this is my:

me@lucid-vaio:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****                                                                   
card 0: PCH [HDA Intel PCH], device 0: HDA Generic [HDA Generic]                                              
  Subdevices: 1/1                                                                                             
  Subdevice #0: subdevice #0  

and list of hardware:

zolkin@lucid-vaio:~$ lspci
00:00.0 Host bridge: Intel Corporation Device 0104 (rev 09)
00:01.0 PCI bridge: Intel Corporation Sandy Bridge PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Device 0126 (rev 09)
00:16.0 Communication controller: Intel Corporation Cougar Point HECI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Cougar Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 3 (rev b4)
00:1c.3 PCI bridge: Intel Corporation Cougar Point PCI Express Root Port 4 (rev b4)
00:1d.0 USB Controller: Intel Corporation Cougar Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Device 1c4b (rev 04)
00:1f.2 RAID bus controller: Intel Corporation Mobile 82801 SATA RAID Controller (rev 04)
00:1f.3 SMBus: Intel Corporation Cougar Point SMBus Controller (rev 04)
01:00.0 VGA compatible controller: ATI Technologies Inc Device 6741
02:00.0 Network controller: Intel Corporation Device 0091 (rev 34)
03:00.0 Class ff00: Realtek Semiconductor Co., Ltd. Device 5209 (rev 01)
04:00.0 USB Controller: NEC Corporation Device 0194 (rev 04)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

and finally response on a pulseaudio

me@lucid-vaio:~$ pulseaudio 
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Does Anybody have any ideas how I can proceed further? Any help is greatly appreciated.

---

### Post by zolkin on 2012-01-24
A little bit more systeminformation
System Settings -> Multimedia shows 2 drivers:
1) Playback/recording through the PulseAudio sound server
2) HDA Intel PCH (HDA Generic)
and some
3)Jack Audio Connection Kit

All of them do not produce sound during the test.

Also I'm not 100% sure about should I have the phonon to be installed (now I have it)

---

### Post by zolkin on 2012-01-25
Does Anybody wants to help me?) I really need dat...

---

### Post by mastablasta on 2012-01-25
have you tried with latest Kubuntu version instead (newer drivers?!)? Have you tried upgrading ALSA?

---

### Post by zolkin on 2012-01-25
*ave you tried with latest Kubuntu version instead (newer drivers?!)? *
No I didn't. For several reasons I want to stay with 10.04 (at least it is LTS)

[I]Have you tried upgrading ALSA?
[/I]Do you mean this?:
me@lucid-vaio:sudo apt-get install alsa
[sudo] password for me: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting alsa-base instead of alsa
alsa-base is already the newest version.
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by mastablasta on 2012-01-25
being an LTS doens't matter so much if you don't get hardware support in it. was in similar situation went to one higher version (10.10), now problem is more or less solved. i am hoping that next LTS will solve it completelly and will upgrade to it when it is out.
 
i ment upgrade alsa (you were installing alsa):
no this: [https://launchpad.net/~team-iquik/+archive/alsa](https://launchpad.net/~team-iquik/+archive/alsa)
 
or this: [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)
 
however you should know that the latter method is annuled when you install new kernel update. also latest stable alsa is 1.0.24 something...
 
ALSA are linux sound drivers.

---

### Post by zolkin on 2012-01-25
Thank you so much! Second method helped me: now i have sound everywhere.

Just in case that someone else interesting in it: check other link
*[http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html](http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html)*

The newest stable drivers are:
```
wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.24.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.24.1.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.24.2.tar.bz2
```

---

### Post by mastablasta on 2012-01-25
great. however as i said updates might (and they will) overwrite the installed drivers leaving a mess behind.
I tried to lock the packages but they somehow still got overwritten. the only/best solution is to find a PPA for ALSA 1.0.24 and add it. this will always keep drivers up to date. the first link should therefore be working as well unless you also need utils and lib and that these two are not included in the PPA.
 
 
 
anyway all this can be avoided by using latest verison of Ubuntu.

---

### Post by SeijiSensei on 2012-01-25
10.10 solved a number of problems for me in Kubuntu 10.04.  I'd have designated 10.10 as the LTS version if it weren't for the fixed scheduling that Ubuntu adopts. 

KDE 4 was in too much flux in April of 2010 to be a good basis for an LTS version of Kubuntu.  By October things were much more stable.

---

