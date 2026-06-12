---
title: "jackd for 2 soundcards"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Ponhovo on 2008-07-20
how can i set my audigy sound blaster pci sound card to work in a loudpseaker and still my realtek ALC883 on-board to work independently for a headphone for exemple?

i can't make any application use my ALC883, else the sound tester of sound configuration [it sends the pink noise right]

i got dbmixer, but i can't send the playback to my on-board device to check the sound bypassed before letting it go to the loudspeakers correctly mixed, so its a really serious problem i got

ponhovo@Ecstasy:~$ lsmod|grep snd
snd_hda_intel         337448  1 
snd_seq_dummy           5380  0 
snd_emu10k1_synth       9344  0 
snd_emux_synth         40064  1 snd_emu10k1_synth
snd_seq_virmidi         9216  1 snd_emux_synth
snd_seq_midi_emul       9088  1 snd_emux_synth
snd_seq_oss            36864  0 
snd_emu10k1           152864  1 snd_emu10k1_synth
snd_ac97_codec        122200  1 snd_emu10k1
ac97_bus                4096  1 snd_ac97_codec
snd_pcm_oss            50048  0 
snd_mixer_oss          20096  1 snd_pcm_oss
snd_seq_midi           11008  0 
snd_pcm                94344  4 snd_hda_intel,snd_emu10k1,snd_ac97_codec,snd_pcm_oss
snd_rawmidi            29824  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
snd_seq_midi_event      9984  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                62496  9 snd_seq_dummy,snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              27272  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         10260  8 snd_seq_dummy,snd_emu10k1_synth,snd_emux_synth,snd_seq_oss,snd_emu10k1,snd_seq_midi,snd_rawmidi,snd_seq
snd_util_mem            6656  2 snd_emux_synth,snd_emu10k1
snd_hwdep              12168  2 snd_emux_synth,snd_emu10k1
snd                    69288  16 snd_hda_intel,snd_emux_synth,snd_seq_virmidi,snd_seq_oss,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device,snd_hwdep
soundcore              10272  1 snd
snd_page_alloc         12560  3 snd_hda_intel,snd_emu10k1,snd_pcm

pleease help :confused:

---

### Post by rich257 on 2008-07-20
Multiple sound cards works fine --- I have three.  If you are using Pulse Audio and the applications playing sound can use Pulse then you should be able to select which sound card the sound goes to using Pulse's tools.

I don't quite understand the problem you are having.

---

### Post by Ponhovo on 2008-07-20
i cant select the program to send the sound to the audio card i want
it seems it doesnt obey the ubuntu configuration of sound

---

### Post by rich257 on 2008-07-20
Yep, with 7.10 I don't know how to do that easily.  With 8.04 and Pulse it's fairly easy, once you have it setup.

---

### Post by Ponhovo on 2008-07-20
> **rich257 said:**
> Yep, with 7.10 I don't know how to do that easily.  With 8.04 and Pulse it's fairly easy, once you have it setup.

can't use pulseaudio o.o
thats what happens:

ponhovo@Ecstasy:~$ pulseaudio
W: main.c: WARNING: called SUID root, but not in group 'pulse-rt'.
W: alsa-util.c: Cannot find mixer control "Capture".
E: module.c: Failed to open module "module-x11-bell": module-x11-bell.so: cannot open shared object file: No such file or directory
E: module.c: Failed to open module "module-x11-publish": module-x11-publish.so: cannot open shared object file: No such file or directory
E: module.c: Failed to open module "module-gconf": module-gconf.so: cannot open shared object file: No such file or directory
E: main.c: Module load failed.
E: main.c: Module load failed.
E: main.c: Module load failed.


and hangs in there

---

### Post by Ponhovo on 2008-07-20
i jsut noticed that my /etc/esound.conf just say to hw:1 work as default
and when i put hw:0, my onboard works
but not the two of them
how can i set both workable and let the programs configure where to send the signal?
[whatver audacity is set to send the signla to, it respects that esound.conf, in that case, hw:1, audigy pci sound card
so even if i configure to send to the labeled card HDA, thats the realtek, it sends to the Audigy just coz the configuration says so]
if i configure by the ubuntu normal sound configure, it doesnt change how it works

i think that might be a ESD problem that mixs all oss and alsa and send it entirely to hw:1

any ideas?

---

### Post by Ponhovo on 2008-07-20
i deleted /etc/asound.conf and now i can switch cards...
still my DBMixer can't send playback to ALC883 realtek
any ideas? =/

---

### Post by Ponhovo on 2008-07-22
i got a Realtek onboard and a Audigy Soundblaster in my pc
DJPlay uses the monitor out and PFL out plug in QtJackCTL list, so i could cue in a diferent headphone before sending it to the dsp and looundspeaker
but jackd doesn't seem helpful to configure 2 soundcards at the same time
anyone knows how to configure 2 soundcards in jackd?

i know it GOT to be a way to configure 4 playback channels for jackd, 2 for each,  coz DJPlay requires jackd server daemon, is designed for it, so it wouldn't use a monitor out and PFL if i can't preview this PFL, so it wud be stupidity. and so does Mixxx too

anyone?

---

### Post by Ponhovo on 2008-07-22
so?

---

### Post by Ponhovo on 2008-07-22
no one?

is it really impossible?

---

### Post by Ponhovo on 2008-07-24
i got to work tomorrow
reinstalled ubuntu yesterday, and the new ubuntu installation don't want to start

two things:
1st. seems like there's no /dev/dsp 
dir shows it, but lsof returns absolutely nothing [just another bash line]

2nd. this is what jackctl shows

19:27:04.378 Patchbay deactivated.
19:27:04.390 Statistics reset.
JACK tmpdir identified as [/dev/shm]
19:27:04.424 MIDI connection graph change.
19:27:04.607 MIDI connection change.
19:27:05.617 Startup script...
19:27:05.618 artsshell -q terminate
JACK tmpdir identified as [/dev/shm]
can't create mcop directory
Creating link /home/ponhovo/.kde/socket-ScarletRuby.
19:27:05.859 Startup script terminated with exit status=256.
19:27:05.859 JACK is starting...
19:27:05.859 /usr/bin/jackd -R -dalsa -r44100 -p1024 -n2 -D -C/dev/dsp -Phw:0 -m -i2 -o2 -zr -I2 -O2
19:27:05.861 JACK was started with PID=6536 (0x1988).
jackd 0.103.0
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread 54529456, from thread 54529456] (1: Operation not permitted)
cannot create engine
19:27:05.872 JACK was stopped successfully.
19:27:05.872 Post-shutdown script...
19:27:05.872 killall jackd
jackd: no process killed
19:27:06.081 Post-shutdown script terminated with exit status=256.
19:27:07.896 Could not connect to JACK server as client. Please check the messages window for more info.
JACK tmpdir identified as [/dev/shm]

2nd's 1st thing is that it doesn't created any audio group to ubuntu,
2nd's 2nd thing is that line saying Operation not permitted
is that a realtime buiffer problem or a permission problem?

need heelp, pleeaaseee

---

### Post by Sef on 2008-07-24
Can you boot in Recovery Mode?  (At start up, press esc (and keep pressing) until you get into GRUB.  then highlight recovery mode.

---

### Post by cariboo on 2008-07-25
It looks like part of the problem is tha you are not using a real time kerenel. You can install a real time kernel from the repostirories. Look for linux-image-2.6.xx-x-rt

Jim

---

### Post by Ponhovo on 2008-07-26
two issues:
1.jackd 109.0 can't find alsa module
how the hell wud jackd 109 not recognize it?
so i need to use /usr/bin/jackd that is 103, but only in sudo, so i can't use jack.ctl
anyone cud help me fix that?

2.seems like i didn't got any /dev/dsp :confused:
when i type lsof /dev/dsp to check, it returns like that:

ponhovo@ScarletRuby:~$ lsof /dev/dsp
ponhovo@ScarletRuby:~$ 

i think it shud be at least:
ponhovo@ScarletRuby:~$ lsof /dev/dsp
COMMAND    PID    USER   FD   TYPE DEVICE SIZE  NODE NAME
ponhovo@ScarletRuby:~$ 

isnt it?
is it an error or just nonsense?

---

### Post by Ponhovo on 2008-07-26
is that impossible? nobody answers me... please
if it is, just say it =/

---

### Post by markbuntu on 2008-07-26
Jack uses ALSA so you need to get that working in ALSA first. 


You should try asking this in the Multimedia Production Forum. The people there are far more familiar with jack. You can also try a google search. I'm sorry I could not help you more but jack is kind of its own creature.

---

### Post by Ponhovo on 2008-07-26
i see... im going to ask it in there
altrough, its already workign in alsa, as hw:1 or hw:0 :P

---

### Post by Ponhovo on 2008-07-26
anybody here knows how to?
i got DJPlay and i need that PFL to preview and mix, so send it to the master itself

got Mixxx too, but my soundcard doesnt split out-lines, just play the same hw:0 twice
and running two jackd doesnt work

is there any possible way the alsa_pcm split over 2 diffrent pci soudn cards one another?

---

### Post by Ponhovo on 2008-07-26
is there a way?

---

### Post by Ponhovo on 2008-07-27
why ppl started ignoring me all over the forum? o.o just explain it to me, so i cant get the hell out of here

is that dificult that nobody answers?!
thats not the first time, holy damn

---

### Post by markbuntu on 2008-07-27
You should be able to patch directly to/from the hardware with Patchage or JackEQ. I am not very familiar with jack because I have not used it for a while but one of those should do the trick for you.

---

### Post by Stochastic on 2008-07-28
> **Ponhovo said:**
> 1.jackd 109.0 can't find alsa module

The most common cause of this error is that another program is locking up the alsa driver.  Quit all sound applications before attempting to start Jack.  One that many people don't think about is FireFox (or other browsers).

As for the /dev/dsp thing; when I run lsof /def/dsp it returns nothing - even when I have music playing.  I don't know enough about that command to troubleshoot your error.

---

### Post by thorgal on 2008-07-29
/dev/dsp is either the block device for the OSS sound driver or a fake one emulated by the ALSA OSS emulation layer (or oss2jack, which is not the case at all here).
/dev/dsp is not needed at all if you use ALSA without OSS emulation. jackd does not need it at all either, jackd uses an audio backend that can communicate to the sound system, be it ALSA, OSS or PortAudio). So unless you use an application that can only output to /dev/dsp, there's absolutely no need to have it. It's a rather deprecated thing.

---

### Post by bsantos on 2008-11-13
I got 3 cards to work with the following (I just use it for playback, great for mixxx):

.asoundrc
```

pcm.multi_playback {
  type multi
  slaves.a.pcm hw:0
  slaves.a.channels 6
  slaves.b.pcm hw:1
  slaves.b.channels 2
  slaves.c.pcm hw:2
  slaves.c.channels 2

# First 6 channels of first soundcard (playback)
  bindings.0.slave a
  bindings.0.channel 0
  bindings.1.slave a
  bindings.1.channel 1
  bindings.2.slave a
  bindings.2.channel 2
  bindings.3.slave a
  bindings.3.channel 3
  bindings.4.slave a
  bindings.4.channel 4
  bindings.5.slave a
  bindings.5.channel 5

# First 2 channels of second soundcard (playback)
  bindings.6.slave b
  bindings.6.channel 0
  bindings.7.slave b
  bindings.7.channel 1

# First 2 channels of third soundcard (playback)
  bindings.8.slave c
  bindings.8.channel 0
  bindings.9.slave c
  bindings.9.channel 1
}

ctl.multi_playback {
  type hw
  card 0
}

```Based on [http://www.sound-man.co.uk/linuxaudio/ice1712multi.html](http://www.sound-man.co.uk/linuxaudio/ice1712multi.html) but adapted for my setup and only playback.

I then use jack with the following .jackdrc:
```

/usr/bin/jackd -R -m -dalsa -P -dmulti_playback -r48000 -p1024 -n2 -m

```I use 2 cheap usb sound cards and choose the outputs 7-8 and 9-10 on mixxx for master and monitor.

It also works well on my setup for playing around with audio production (seq24,hydrogen,nekobee,zynaddsubfx,jamin,jackeq,patchage). On the Macbook the "line as output" option doesn't work since the line is muted when using the headphone jack, and I couldn't use it for monitor.

---

