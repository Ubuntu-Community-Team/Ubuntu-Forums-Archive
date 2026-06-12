---
title: "still no sound"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by sven_wien on 2008-11-11
Hello all i have an Acer Aspire 6920G with an Realteak ALC889 Soundcard and i need some easy instructions to get this porblem sorted asap.

many thanks

Sven

---

### Post by shredder12 on 2008-11-11
are you able to get system beeps or start up sound..??

---

### Post by sven_wien on 2008-11-11
No beeps no sounds

---

### Post by shredder12 on 2008-11-11
open System->preferences->sound what do you seee??
It should be a window you will see about 4 "Test" buttons..
Is this what you see??

---

### Post by kansasnoob on 2008-11-11
Start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by sven_wien on 2008-11-11
thats what i see but the test buttons dont give sound, u can press them its analysing but silence. its a problem from the ALC889 driver?

---

### Post by sven_wien on 2008-11-11
Anything i can do? Is it a problem with the driver or not?

---

### Post by sven_wien on 2008-11-11
Hello all,

i have an Acer Aspire 6920G with an ALC889 Sound Card and now i downloaded the Alsa-Projekt driver 1.0.18 (what driver is installed on ubuntu 8.10) i just dont know how to install it now!
I downloaded all in a folder called audio on the desktop (also-driver, alsa-lib-1.0.18 , alsa-tools-1.0.18, alsa firmware1.0.18) its a gz.tar file!

thanks

or if there is a quicker or easier way to get sound on my pc please also let me know

thanks

---

### Post by sven_wien on 2008-11-11
or if its easier i got following problem:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

---

### Post by Elfy on 2008-11-11
I'll have a look into it - not sure I'll be able to help 

Couple of things to say though -

Firstly - people search for 0 reply threads - so it's best to not bump for at least 24hours, if you need to add information then edit the first post.

Secondly - it is not all right to add things like > thats the same problem i have so pls keep me informed to someone elses thread - especially when it stops it from having 0 replies. Youcan subscribe to threads if you feel that it might help you - Thread Tools - Subscribe to thread

Thirdly - don't post duplicate threads on the same problem - one is sufficient. In this thread of yours [http://ubuntuforums.org/showthread.php?t=978320](http://ubuntuforums.org/showthread.php?t=978320) - post #5 suggests the troubleshooting guide - did you do that - if not try to do so, if you did then say so there, it will help people diagnose your issue if you give where the error occurred.

I have subscribed to that thread and will follow it from there once you have answered that #5 post.


Edit - this looks odd after thread merging :)

---

### Post by sven_wien on 2008-11-11
okyes i have tried the helping point # 5 but did not help me as i realy struggle to get things working here. and i realy just want to install newer driver if i would know that ubuntu 8,10 is using a lower driver.
its real bad as i am using this pc for presentations and i need sound with that and now i cant do that. so f u could help i realy would be greatful for that.

thanks

sven

---

### Post by Elfy on 2008-11-11
Please open a terminal and run this, post output in code tags please - either use # button in New Reply or in a quick reply box add [noparse]```
[/noparse] before the pasted output and [noparse]
```[/noparse] after it.

```
lspci
```

---

### Post by sven_wien on 2008-11-11
```
xxl@xxl-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 9500M GS (rev a1)
02:00.0 Ethernet controller: Attansic Technology Corp. L1 Gigabit Ethernet Adapter (rev b0)
08:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
0a:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
0a:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
0a:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
0a:00.4 System per
```

---

### Post by Elfy on 2008-11-11
Please run this and paste output 

```
aplay -l
```

---

### Post by sven_wien on 2008-11-11
```
xxl@xxl-laptop:~$ aplay -l
**** Liste von PLAYBACK Geräten ****
Karte 0: Intel [HDA Intel], Gerät 0: ALC889 Analog [ALC889 Analog]
  Untergeordnete Geräte: 1/1
  Untergeordnetes Gerät '0: subdevice #0
xxl@xxl-laptop:~$ 

```

---

### Post by shredder12 on 2008-11-11
hey before doing anything you should first try to configure sound preferences..
System->preferences->sound
there try different..options e.g. yours might be initially set to autodetect for audio playback by default..so change it to Alsa and then test of change it into OSS and then test..this is how i got mine to work. ..If you get a beep..then your problem is solved..
I hope this helps..

---

### Post by sven_wien on 2008-11-11
i tried that it gives me an error
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```
and i tried all and no beep

---

### Post by Elfy on 2008-11-11
assuming that you have tried to up volumes in alsa-mixer look at this thread, come back with any issue you have - make sure you know what you change so you can undo it if necessary

back it up to your home before you start
```
sudo cp /etc/modprobe.d/alsa-base ~/alsabase
```

Thread is here [http://ubuntuforums.org/showpost.php?p=5017453&postcount=2](http://ubuntuforums.org/showpost.php?p=5017453&postcount=2)

we'll try that before we look at the driver you got.

---

### Post by sven_wien on 2008-11-11
strange, nothing happendQ!

```
xxl@xxl-laptop:~$ sudo cp /etc/modprobe.d/alsa-base ~/alsabase
xxl@xxl-laptop:~
```

i restarted laptop but nothing no sound!

---

### Post by Elfy on 2008-11-11
Check it did it - from terminal

```
ls alsa*
```

If it's there look into that thread

---

### Post by sven_wien on 2008-11-11
xxl@xxl-laptop:~$ ls alsa*
alsabase
xxl@xxl-laptop:~$ 

can it realy bethat complcated?

i dont understand what is wrong

---

### Post by Elfy on 2008-11-11
can what be that complicated - have you looked at the thread link I gave you?

---

### Post by sven_wien on 2008-11-11
yes i have but it didnt help me

---

### Post by Elfy on 2008-11-11
Did you reboot?

I'll have a look about - but I'm not sure atm.

---

### Post by sven_wien on 2008-11-11
yes i rebooted and ubuntu installed updateds but still no sound

---

### Post by Elfy on 2008-11-11
Try setting sound to alsa - it's set to autodetect default - System > Prefernces > Sound 

Set sound playback to alsa or try oss

---

### Post by sven_wien on 2008-11-11
```
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Could not open audio device for playback.
```
this i got with HDA Intel ALC889 Analog ALSA

and others dont work either

---

### Post by shredder12 on 2008-11-11
Now, your problem looks a bit complicated but lets clear the basics first...have you tried to increase the volume in alsamixer..
if not..execute "alsamixer" and increse the volume..
Then you might have got a drivers cd with you computer...provided by the manufacturer..
there he might have provided you with drivers to be used with linux..check it out..
may be they could solve your problem..

---

### Post by sven_wien on 2008-11-11
no there was no cd given with the laptop and it was all vista.
and the only drivers i now got isthe alsa drivers and they are 1 number higher then the istalled once so how do i install them?

---

### Post by shredder12 on 2008-11-11
from where did you get the drivers..
If its from realtek site..then its alright..otherwise you should visit that site and download the drivers that are compatible with your system..
Could you tell me a bit more about the drivers you have downloaded..??

---

### Post by sven_wien on 2008-11-11
well i downloaded it from alsa project but ts a simelar drier than ubuntu has just more up to date. just how do i install it or how else do i get sound working?

---

### Post by shredder12 on 2008-11-11
I am not sure about the drivers you have downloaded..but i would still insist to search for appropriate linux drivers for your sound card..on realtek site..at least it is a reliable source..and i think the will provide  you with an brief installation manual to install the drivers..

---

### Post by sven_wien on 2008-11-11
well i had a look there but i didnt find a driver there if someone does pls leave the link here thaks

---

### Post by sven_wien on 2008-11-11
so i been thru most online websites to try to get sound but nothing anyone else here having that problem or had that problem?

---

### Post by sven_wien on 2008-11-12
hi all,

ok i now tried to install the new audio driver (ALSA 1.0.18) but i seem to do something wrong i still got no sound!
Anyone has same problem as I ?

Maybe someone can give me easy to use discription how to install the driver or maybe other solution to finaly get sound on my acer aspire 6920g


thanks to all until now!

---

