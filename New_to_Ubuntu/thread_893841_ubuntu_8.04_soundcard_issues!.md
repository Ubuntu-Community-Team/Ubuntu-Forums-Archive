---
title: "ubuntu 8.04 soundcard issues!"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by hitman1985 on 2008-08-18
i got big issues with the easiest stuff here, 

i cant get 5.1 sound, i cant get a precision microphone to sound what it cost me, because of the pulse audio just keeps a static tone in the back and so on

maybe someone could tell me how im supposed to install a driver or whatever for a REALTEK 5.1 chip

> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5200] (rev a1)
02:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)


there is the lspci stuff

thanks for help in advance.

---

### Post by nicedude on 2008-08-18
You might need a special driver but I am not sure you do. First try these 3 commands that have to do with sound issues. Each one will open a GUI type window and you can check settings. Run each of these in a terminal window.

sudo alsamixer

gnome-sound-properties

gnome-sound-recorder

Try each of those and see if you can find somewhere where you see a microphone input turned off. Also if under Gnome sound properties yours has pulse selected for all of them try changing to alsa or automatic and see if that does it.

---

### Post by markbuntu on 2008-08-18
That is an AC'97 sound chip and should work without any special drivers. You may need to turn on the mic boost in the sound mixer to get that mic to work. 

For 5.1 surround sound you need to do this (2 channel sound is the default and you need to change that):

Open the etc/pulse/daemon.conf file in an editor as sudo. In a terminal type:

 sudo gedit /etc/pulse/daemon.conf

find the line:

default-sample-channels=2

change the 2 to 5, for 4.1, 6 for 5.1, 8 for 7.1. Save the file and restart the pulseaudio daemon.

---

### Post by hitman1985 on 2008-08-18
hmm ok
i did like you said the terminal stuff, but nothing is different, cant i just get rid of this pulseaudio stuff, i tried to solve the issue with the output sound by puting this stuff on there, because before i had the pulseaudi stuff my mic worked perfectly fine, just no surround.

if so, please let me know how to erase every single bit of this pulseaudio "crap", because its not necessary right ?

the mic problem is not because turned off or on, it just gives me a very silent flickering witch i can see in the volume Meter for input.

thx again

---

### Post by markbuntu on 2008-08-18
Did you try changing the device in System/Preferences/Sound/Audio Conferencing/Sound Capture?

---

### Post by hitman1985 on 2008-08-18
[IMG]http://hitman1985.com/gallery/albums/album05/sound.sized.png[/IMG]

thats how i had it setup 

isnt that how i need it ?

---

### Post by markbuntu on 2008-08-18
No, the OSS mixer might not work, do you have a choice for ALSA?
Also, you should change those other settings from autodetect to ALSA.

If you really want to get deep into this, you can read my guide:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by hitman1985 on 2008-08-18
skype wont give me the alsa option, just default or pulse and all the ich... stuff, 

i also would like to hear some opinions on screen recording tools ;)

thank you

---

