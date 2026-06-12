---
title: "Scrambled Audio"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Vock on 2008-06-03
Hello all,

I'm having trouble getting any audio beyond my PC speaker in Ubuntu. I'm using the Sound Blaster Audgiy SE card in my computer. 

I followed reassuringlyoffensive's guide "Comprehensive Multimedia & Video How-to" to install the codecs and Gnome's MPlayer, and from what I can tell i have decoders.

When i play back an mp3, it honestly sounds as if i'm listening to a really bad radio station, and when there is no music playing I get a constant hum in the background.

Any ideas on what the problem(s) are or where to start? I know it's not hardware as the soundcard works under XP.

Thanks

---

### Post by ZabiGG on 2008-06-04
Did you install the Alsa Mixer?

---

### Post by Vock on 2008-06-04
Just installed it, still no audio, the levels are all up as well. :(

I also get this error in Alsa Mixer:

Bad key or directory name: "/apps/gnome-alsamixer/slider_display_names/SigmaTel_STAC9721,23-Master": `,' is an invalid character in key/directory names

---

### Post by iaculallad on 2008-06-04
Navigate to System->Preferences->Sound, and on the "Device" tab, try changing "AutoDetect" to "ALSA - Advanced Linux Sound Architecture". (Sound Events, Music and Movies, and Audio Conferencing) Click on close button and retry playing your mp3.

---

### Post by Vock on 2008-06-04
With that done, it plays the mp3 but it sounds like it's a radio station between frequencies... just a ton of static and barely make it out in the background... for both .ogg and .mp3 files

---

### Post by iaculallad on 2008-06-05
Had you tried to remove and reinstall the ALSA package?


-Remove

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```


-Reinstall

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

and do a Reboot and check your sound.

---

### Post by Vock on 2008-06-08
Sorry it's been late in replying, hopefully someone still reads this and helps me out. I'll write down everything I did and what i got back from the terminal, sorry for the length of the post, but I really would like to get this issue settled so i can move on to everything else i'm sure i need to do for my first linux setup:

Following the steps in the Comprehensive Sound Problem Solutions Guide v0.5e by LordRaiden:

```
aplay -l
```

Which gives me:
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Audigy [Audigy 1 ES [SB0160]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Audigy [Audigy 1 ES [SB0160]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Audigy [Audigy 1 ES [SB0160]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I'm trying to get my Audigy to work, haven't tried the onboard ICH6 beyond just plugging it in and trying an MP3, didn't tinker around with it at all, focussing on the Audigy.

Next, I typed ```
lspci -v
```

which listed all my pci cards, which gave me this:

```
03:03.0 Multimedia audio controller: Creative Labs SB Audigy (rev 03)
	Subsystem: Creative Labs Unknown device 0052
	Flags: bus master, medium devsel, latency 32, IRQ 18
	I/O ports at d000 [size=32]
	Capabilities: <access denied>

03:03.1 Input device controller: Creative Labs SB Audigy Game Port (rev 03)
	Subsystem: Creative Labs SB Audigy MIDI/Game Port
	Flags: bus master, medium devsel, latency 32
	I/O ports at d100 [size=8]
	Capabilities: <access denied>

```

Don't know if the <access denied> part is supposed to be there or not, but every other thing on that list had the same under Capabilities, and they're working.

Next, went to the Alsa website, to check which specific driver my soundcard needed, from what I saw at the website ([http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs)), I'm using the Sound Blaster Audigy ES (From what i see in the aplay -l), and I need the driver emu10k2, (right now it's using emu10k1?)

Next i typed this into the console
```
sudo modprobe -snd
``` and hit tab twice, which i'm assuming listed all the drivers i have installed:

```
snd-ac97-codec      snd-cs4236-lib      snd-hdsp            snd-opl3-synth      snd-seq-device
snd-ad1816a         snd-cs4281          snd-hdspm           snd-opl4-lib        snd-seq-dummy
snd-ad1848          snd-cs46xx          snd-hifier          snd-opl4-synth      snd-seq-midi
snd-ad1848-lib      snd-cs5530          snd-hwdep           snd-opti92x-ad1848  snd-seq-midi-emul
snd-ad1889          snd-cs5535audio     snd-i2c             snd-opti92x-cs4231  snd-seq-midi-event
snd-adlib           snd-cs8427          snd-ice1712         snd-opti93x         snd-seq-oss
snd-ak4114          snd-darla20         snd-ice1724         snd-oxygen          snd-seq-virmidi
snd-ak4117          snd-darla24         snd-ice17xx-ak4xxx  snd-oxygen-lib      snd-serial-u16550
snd-ak4531-codec    snd-dt019x          snd-indigo          snd-page-alloc      snd-sgalaxy
snd-ak4xxx-adda     snd-dummy           snd-indigodj        snd-pcm             snd-sis7019
snd-ali5451         snd-echo3g          snd-indigoio        snd-pcm-oss         snd-soc-core
snd-aloop           snd-emu10k1         snd-intel8x0        snd-pcsp            snd-sonicvibes
snd-als100          snd-emu10k1-synth   snd-intel8x0m       snd-pcxhr           snd-sscape
snd-als300          snd-emu10k1x        snd-interwave       snd-pdaudiocf       snd-tea575x-tuner
snd-als4000         snd-emu8000-synth   snd-interwave-stb   snd-pdplus          snd-tea6330t
snd-asihpi          snd-emux-synth      snd-korg1212        snd-portman2x4      snd-timer
snd-atiixp          snd-ens1370         snd-layla20         snd-pt2258          snd-trident
snd-atiixp-modem    snd-ens1371         snd-layla24         snd-rawmidi         snd-usb-audio
snd-au8810          snd-es1688          snd-maestro3        snd-riptide         snd-usb-caiaq
snd-au8820          snd-es1688-lib      snd-mia             snd-rme32           snd-usb-lib
snd-au8830          snd-es18xx          snd-miro            snd-rme96           snd-usb-usx2y
snd-azt2320         snd-es1938          snd-mixart          snd-rme9652         snd-util-mem
snd-azt3328         snd-es1968          snd-mixer-oss       snd-rtctimer        snd-via82xx
snd-bt87x           snd-es968           snd-mona            snd-sb16            snd-via82xx-modem
snd-bt-sco          snd-fm801           snd-mpu401          snd-sb16-csp        snd-virmidi
snd-ca0106          snd-gina20          snd-mpu401-uart     snd-sb16-dsp        snd-virtuoso
snd-cmi8330         snd-gina24          snd-msnd-pinnacle   snd-sb8             snd-vx222
snd-cmipci          snd-gusclassic      snd-mtpav           snd-sb8-dsp         snd-vx-lib
snd-cs4231          snd-gusextreme      snd-mts64           snd-sbawe           snd-vxpocket
snd-cs4231-lib      snd-gus-lib         snd-nm256           snd-sb-common       snd-wavefront
snd-cs4232          snd-gusmax          snd-opl3-lib        snd-sc6000          snd-ymfpci
snd-cs4236          snd-hda-intel       snd-opl3sa2         snd-seq             

```

And from what I can see, there is no emu10k2, so I then did what you suggested:

```
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
```

and then

```
sudo apt-get install linux-sound-base alsa-base alsa-utils
```

rebooted, and still no luck... about to move on to compiling the drivers myself following the guide, i'll let you know how that goes

---

### Post by RequinB4 on 2008-06-08
Right click on teh speaker on your panel, right click, click Open Volume Control, turn PCM down to a reasonable level.

That's it.  No compiling required.

---

### Post by Vock on 2008-06-08
Aborted the recompile idea then, but I still have this really wierd buzzing from my speakers, and still no sound coming out, even dropping down the PCM and turning it off. Sorry this is turning out to be so difficult...

---

### Post by Vock on 2008-06-08
I realized the buzzing is a result of the digital audio out connection, so after toggling the digital/audio output jack on ASLA mixer i got rid ofthe buzzing, but now I just have no audio.

---

### Post by RequinB4 on 2008-06-08
[http://www.neowin.net/forum/index.php?showtopic=629585&pid=589313746&st=0&#entry589313746](http://www.neowin.net/forum/index.php?showtopic=629585&pid=589313746&st=0&#entry589313746)

I'd play around in volume control, try dropping down mic playback or the optical.

---

### Post by kansasnoob on 2008-06-08
My daughters Soundblaster card required the alsa-firmware package from Medibuntu. But I don't have her build sheet and I don't know if it was the same sound card.

Couldn't hurt to try, and it's easily reversible if it doesn't help.

---

### Post by Vock on 2008-06-08
Already have the latest alsa-firmware package installed, and mucking around with the volume controls didn't help any either...

Would doing a fresh wipe/reload be beneficial anyone think?

---

### Post by Vock on 2008-06-08
Okay, so funny enough, i tried playing a game and i got sound out of it, so i'm guessing my hardware problems are fixed. I still don't understand why i can't play any MP3s, or videos either, but at least i know the sound is working...

EDIT:
Here's what the fix was:

```
sudo gedit /etc/modprobe.d/alsa-base
```

and then at the very end of the file i added

```
options snd-emu10k1 enable=1
```

I'm guessing for the other playback issues, it's the codecs i'm lacking?

Edit 2: Got it working, thanks all

---

