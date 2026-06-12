---
title: "Cant find diagnosis/solution to no sound"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by moltar3000 on 2008-09-07
Hello,

I'm running Hardy on an Asus F80s laptop.  I've had no sound for a while now and I still haven't been able to fix it despite my attempts at following many of the guides here at ubuntuforums and elsewhere.

My soundcard is a Realtek ALC662, SIS966, hda-intel

Everything is unmuted in the alsamixer.  I've reinstalled and updated ALSA.  I've added a whole bunch of extra hda-intel oriented lines to various modprobes.

One thing I have noticed is when I run dmesg, one of the lines reads[B]
[   27.952330] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...
[/B]
I have a feeling this might have something to do with it.  Otherwise, I am totally baffled!
Any help diagnosing/solving this problem is greatly appreciated.

---

### Post by Xiong Chiamiov on 2008-09-07
Did you try [this guide]("http://ubuntuforums.org/showthread.php?t=205449") specifically?  If so, it would be helpful to tell what specific errors you got at certain points in the process (or if you didn't get any).

---

### Post by moltar3000 on 2008-09-07
OK, I have seen this thread before.  Basically, I get a failure at

sudo modprobe snd-hda-intel

The terminal gives no response whatsoever to the command.

So, I move onto **Getting the ALSA drivers from a *fresh* kernel**
Completed all the steps.  Still no sound.

So I go onto the **ALSA driver Compilation** section.

I downloaded, extracted, compiled and installed the latest drivers, utils and lib from alsa-project.org
Still no sound.
The ones I have downloaded and installed are:
alsa-driver-1.0.17
alsa-lib-1.0.17a
alsa-utils-1.0.17

I followed the instructions in **Using alsasource** as well
Using the module assistant (blue screen thing), it installed the drivers successfully.  No error messages.

However for some reason this process seems to have uninstalled my wireless card... That was a nice surprise.  Having now moved back to a wired connection, I proceed....

So, following instructions, I go back to type in

sudo modprobe snd-hda-intel

Still no response.  And NO SOUND..........  ](*,)


Some more information about my system (if necessary)

Audio devices detected through
lspci -v
are

00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
Subsystem: ASUSTeK Computer Inc. Unknown device 19c3
Flags: bus master, medium devsel, latency 0, IRQ 18
Memory at fddf4000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

and

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
Subsystem: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
Flags: bus master, fast devsel, latency 0, IRQ 16
Memory at fdeec000 (32-bit, non-prefetchable) [size=16K]
Capabilities: <access denied>

---

### Post by moltar3000 on 2008-09-07
Oh and I forgot to mention.  The sound works perfectly fine if I boot to Windows Vista

---

### Post by phidia on 2008-09-07
The Ubuntu [wiki on sound troubleshooting]("https://help.ubuntu.com/community/SoundTroubleshooting") is similar to the link already provided but I'm listing it here in case it offers anything the howto missed.

---

### Post by moltar3000 on 2008-09-08
Thanks, but this didn't offer anything new.
I've also gone through everything at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Still no sound and no response to *sudo modprobe snd-hda-intel*

---

### Post by littlemog on 2008-09-08
Encountering a similar problem on my LG laptop with Hardy... lmk if you find a way around. tks

---

### Post by moltar3000 on 2008-09-08
bump

---

### Post by moltar3000 on 2008-09-08
So I've just tried the advice offered at this thread [http://ubuntuforums.org/showthread.php?t=854472](http://ubuntuforums.org/showthread.php?t=854472)

Under... *sudo gedit /etc/modprobe.d/alsa-base*...I have entered every model provided in my Alsa-configuration.txt file in the directory of my alsa driver.  These were (for ALC662)....

	  3stack-dig.....	3-stack (2-channel) with SPDIF 
	  3stack-6ch.....	 3-stack (6-channel) 
	  3stack-6ch-dig..... 3-stack (6-channel) with SPDIF 
	  6stack-dig.....	 6-stack with SPDIF 
	  lenovo-101e.....	 Lenovo laptop 
	  eeepc-p701.....	ASUS Eeepc P701 
	  eeepc-ep20.....	ASUS Eeepc EP20 
	  m51va......	ASUS M51VA 
	  g71v.....		ASUS G71V 
	  h13.....		ASUS H13 
	  g50v.....	ASUS G50V 
	  auto......		auto-config reading BIOS (default)

I entered each model number using the code....*options snd-hda-intel model=xxx*... where xxx was the model name provided above.  Saved and rebooted after each change.  None of them worked.

I am now wondering, since I have done seemingly everything that solves most people's problems, whether there is an issue with the communication between hardy and the settings in my BIOS.  The *dmesg* line I mentioned in the first post seems to relate to this theory.

[ 27.952330] hda_codec: Unknown model for ALC662, trying auto-probe from BIOS...

...But to be honest, I am a total noob.  So I would never act on my own judgment with issues like this.  As I have said before, everything works fine under Vista, so I would be reluctant to tamper with my BIOS for fear of screwing things up across both platforms.

If anyone thinks they know what to do PLEASE help!

---

### Post by eggdeng on 2008-09-08
@littlemog
> Encountering a similar problem on my LG laptop with Hardy... lmk if you find a way around. tks
Open the config file
```
gksudo gedit /etc/modprobe.d/alsa-base
```
Add the line
```
options snd-hda-intel model=lg
```
and [COLOR="Red"]reboot[/COLOR].
This works for me on my LG P1 Express Dual.

@moltar3000
Hi again. I did a bit of searching to see if anyone had got sound up and running on your model but there is very little info to be had. :( The most likely candidates for the alsa-base options line seem to be auto and 3stack-dig. You did [COLOR="Red"]reboot[/COLOR] after trying those, right?
One other thing which intrigues me was the output you posted for ```
aplay -l
```
There seemed to be two cards: 2 entries for the ALC and then one for a HDA ATI? Is it possible you have two cards installed? If so, it might be an idea to look at trying to get the other one to work.
You can set the default device as follows

Run
```
asoundconf list
```
to see how alsa identifies the available devices. Then run
```
asoundconf set-default-card xyz
```
where xyz is the name of the device you want to use, according to the output of the 1st command.
Again, [COLOR="Red"]reboot[/COLOR] for changes to take effect.

---

### Post by moltar3000 on 2008-09-08
Hey,

Thanks again.  The two devices noted via 
```
aplay -l
```
are my soundcard and my HDMI-out which, I assume, interlinks my soundcard to my graphics card (which I also haven't got to work yet) which is an ATI Mobility Radeon HD3470 256MB.

Could the fact that I don't have sound be caused by my video card?

Running
```
asoundconf list
```
I get[I]
Names of available sound cards:
SIS966
HDMI
[/I]

When I run
```
asoundconf set-default-card xyz
```
It gives me back[I]
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 429, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 354, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack
[/I]

Thanks a lot for the help:)

---

### Post by eggdeng on 2008-09-08
Not sure if you read me right. That should be
```
asoundconf set-default-card SIS966
```
to choose the first device or
```
asoundconf set-default-card HDMI
```
to choose the second.

---

### Post by moltar3000 on 2008-09-08
```
asoundconf set-default-card SIS966
```
Response is:

Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 429, in <module>
    exit_code(set_default_card(sys.argv[2]))
  File "/usr/bin/asoundconf", line 354, in set_default_card
    (j, k) = sep.split(i)
ValueError: need more than 1 value to unpack


I rebooted and now my computer takes a lot longer to boot up.  I tried playing a sound file through Movie Player, and instead of it playing the file like it would before (without any sound output) and getting a visualizion from it, the player doesnt load the file and instead gives me:
[B]An error occurred
Failed to connect stream: Invalid argument[/B]

How do I **undo** what you just told me to do?

---

### Post by eggdeng on 2008-09-09
Try setting the HDMI as default.

---

### Post by moltar3000 on 2008-09-09
I get back the exact same message.

The options it gives me when I enter
```
asoundconf set-default-card
```
and hold down tab are:

.adobe/    ...........                .ICEauthority
.asoundrc    ..............              .local/
.asoundrc.asoundconf ............      .macromedia/
.bash_history .............            madwifi-hal-0.10.5.6/
.bash_logout ...............              .metacity/
.bashrc      ..............              .mozilla/
.cache/      ..............              Music/
.compiz/ ...........                  .nautilus/
.config/  ............                 .openoffice.org2/
.dbus/   ...............                  Pictures/
Desktop/  ..............                 .profile
.dmrc      ..............                Public/
Documents/   ...............              .pulse/
Downloads/   ..............              .pulse-cookie
.esd_auth     ...............             .purple/
.evolution/   ..............             .recently-used
Examples/    ..............              .recently-used.xbel
.fontconfig/  ..............             .ssh/
.gconf/   .................                 .subversion/
.gconfd/  .............                 .sudo_as_admin_successful
.gksu.lock  ..............               Templates/
.gnome2/   ................                .thumbnails/
.gnome2_private/...................           .update-manager-core/
.gnupg/  .................                  .update-notifier/
.gstreamer-0.10/ .................          Videos/
.gtk-bookmarks ..................            .Xauthority
.gvfs/    ..................                 .xsession-errors

I dont see sis966 or hdmi in there.  Which was the one I was using before?

---

### Post by eggdeng on 2008-09-09
You posted above
```
Names of available sound cards:
SIS966
HDMI
```
I can understand you're getting a bit frustrated at this stage but bear in mind a couple of things. As far as I can see, (I would love to be wrong), _no-one_ has yet managed to get sound working in Linux on this particular model. All you can do is experiment with things that have worked on similar configurations and hope to get lucky.
The ```
asoundconf set-default-card
``` command is the command provided by the writers of the alsa driver to select the default sound device. It's perfectly in order as long as you use it properly ie to choose a card recognised by ```
asoundconf list
```
With any sort of tinkering, there is always a risk of doing damage to your installation. Those are the breaks. If that happens, the worst case scenario is back up and re-install from scratch. 8)

---

### Post by moltar3000 on 2008-09-09
> **eggdeng said:**
> 
I can understand you're getting a bit frustrated at this stage but bear in mind a couple of things. As far as I can see, (I would love to be wrong), _no-one_ has yet managed to get sound working in Linux on this particular model. All you can do is experiment with things that have worked on similar configurations and hope to get lucky.


Well I appreciate all the effort and help. Hey, at least we tried.  I'll keep poking about in my spare time and I'll give intrepid a try when it comes out, but having gone through all of this, my expectations of linux are now much lower.

It is frustrating that a distro that aims and has a reputation of being the most user friendly and 'ready to go' can't even manage something as basic as sound.  And it's not as if I am using obscure hardware.  I will reluctantly return to vista until a solution can be found.

---

### Post by nnl on 2008-10-20
I've tried all the guides and installing Realtek drivers on Asus F6V notebook and got no result. 

Did a fresh install of Ubuntu Intrepid 8.10 Beta and did:
sudo gedit /etc/modprobe.d/alsa-base

and added in the bottom of the file: 
options snd-hda-intel model=3stack-dig

rebooted and it worked!

---

### Post by SESF0908 on 2008-11-01
> **nnl said:**
> I've tried all the guides and installing Realtek drivers on Asus F6V notebook and got no result. 

Did a fresh install of Ubuntu Intrepid 8.10 Beta and did:
sudo gedit /etc/modprobe.d/alsa-base

and added in the bottom of the file: 
options snd-hda-intel model=3stack-dig

rebooted and it worked!

That works for me, thank's alot, i'm looking for this seen i bought this laptop. Thank Gods.

---

### Post by Tomash on 2008-11-22
Hello!
I found the thread on these forums regarding problems with Ubuntu on the same laptop as mine (Asus F80S - great machine, but still some linux issues).

Did you manage to solve problem with no sound on this laptop?

---

### Post by lopoetve on 2008-11-22
Dot as I'm having the same issue on an Asus N80

---

### Post by lopoetve on 2008-11-22
> **nnl said:**
> I've tried all the guides and installing Realtek drivers on Asus F6V notebook and got no result. 

Did a fresh install of Ubuntu Intrepid 8.10 Beta and did:
sudo gedit /etc/modprobe.d/alsa-base

and added in the bottom of the file: 
options snd-hda-intel model=3stack-dig

rebooted and it worked!

after a reinstall this did it for me!

---

### Post by Tomash on 2008-11-23
Lopetve, which laptop / model?
The issue seems to be related to HDMI and/or ATI 3470 display adapter.

---

### Post by danielfortin86 on 2008-11-26
I'm also having problems on an Asus N80. I added the 3stack-dig to the alsa-base file and i now get sound out of the laptop's speakers. However, when I plug in actual speakers or headphones into the line-out jack i get nothing. This works fine in Vista so the line-out is working.
Any ideas?

Thanks

---

### Post by Tomash on 2008-11-29
Sounds promising, Daniel. Could you give us full lspci?

I begin to have a suspicion that one of the sources of our problem with asus F80S is ATI graphic adapter, having also some sound device (for HDMI or something like that) and thus "covering" the SIS sound adapter. Anyway there are no reports in the system about any failure to use sound device, it's just that I can't hear it anywhere.

---

### Post by Tomash on 2008-11-29
Sounds promising, Daniel. Could you give us full lspci?

I begin to have a suspicion that one of the sources of our problem with asus F80S is ATI graphic adapter, having also some sound device (for HDMI or something like that) and thus "covering" the SIS sound adapter. Anyway there are no reports in the system about any failure to use sound device, it's just that I can't hear it anywhere.

---

### Post by danielfortin86 on 2008-11-30
The video card in the Asus N80 should be an Nvidia 9650M GT. So I'm not sure why the other user shows an ATI card. Anyway, here's my lspci:

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)                                                                   
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)                                                                
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)                                                                  
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)                                                                  
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 064c (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR928X Wireless NetworkAdapter (PCI-Express) (rev 01)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
07:03.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:03.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:03.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:03.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:03.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Tomash on 2008-12-13
> **lopoetve said:**
> after a reinstall this did it for me!

Worked for me too, even without reinstalling. Asus F80S here (HDA SIS 966). Remember to comment-out the line that's been here previously and put all relevant sliders in alsamixer to the  maximum:
```
tomek@tomek-asus-f80s:~$ tail /etc/modprobe.d/alsa-base
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2

#solution from http://ubuntuforums.org/archive/index.php/t-913240.html
#options snd-hda-intel model=3stack-dig

#solution from http://vip.asus.com/forum/view.aspx?board_id=3&model=X50N&id=20080921231843718&page=1&SLanguage=en-us
#options snd-hda-intel model=lenovo
options snd-hda-intel model=3stack-dig

```

I'm off playing my mp3 collection on F80S, cya :)

---

