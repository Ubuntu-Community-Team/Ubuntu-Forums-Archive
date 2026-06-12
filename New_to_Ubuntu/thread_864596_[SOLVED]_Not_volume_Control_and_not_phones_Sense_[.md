---
title: "[SOLVED] Not volume Control and not phones Sense [SOLVED]"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by sagdall on 2008-07-19
I'm a novice Mexico user of Ubuntu and any other distribution.

About 3 weeks ago I noticed that I can't move the slider of volume (only PCM-2 100% or Mute) and also I can't change the volume using the keyboard (the same 100% or mute). Also I noticed if I plugged the headphones at front connector still have output at speakers (not commute sensitivity). I checked At System --> preferences --> Sound only appeared 3 devices:

1: Realtek ALC861 (OSS Mixer)
2: Playback: ALSA PCM on front:0 (Realtek ALC861 analog) via DMA (PulseAudio Mixer)
3: Capture: Monitor source of ALSA PCM on front:0 (Realtek ALC861 analog) via DMA (PulseAudio Mixer)
4: Capture: ALSA PCM on front:0 (Realtek ALC861 analog) via DMA (PulseAudio Mixer)

Also these 4 devices are showed at Sound Icon at panel using mouse right button and selecting preferences

Alsa Mixer also didn't work because appeared following if I typed at Terminal: alsamixer:

snd_alsamixer_load failed: Not such directory (or something like that)

My computer is a Desktop Gateway model GT3072m with a P4 HT processor. the motherboard is Micro Star Int'l with integrated Video card and Sound card.

The sound card model is ATI IPX SB450 with the Azalia HD Audio Codec from Realtek ALC861. The computer has 6 jacks at rear and 2 at front.

I search at many, many threats at many, many forums (also here) and after read and do some advices from them, Today I finally get to works both: The slider for volume (PCM Level) can be controlled by the Icon on the panel and the keyboard. Also I get to sense the phones so when I plug the phones the speaker goes off. 

1. First I opened the alsa-base
        sudo gedit /etc/modprobe.d/alsa-base

 and wrote at the end of file the following (for realtek ALC861):
        options snd-hda-intel model=6stack

Save and close the file.( I'm not really sure if this was useful because I have Audio from Speakers and phones).

2. After that I installed the asoundconf-gtk from Synaptic (or using the terminal sudo apt-get install asoundconf-gtk). Reboot . And I went to System --> Prefrences --> Default sound Card. After application opened appeared 2 boards 1: SB and 2: PulseAudio. I selected SB (because the board is AT IPX SB450, I think) and reboot.

3. After I Recompiled the alsa-source to get work the Alsa Mixer so I did following (I can't remember in what threat I read this):
sudo apt-get install module-assistant

After installations I did:

sudo module-assistant a-i alsa-source

(maybe if it isn't possible to recompile, it is necessary to check if we have alsa-tool and alsa-util, alsa-lib. So download them from Synaptic). recompile process take me about 30 minutes

Reboot the computer.

4. After reboot I got work Alsa Mixer. So it is possible to view mixer control typing on Terminal alsamixer. it possible to view it graphically using the ALSA Mixer for gnome from Synaptic : alsamixergui)
At this moment It isn't possible to control the volume from slide of Sound Icon on Panel and keyboard. But when I opened Sound preferences at System --> Preferences --> Sound appears other device option:

HDA ATI SB (Alsa Mixer)

So I select it. Then I opened preferences at Sound Icon on panel using mouse right button and select the same option. ( at both selections I used PCM as a Default track)

So after that I finally got control the volume using the Keyboard and using the slide on Sound Icon on panel. Also I got to sense the phone jack, so when I plug the phones the speaker goes off and if I unplug the phones the speakers goes ON.

That was all !!! Solved !!!!

Ok See you and Best Regards

---

