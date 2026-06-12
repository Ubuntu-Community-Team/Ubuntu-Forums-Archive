---
title: "[SOLVED] Sound troubleshooting"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by Camilia on 2008-08-13
Hi
I have lost my sound. Should I fix the problem in windows xp before I move to Ubuntu or can it be done in Ubuntu.

---

### Post by Dill on 2008-08-13
Is your sound not working in Windows XP or Ubuntu (or both)? If your sound suddenly stopped working in both, it could be a hardware issue. If your sound is working in one OS and not in the other, you'll want to troubleshoot it in the OS in which the sound *isn't* working. 

Do you have a laptop or a desktop? 

Do you have built-in or external speakers? 

Did you make any changes to your sound configuration recently?

If you have a laptop with a mute button, have you tried pressing that on and off to see if you accidentally may have turned off the sound?

Have you tried anything thus far to fix the problem?

Sorry about all the questions. I just want to help you figure out what's up.

Cheers, 
Dylan

---

### Post by ajmorris on 2008-08-13
hi there,
as well as the questions outlined above, can you please post the output of:
```
sudo lspci
```
from a terminal.
This will give us a list of the hardware connected to your computer, so that we can help you get your sound card working in ubuntu :)

AJ

---

### Post by Camilia on 2008-08-13
I don't have ubuntu downloaded permanently at present on my desktop. I am positive the problem is software. I had it working then did a mini restore, for unable to remove hp printer in remove area. The mini restore got stuck. After waiting for 1.5 I decided I had to do a restore with the factory disk.

Now my computer says I don't have the card. Don't see the nvidia mixer I saw before. Tried the add programs, which worked before the restore and got message all working. 

I ran driver inspector and it said I am missing drives. Will repair for $30. That's a waste for eventually switching to ubuntu.

---

### Post by Camilia on 2008-08-13
> **ajmorris said:**
> hi there,
as well as the questions outlined above, can you please post the output of:
```
sudo lspci
```
from a terminal.
This will give us a list of the hardware connected to your computer, so that we can help you get your sound card working in ubuntu :)

AJ

I don't understand how to get the sudo lspci. Is that in ubuntu. I don't have that downloaded at present. Am downloading it now.

---

### Post by OldTimeTech on 2008-08-13
go to applications->accessories->terminal

it will come up with: marianne@RebelWoman:~$ which is where you put sudo lspci
it will then ask for your password.

You can then highlight and paste into this conversation.

---

### Post by Dill on 2008-08-13
> I don't have ubuntu downloaded permanently at present on my desktop. 

So are you in Windows at this point?

> I am positive the problem is software. I had it working then did a mini restore, for unable to remove hp printer in remove area.

What did you do when you did a "mini restore"? And why were you removing something relating to your hp printer?

> The mini restore got stuck. After waiting for 1.5 I decided I had to do a restore with the factory disk.

After waiting for 1.5 what? And what kind of factory restore did you do? Did you reinstall a piece of software, or try to reinstall Windows?

> Now my computer says I don't have the card. Don't see the nvidia mixer I saw before. Tried the add programs, which worked before the restore and got message all working. 

So at this point, can you see your sound card in Windows XP? Do you know how to check your devices out in the Device Manager?

> I ran driver inspector and it said I am missing drives. Will repair for $30. That's a waste for eventually switching to ubuntu.

If you're missing drivers, you shouldn't have to pay $30 for them. They should be freely available on the internet. If you can tell me what kind of sound card you have (check in the Device Manager-- you should be able to right-click on "My Computer", which should either be an icon on your Desktop or somewhere in your Start Menu, go to Properties, and a new window should pop up; go to the Hardware tab and click on the icon for the "Device Manager"; if your sound card appears, it may have a small yellow exclamation point near it).

If you can fill me in a bit more, I may be able to help you.

---

### Post by Camilia on 2008-08-13
> **Dill said:**
> So are you in Windows at this point?

What did you do when you did a "mini restore"? And why were you removing something relating to your hp printer?

After waiting for 1.5 what? And what kind of factory restore did you do? Did you reinstall a piece of software, or try to reinstall Windows?
Reinstalled windows.

So at this point, can you see your sound card in Windows XP? Do you know how to check your devices out in the Device Manager?

If you're missing drivers, you shouldn't have to pay $30 for them. They should be freely available on the internet. If you can tell me what kind of sound card you have (check in the Device Manager-- you should be able to right-click on "My Computer", which should either be an icon on your Desktop or somewhere in your Start Menu, go to Properties, and a new window should pop up; go to the Hardware tab and click on the icon for the "Device Manager"; if your sound card appears, it may have a small yellow exclamation point near it).

If you can fill me in a bit more, I may be able to help you.
Yes still using Windows.

Went into accessories to restore back to a few days. To resolve problems with printer hp rep said to remove but I was unable to do so.

No, I don't see the sound card in there now. I had seen it previously. I have checked everything that applies to sound. All is working properly.

Driver Detective says I am missing multimedial audio controller, PCI Bridge Device, and SM Bus Controller. Also out of date is the NVIDA GeForce4 MX integrated GPU and Standard Dual Channel P CI IDE Controller.

In emachine forum specificationss say sound is n-Force 6 channel audio. Emachine sent me a link to upgrade the motherboard but it kept warning that my system may crash, thus don't want to use it.

---

### Post by Camilia on 2008-08-13
Well I have ubuntu on my computer now, temporary mode until I can figure out how to burn backups.  The sound came on when it started up. Another reason to switch to ubuntu. Just it boots up slower. Probably keep windows to check traffic when i am in rush.

I pasted sudo lspci in terminal and didn't get prompted for password. I don't know how to post the results.

Tried to go to other area, youtube and new on film, to test the sound. Unable to because need flash player.

Need to download flash player. There are 3 versions to download.
There is tar.gz, .rpm. and YUM. Which 1 should I download?

---

### Post by Camilia on 2008-08-13
> **Camilia said:**
> I don't understand how to get the sudo lspci. Is that in ubuntu. I don't have that downloaded at present. Am downloading it now.

I went into ubuntu and it did as you said. It showed all the drivers I need for sound. Am I suppose to do something with them? Didn't get prompt for password.

---

### Post by enz on 2008-08-13
Hi, I am also having the same problem.
This is my message after I typed sudo lspci

enz@enz-laptop:~$ sudo lspci
[sudo] password for enz:
00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
02:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:00.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev aa)
02:00.2 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 02)
02:02.0 Network controller: Intel Corporation PRO/Wireless LAN 2100 3B Mini PCI Adapter (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

I saw a Multimedia audio controller there....so what's the problem causing no sound? Thanks:)

---

### Post by Dan_Cl on 2008-08-13
I am also having the same problems,

my lspci dump;

[sudo] password for dan: 
00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:06.0 Multimedia audio controller: nVidia Corporation nForce3 250Gb AC'97 Audio Controller (rev a1)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:09.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation CK8S Serial ATA Controller (v2.5) (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV40 [GeForce 6800 Ultra] (rev a1)
02:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
02:0a.0 Multimedia audio controller: Ensoniq 5880 AudioPCI (rev 02)
02:0c.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 46)
02:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)


Thanks folks :)

Ok - so I can play music with the MP3 software but when I try writing tab in Rosegarden I dont get anything played back.

---

### Post by ajmorris on 2008-08-13
good ol' AC'97 audio controllers. Ok, all those having issues, you will need to install the alsa-utils package from the repositories. and run ```
sudo alsaconf
``` in a terminal. Follow the prompts to set up your card using AC'97 not generic. If this does not resolve your issue, make sure in alsamixer, or another mixer, that your volume is not muted, and is turned up an efficient amount. If it is still not rectified, can you please post the output of sudo lsmod, and the kernel config file if you make your own kernel, or just the config file from the kernel headers. -- however, i doubt the kernel is at fault if you use an ubuntu kernel, as everyone using your kernel version in ubuntu would have issues with AC'97.... co-incidentally, what kernel version are you using? (```
uname -a
```)
 
AJ

---

### Post by BirkMcGirk on 2008-08-14
i am completely new to ubuntu, i have no idea what to do, and i'm not that good with computers to begin with. but my problem is that i installed ubuntu 8.04 onto my desk top, and the sound wont work, and yes i've tried putting alsa mixer in the terminal window, and no, nothing was muted. any suggestions?

---

### Post by Camilia on 2008-08-14
I think I have sound for heard sound out of speaker when I rebooted. Can can verify it. When trying to view film news at comcast.net got message that I need adobe reader. Suggestion for 3 versions - tar.gz, .rpm. and YUM. Which 1 do I use?

---

