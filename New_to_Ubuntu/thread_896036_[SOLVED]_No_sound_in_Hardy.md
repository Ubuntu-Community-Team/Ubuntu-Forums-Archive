---
title: "[SOLVED] No sound in Hardy"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by talibanned on 2008-08-20
Hi guys,

I am a newbie user, as in 2 days experience. Hardy hs been wonderful to load up on my computer. I have got my video card drivers working and it all seems very nice indeed.... however:

i cant get my sound to work.  I realise there are a lot of threads about Intel soundcard issues with hardy and have tried my best to read through them and follow the instructions. i seem to be hitting a brick wall somewhere though.

for instance when i go 

cat /proc/asound/card0/codec#* | grep Codec

to look at what sound card i have got, it doesnt find the folder. (there is no folder asound in the proc directory)

i have also hit a brick wall in trying to get OSS to work. i have no idea what to do now.


Thanks in advance guys....

---

### Post by spiderbatdad on 2008-08-20
[http://ubuntuforums.org/showthread.php?t=891485](http://ubuntuforums.org/showthread.php?t=891485)

see if the second post in that thread helps.

---

### Post by talibanned on 2008-08-20
ok i installed those additional items as shown in post 2 but now no device is showing up in my Default Mixer Tracks in the Sound Preferences window.

Also now when I double click the volume icon on the taskbar i now get the following message:

"The volume control did not find any elements or devices to control, that means either you dont have the right Gstreamer plug-ins installed or that you dont have a sound card configured."


hmmmmmmmm O_o

thanks for your help by the way!!!

---

### Post by spiderbatdad on 2008-08-20
I too had a lot of trouble with the 2.6.24 kernel and my intel sound card. I ran hardy with the alpha kernel 2.6.22 for a long time. I'm now using Intrepid 2.6.26. It detected my sound card right away, and has worked perfectly. I'm not sure what to recommend regarding the kernel you are using. Rebuilding alsa can be difficult, and then it may not work. My best suggestion is to install Gutsy or Intrepid. Sorry for the cop-out. Maybe someone else knows a fairly easy way to get ICH3 or ICH5 working on the hardy kernel...I assume that is your sound card.

---

### Post by talibanned on 2008-08-20
yep im pretty sure its the ICH5 :(

hmmm this is a massive problem...

---

### Post by spiderbatdad on 2008-08-20
here's an interesting thread: [http://ubuntuforums.org/showthread.php?t=720043](http://ubuntuforums.org/showthread.php?t=720043)

There may be help at launchpad here:[https://bugs.launchpad.net/bugs/194816](https://bugs.launchpad.net/bugs/194816)
but the site is temporarily doing routine maintenance...shouldn't take too long to get back up.

---

### Post by talibanned on 2008-08-21
ok here is part of the output of my lspci....

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 11
	Region 0: Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>


i was wrong about it being ich5, it seems to actually be ICH8....


i looked at the threads you gave me but i am still getting nowhere! i dont know whether to laugh or cry....

---

### Post by talibanned on 2008-08-21
[I]
 Hanusz leszek wrote on 2008-03-24: (permalink)

@earthforce:

Your (and mine) bug is reported here (and got high priority):
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/188287/)

So you're right, it comes an incorrect dependency of the nvidia driver.
[/I]


hmmm i do have a set of proprietory nvidia drivers running. i will report back if i find out if this is whats causing it....

---

### Post by talibanned on 2008-08-21
here is a screen dump of my installed nvidia drivers in synaptic manager.

how do i know if i have the right ones installed?

are there any known issues with the nvidia dependancy for driver version 169.12+2.6.24.13-19.45??

:confused:

---

### Post by talibanned on 2008-08-21
top. need help :(

---

### Post by talibanned on 2008-08-21
top.

i just reinstalled hardy from scratch and im still having the same problem.

does anybody have any idea about support for ICH8 Intel Soundcards??
please help!!

---

### Post by talibanned on 2008-08-21
How do i run my alsa-info script to obtain alsa-info.txt ?????

---

### Post by talibanned on 2008-08-21
top. not getting any help with this.... ((here is some more info))



arthur@arthur:~$ uname -a
Linux arthur 2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux
arthur@arthur:~$ sudo lspci -vvv -s lb.0
[sudo] password for arthur: 
lspci: -s: Invalid slot number
arthur@arthur:~$ sudo lspci -vvv -s 1b.0
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: QUANTA Computer Inc Unknown device 0770
	Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
	Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
	Latency: 0, Cache Line Size: 64 bytes
	Interrupt: pin A routed to IRQ 22
	Region 0: Memory at f0700000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
		Flags: PMEClk- DSI- D1- D2- AuxCurrent=55mA PME(D0+,D1-,D2-,D3hot+,D3cold+)
		Status: D0 PME-Enable- DSel=0 DScale=0 PME-
	Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
		Address: 0000000000000000  Data: 0000
	Capabilities: [70] Express Unknown type IRQ 0
		Device: Supported: MaxPayload 128 bytes, PhantFunc 0, ExtTag-
		Device: Latency L0s <64ns, L1 <1us
		Device: Errors: Correctable- Non-Fatal- Fatal- Unsupported-
		Device: RlxdOrd- ExtTag- PhantFunc- AuxPwr- NoSnoop+
		Device: MaxPayload 128 bytes, MaxReadReq 128 bytes
		Link: Supported Speed unknown, Width x0, ASPM unknown, Port 0
		Link: Latency L0s <64ns, L1 <1us
		Link: ASPM Disabled CommClk- ExtSynch-
		Link: Speed unknown, Width x0

---

### Post by phantomjoker on 2008-08-21
ok, im not a great ubuntu user since i am quite new, but i have had a problem with sound after a perticular update - 

try installing the package alsa-base

(ps - try not to bump so often, although guilty of it myself previously, it can get a thread removed) - just helpful advice, im not getting at you :)

---

### Post by talibanned on 2008-08-21
thanks but ive already tried that :/

sorry for bumping this thread so much but it has been going on for a few days now and is really stressing me out. almost to hte point of me deleting hardy.

---

### Post by talibanned on 2008-08-21
sorry but top.

---

### Post by talibanned on 2008-08-23
SOLVED.

Obtain your audio controller information in the Terminal application using

**lspci -v**

my card is an Intel 82801H **ICH8 rev 03** Audio Systems 

now type in

**grep Codec /proc/asound/card0/codec#***

this will tell you what sound drivers you are running. in my case it is a Realtek ALC885.
make a note of your driver.

Now type in

**zless /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz**

this will get you to a huge list of information on Alsa configurations.
Scroll down through this list until you find the driver that corresponds to yours, i.e. in my case the ALC885.
Under that driver heading you will find a list of codes which you can try to input into your alsa base file.

eg.

[B]ALC882/885
	  3stack-dig	- 3-jack with SPDIF I/O
	  6stack-dig	- 6-jack digital with SPDIF I/O
	  arima		- Arima W820Di1
	  targa		- Targa T8, MSI-1049 T8
	  asus-a7j	- ASUS A7J
	  asus-a7m	- ASUS A7M
	  macpro	- MacPro support
	  mbp3		- Macbook Pro rev3
	  imac24	- iMac 24'' with jack detection
	  w2jc		- ASUS W2JC
	  auto		- auto-config reading BIOS (default)[/B]


copy these codes related to your drivers to a notepad or something. you might need to try a few of them!

in Terminal type

**sudo gedit /etc/modprobe.d/alsa-base**

this will take you to the alsa-base file.  Scroll down to the bottom and input

**options snd-hda-intel model=**

then add whatever code you want to try from the list you wrote down.
in my case (I am running an Alienware M15x) I successfully used the macbook pro rev 03 code (mbp3) which gives me:

**options snd-hda-intel model=mbp3**

now save the alsa-base file and restart ubuntu, make sure that all your sound options are turned up.
if you hear a lot of static when you boot up it might be because the microphone gain is too high and is feeding back, just reduce the mic levels until the hiss subsides.

ok thanks dudes!

---

