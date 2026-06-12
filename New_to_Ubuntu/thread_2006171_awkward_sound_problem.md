---
title: "awkward sound problem"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Feraios on 2012-06-18
I have installed lubuntu 11.10
I search in google but I couldn't find a appropriate solution!
I use lubuntu so many months with no problem when suddenly after a reboot I had a problem with the sound!

[COLOR="Red"]The problem is that i can't use my sound card,which I had so many months,but the sound come through the motherboard![/COLOR]
In sound preferences I see my sound card but i can't use it!

---

### Post by dyous87 on 2012-06-18
There is a chance your sound car is busted. Do you have a dual boot you can try it with? Also try booting into a 12.04 live cd to see if the problem can be replicated.

---

### Post by Feraios on 2012-06-18
On windows everything works great with the card..
Sometimes after some reboots lubuntu fix the problem.

I also did that   [http://ubuntuforums.org/showpost.php?p=11384964&postcount=16]("http://ubuntuforums.org/showpost.php?p=11384964&postcount=16")    but nothing

---

### Post by dyous87 on 2012-06-18
Do you notice that this problem occurs after any particular action or application. Sometimes on certain systems sound can stop working after running Rhythmbox or watching a flash video. This happens if the application using sound crashes however sorta looks the sounds device. 

Can anyone here verify this. I've noticed this on my system before with past versions however I don't believe it happens any longer since upgrading to 11.10 and now 12.04.

---

### Post by anewguy on 2012-06-18
Perhaps we should start with the basics:  finding out what you have.  In this instance, I think we only need to look at the audio, but please post the output of the following in code tags (use the # on the message menu and paste your text between the 2 tags):

lspci 

This will help us to know what you have, allow us to identify the manufacturer/model/chipset.

Thanks
Dave ;)

---

### Post by Feraios on 2012-06-19
dyous87 it is a general problem.
anewguy you mean something like this?

00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by anewguy on 2012-06-22
I'm sorry I didn't get back to you.  I've been having some problems on the forum and just plain forgot about this post.  I'll do a net search with:

ubuntu 12.04 Creative Labs CA0106 Soundblaster

and see what comes up.  If I find something, I'll post back here later.

---

### Post by anewguy on 2012-06-22
OK, there are many posts out there for this problem.  Although some refer to a prior release, it might still be worthwhile trying their solutions. If there are version numbers in some of the posts we may have to deal with that.  Here's small list to look at:

[http://ubuntuforums.org/showthread.php?t=1491560]("http://ubuntuforums.org/showthread.php?t=1491560") - a combination of removing/installing some software and also changing a setting in the mixer.

[http://ubuntuforums.org/showthread.php?t=963027]("http://ubuntuforums.org/showthread.php?t=963027") - an old post, but what is discussed there isn't release dependant.

[http://askubuntu.com/questions/29457/sound-driver-for-motherboard-gigabyte-ga-g1975x-c-creative-sound-blaster-live-2]("http://askubuntu.com/questions/29457/sound-driver-for-motherboard-gigabyte-ga-g1975x-c-creative-sound-blaster-live-2") - talks about your adapter and some more system settings to try

Rather than continue, I would suggest you read through these and try some out.  There are also many mention of a driver "snd-ca0106" - I don't know if that's included in the current release or not, or if it's loaded (an lsmod should show if it's there or not).

---

### Post by Feraios on 2012-06-24
thanks for your time!
I hope I will find a solution!

---

### Post by jmfal on 2012-06-24
try this in a terminal:
```
 lspci -v   
```

This will list your hardware and the kernal(driver) that is being used.

Post the results , using the code tag "#" by pasting  between the code brackets, it makes it easier to read
Thanks

---

### Post by Feraios on 2012-06-24
Sry but i didnt understand...
```

#
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64
	Memory at <ignored> (64-bit, non-prefetchable)
	Kernel modules: ati-agp

00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	I/O behind bridge: 0000e000-0000efff
	Memory behind bridge: fde00000-fdefffff
	Prefetchable memory behind bridge: 00000000d0000000-00000000dfffffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80) (prog-if 8f [Master SecP SecO PriP PriO])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 22
	I/O ports at ff00 [size=8]
	I/O ports at fe00 [size=4]
	I/O ports at fd00 [size=8]
	I/O ports at fc00 [size=4]
	I/O ports at fb00 [size=16]
	Memory at fdfff000 (32-bit, non-prefetchable) [size=512]
	[virtual] Expansion ROM at 40000000 [disabled] [size=512K]
	Capabilities: <access denied>
	Kernel driver in use: sata_sil
	Kernel modules: sata_sil

00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffe000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80) (prog-if 10 [OHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffd000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ohci_hcd

00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80) (prog-if 20 [EHCI])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
	Memory at fdffc000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: 66MHz, medium devsel
	I/O ports at 0500 [size=16]
	Memory at fdffb000 (32-bit, non-prefetchable) [size=1K]
	Kernel driver in use: piix4_smbus
	Kernel modules: i2c-piix4

00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80) (prog-if 82 [Master PriP])
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at f900 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: pata_atiixp
	Kernel modules: pata_atiixp

00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at fdff4000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
	Subsystem: Micro-Star International Co., Ltd. Device 7254
	Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80) (prog-if 01 [Subtractive decode])
	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=64
	I/O behind bridge: 0000d000-0000dfff
	Memory behind bridge: fdd00000-fddfffff
	Prefetchable memory behind bridge: fdc00000-fdcfffff

01:00.0 VGA compatible controller: ATI Technologies Inc RV710 [Radeon HD 4550] (prog-if 00 [VGA controller])
	Subsystem: Giga-byte Technology Device 21ae
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	Memory at fdee0000 (64-bit, non-prefetchable) [size=64K]
	I/O ports at ee00 [size=256]
	[virtual] Expansion ROM at fde00000 [disabled] [size=128K]
	Capabilities: <access denied>
	Kernel driver in use: radeon
	Kernel modules: radeon

01:00.1 Audio device: ATI Technologies Inc RV710/730
	Subsystem: Giga-byte Technology Device aa38
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at fdefc000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

02:00.0 Multimedia audio controller: Creative Labs CA0106 Soundblaster
	Subsystem: Creative Labs SB0790 X-Fi XA
	Flags: bus master, medium devsel, latency 64, IRQ 20
	I/O ports at df00 [size=32]
	Capabilities: <access denied>
	Kernel driver in use: CA0106
	Kernel modules: snd-ca0106

02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
	Subsystem: Micro-Star International Co., Ltd. Device 254c
	Flags: bus master, medium devsel, latency 64, IRQ 23
	I/O ports at dc00 [size=256]
	Memory at fddff000 (32-bit, non-prefetchable) [size=256]
	Capabilities: <access denied>
	Kernel driver in use: 8139too
	Kernel modules: 8139too, 8139cp
#
```

---

### Post by jmfal on 2012-06-24
OK, I see three listed but you only have two  1.onboard  and 2.sound blaster

open a terminal and enter:
```
 alsamixer    
```

Press enter,  which card is in use (Card:) top left.

If you where using the sound blaster when you lost sound and it is not there now press F6 and use the arrows on your keyboard (up/down) to select SB hit enter then esc.

if your volumes are muted you will see  MM  between the volume and the vertical bar, if it's muted  use the left/right arrows to move to that vol. cont. press "m" or "M" to unmute it then use the up arrow to increase the volume.
Try to play some music.

The code tag>>>>>> in the reply box are options to change font size , bold , italics, etc...
you will see "#" that is the code tag and when you click on it you will get this:
[CODE][CODE]  you can copy the terminal output and then paste it between the code brackets.
I put the cursor where I want the code then click on the "#" tag then put the cursor between the brackets to spread them apart, then do your copy/paste.

---

### Post by Feraios on 2012-06-24
I choose SB and only s/pdif is MM, but the default sound card didn't change..
the sound still comes from the onboard...

---

### Post by jmfal on 2012-06-24
OK,  this is a longshot
C lick on the speaker icon (top right) >>settings> select  sb card > play some music>> if there are two, one for analog, and one for digital>> try both

No sound try this link:
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

At step 10  you will need to install gnome-system-tools using synaptic or a terminal:
```
  sudo apt-get install gnome-system-tools       
```
If it won't ins tall replace the hyphens with a space
This will install a GUI "Users and Groups" so you can take ownership of those apps.
Open 'Users and Groups" > click "manage groups">  click on one of those apps > properties > put a check mark in box by your name >click OK > do the next and so on
If any problems post  and somebody will try to help.

---

### Post by Feraios on 2012-06-24
*I use lubuntu*

---

### Post by jmfal on 2012-06-24
I'm sorry, I forgot,  hope I didn't waste your time.

I'm checking on the lubuntu users, but I have to leave be back in a while.

---

### Post by Feraios on 2012-06-24
you didn't waste my time! ty!
lubuntu is similar with ubuntu but they don't have a sound manager

---

### Post by jmfal on 2012-06-24
Try this:
```
 sudo modprobe snd-ca0106        
```
This should load that module(driver) till you log out or restart

And play some music,  if there is an error post it
If you have sound then run this command and restart, post back either way

```
 sudo nano /etc/modules ca0106    
```

This should load the module(driver) at boot >

---

### Post by Feraios on 2012-06-25
> **jmfal said:**
> Try this:
```
 sudo modprobe snd-ca0106        
```
This should load that module(driver) till you log out or restart

And play some music,  if there is an error post it
If you have sound then run this command and restart, post back either way

```
 sudo nano /etc/modules ca0106    
```

This should load the module(driver) at boot >

After the first code and a restart  sound still from the onboard.
The second code retutn this:
```
 /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp


```

---

### Post by Feraios on 2012-06-25
[http://www.jordswart.org/archives/63]("http://www.jordswart.org/archives/63")
sould I try this? how should I write correctly the code?

can i do something from lubuntu system tools--> "system profiler and benchmark" ??

---

### Post by Hadaka on 2012-06-25
Hi.  re-enter the line jmfal gave you.

sudo modprobe snd-ca0106


except this time dont restart or boot, try to play something
and see which card is used.
If it works, report back please.
thanks

---

### Post by Feraios on 2012-06-25
still the onboard...

is there a program to download?

---

### Post by Hadaka on 2012-06-25
I found this post that may be of help to you.
[http://ubuntuforums.org/showthread.php?t=1816583](http://ubuntuforums.org/showthread.php?t=1816583)

if you need help or have questions,please
let me know and i will walk you through it.
thanks

---

### Post by Hadaka on 2012-06-25
Have you tried pressing f6 in alsamixer and changing the default soundcard?

---

### Post by Feraios on 2012-06-25
alsamixer didnt change the default soundcard...i tried

---

### Post by Hadaka on 2012-06-25
OK..try reading through this thread and see if updating your alsamixer
will help. I can see by your lspci post that the card is loaded..so it should
work,
[http://ubuntuforums.org/showthread.php?t=1567445&page=2](http://ubuntuforums.org/showthread.php?t=1567445&page=2)

---

### Post by Feraios on 2012-06-27
I upgrade to 12.04 and the problem solved.
Thank Everybody for Everything !!

---

### Post by jmfal on 2012-06-27
OK Ferios.
Now that you have the soundcard changed in the alsamixer press F5  and make sure all volume controls are turnedup.
Use the right arrow and go all the way to right sometimes there are more volume controls that are not on the screen until you navigate farther right, look for PCM control, turn it up.
Play some music.
No sound >>click on speaker icon>>click settings >>are two sound cards in the output tab,
one for analog and one for digital?? 

Click on the analog card and play some music,

---

