---
title: "Speakers will not work"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by JSF16 on 2012-10-28
My speakers do not work, neither do headphones. The little opening sound plays when I power up Ubuntu, but nothing else. I have included a screenshot of my soundboard/control panel thing brought up with terminal. 

I have googled this issue repeatedly, and the answers either are beyond my lack of linux know-ho or have not worked.

---

### Post by sandyd on 2012-10-28
looks like this thing [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/839297](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/839297)

---

### Post by Bucky Ball on 2012-10-28
This much is obvious; the headphones aren't turned up so no sound out of there. I used to use gnome-alsamixer which is a little friendlier, but no idea if that works in Unity. You may also want to try fiddling with PulseAudio Volume Control. Not sure if that is a default app in Ubuntu 12.04 or not. Would be in multimedia if so. If not, install from Software Centre (pavucontrol) .

---

### Post by alkh3myst on 2012-10-28
Hi, JSF16. This problem is actually pretty common in Ubuntu when people do a new installation, or upgrade to a new version. What you can do is to open Pulse Audio's controls (package name = "pavucontrol" if it's not installed, install it from the terminal or Synaptic). A GUI will open, and you need to select whichever device you want audio to come out of, and try toggling the controls until you get sound. The mute/unmute, and select (the green checkbox) are the ones you need to fool with.

Hopefully Alsamixer isn't one of your problems, it's awkward to work with. You need to open it from the terminal, use the function keys (F6) to select your audio device, then use the arrow keys to choose playback/record, etc. Also you select to mute/unmute with the "M" key on your keyboard. I just included this as a "what if", Pusle Audio should handle your device selection. 

Beyond that, if you still can't get sound, you may need to add the latest audio plugins etc, from the Ubuntu Audio Dev team, by adding a "PPA" to your software sources either in the terminal or Synaptic. It's on Launchpad, which is a semi-official repository. Here's a helpful link: [https://wiki.ubuntu.com/Audio](https://wiki.ubuntu.com/Audio)

Beyond that, there are some more advanced troubleshooting guides, and they may be beyond your comfort level for now. Good luck. 


:popcorn:

---

### Post by JSF16 on 2012-10-28
That bug report page confused me, I have no idea what to do on it. And I downloaded the recommended audio manager with zero success. 

How do I download the latest audio pluggin? The link failed to assist me, sorry.

---

### Post by Bucky Ball on 2012-10-29
Open PulseAudio Volume Control; 
Open VLC or whatever you want to get audio out of;
In the Playback tab of PAVControl you should see a level meter for the application you have just started playing sound on;
Tweak the devices until you get sound out of a combination;
You can also check in the Output tab and see if you can tweak something in there.

It can sometimes be tricky and hard to get the combination right. If your level meter for your audio player in PAVControl is showing a level but you're not hearing anything, you shouldn't be far away. Change the default device and make sure nothing is muted.

---

### Post by newb85 on 2012-10-29
PAV isn't a default app in 12.04, but is in the Software Center.  However, application volume control is also handled in the Applications tab of Sound Settings (Just "Sound" from the Dash).  PAV may give you more advanced options, though.  I don't know that.

---

### Post by JSF16 on 2012-10-29
Well I'm still having trouble, although the instructions were a bit confusing. Sorry. But a picture says a thousand words, so here. This is how I am in PAV. Not muted, I've turned the volume up, but no sound.

---

### Post by JSF16 on 2012-10-30
Bumped due to the heavy activity in this forum.

---

### Post by NikTh on 2012-10-30
Hi , 

open a terminal and apply these commands 

```
wget -O alsa-info.sh http://www.alsa-project.org/alsa-info.sh && chmod +x ./alsa-info.sh && ./alsa-info.sh
bash alsa-info.sh --upload
```

and then give the link here. 

Thanks

---

### Post by JSF16 on 2012-10-30
This is the only link I got out of it, [www.alsa-project.org?](www.alsa-project.org?)

Is this supposed to happen?

---

### Post by NikTh on 2012-10-30
After the command 
```
bash alsa-info.sh --upload
``` it has to give you this answer 

```
Your ALSA information is located at : <and here the link>
```

---

### Post by Bucky Ball on 2012-10-30
> **JSF16 said:**
> Bumped due to the heavy activity in this forum.

Please wait twenty four hours before bumping.

---

### Post by JSF16 on 2012-10-30
Right-o. 

And the URL I got is  [http://www.alsa-project.org/db/?f=ffb45ce24880776fbd20e6d5a21df292cda813ac](http://www.alsa-project.org/db/?f=ffb45ce24880776fbd20e6d5a21df292cda813ac)

---

### Post by NikTh on 2012-10-30
What weird messages I see . 

[quote="alsa-info"]```

!!ALSA Version !!------------  [B]
Driver version:     1.0.24[/B] 
Library version:    1.0.25 
Utilities version:  1.0.25
```[/quote]
[s]The current alsa driver version in **Ubuntu 12.04.1** is **1.0.25**[/s]. Have you updated your system lately ? 

[quote="alsa-info"]```
!!Aplay/Arecord output
!!--------------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 2: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```[/quote]
Here listed 2 devices , 1 analog and 1 digital. But bellow it seems like one device in ON (work).

[quote="alsa-info"]```
!!HDA-Intel Codec information
!!---------------------------
--startcollapse--

Codec: Realtek ALC1200
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x10ec0888
Subsystem Id: 0x10250121
Revision Id: 0x100101
No Modem Function Group found
Default PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=2, o=0, i=0, unsolicited=1, wake=0
  IO[0]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
  IO[1]: enable=0, dir=0, wake=0, sticky=0, data=0, unsol=0
Node 0x02 [Audio Output] wcaps 0x11: Stereo
  Device: name="ALC1200 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x03 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x04 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x05 [Audio Output] wcaps 0x11: Stereo
  Converter: stream=0, channel=0
  PCM:
    rates [0x560]: 44100 48000 96000 192000
    bits [0xe]: 16 20 24
    formats [0x1]: PCM
Node 0x06 [Audio Output] wcaps 0x211: Stereo Digital
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="IEC958 Default PCM Playback Switch", index=0, device=0
  Device: name="ALC1200 Digital", type="SPDIF", device=1
  Converter: stream=8, channel=0
  Digital:
  Digital category: 0x0
```[/quote] 

and the most weird messages are in dmesg 
[quote="alsa-info"]```
[ 9850.236179] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[ 9850.256056] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 123.280 msecs
[ 9850.536214] PM: suspend of drv:sd dev:0:0:0:0 complete after 487.340 msecs
--
[ 9853.232684] ehci_hcd 0000:00:1a.7: PME# disabled
[ 9853.232726] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[ 9853.232734] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[ 9853.232771] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
--
[ 9853.235575] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[ 9853.235617] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[ 9853.235627] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[ 9853.235672] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[ 9853.235685] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[ 9853.235682] uhci_hcd 0000:00:1d.0: setting latency timer to 64
--
[14934.284063] ehci_hcd 0000:00:1a.7: PCI INT C disabled
[14934.352172] snd_hda_intel 0000:00:1b.0: PCI INT A disabled
[14934.368055] PM: suspend of drv:snd_hda_intel dev:0000:00:1b.0 complete after 119.672 msecs
[14934.427485] [drm] nouveau 0000:01:00.0: Idling channels...
--
[14937.468681] ehci_hcd 0000:00:1a.7: PME# disabled
[14937.468724] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x3 (was 0x0, writing 0x10)
[14937.468732] snd_hda_intel 0000:00:1b.0: restoring config space at offset 0x1 (was 0x100006, writing 0x100002)
[14937.468769] pcieport 0000:00:1c.0: restoring config space at offset 0xf (was 0x40100, writing 0x4010a)
--
[14937.471594] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[14937.471636] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[14937.471645] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[14937.471687] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 23 (level, low) -> IRQ 23
[14937.471699] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[14937.471708] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[14937.471735] usb usb5: **root hub lost power or was reset**
```[/quote] 

here it seems like you connect a USB device or your speakers are connected through a usb port that is not working well. 

In any case , wait for a most experienced user to translate the alsa-info messages more accurate.

---

### Post by JSF16 on 2012-10-30
I've tried updating, but due to prior update manager problems, I had to disable getting updates from 'pmcenery' because when they were checked, and I tried to update, I said I had connection problems with my internet. I checked the pmcenery options off, and I can update now, but I believe I am missing out on a vast portion of the updates I need.

---

### Post by newb85 on 2012-10-31
> **JSF16 said:**
> I've tried updating, but due to prior update manager problems, I had to disable getting updates from 'pmcenery' because when they were checked, and I tried to update, I said I had connection problems with my internet. I checked the pmcenery options off, and I can update now, but I believe I am missing out on a vast portion of the updates I need.

Doubtful.  That PPA looks like it's just software for syncing iPods and iPhones.  I looked up a handful of the packages there, and most of them have more current versions available in the main repositories, anyways.

---

### Post by JSF16 on 2012-10-31
So how would I get an update for my audio then?

---

### Post by newb85 on 2012-10-31
Alsa drivers are in the main repository.  Updates should come from there.

---

### Post by JSF16 on 2012-10-31
Forgive my ignorance, but where do I find the main repository?

---

### Post by HiImTye on 2012-11-01
> Forgive my ignorance, but where do I find the main repository?
```
sudo apt-get update; sudo apt-get upgrade
```

---

### Post by newb85 on 2012-11-01
The main repository should be enabled by default.  (I can't think of a reason you would disable it, except for experimentation.)

If you pull up Software Sources (In Software Center, Edit>...), the first repository listed should be the main repository.

---

### Post by JSF16 on 2012-11-01
I entered that code into Terminal, and I believe it updated, but my speakers still do not work. And as far as I can tell, all my repositories are checked (pic included) And my speakers STILL won't work.

---

### Post by newb85 on 2012-11-01
What is the output of 
```
sudo apt-get install alsa-base
```

(This should ensure that your alsa drivers are at the current version for your release.)

---

### Post by JSF16 on 2012-11-01
Reading package lists... Done
Building dependency tree       
Reading state information... Done
alsa-base is already the newest version.
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans language-pack-kde-en linux-headers-3.2.0-29
  language-pack-kde-zh-hans language-pack-kde-en-base kde-l10n-engb
  linux-headers-3.2.0-29-generic-pae kde-l10n-zhcn language-pack-zh-hans-base
  language-pack-kde-zh-hans-base amarok-help-en
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by Bucky Ball on 2012-11-01
```
Use 'apt-get autoremove' to remove them.
```Run:

```
sudo apt-get autoremove
```... to get rid of the unused stuff.

The command given previously to update/upgrade, which you ran, did not, of course, answer your question: Where is main repository? That is on a server somewhere and you access it locally. The command updated and upgraded your system from the main, and other, repositories. As mentioned, it should be enabled by default and not a concern in this. Everything is coming down the line from there just fine ...

---

### Post by JSF16 on 2012-11-01
Okay, I ran the command. And please pardon my Linux in-adeptness, but what do I do now?

---

### Post by Bucky Ball on 2012-11-01
This is probably what is most relevant about that output:

```
alsa-base is already the newest version.
```

---

### Post by JSF16 on 2012-11-02
Well my speakers are still not operating and I am still at a loss as to what to do.

---

### Post by JSF16 on 2012-11-03
Bumped after one day of inactivity.

---

### Post by Bucky Ball on 2012-11-03
Seems nobody has any clues. I can't work out why you're seeing nothing in Pulse Volume Control, though. 

You get a sound app playing something, open PVControl, go to playback and see nothing? Do you even see that the app is open and playing an audio stream? Nothing on the level meter? Anything on the meter in the output tab? Nothing muted?

May seem like some dumb questions but one never knows ...

---

### Post by NikTh on 2012-11-03
OK , 

because I want to clarify things and I don't want to confuse things, after I searched this I saw that **I was wrong**. 

> **NikTh said:**
> 
The current alsa driver version in **Ubuntu 12.04.1** is **1.0.25**. Have you updated your system lately ?

The current **alsa driver version for 12.04.1 [SIZE="3"]is[/SIZE] 1.0.24** and not 1.0.25. 

You can see the alsa's driver version in terminal, with this command ```
cat /proc/asound/version
```. 

The confusion to me came due to multiple kernels I have (for testing proposes) and the time I told you for the 1.0.25 I had booted my system with the newer 3.6.3 mainline kernel. So , sorry for that , we have to focus elsewhere. 

Are your speakers with USB connection ? If yes, have you tried to connect them to another usb port ? 
Also run this command and see if helps 
```
sudo alsa force-reload
```

Thanks

---

### Post by Swagman on 2012-11-03
This might sound obvious but in one of your first pictures you have spdif selected. Are you really outputting to that device/port ? 

Not many people do !!

---

### Post by JSF16 on 2012-11-03
Spdif is the only option available to me, so it's selected.

I have 1.0.24

No, I'm on my laptop, so my speakers are built in and not functioning. They still play that opening sound when you power up Ubuntu, but no sound otherwise. Even though, when I am in pulse and I do an activity that would create sound, the meter rises. I mean, it indicates sound is playing. But nothing comes out over the speakers. I also used that command, and nothing happened. I am posting a photo of the results of using said command.

---

### Post by JSF16 on 2012-11-03
Well, this is embarrassing. 

Changed my output in sound setting. It, worked. Yeah.

Thanks, and sorry for wasting your time.

---

### Post by Swagman on 2012-11-06
lol ..Been there..done that..

Felt a muppet too.

Hey, if only everything was that simple to fix.

:-)

Rock on

---

