---
title: "Do Redhat linux drivers work on ubuntu?"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by distinct on 2008-10-29
Pretty much got a hp xw8000 workstation and wanted to try linux on it, but does ubuntu actually support the redhat drivers since those were really the only ones beside the windows ones that were made for the computer?
Else how would it be possible to get a sound driver to work on the computer?

---

### Post by macogw on 2008-10-29
Uh, maybe?  It all depends.  If it's a .rpm, no.  If it's a .tar.gz or .tar.bz2 or .tgz, maybe.  Red Hat uses a very old kernel, so it's possible the driver wouldn't be compatible with the Ubuntu kernel.  It's also possible the install script would look in RedHat-specific directories.

What sound hardware do you have?  Post the output of "lspci" from your terminal, please.  Either that, or try going on IRC (you can use Pidgin for this, but XChat might be easier to figure out), connecting to the irc.freenode.net server, and asking in #ubuntu-audio-help.  I'm often there, and there's a guy that does sound drivers that's in there too.  He's not always at his keyboard, but if you try between like 21:00 UTC and 04:00 UTC (or between 5pm and midnight Easter US time), he's usually around.

---

### Post by distinct on 2008-10-29
Pretty much trying to get sound working on the computer our of the rear and front jacks instead of having to listen to it on the computers default loudspeaker :/
I also had a look in the sound section with the vanilla system, it seems there were like 7 options in the drop down, all of the contributed to the loudspeaker and the the jacks at the time except for the second option which contributed to neither "Intel 82801-ICH4 with AD1981 Intel 82801DB-ICH4 0 IEC958 (ALSA)" (I have no clue :/) as i know from windows, sound doesn't usually work on the computer except for the default beeps without drivers, though just wondering if this one may be a bit different as it already seems to connet to the computer default loudspeaker.

```
ryan@Workstation:~$ lspci
00:00.0 Host bridge: Intel Corporation E7505 Memory Controller Hub (rev 03)
00:00.1 Class ff00: Intel Corporation E7505/E7205 Series RAS Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation E7505/E7205 PCI-to-AGP Bridge (rev 03)
00:02.0 PCI bridge: Intel Corporation E7505 Hub Interface B PCI-to-PCI Bridge (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV28GL [Quadro4 980 XGL] (rev a1)
02:1c.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1d.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
02:1e.0 PIC: Intel Corporation 82870P2 P64H2 I/OxAPIC (rev 04)
02:1f.0 PCI bridge: Intel Corporation 82870P2 P64H2 Hub PCI Bridge (rev 04)
03:03.0 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
03:03.1 Ethernet controller: Intel Corporation 82546EB Gigabit Ethernet Controller (Copper) (rev 01)
03:05.0 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
03:05.1 SCSI storage controller: LSI Logic / Symbios Logic 53c1030 PCI-X Fusion-MPT Dual Ultra320 SCSI (rev 07)
05:00.0 VGA compatible controller: nVidia Corporation NV17GL [Quadro NVS] (rev a3)
05:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:03.0 Ethernet controller: Intel Corporation 82540EM Gigabit Ethernet Controller (rev 02)

```

---

### Post by macogw on 2008-10-29
In Linux, the drivers are generally included as part of the kernel.  It's likely that your hardware just needs some quirk to tell it exactly how to behave.

What do you mean when you say they contribute to the loudspeaker and the jacks?  Your issue is that you have no sound from your headphone jacks, right?  And your microphone jack is...untested?

---

### Post by bumanie on 2008-10-29
It is a bit hit and miss, but there is a program called alien that converts .rpm --> .deb and .deb --> .rpm [Look here]("http://linux.softpedia.com/get/Utilities/Alien-2594.shtml"). If you look on the internet, there will be tutorials re how to use alien.

---

### Post by macogw on 2008-10-29
> **bumanie said:**
> It is a bit hit and miss, but there is a program called alien that converts .rpm --> .deb and .deb --> .rpm [Look here]("http://linux.softpedia.com/get/Utilities/Alien-2594.shtml"). If you look on the internet, there will be tutorials re how to use alien.

1. It's most likely a tarball
2. If it's a driver .rpm, that is a very very bad idea.  The driver would be compiled for a different kernel version and is thus 99% guaranteed not to work, and probably not even to install.

---

### Post by bumanie on 2008-10-29
> **macogw said:**
> 1. It's most likely a tarball
2. If it's a driver .rpm, that is a very very bad idea.  The driver would be compiled for a different kernel version and is thus 99% guaranteed not to work, and probably not even to install.

Totally agree, in fact I would not use alien unless there was a 'must have application' that doesn't have a .deb equivalent. Alien can break your system. One should be able to find a .deb for nearly any need.

---

### Post by distinct on 2008-10-29
> **macogw said:**
> What do you mean when you say they contribute to the loudspeaker and the jacks?  Your issue is that you have no sound from your headphone jacks, right?  And your microphone jack is...untested?

The computers inbuilt speaker in this computer does sound as well as the normal simple beeps that its used for in most computers (loudspeaker) and when i was doing the test sounds on the computer in preferences -> sounds, sound was coming out of both the in-built speaker and the earphones that i was testing on it. As yes, the microphone is yet to be tested, as i don't quite know how i am going to do that yet (don't worry about that part for the moment.
My issue seems to be more concerning how to get sound working out of just the headphone jacks at the front and back of the desktop without it coming out of the computer itself.
Any ideas?

Edit: I just tested music in Amarok, at that stage it only outputted it through the computer's inbuilt speaker, any idea how to switch it between that and the headphone jacks?

---

### Post by macogw on 2008-10-29
So the speakers aren't muted when you plug in the headphones...yeah, kernel bug. Can you run [http://alsa-project.org/alsa-info.sh](http://alsa-project.org/alsa-info.sh) and give me the link it gives you?

Um, what do you mean about Amarok?  Are you using a GNOME system but then using Amarok inside it?  Or are you using Kubuntu?  That makes a difference to how I answer this.

---

### Post by distinct on 2008-10-29
Ok, going to be th noobiest thing ever right here: I am running ubuntu, not kubuntu and if i click system, one of the options is "about gnome" so i gather im running gnome platform.
And whether the speakers are muted, i right clicked on the sound icon at the top while i was writing this, so sound seems to work out of the earphones themselves and not the computer now after i turned on "detect headphone jack" and muted "PCM" volume.

The link too seems to keep lagging out everytime i try and load it :/
I instially opened it on my other computer (xp) and it loaded just the text document style. Though a couple minutes later the link wouldn't work on either this computer nor the other :<

EDIT: got the url to load, no idea what to do though, it came up as a text file just like on the computer running xp, i tried to run it through terminal, though that had no effect either (see clearly no idea ;D)

---

### Post by macogw on 2008-10-29
Sorry, just save it to your desktop, and open a terminal, then copy this in, one line at a time, hitting enter in between
```

cd Desktop
chmod +x alsa-info.sh
./alsa-info.sh
```
That'll gather all the sound info I need about your hardware.

And let's summarize the exact issue:
- Using GNOME
- KDE apps (ex: Amarok) have no sound at all
- Using 8.04, I assume?
- After you enabled headphone jack sensing, speakers are muted when headphones are in use

Until we figure out Amarok's issue, if you want something with a similar interface that should work for now, try Exaile...it's a GNOME app modeled after Amarok.

So, anything else?  Do you have more than one headphone jack?  If so, do they all work, or only some?

---

### Post by macogw on 2008-10-29
Sorry, just save it to your desktop, and open a terminal, then copy this in, one line at a time, hitting enter in between
```

cd Desktop
chmod +x alsa-info.sh
./alsa-info.sh
```
That'll gather all the sound info I need about your hardware.

And let's summarize the exact issue:
- Using GNOME
- KDE apps (ex: Amarok) have no sound at all
- Using 8.04, I assume?
- After you enabled headphone jack sensing, speakers are muted when headphones are in use

Until we figure out Amarok's issue, if you want something with a similar interface that should work for now, try Exaile...it's a GNOME app modeled after Amarok.

So, anything else?  Do you have more than one headphone jack?  If so, do they all work, or only some?

---

### Post by distinct on 2008-10-29
Dunno why but cd cmd didn't work stright off with going from my thing to desktop...i got it worked out though =]

[http://www.alsa-project.org/db/?f=9d0ed8e440ac709ef913d257000ebe47eb1810bb](http://www.alsa-project.org/db/?f=9d0ed8e440ac709ef913d257000ebe47eb1810bb)
^link about infoz

THOUGH i put an mp3 song on the computer last night when i posted here and downloded the pack o support mp3 and it now seems after a computer reboot that its working in amarok, and it only comes out of the earphones =D good as. Do you have any idea how to boot the sound volume though? because it seems quite low at the moment when both the volume in the system tray above in and the application are at full.

---

### Post by macogw on 2008-10-29
Right click the volume thing and go to Open Volume Control, then go Edit -> Preferences.  Maybe try enabling some of the other sliders and see if they make a difference?  If not, please test with an Intrepid live cd (will be released tomorrow) and see if the sound's too quiet there as well.  If it works right, you can upgrade from Hardy to Intrepid by running ```
gksu "update-manager -c"
``` in a terminal.  If it doesn't, please file a bug at [http://bugs.launchpad.net/ubuntu/+source/linux/+filebug](http://bugs.launchpad.net/ubuntu/+source/linux/+filebug)

---

### Post by distinct on 2008-10-30
Ok, got it working all good, once again its my simple stupidity no bug...PCM i thought was the computers in-built speaker, but obviously not:-|
turns out that when i enable the headphone jack detection, it mutes the PC's built-in speaker entirely, so once increasing PCM (PC master?) volume, blew my ears almost...all good now thanks for the help.

Just need to sort out Display drivers so i can use opengl games and fix one other thing then might start using it as default OS instead of windows which is guaranteed to screw up in the first month of installing :/

One more question i do have concerning driver though, on windows you have the 3 standard drivers usually: Chipset, Display and Sound.
While Sound seems to be working straight off in this case thus no driver required, would i need the chipset ones at all? Or does Linux compensate for that straight away?

---

### Post by macogw on 2008-10-30
Pretty much all drivers are included by default in the kernel.  They're built-in.  The ones that aren't generally fall into 3 categories:
- Closed-source (ex: Nvidia or ATI 3D graphics)
- In need of testing before submission to the kernel
- Ones that haven't been written yet

---

### Post by distinct on 2008-10-30
ok cheers, thanks for the help, find how it is possible to get drivers for a good, old, rare card :/

---

### Post by macogw on 2008-10-30
Nvidia.... if it's really old, it's possible it only has 2D drivers available.  If it's slightly newer than "really old" maybe the nvidia-legacy driver?  The System -> Admin -> Hardware Drivers thing might help.

---

### Post by distinct on 2008-10-30
Yea tried there, started new thread about it:
[http://ubuntuforums.org/showthread.php?p=6061765](http://ubuntuforums.org/showthread.php?p=6061765)

If you can be bothered or know anything further =P

---

