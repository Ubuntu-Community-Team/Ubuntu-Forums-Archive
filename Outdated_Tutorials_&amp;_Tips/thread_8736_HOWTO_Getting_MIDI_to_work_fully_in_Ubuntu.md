---
title: "HOWTO: Getting MIDI to work fully in Ubuntu"
date: 2004-12-20
forum: Outdated Tutorials &amp; Tips
---

### Post by Quest-Master on 2004-12-20
**MIDI: Getting to Create, Play, Anything with Ubuntu!**

*Intro*
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult; you just need the right packages and a loaded GM Soundfont.

*Prerequisites*
- A MIDI enabled sound card (most people have a SoundBlaster Audigy or Live! card-- if you have onboard sound, meaning the motherboard does the MIDI work, you'll need to use FluidSynth, which I'll talk about later).
- A fully working ALSA sound system.
- A fully working OSS sound system. (in case the upper doesn't work, you can use this and then do a sudo modprobe snd-seq-oss)
- The following ALSA packages installed (get these through apt-get/synaptic/aptitude): alsa-base, libasound, alsa-headers, libasound-dev, alsa-modules-2.4.26-1-686 (replace the 686 with 586, 386, k6, k7, etc. according to your system), alsa-oss, alsa-source.
- A program that plays MIDI files. (KMid is a nice one)
- The awesfx package if you are not using FluidSynth. (get this through apt-get)

*Blood, Sweat, and Tears time (not really)*
You've gotten past most of the work which took me the most time. Some of the packages you install may seem like overkill, but for people who use FluidSynth and have to compile it and other things, those packages are good to have just in case.

Do an lsmod in the terminal. It should return something like this

> snd_seq_midi            8096  1
snd_emu10k1_synth       6784  4
snd_emux_synth         33408  5 snd_emu10k1_synth
snd_seq_virmidi         7296  1 snd_emux_synth
snd_seq_midi_emul       7680  1 snd_emux_synth
snd_seq_oss            29440  0
snd_seq_midi_event      7552  3 snd_seq_midi,snd_seq_virmidi,snd_seq_oss
snd_seq                46608  19 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi_event
nls_iso8859_1           4352  2
nls_cp437               6016  2
vfat                   13312  2
fat                    41792  1 vfat
i830                   68644  6
proc_intf               3968  0
freq_table              4356  0
cpufreq_userspace       5336  0
cpufreq_powersave       2048  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
8139too                23936  0
8139cp                 19072  0
mii                     4864  2 8139too,8139cp
crc32                   4608  2 8139too,8139cp
emu10k1_gp              3840  0
gameport                4736  1 emu10k1_gp
snd_emu10k1            80776  11 snd_emu10k1_synth
snd_rawmidi            23232  3 snd_seq_midi,snd_seq_virmidi,snd_emu10k1
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  3 snd_emu10k1,snd_pcm_oss
snd_timer              23172  2 snd_seq,snd_pcm
snd_seq_device          7944  7 snd_seq_midi,snd_emu10k1_synth,snd_emux_synth,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi
snd_ac97_codec         59268  1 snd_emu10k1
snd_page_alloc         11144  2 snd_emu10k1,snd_pcm
snd_util_mem            4608  2 snd_emux_synth,snd_emu10k1
snd_hwdep               9120  2 snd_emux_synth,snd_emu10k1
snd                    50660  27 snd_seq_midi,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_seq_midi_event,snd_seq,snd_emu10k1,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_seq_device,snd_ac97_codec,snd_util_mem,snd_hwdep
soundcore               9824  3 snd
pci_hotplug            30640  0
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
intel_agp              20512  1
agpgart                31784  3 intel_agp
pcspkr                  3816  0
rtc                    12216  0
floppy                 54996  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
tsdev                   7168  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
evdev                   9088  0
mousedev               10124  1
psmouse                17800  0
ext3                  109544  1
jbd                    54552  1 ext3
ide_generic             1664  0
piix                   12576  1
ide_disk               16768  5
ide_core              125272  4 ide_cd,ide_generic,piix,ide_disk
unix                   25904  762
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb


If you don't see any MIDI related modules (the important ones are snd_seq_midi,snd_emu10k1_synth,snd_emux_synth,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi),
then that means ALSA hasn't been configured properly. Try sudo modprobe for these modules, and see what results.

Now, that you have MIDI devices working, go over to [http://www.hammersound.net](http://www.hammersound.net), go to Sounds -> Soundfont Library -> Collections (this is over at the bottom). Now, find a GM library which you think will sound good, etc. I am using the Ultimate GM/GS Soundfont collection, which can be downloaded through [http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip)

Now, download it to your home directory. This one should be in a ZIP file (note: if it is in sfArk form, continue reading), so simply unzip it and there should be a sf2 file inside it. Go to the terminal and do a sfxload thenameofthefile.sf2. It should return to a new $ line, and that is good. Go into KMid and open up a MIDI and it should work. You can use Rosegarden 4 (apt-get install rosegarden4) to create MIDIs with ease and a bit of musical knowledge. ;)

*FLUIDSYNTH*
FluidSynth is a software synthesizer, meaning there is no hardware involved since your card doesn't support SoundFont synthesis (otherwise, you shouldn't be doing this, hehe). It obviously doesn't relay as much quality as hardware does, but that's a small price to pay. You can find their homepage at [http://www.fluidsynth.org/](http://www.fluidsynth.org/).

It can also be easily installed through apt-get. Once it is installed, open up your terminal and do this: fluidsynth -m alsa_seq ./thenameofthefilehere.sf2. This will load the soundfont into your computer's memory. 

Now, that wasn't difficult was it? Open up whatever MIDI program and you should be able to listen to your MIDIs.

*SFARK*
sfArk is a common compression method composers use to zip up their SoundFonts, and luckily, the company behind it has a Linux version of their utility. Download it at [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). It is a command-line based utility, but again, easy to use. Just do this: sfarkxtc ./thenameofthefilehere.sfArk

That should decompress the sfArk and give you a .sf2 file. If it gives you any other kind (such as an EXE), that means you'll have to move onto another soundfont since this one won't be usable.

*CONCLUSION*
This hasn't been 100% tested, but it worked just fine for me and I hope it does for you as well. Post all of your errors, suggestions, comments, and I'll be happy to edit them into this. May your musical talent flourish with Ubuntu ;)

---

### Post by CowPie on 2004-12-20
> **Quest-Master]**MIDI: Getting to Create, Play, Anything with Ubuntu!**

*Intro*
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult said:**
> http://www.hammersound.net[/url], go to Sounds -> Soundfont Library -> Collections (this is over at the bottom). Now, find a GM library which you think will sound good, etc. I am using the Ultimate GM/GS Soundfont collection, which can be downloaded through [http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip)

Now, download it to your home directory. This one should be in a ZIP file (note: if it is in sfArk form, continue reading), so simply unzip it and there should be a sf2 file inside it. Go to the terminal and do a sfxload thenameofthefile.sf2. It should return to a new $ line, and that is good. Go into KMid and open up a MIDI and it should work. You can use Rosegarden 4 (apt-get install rosegarden4) to create MIDIs with ease and a bit of musical knowledge. ;)

*FLUIDSYNTH*
FluidSynth is a software synthesizer, meaning there is no hardware involved since your card doesn't support SoundFont synthesis (otherwise, you shouldn't be doing this, hehe). It obviously doesn't relay as much quality as hardware does, but that's a small price to pay. You can find their homepage at [http://www.fluidsynth.org/](http://www.fluidsynth.org/).

It can also be easily installed through apt-get. Once it is installed, open up your terminal and do this: fluidsynth -m alsa_seq ./thenameofthefilehere.sf2. This will load the soundfont into your computer's memory. 

Now, that wasn't difficult was it? Open up whatever MIDI program and you should be able to listen to your MIDIs.

*SFARK*
sfArk is a common compression method composers use to zip up their SoundFonts, and luckily, the company behind it has a Linux version of their utility. Download it at [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). It is a command-line based utility, but again, easy to use. Just do this: sfarkxtc ./thenameofthefilehere.sfArk

That should decompress the sfArk and give you a .sf2 file. If it gives you any other kind (such as an EXE), that means you'll have to move onto another soundfont since this one won't be usable.

*CONCLUSION*
This hasn't been 100% tested, but it worked just fine for me and I hope it does for you as well. Post all of your errors, suggestions, comments, and I'll be happy to edit them into this. May your musical talent flourish with Ubuntu ;)
 HI, bump!! Wow I have just found this, very useful for me.  Iw ill try, and tell you if it works!

---

### Post by strips on 2004-12-21
> FLUIDSYNTH 

Is what I have been looking for the last weeks. Will try when I come home.

---

### Post by Quest-Master on 2004-12-21
Luckily, Fluidsynth is apparently a very easy to set up program. I have an SBLive! though, so no need for that.

Also, many of you might have heard of Timidity, which is also a nice program, but for optimum quality, I suggest simply using the instructions provided if you have the proper soundcard, or use Fluidsynth as strips will be using. ;)

---

### Post by mr_ed on 2004-12-23
Something tells me that this isn't supposed to happen:

jeramy@tuscany:~ $ lsmod |grep midi
snd_seq_midi            8416  0
snd_rawmidi            24704  1 snd_seq_midi
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                52176  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8040  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    55300  14 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_seq_device,snd_maestro3,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
jeramy@tuscany:~ $ fluidsynth -m alsa_seq ./Ultimate.SF2
cca_open_socket: could not connect to host 'localhost', service '14541'
cca_init: could not connect to server 'localhost' - disabling ladcca
fluidsynth: warning: Ignoring sample WhiteNoiseWave #03: can't use ROM samples
fluidsynth: warning: Ignoring sample ColdGlass7Wave #04: can't use ROM samples
fluidsynth: warning: Ignoring sample tbelld4wave: can't use ROM samples
fluidsynth: warning: Ignoring sample SineWave #11: can't use ROM samples
fluidsynth: warning: Ignoring sample FloorTomBrite #08: can't use ROM samples
fluidsynth: warning: Ignoring sample AccordFx3 #02: can't use ROM samples
fluidsynth: warning: Ignoring sample AccordAx2 #02: can't use ROM samples
fluidsynth: warning: Ignoring sample AccordFx2 #02: can't use ROM samples
fluidsynth: warning: Ignoring sample femalevoiceg2: can't use ROM samples
fluidsynth: warning: Ignoring sample crash5: can't use ROM samples
fluidsynth: warning: Ignoring sample xyloe4looped: can't use ROM samples
fluidsynth: warning: Ignoring sample banjod3: can't use ROM samples
fluidsynth: warning: Ignoring sample banjog2: can't use ROM samples
fluidsynth: warning: Ignoring sample ocarinafx2: can't use ROM samples
fluidsynth: warning: Ignoring sample organwavea3: can't use ROM samples
fluidsynth: warning: Ignoring sample organwave: can't use ROM samples
fluidsynth: warning: Ignoring sample octavewave: can't use ROM samples
fluidsynth: warning: Ignoring sample chanterax1: can't use ROM samples
fluidsynth: warning: Ignoring sample bagpipedrna: can't use ROM samples
fluidsynth: warning: Ignoring sample pluckharp: can't use ROM samples
fluidsynth: warning: Ignoring sample acbasse1: can't use ROM samples
fluidsynth: warning: Ignoring sample pizzviolinc3: can't use ROM samples
fluidsynth: warning: Ignoring sample brasssectf5: can't use ROM samples
fluidsynth: warning: Ignoring sample brasssectc3: can't use ROM samples
fluidsynth: warning: Ignoring sample bsawtoothwavea3: can't use ROM samples
fluidsynth: warning: Ignoring sample sawstackwavems: can't use ROM samples
fluidsynth: warning: Ignoring sample lefone: can't use ROM samples
fluidsynth: warning: Ignoring sample ShakuA2: can't use ROM samples
fluidsynth: warning: Ignoring sample SikuE2: can't use ROM samples
fluidsynth: warning: Ignoring sample KPianoB5: can't use ROM samples
fluidsynth: warning: Ignoring sample Timpani: can't use ROM samples
** Using format s16, rw, interleaved
fluidsynth version 1.0.3
Copyright (C) 2000-2002 Peter Hanappe and others.
FLUID Synth comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to redistribute it
under certain conditions; see the COPYING file for details.
SoundFont(R) is a registered trademark of E-mu Systems, Inc.

Type 'help' to get information on the shell commands.

>

It's on an HP Omnibook 6000 with an AC97 sound card.

---

### Post by Quest-Master on 2004-12-23
That's really weird. Did you try playing a MIDI after all of those warning stopped appearing? It appears that what will happen is that it'll only load some of the samples and use them. Probably because of how the soundfonts were created.

I'd suggest looking for another soundfont collection over at [http://www.hammersound.net/](http://www.hammersound.net/) and try to load it and see if it works.

---

### Post by CowPie on 2004-12-26
[QUOTE=CowPie]HI, bump!! Wow I have just found this, very useful for me.  Iw ill try, and tell you if it works![/QUOTE]
 Hi, I try this yet no sound comes out?

Luckily no more warnign about /dev/sequencer though :)

---

### Post by fuzzix on 2004-12-26
I have a Soundblaster Digital 4.1 which AFAIK has sequencer hardware. The relevant modules are loaded as follows:
```
snd_seq_oss            29440  0
snd_seq_midi_event      7552  2 snd_seq_midi,snd_seq_oss
snd_seq                46608  6 snd_seq_midi,snd_seq_oss,snd_seq_midi_event
snd_seq_device          7944  4 snd_seq_midi,snd_rawmidi,snd_seq_oss,snd_seq
snd_pcm_oss            48168  0
snd_pcm                85540  3 snd_bt87x,snd_ens1371,snd_pcm_oss
snd_page_alloc         11144  2 snd_bt87x,snd_pcm
snd_timer              23172  2 snd_seq,snd_pcm
snd_mixer_oss          16640  1 snd_pcm_oss
snd                    50660  16 snd_seq_midi,snd_bt87x,snd_ens1371,snd_rawmidi,snd_ac97_codec,snd_seq_oss,snd_seq_midi_event,snd_seq,snd_seq_device,snd_pcm_oss,snd_pcm,snd_timer,snd_mixer_oss
soundcore               9824  2 bttv,snd

```
Using Kmid *appears* to work - I can select the ALSA midi sequencer device, the "tempo" bar lights, but no sound plays. I have checked the volumes with alsamixer - nothing has any effect.

Does anyone know if this card actually supports midi sequencer? Is the ensoniq module appropriate for this card? I can't locate the original docs, Creative's site is suprisingly general and the manual is unavailable online. According to [Amazon](http://www.amazon.co.uk/exec/obidos/ASIN/B00005TT49/202-8516889-5967008) it features:

...
# 128-voice Wave-Table synthesiser for rich MIDI playback
...

Attempting to get ScummVM to use the sequencer - with /dev/sequencer there is no error but no output either.

```
$ scummvm -ghq2x -eseq
Switched to configuration /home/fuzzbucket/.scummvmrc
Looking for tentacle
Trying to start game 'Day Of The Tentacle'
WARNING: IMuse doCommand(6) - setMasterVolume (74)!

```

(the WARNING appears using the default emulated device too - it doesn't appear to have a negative effect)

```
Using ALSA:
$ scummvm -ghq2x -ealsa
Switched to configuration /home/fuzzbucket/.scummvmrc
Looking for tentacle
Trying to start game 'Day Of The Tentacle'
(0:0:0x0): Can't subscribe to MIDI port (65:0)!

```

Any help or suggestions at all appreciated!

*edit* [This page](http://216.239.59.104/search?q=cache:HotJ1O03zmkJ:electronics.reviewindex.co.uk/reviews_uk/B00005TT49.html+%2B%22soundblaster+digital+4.1%22+%2Bmidi&hl=en) suggests a capable midi system.

---

### Post by alainhenry on 2004-12-27
I managed to have Timidity working as a midi server and opening two midi ports, so that the command
pmidi -p 128:0 mymusic.mid  works
See thread [http://www.ubuntuforums.org/showthread.php?t=8286](http://www.ubuntuforums.org/showthread.php?t=8286)

Alain

---

### Post by fuzzix on 2004-12-27
Is that "emulated" - as in PCM data generated on the fly? The Timidity client doesn't perform very well here so I can only assume I'll have the same problems emulating a midi server (high CPU use, choppy output).

Interesting functionality, though - if I had a faster machine I'd be right on it :)

---

### Post by alainhenry on 2004-12-28
To improve response time, it's important to run the Timidity midiserver from a root session (higher priority).  Did you try that ?

Alain

---

### Post by fuzzix on 2004-12-28
I'd rather not use Timidity at all if there's midi hardware available to me - as far as I can ascertain there is, it's just not "sounding off" :)

If the card is lacking I can do without - Timidity's resource use on this box is hideous and doing a setuid root could only make it worse.

Thanks for the suggestion, but I'd rather go without... :)

---

### Post by Quest-Master on 2004-12-28
For those who are getting the MIDI to actually **play** in KMid but no output, there's this weird thing with some SoundBlaster songs with loading snd-seq-oss. Do this in the terminal and see if it works: sudo modprobe snd-seq-oss

---

### Post by fuzzix on 2004-12-29
Starting to understand this issue a little more now. I cannot load a soundfont with sfxload.
```
$ sfxload Ultimate.SF2
No AWE synth device is found
```Does this mean I do not have the required hardware? According to [every spec I can find](http://www.amazon.co.uk/exec/obidos/tg/stores/detail/-/electronics/B00005TT49/system-requirements/ref%3Ded%5Ftec%5Fdp%5F2%5F1/026-9603251-8028436) I should have a wavetable synth... Is there another method for loading sound fonts?

Also, those having trouble with fluidsynth might find [qsynth](http://qsynth.sourceforge.net/qsynth-index.html) helpful. Very easy to set up.

... and for those who know what it is here's the [EAW patch set](http://www.fbriere.net/debian/dists/unstable/deb/timidity-patches-eaw_12-0fbriere.1_all.deb)

---

### Post by Suzan on 2005-01-22
I've got the same problem with my  soundblaster pci 512. When i load the soundfont, the same error appear:

No AWE synth device is found

All other sounds works perfect with these soundcard, except midi.

---

### Post by Quest-Master on 2005-01-22
I'm on a SBLive! 5.1 LS card.. what're you guys on?

---

### Post by CowPie on 2005-01-23
[QUOTE=Quest-Master]I'm on a SBLive! 5.1 LS card.. what're you guys on?[/QUOTE]
 SBLive! 5.1 MP3+ card.  I think midi on ubuntu will be forever impossible for me, I've tried for weeks!!  My bugzilla bug doesn't seem to be helping either ;(

---

### Post by alainhenry on 2005-01-23
[QUOTE=Quest-Master]I'm on a SBLive! 5.1 LS card.. what're you guys on?[/QUOTE]
I have a Yamaha YMF-724F (DS1 Audio controller) and I am now moderately happy with MIDI on my machine
Alain

---

### Post by Quest-Master on 2005-01-23
That's great alainhenry. :D

CowPie, since the MP3+ card is external (or is there a PCI version of it?), I believe it might not be able to functino the same way as the SB PCI cards do.

---

### Post by CowPie on 2005-01-23
[QUOTE=Quest-Master]That's great alainhenry. :D

CowPie, since the MP3+ card is external (or is there a PCI version of it?), I believe it might not be able to functino the same way as the SB PCI cards do.[/QUOTE]
 Oh no, its a PCI card!  AFAIK the only difference was the software included in the bundle, but then the Futureshop guys were probably lying to me.  The thing is that midi works on Windows perfectly, it sounds pretty good as well.

---

### Post by fuzzix on 2005-01-23
As far as I can tell the AudioPCI/Ensoniq cards do not support hardware wavetable midi - the windows device driver from Creative uses a software midi engine so uploading a soundfont is not possible.

---

### Post by CowPie on 2005-01-24
[QUOTE=fuzzix]As far as I can tell the AudioPCI/Ensoniq cards do not support hardware wavetable midi - the windows device driver from Creative uses a software midi engine so uploading a soundfont is not possible.[/QUOTE]
 Just so you know, Suse 9.1 worked with MIDI out of the box with this Live! card.  I just can't get debian-based distros to..

---

### Post by Quest-Master on 2005-01-24
I think you should bring this up on the mailing lists and make the developers aware of this. They just might get it to work by the Hoary stable release. :)

---

### Post by Quest-Master on 2005-01-27
Update:

On a new install, I tried a ton of things to get it working. Load the soundfont into memory with sfxload as it says in the guide, and then use **Rosegarden 4** instead of KMid to develop your application. Rosegarden initialized some modules KMid didn't which in turn.. played MIDIs for me. :D

---

### Post by xy77 on 2005-03-23
Okay, up till now, midi is not working for me.

lspci tells me:
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)

I loaded all the midi modules (snd_seq_virmidi snd_seq_midi_emul snd_seq_midi snd_rawmidi snd_seq_midi_event snd_seq snd_seq_device) and tried to use rosegarden4. It would start, but no sound is available. Here the rosegarden jack status output:
> Rosegarden 0.9.9 - AlsaDriver - alsa-lib version 1.0.5

JackDriver::initialiseAudio - JACK server not running

  ALSA Client information:


    Current timer set to "system timer"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "system timer"
Creating device 0 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 1
    Current timer set to "system timer"
    Current timer set to "system timer"
AlsaDriver::setPlausibleConnection: connection like 64:0 M Audio Audiophile 24/96 MIDI (duplex) requested for device 0
AlsaDriver::setPlausibleConnection: nothing suitable available
Creating device 1 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 2
AlsaDriver::setPlausibleConnection: connection like 72:0 MK-225C USB MIDI keyboard MIDI  (duplex) requested for device 1
AlsaDriver::setPlausibleConnection: nothing suitable available
Creating device 2 in Play mode -- no connection available 
Default device name for this device is Anonymous MIDI device 3
AlsaDriver::setPlausibleConnection: connection like 128:0 KAMix: qamix (write) requested for device 2
AlsaDriver::setPlausibleConnection: nothing suitable available
    Current timer set to "system timer"
    Current timer set to "system timer"
    Current timer set to "system timer"


And here what happens, when I try to start jack.
```

$ jackd -d alsa
jackd 0.99.0
Copyright 2001-2003 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa

```

I couldnt figure out, what is blocking jack from starting. The sequencer devices /dev/sequencer and /dev/sequencer2 are present.

Rosegarden complains that "The following plugins could not be loaded: -- Xsynth (from xsynth-dssi.so)". I hope this is not critical.

Just in case anyone wondered, sound from bmp or xmms is working.

Any help would be appreciated!

- David (xy77)

---

### Post by alainhenry on 2005-03-23
Hello,

Could you tell what is the midi equipmùent that you are using ? I did not get it from your message.

Alain

---

### Post by SilvioTO on 2005-07-21
I have sound blaster live and need to play with sound a game (runescape) that have midi music. I'm follow this howto but when I trying to unpack with sfarkxtc utility...

$ sfarkxtc ./Fluid R3 GM.sfArk
bash: sfarkxtc: command not found

sfarkxtc is in the same folder fo the file to unpack. can you help me please?

Thanks, Silvio.

---

### Post by alainhenry on 2005-07-25
Sorry for a late answer, I was on holiday for a week.  Unfortunately, I do not know how to help in this case.  
Anyone else ?
Alain

---

### Post by fishfork on 2005-07-26
SilvioTO: you need to type ./sfarkxtc instead of sfarkxtc - for security, linux doesn't include the current directory in the path.

---

### Post by RJARRRPCGP on 2005-07-29
Does this apply to Hoary, too? I'm confused, thus I may be in the wrong section.  :-? 

I have a SoundBlaster Live SB0100 sound card, but I don't see emu10k1_synth nor snd_emux_synth in the list when using the **lsmod** command!

---

### Post by chruesu on 2005-08-26
hi folks

thanks for all those nice suggestions, howto's and everything you posted here.
my prob:

no sound in rosegarden!
stats:
```
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.8

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 2048
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "alsa_pcm:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "alsa_pcm:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    128,0 - (TiMidity, TiMidity port 0)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]

Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
    Current timer set to "PCM playback 0-0-0"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "PCM playback 0-0-0"
```

what might be the prob. in my case?
I  can play *.mid files by the following command:
```
timidity acommonmidifile.MID
```
There is even some "blinking", when I try to play a *.MID flie with rosegarden.
However, as I stated above: no sound for rosegarden
Note: i have no probs with alsa in general.

Thanks for any advice!!

---

### Post by chruesu on 2005-09-23
Please anybody!

I still have troubles with my soundconfiguration. I'd like to use rosegraden, however as complete NOB I don't manage to get it working. As I said, I can even *play* a midi-file with rosegarden however, I cant here any sound...

the last thing I did is the following:

```
timidity -iA -B2,8 -Os1l -s 44100
```
Requested buffer size 2048, fragment size 1024
ALSA pcm 'default' set buffer size 16384, period size 4096 bytes
Output rate adjusted to 48000 Hz (requested 44100 Hz)
TiMidity starting in ALSA server mode
Opening sequencer port: 128:0 128:1 128:2 128:3
ALSA lib pcm_dmix.c:868:(snd_pcm_dmix_open) unable to open slave
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')

Then I started roesgarden
The sequencerstatus:
```
Rosegarden 1.0 - AlsaDriver - alsa-lib version 1.0.8

JackDriver::initialiseAudio - JACK sample rate = 44100Hz, buffer size = 2048
JackDriver::initialiseAudio - creating disk thread
JackDriver::initialiseAudio - found 2 JACK physical outputs
JackDriver::initialiseAudio - connecting from "rosegarden:master out L" to "alsa_pcm:playback_1"
JackDriver::initialiseAudio - connecting from "rosegarden:master out R" to "alsa_pcm:playback_2"
JackDriver::initialiseAudio - found 2 JACK physical inputs
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_1" to "rosegarden:record in 1 L"
JackDriver::initialiseAudio - connecting from "alsa_pcm:capture_2" to "rosegarden:record in 1 R"
JackDriver::initialiseAudio - initialised JACK audio subsystem

  ALSA Client information:

    128,0 - (TiMidity, TiMidity port 0)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,1 - (TiMidity, TiMidity port 1)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,2 - (TiMidity, TiMidity port 2)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]
    128,3 - (TiMidity, TiMidity port 3)  (WRITE ONLY) [ctype 1, ptype 2, cap 66]

Creating device 0 in Play mode for connection 128:0 TiMidity port 0 (write)
Default device name for this device is MIDI software device
Creating device 1 in Play mode for connection 128:1 TiMidity port 1 (write)
Default device name for this device is MIDI software device 2
Creating device 2 in Play mode for connection 128:2 TiMidity port 2 (write)
Default device name for this device is MIDI software device 3
Creating device 3 in Play mode for connection 128:3 TiMidity port 3 (write)
Default device name for this device is MIDI software device 4
    Current timer set to "PCM playback 0-0-0"
AlsaDriver::initialiseMidi -  initialised MIDI subsystem

    Current timer set to "PCM playback 0-0-0"
```

---

### Post by alainhenry on 2005-09-24
recently, when I try to load timidity as midi server, i receive the same error message as you do (at least, the end of it)
After entering the timidity command, I receive: 

>timidity -iA -B2,8 -Os1l -s 44100
Can't open pcm device 'default'.
Couldn't open ALSA pcm device (`s')
>

And no sound after that, of course

I am still searching to know what to do

Alain

Edit: "killall esd" did the trick  see thread:
[http://www.ubuntuforums.org/showthread.php?t=26567](http://www.ubuntuforums.org/showthread.php?t=26567)

---

### Post by cosimo on 2005-10-17
Hello,
 Well i tried your suggestion and midi still does not work. I have a sound blaster live in this machine  and I have tried timidity, however, unless I am missing something, timidity doesn't show up anywhere on the system after install. This may be a command line app.
 All my settings seem to match the ones listed, yet no midi. I am new at this unix/lyinux stuff so any help would be appreciated.
After a week of trial and error , I finally got my dvd's to play flawlessly on Breezy final. I woul dlike the same for midi.
 Thanks
 Coz

---

### Post by cosimo on 2005-10-28
Hello,
 Well I got my midi up and working just fine, however, with no help from these pages.
I want to thank anyone that suggested things, 
 thanks again

---

### Post by AgenT on 2005-11-11
[http://melodymachine.com/](http://melodymachine.com/) is dead, which is a major problem because that is where the extraction utility should be. Does anyone know where a utility to extract sfark files can be located?

---

### Post by fishfork on 2005-11-11
[QUOTE=AgenT][http://melodymachine.com/](http://melodymachine.com/) is dead, which is a major problem because that is where the extraction utility should be.[/QUOTE]
Are you sure? It seems to be working here.

---

### Post by AgenT on 2005-11-11
Are you sure? ;) Refresh your cache. [http://melodymachine.com]("http://melodymachine.com") gives a cpanel webpage (error - not configured) and [http://melodymachine.com/sfark.htm]("http://melodymachine.com/sfark.htm") gives this:

> **Not Found**

  The requested URL /sfark.htm was not found on this server.  
 Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the request.

**EDIT**: There seems to be some strange routing problems! Using a proxy that website works. This is strange because every other website (including ubuntu forums) works fine.

---

### Post by |cJ| on 2006-02-27
this worked a treat for me thanks!

---

### Post by warp99 on 2006-03-20
After reading this thread I did a little investigation based on a prior post which said midi worked in SuSe, but not ubuntu. Well I beleive I have the simplest setup for a fully functional midi sequencer or even an ALSA sequencer server.

First you need timidity:

[FONT="Fixedsys"]sudo apt-get install timidity[/FONT]

Then read up on the some background information here:
[SUSE LINUX – User Guide Chapter 15]("http://nfs-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.2/suselinux-userguide_en/ch15s10.html")

The file eawpats12_full.rar listed in the manual is a dead link, but you can get it here:
[eawpats12_full.rar]("http://people.fruitsalad.org/lauri/stuff/eawpats12_full.rar")

Download and unrar following the directions, you can change the path to the eawpats directory to your choosing, it doesn't matter. At this point we shift from the SuSe directions doing the following:

[FONT="Fixedsys"]cd /<path of your choice>/eawpats
sudo gedit timidity.cfg[/FONT]

Change two lines in timidity.cfg as follows:

Change [FONT="Fixedsys"]dir  c:\timidity[/FONT] 
to [FONT="Fixedsys"]dir /<path of your choice>/eawpats[/FONT]

Change [FONT="Fixedsys"]dir c:\eawpats[/FONT]
to [FONT="Fixedsys"]dir /<path of your choice>/eawpats[/FONT]

Save the file, then change permissions on the eawpats directory per instructions. We then need to change the timidity.cfg for timidity itself, so we do the following:

[FONT="Fixedsys"]cd /etc/timidity
sudo gedit timidity.cfg[/FONT]

Change the last reference line to the following:
[FONT="Fixedsys"]source /<path of your choice>/eawpats/timidity.cfg[/FONT]

Save the file, then timidity -iatv to open the graphical interface, open a midi file and your should have a working 16 channel midi sequencer. \\:D/

You can set up timidity as an ALSA server if you like. It's looks fairly easy, I just didn't have a chance to test it out. :cool:

---

### Post by umuro on 2006-04-01
Yes, timidity is working standalone. But

timidity -iA -B2,8 -Os &

returns an error message:

TiMidity starting in ALSA server mode
ALSA lib seq_hw.c:455:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
error in snd_seq_open

In fact this was the very first problem in this thread. Now, I still have a ubuntu where I cannot use any midi software other than timidity.

[QUOTE=warp99]After reading this thread I did a little investigation based on a prior post which said midi worked in SuSe, but not ubuntu. Well I beleive I have the simplest setup for a fully functional midi sequencer or even an ALSA sequencer server.

First you need timidity:

[FONT="Fixedsys"]sudo apt-get install timidity[/FONT]

Then read up on the some background information here:
[SUSE LINUX – User Guide Chapter 15]("http://nfs-uxsup.csx.cam.ac.uk/pub/doc/suse/suse9.2/suselinux-userguide_en/ch15s10.html")

The file eawpats12_full.rar listed in the manual is a dead link, but you can get it here:
[eawpats12_full.rar]("http://people.fruitsalad.org/lauri/stuff/eawpats12_full.rar")

Download and unrar following the directions, you can change the path to the eawpats directory to your choosing, it doesn't matter. At this point we shift from the SuSe directions doing the following:

[FONT="Fixedsys"]cd /<path of your choice>/eawpats
sudo gedit timidity.cfg[/FONT]

Change two lines in timidity.cfg as follows:

Change [FONT="Fixedsys"]dir  c:\timidity[/FONT] 
to [FONT="Fixedsys"]dir /<path of your choice>/eawpats[/FONT]

Change [FONT="Fixedsys"]dir c:\eawpats[/FONT]
to [FONT="Fixedsys"]dir /<path of your choice>/eawpats[/FONT]

Save the file, then change permissions on the eawpats directory per instructions. We then need to change the timidity.cfg for timidity itself, so we do the following:

[FONT="Fixedsys"]cd /etc/timidity
sudo gedit timidity.cfg[/FONT]

Change the last reference line to the following:
[FONT="Fixedsys"]source /<path of your choice>/eawpats/timidity.cfg[/FONT]

Save the file, then timidity -iatv to open the graphical interface, open a midi file and your should have a working 16 channel midi sequencer. \\:D/

You can set up timidity as an ALSA server if you like. It's looks fairly easy, I just didn't have a chance to test it out. :cool:[/QUOTE]

---

### Post by umuro on 2006-04-01
I've got MIDI working! Read the full experience in [http://conceptspace.server.us/conceptspace/40]("http://conceptspace.server.us/conceptspace/40").

Somebody could still help. Because as described in that page, I've not been able to get it autostart. Somehow timidity is becoming silent when it is not explicitly started after logging in.

---

### Post by Nordoelum on 2006-04-03
Make it in my subscribtions :P

---

### Post by umuro on 2006-04-04
In Summary
 Go an fetch Automatics to "Enable MIDI Capability" 
 If your midi is silent then simply start "/etc/init.d/timidity" again. 
 You can then switch eawpats if you wish. 

 Why do you think Automatix solution worked? In my case, it was issuing
 
```
timidity -iA -B2,8 -Os -s 44100 &
```

 Yes, the parameter -s 44100. Timidity has to serve using the same frequency as the rest of the system. And Automatix is detecting this correctly. The frequency might be different for your system.
 
 Sometimes timidity is sliencing especially at the system ```
startup.Then I do 
sudo killall timidity
/etc/init.d/timidity start &
```

_____
[http://conceptspace.server.us/conceptspace]("http://conceptspace.server.us/conceptspace")

---

### Post by mjshepherd on 2006-06-24
Hi There,

I've been trying to get MIDI sound to play in Rosegarden4 for some time - it tells me that "MIDI OK, Audio OK" but nothing comes out of the speakers when i play my sequences.  I have tried to follow your instructions and have come across some problems, which i wondered if you'd help me with?
I think i have most of the packages you list, but couldn't get alsa-headers, or alsa-modules-2.4.26-1-386 through apt-get.  Is this a problem?  How do i solve it?

I have a midi-enabled soundcard (which works on my windows partition) and have installed awesfx.  I have also intalled Fluidsynth (with qsynth front end) just in case - should i get rid of it?

In the lsmod all the necessary lines you mention are there, and more besides.  I didn't do a sudo modprobe, did i need to?

I downloaded the "Gort's_Synth.sf2" zipfile and have extracted it into my home directory.  However, when i run the command 

sfxload Gort's_Synth.sf2

I don't get a $ command line, but a > line instead.  I don't know what to do at this point.  Exactly the same thing happens if I try to load this soundfont to Fluidsynth using your instructions.  Please help!

Is it to do with the name of the sf2 file having too much punctuation?

Cheers,

Matthew

---

### Post by spookypeanut on 2007-08-15
OK, so I got MIDI working, using the hardware synth on my SB Live. And it's great!

However, there is a slight catch that I'm hoping someone can help me with. The software I'm using (scummvm, dosbox) wants me to input the port number, which I do, not a problem. But the port number seems to be different every time I boot up, usually around 16-21. Is there any way I can stop this happening?

---

### Post by Yfrwlf on 2007-11-23
I think this guide only worked for me because there is a setting in Kmid that allowed me to switch devices to the Emu10K1 which I guess is software emulation?  The Audigy 2 ZS MPU-401 device doesn't give me any sound though after doing the loading the new soundfont thingy.

---

### Post by Amaroq on 2008-01-27
I was able to get midi sound simply by installing timidity via apt-get (timidity++ I think), but it was missing some instruments.

This guide helped me out a lot.
[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo)

My card doesn't support hardware midi, so I had to use timidity. Use that guide to set up timidity to use a soundfont. Setting up a soundfont fixed the missing instruments problem for me as well as improved the quality of the midi play.

I originally tried Ultimate.sf2 like the creator of this thread suggested, but I thought one of the drum instruments were too loud and the distortion guitar sounded too generic to me. I now use the Unison.sf2 soundfont as recommended in that guide, and while I'd still like a different distortion guitar (this one is better, but a midi I like to listen to, Cosmo Canyon, that contains that instrument sounds a little strange with this one), overall I'm extremely satisfied with the midi quality I'm getting now.

---

### Post by subitul on 2008-02-02
Right, I've got MIDI working nicely with a SBLive! Value but I have one small problem. My current soundfont is horrible so I decided to get another but it is pretty large - 140MB - and when I load it it says:

```
$ sfxload FluidR3\ GM.SF2
sfxload: no memory left
```

I've found a few mentions of how to create a cache in the system RAM but only for Windows. I was wondering if there was a method of doing this in linux (Kubuntu Gutsy). Any help would be great please.

---

### Post by ThingsThatGoFlirInTheShla on 2008-02-18
Hi.This is my first post and I'm a complete newbie with Linux (been using it for 2 weeks).
I see all these helpful posts about, finaly solving problems, which have had me tearing my hair out and then I'm stumped because I don't know how to do this command or that command :-? 
It would be a pain in the **** for everyone who wrote a 'how to' to cater for the newbies and the more experienced users, so I wouldn't expect it to be laid out every time,  but I was just wondering whether there was a site with explanations of all the basic commands because I really really really wanted to get midi going!! :)
Cheers

---

### Post by ThingsThatGoFlirInTheShla on 2008-02-18
sorry. I did't realise a.rse was a bad word. lol
:-\"

---

### Post by alainhenry on 2008-02-19
Can you be a bit more specific about the commands you would like to be explained ? Does these Howto's help ?

[https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo?highlight=%28midi%29%7C%28synthesis%29](https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo?highlight=%28midi%29%7C%28synthesis%29)
[https://help.ubuntu.com/community/MidiHardwareSynthesisSetup?highlight=%28midi%29%7C%28synthesis%29](https://help.ubuntu.com/community/MidiHardwareSynthesisSetup?highlight=%28midi%29%7C%28synthesis%29)
Alain

---

### Post by ThingsThatGoFlirInTheShla on 2008-02-26
Thanks Alain.
I've been able to figure all the basics out now but hopefully your links willl be helpful to other newbies tearing their hair out!

---

### Post by Mr_Ada on 2008-03-23
I still have no MIDI.

chris

---

### Post by contactMW on 2008-04-02
> **Quest-Master said:**
> **MIDI: Getting to Create, Play, Anything with Ubuntu!**

*Intro*
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult; you just need the right packages and a loaded GM Soundfont.

*Prerequisites*
- A MIDI enabled sound card (most people have a SoundBlaster Audigy or Live! card-- if you have onboard sound, meaning the motherboard does the MIDI work, you'll need to use FluidSynth, which I'll talk about later).
- A fully working ALSA sound system.
- A fully working OSS sound system. (in case the upper doesn't work, you can use this and then do a sudo modprobe snd-seq-oss)
- The following ALSA packages installed (get these through apt-get/synaptic/aptitude): alsa-base, libasound, alsa-headers, libasound-dev, alsa-modules-2.4.26-1-686 (replace the 686 with 586, 386, k6, k7, etc. according to your system), alsa-oss, alsa-source.
- A program that plays MIDI files. (KMid is a nice one)
- The awesfx package if you are not using FluidSynth. (get this through apt-get)

*Blood, Sweat, and Tears time (not really)*
You've gotten past most of the work which took me the most time. Some of the packages you install may seem like overkill, but for people who use FluidSynth and have to compile it and other things, those packages are good to have just in case.

Do an lsmod in the terminal. It should return something like this



If you don't see any MIDI related modules (the important ones are snd_seq_midi,snd_emu10k1_synth,snd_emux_synth,snd_seq_oss,snd_seq,snd_emu10k1,snd_rawmidi),
then that means ALSA hasn't been configured properly. Try sudo modprobe for these modules, and see what results.

Now, that you have MIDI devices working, go over to [http://www.hammersound.net](http://www.hammersound.net), go to Sounds -> Soundfont Library -> Collections (this is over at the bottom). Now, find a GM library which you think will sound good, etc. I am using the Ultimate GM/GS Soundfont collection, which can be downloaded through [http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip](http://www.hammersound.net/cgi-bin/soundlink.pl?action=view_download_page;ID=72;SoundFont_Location_Selected=Download%20UK;SoundFont_Filename_Selected=Ultimate.zip)

Now, download it to your home directory. This one should be in a ZIP file (note: if it is in sfArk form, continue reading), so simply unzip it and there should be a sf2 file inside it. Go to the terminal and do a sfxload thenameofthefile.sf2. It should return to a new $ line, and that is good. Go into KMid and open up a MIDI and it should work. You can use Rosegarden 4 (apt-get install rosegarden4) to create MIDIs with ease and a bit of musical knowledge. ;)

*FLUIDSYNTH*
FluidSynth is a software synthesizer, meaning there is no hardware involved since your card doesn't support SoundFont synthesis (otherwise, you shouldn't be doing this, hehe). It obviously doesn't relay as much quality as hardware does, but that's a small price to pay. You can find their homepage at [http://www.fluidsynth.org/](http://www.fluidsynth.org/).

It can also be easily installed through apt-get. Once it is installed, open up your terminal and do this: fluidsynth -m alsa_seq ./thenameofthefilehere.sf2. This will load the soundfont into your computer's memory. 

Now, that wasn't difficult was it? Open up whatever MIDI program and you should be able to listen to your MIDIs.

*SFARK*
sfArk is a common compression method composers use to zip up their SoundFonts, and luckily, the company behind it has a Linux version of their utility. Download it at [http://melodymachine.com/sfark.htm](http://melodymachine.com/sfark.htm). It is a command-line based utility, but again, easy to use. Just do this: sfarkxtc ./thenameofthefilehere.sfArk

That should decompress the sfArk and give you a .sf2 file. If it gives you any other kind (such as an EXE), that means you'll have to move onto another soundfont since this one won't be usable.

*CONCLUSION*
This hasn't been 100% tested, but it worked just fine for me and I hope it does for you as well. Post all of your errors, suggestions, comments, and I'll be happy to edit them into this. May your musical talent flourish with Ubuntu ;)

The site [www.hammersound.net](www.hammersound.net) looks like a hacking site - may it wasn't originally like this but doesn't look like there are any sound-related things on there. I see the message:

"
# Attention #
Your Security Has Been Passed by .. 
r00t-x ,
"

( added about 30 mins later )

the download link seems to look more legitimate, but I haven't tried downloading from work as I don't want to get into trouble !- will try when I get home .  I can't see how to get from the main page to the soundfont library one still...

---

### Post by FranciscoPadillaGarcia on 2008-05-05
I followed this guide literally, but I couldn't get MIDI's to play in Audacious. However, I was able to fix the problem by installing timidity and wildmidi as explained in this page: [http://www.funnestra.org/ubuntu/hardy/#wildmidi](http://www.funnestra.org/ubuntu/hardy/#wildmidi)

I don't know which one made the trick, but only then I can play MIDI's. Maybe you should add this to the guide.

---

### Post by PaulosCZ on 2008-06-26
> **warp99 said:**
> 
First you need timidity:

[FONT="Fixedsys"]sudo apt-get install timidity[/FONT]

And that's last thing you need :) You can play MIDI files by KMid now :)
Tested, working - I didn't need anything else than install that package.

---

### Post by Yfrwlf on 2008-06-26
It'd be neat if Timidity was a suggested package or something for any program that required midi, or if Pulse Audio could do midi, because so far I've never seen hardware midi working out of the box and don't really expect that to take off anytime soon. :-?

Not that midi is used much anymore any way...

---

### Post by danellisuk on 2008-08-13
> **subitul said:**
> Right, I've got MIDI working nicely with a SBLive! Value but I have one small problem. My current soundfont is horrible so I decided to get another but it is pretty large - 140MB - and when I load it it says:

```
$ sfxload FluidR3\ GM.SF2
sfxload: no memory left
```

I've found a few mentions of how to create a cache in the system RAM but only for Windows. I was wondering if there was a method of doing this in linux (Kubuntu Gutsy). Any help would be great please.

I have just discovered that the SoundBlaster Live does not have its own memory, it instead uses the system memory.  I had the same problem as you trying to load the Fluid R3 soundfont.

You can determine how much memory is set aside for use with soundfonts.  

First clear any existing soundfounds:-

```
$ asfxload -i
```

Then show the remaining memory:-

```
$ asfxload -M
DRAM memory left = 131068 kB

```

(Which shows 128 MB available.)

Now edit the file: **/etc/modprobe.d/alsa-base**
And add the following line to the end:-

```
options snd-emu10k1 max_buffer_size=256 max_synth_voices=256
```

Restart your system.  Then you can see the memory size has increased.

```
$ asfxload -M
DRAM memory left = 262132 kB

```

You can now load the Fluid R3 soundfont without issue.

*Note, this is another one-up on Windows, because the Creative XP drivers limit the memory available for soundfonts to 32MB.*
:guitar:

---

### Post by jharr on 2008-09-26
Good post. I wrote a small shell script and set it to start up with gnome (System->Prefs->Session).

bin/start-fs.sh
```

#!/bin/bash
exec padsp fluidsynth \
    -a oss \
    -m alsa_seq \
    -z 1000 \
    -g 0.8 \
    .fluidsynth/Ultimate.SF2 

```

[LIST]
[*] `padsp` program, and the `-a oss` flag are a hack to get FluidSynth to work with pulseaudio. This keeps FluidSynth from stealing & locking your audio device.
[*] `-z 1000` - increase the buffer size. I have no idea what units this is, but this number worked for me.
[*] `-g 0.8` - increase the gain from 0.2 to 0.8.
[*] `.fluidsynth/Ultimate.SF2` where I stashed the soundfont.
[/LIST]

:guitar:

---

### Post by Perkins on 2008-12-04
Thos should probably go into the how-to section.  Or, if it's already there, it should be made a little easier to find...

---

### Post by MishMich on 2009-03-25
The original post was very helpful I have just installed Ubuntu Studio (8.10) and had expected this to just work (I use Debian for those times I don't want to play - Ubuntu for when I just want stuff to work, like wireless or, in this case set up a PC to run my Technics Digital Piano through).  OK, so I read up on this first, and managed to get a Creative Live! card as that allowed for hardware sythesis and was midi compatible via the joystick port.  Running through the steps above, I managed to get the Creative soundcard to play midi tracks out via the stereo jack and the same for the software synthesis.  But, I cannot get the keyboard to talk to the PC - either in or out.  It is quite important for me to do this, because I like to set up a score and have it play through the keyboard, or play into the PC so I can add synth sounds to the presets on the keyboard.  I used to be able to do this with a cheapo-keyboard on the Atari ST fairly easily over 20 years ago.  I also was able to do this with this keyboard using an old Pentium with a Steinberg ISA card without much hassle.  So, am I missing something crucial here?  Surely it should just play through the soundcard as an external device - but I only see one channel listed.  When I set the channel 1 on rosegarden to the external device, it reads as 'grand piano' (which is what the keyboard is set to), but the notes I play do not appear and nothing is recorded.  Similarly, if I play the SF2 file and direct it to the external device, nothing happens.

Thanks.

---

### Post by MishMich on 2009-03-25
Ah.  It was something obvious I was missing - the din plug that says 'in' goes in the 'out' port on the keyboard, and the one that says 'out' goes in the 'in' port.  I figured 'in' went with 'in' and 'out' went with 'out'.  All seems to work fine so far.  Thanks again.

---

### Post by adamgram on 2009-04-03
I went through this how-to this morning and wasn't able to get very far.  I'm trying to run rosegarden on my laptop so I can write music in the notation editor and record midi files from a keyboard.  For now, I just want to be able to hear the music I write in rosegarden.

Before going through this how-to I downloaded Jack and QSynth, but I'm a little confused about how each of these is supposed to work.  Assuming the onboard sound on my laptop does not have built in midi sounds, do I need QSynth to make sounds while using rosegarden?  Is it a matter of rosegarden telling the synth what to play and the synth making the sound or can rosegarden work without it?  Also, should QSynth by itself be able to make sounds?  (That would help me troubleshoot the problem if nothing else).  

As for the actual how-to, I pasted below the problems I ran into (marked with a *** prefix to my expaination), if anyone could explain these errors I would really appreciate it.


HOWTO: Getting MIDI to work fully in Ubuntu
MIDI: Getting to Create, Play, Anything with Ubuntu!

Intro
MIDI support has been asked for mostly musically involved people who use Linux, and it hasn't come easily. Most of the HOW-TOs for setting up MIDIs don't even work, and I'd know. So, today, after almost a month of working towards it, I've finally been able to listen, play, and create MIDIs with ease. It's actually not very difficult; you just need the right packages and a loaded GM Soundfont.

Prerequisites
- A MIDI enabled sound card (most people have a SoundBlaster Audigy or Live! card-- if you have onboard sound, meaning the motherboard does the MIDI work, you'll need to use FluidSynth, which I'll talk about later).
*** I have ATI IXP AC97 onboard sound

- A fully working ALSA sound system.
*** ALSA shows up under system--> preferences--> sound and the test sound plays for everything EXCEPT sound capture

- A fully working OSS sound system. (in case the upper doesn't work, you can use this and then do a sudo modprobe snd-seq-oss)
*** OSS shows up under system--> preferences--> sound but I get an error message when I hit the 'test' button:
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.

- The following ALSA packages installed (get these through apt-get/synaptic/aptitude):
alsa-base
libasound
*** E: Couldn't find package libasound 
*** I do have libasound2
alsa-headers
*** heather@heather-laptop:~$ sudo apt-get install alsa-headers
*** Reading package lists... Done
*** Building dependency tree
*** Reading state information... Done
*** Package alsa-headers is not available, but is referred to by *** another package.
*** This may mean that the package is missing, has been 
*** obsoleted, or is only available from another source
*** However the following packages replace it:
*** libasound2-dev
*** E: Package alsa-headers has no installation candidate

libasound-dev,
alsa-modules-2.4.26-1-686 (replace the 686 with 586, 386, k6, k7, etc. according to your system)
*** E: Couldn't find package alsa-modules-2.4.26-1-686

alsa-oss
alsa-source

- A program that plays MIDI files. (KMid is a nice one)
*** E: Couldn't find package KMid

The awesfx package if you are not using FluidSynth. (get this through apt-get)

Blood, Sweat, and Tears time (not really)
You've gotten past most of the work which took me the most time. Some of the packages you install may seem like overkill, but for people who use FluidSynth and have to compile it and other things, those packages are good to have just in case.

Do an lsmod in the terminal. It should return something like this

Quote:
snd_seq_midi 8096 1
snd_emu10k1_synth 6784 4
snd_emux_synth 33408 5 snd_emu10k1_synth
snd_seq_virmidi 7296 1 snd_emux_synth
snd_seq_midi_emul 7680 1 snd_emux_synth
(etc)

If you don't see any MIDI related modules 
the important ones are
snd_seq_midi
snd_emu10k1_synth
*** E: Couldn't find package snd_emu10k1_synth

snd_emux_synth
*** E: Couldn't find package snd_emux_synth

snd_ seq_oss
snd_seq
snd_emu10k1
*** E: Couldn't find package snd_emu10k1

snd_rawmidi

---

### Post by Fenderian_Mayhew on 2010-04-14
okay. i just got midi out (my personal goal) by using Linux MultiMedia studio and a SF2 file.

---

### Post by curts on 2011-03-11
After several evenings of digging, I've come to the conclusion the hardware synthesis for the Ensoniq/Creative AudioPCI ES1371+ chip is simply not supported by Debian/Ubuntu (i.e. no synth driver like the emu10k1), but MIDI communication probably is (but that wasn't my goal and I do not have any MIDI h/w to test it).

Using Ubuntu 10.4.x:
```
cat /dev/sndstat
Sound Driver:3.8.1a-980706 (ALSA v1.0.21 emulation code)
Kernel: Linux Panther2 2.6.32-29-generic #58-Ubuntu SMP Fri Feb 11 20:52:10 UTC 2011 x86_64
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Ensoniq AudioPCI ENS1371 at 0xdc00, irq 17
USB Device 0x46d:0x8d7 at usb-0000:00:10.1-2, full speed
VIA 8237 with ALC850 at 0xd800, irq 22

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)
1: USB Audio
2: VIA 8237 (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
31: system timer

Mixers:
0: TriTech TR28602
1: USB Mixer
2: Realtek ALC850 rev 0
```

This conclusion is further supported by the information in the [_ALSA sound card database_]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs").  The ES1371 is not listed as having wavetable support, while the emu10k1 Sound Blaster Live and Sound Blaster 32 AWE cards others mention do have wavetable support.  Hopefully, this post will be helpful for other ES1371 owners.

Further complicating my search, most of the ALSA configuration info I could find predated the use of Pulse Audio.  While MIDI is perhaps a niche area for Linux support, I believe it is still of significant interest to musicians with MIDI-capable instruments.  The MIDI How-to guides could probably use an update.

---

### Post by treii28 on 2011-06-24
> **curts said:**
> After several evenings of digging, I've come to the conclusion the hardware synthesis for the Ensoniq/Creative AudioPCI ES1371+ chip is simply not supported by Debian/Ubuntu

I've been arriving at a similar conclusion after similar searching.  I picked up a SB 16 PCI the other day and although I can see the midi port and can seem to send data to it with aconnect, no sound comes out.  Either there's a mixer bar  hiding somewhere that isn't showing up in the alsa mixers or it thinks it's sending it out the joystick/midi-out port.
(that or there's some other magic word or black-magic rite I haven't done yet to please the Linux gods.  Maybe I'll trying sprinkling the burnt remains of a rainbow butterfly at the foot of a penguin idol tonight and see if that helps)

---

### Post by mistermanugo on 2011-09-01
Hey everyone, I tried to do what is told in the first post. I installed all the alsa packages, fluidsynth, etc...

This is what I obtain after typing the lsmod command:

"
Module                  Size  Used by
btrfs                 462393  0 
zlib_deflate           19568  1 btrfs
crc32c                  2519  1 
libcrc32c                875  1 btrfs
ufs                    72774  0 
qnx4                    6484  0 
hfsplus                70800  0 
hfs                    40754  0 
minix                  25197  0 
ntfs                   94919  0 
vfat                    8933  0 
msdos                   6392  0 
fat                    47767  2 vfat,msdos
jfs                   172461  0 
xfs                   513318  0 
exportfs                3437  1 xfs
reiserfs              225449  0 
aes_i586                7268  3 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
vboxnetadp              6390  0 
vboxnetflt             12740  0 
vboxdrv               169169  2 vboxnetadp,vboxnetflt
snd_hda_codec_atihdmi     2367  1 
snd_hda_codec_idt      52042  1 
snd_hda_intel          22165  2 
snd_hda_codec          74201  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
arc4                    1153  2 
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                  8740  0 
ath9k                 306430  0 
fbcon                  35102  71 
tileblit                1999  1 fbcon
fglrx                2093229  32 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
mac80211              205402  1 ath9k
ath                     7611  1 ath9k
lirc_ene0100            6600  0 
lirc_dev                8884  1 lirc_ene0100
video                  17375  0 
psmouse                63677  0 
output                  1871  1 video
serio_raw               3978  0 
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
agpgart                31788  1 fglrx
soundcore               6620  1 snd
vga16fb                11385  1 
vgastate                8961  1 vga16fb
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
uvcvideo               57406  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
shpchp                 28899  0 
i2c_piix4               8527  0 
cfg80211              126144  3 ath9k,mac80211,ath
led_class               2864  2 ath9k,hp_accel
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34396  0 
mii                     4381  1 r8169
ahci                   32392  2 
"

It seems that I'm missing some midi lines, so if someone knows what do I have to do, please help mme :)

Thank you !

---

