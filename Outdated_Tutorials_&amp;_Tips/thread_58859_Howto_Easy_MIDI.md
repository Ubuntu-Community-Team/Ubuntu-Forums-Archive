---
title: "Howto: Easy MIDI"
date: 2005-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by RastaMahata on 2005-08-21
I was trying to play scummvm with alsa, and I coudlnt get it to play midis.. So I did a Little research, and found [this](http://www.ubuntu-es.org/node/3777). He did an excellent job at adding midi in hoary, so this is kind of a translation and a bit of fix.
[list=1]
[*]Install timidity & pmidi: ```
sudo apt-get install timidity pmidi
```
[*]```
sudo gedit /etc/modules
``` and add the following lines: ```
snd-seq-device
snd-seq-midi
snd-seq-oss
snd-seq-midi-event
snd-seq
```
[*]Download the Unison Soundfont: ```
wget ftp://ftp.personalcopy.net/pub/Unison.sf2.gz
```
[*]Extract it to /etc/sounds: ```
sudo mkdir /etc/sounds/
tar -xzf Unison.sf2.gz
mv Unison.SF2 Unison.sf2
sudo mv Unison.sf2 /etc/sounds/
```
[*]```
sudo gedit /etc/timidity/timidity.cfg
```It should look like this (No more, no less):```
soundfont /etc/sounds/Unison.sf2

```
[*]```
sudo gedit /etc/init.d/timidity
```variable TIM_ALSASEQPARAMS (variable 22 I think), should look like this:```
TIM_ALSASEQPARAMS="-iA -B2,8 -Os1l -s 44100"
```
[*]```
sudo gedit /etc/default/timidity
```Uncomment the two TIM variables. It should look like this: ```
# Defaults for TiMidity++ scripts
# sourced by /etc/init.d/timidity
# installed at /etc/default/timidity by the maintainer scripts
# $Id: timidity.default,v 1.3 2004/08/07 14:33:26 hmh Exp $

#
# This is a POSIX shell fragment
#

# Enable MIDI sequencer (ALSA), default is disabled
TIM_ALSASEQ=true

# Setting overrides (of /etc/timidity.conf) for the ALSA sequencer daemon
TIM_ALSASEQPARAMS="-iA -B2,8 -Os1l -s 44100"

```
[*]```
gedit ~/.bashrc
```Add the following line (A good idea is to add it after line 9):```
export ALSA_OUTPUT_PORTS="128:0"
```
[*]Done! Now you can play midis with **pmidi**. Like this:```
pmidi Song.mid
```If it doesnt work, reboot (just to be sure... Damn windows tick!)
[/list]

**Bonus: SCUMMVM**
Now you can play scumm vm through alsa! Just follow these steps:[list=1]
[*]```
gedit ~/.bashrc
```Add the following line (Again, after line 9 is a good idea):```
export SCUMMVM_PORT=128:0
```
[*](If you want to create a launcher)```
gedit ~/.gnomerc
```Add the folowing lines:```
export ALSA_OUTPUT_PORTS="128:0"
export SCUMMVM_PORT=128:0
```
[*]In scummvm, go to options, audio, music driver: ALSA
[/list]

Good luck.

PD: Thanks to:[list]
[*][http://www.ubuntu-es.org/node/3777](http://www.ubuntu-es.org/node/3777)
[*][http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo](http://www.ubuntulinux.org/wiki/MidiSoftwareSynthesisHowTo)
[*][http://www.personalcopy.com/home.htm](http://www.personalcopy.com/home.htm)
[*][http://ubuntuforums.org/showthread.php?t=30559&highlight=timidity](http://ubuntuforums.org/showthread.php?t=30559&highlight=timidity)
[/list]

Note: I think Ubuntu should have MIDI support by default :(

---

### Post by deaderthanyou on 2005-08-22
Wow, worked perfectly :)  I like your choice of soundfont, could you tell me why you use it?  Reboot was required.  Just wondering if you know of any command that I can use with pmidi or timidity that would save a midi as a .wav file.

---

### Post by gammyhand on 2005-08-22
[QUOTE=deaderthanyou]Wow, worked perfectly :)  I like your choice of soundfont, could you tell me why you use it?  Reboot was required.  Just wondering if you know of any command that I can use with pmidi or timidity that would save a midi as a .wav file.[/QUOTE]
 I have an audigy2 zs sound card, surely I can use it's rom stored soundfonts?

---

### Post by gammyhand on 2005-08-22
[QUOTE=gammyhand]I have an audigy2 zs sound card, surely I can use it's rom stored soundfonts?[/QUOTE]
 I get these errors when trying to run the tar command:

ralph@ralph:~$ tar -xzf Unison.sf2.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors

---

### Post by RastaMahata on 2005-08-22
[QUOTE=gammyhand]I get these errors when trying to run the tar command:

ralph@ralph:~$ tar -xzf Unison.sf2.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors[/QUOTE]
 I think you should download it again... maybe its a corrupted download.
Try downloading the file through your browser.

---

### Post by deaderthanyou on 2005-08-22
[QUOTE=RastaMahata]I think you should download it again... maybe its a corrupted download.
Try downloading the file through your browser.[/QUOTE]

Actually, mine did the same thing.  I just went to my home folder, right clicked on the file, and chose extract here.  Something must be wrong with that command :(

---

### Post by papabean on 2005-08-27
[QUOTE=gammyhand]I get these errors when trying to run the tar command:

ralph@ralph:~$ tar -xzf Unison.sf2.gz
tar: This does not look like a tar archive
tar: Skipping to next header
tar: Archive contains obsolescent base-64 headers
tar: Error exit delayed from previous errors[/QUOTE]
I think it's because this file is just g'zipped and not tar g'zipped. A simple ```
gunzip Unison.sf2.gz
``` should do the trick.

Many thanks, RastaMahata, for posting this HOWTO. ScummVM was the EXACT reason I even started looking for sequencer support in ALSA. I just found my old *Day of the Tentacle* CD and had no sound.

---

### Post by Kyral on 2005-08-27
Hopefully this will let me play Final Fantasy 8 on Cedega now :D (Thing wouldn't load b/c it couldn't find MIDI support)

---

### Post by drx on 2005-09-04
Hi RastaMahata,

thanks for this guide which is the first that seems to work ok for me ;) But still, i have problems with MIDI ... the sound is skippy (crackling replay) and laggy. It sounds like wavetable sonftware synthesis five years ago on my incredibly slow Pentium that wasn't fast enough to do it. But now i have a 2Ghz computer and an Audigy ZS. Is there a good guide how to set up the Audigy "natively"?

---

### Post by Quirky on 2005-09-04
No need to reboot!

```
sudo modprobe snd-seq-device
sudo modprobe snd-seq-midi
sudo modprobe snd-seq-oss
sudo modprobe snd-seq-midi-event
sudo modprobe snd-seq
sudo /etc/init.d/timidity start

```

---

### Post by RastaMahata on 2005-09-20
[QUOTE=deaderthanyou]Wow, worked perfectly :)  I like your choice of soundfont, could you tell me why you use it?  Reboot was required.  Just wondering if you know of any command that I can use with pmidi or timidity that would save a midi as a .wav file.[/QUOTE]
 easy... ```
timidity <type> <file>
```
where type is what kind of file output you want.
  -Od          dsp device
  -Os          ALSA pcm device
  -OR          aRts
  -Oe          Enlightened sound daemon
  -Oj          JACK device
  -On          Network Audio Server
  -Ow          RIFF WAVE file
  -Or          Raw waveform data
  -Ou          Sun audio file
  -Oa          AIFF file
  -Ov          Ogg Vorbis
  -OF          FLAC / OggFLAC
  -Ol          List MIDI event
  -OM          MOD -> MIDI file conversion

---

### Post by RastaMahata on 2005-09-20
ack, double post. My bad :(

---

### Post by fragmental on 2005-09-23
[QUOTE=drx]Hi RastaMahata,

thanks for this guide which is the first that seems to work ok for me ;) But still, i have problems with MIDI ... the sound is skippy (crackling replay) and laggy. It sounds like wavetable sonftware synthesis five years ago on my incredibly slow Pentium that wasn't fast enough to do it. But now i have a 2Ghz computer and an Audigy ZS. Is there a good guide how to set up the Audigy "natively"?[/QUOTE]
 Should be the same as it is for sblive.  I could be wrong, though, but I think it is.  In that case you want awesfx. I think there's a good howto somewhere in this forum, so you should be able to find it.  I'm too tired too look right now.  You can try the search items "midi awesfx".

You should not need timidity or any other software synth but you will need a soundfont.  The soundfont mentioned in this post is probably not a bad one.  My personal favorite is [AnotherGS](http://bennetng.kc-studio.com/AnotherGS/AnotherGS.html), but it comes in an exe archive. I extracted it while in windows but it might work using wine. I haven't tried it.
[Here](http://tangentmind.blogspot.com/2005/08/soundfonts.html)  is a link to my blog that has 3 links to some other soundfonts which may be alright, but I can't guarantee that they will be easy to extract in linux.  If you have a windows install you should have a "soundbank" floating around somewhere too.  I forgot what it should be called.

---

### Post by PatrickMay16 on 2005-09-23
EDIT: No matter, I realised what to do. 
It's working perfectly. Thanks very much!

---

### Post by serzz on 2005-12-02
Can somebody post own /etc/init.d/timidity and /etc/dafault/timidity files? I have deleted them and I can't find way to bring them back.

---

### Post by thetictacaddict on 2006-08-22
Maybe I was a little late finding this.  Perhaps there's a newer document.  I tried to use EasyUbuntu to install midi support but I had already installed something which prevented it from EasyUbuntu from taking action (I think it was Timidity).  Anyhow, this document helped me get MIDI support working.  Thanks a lot, RastaMahata!

---

### Post by detyabozhye on 2006-11-27
All works with just installing timidity in Edgy; I have an Audigy 2.

---

### Post by scunc_dvl on 2006-12-14
In my Edgy this thread came in handy when I wanted to install Unison.sf2 to fix a few missing instruments in freepats, the instrument patch is all that's missing from the Edgy ubuntuguide.

Has anyone noticed staticy sound mixing? timidity in Zdoom works but sounds a bit staticy like it's been turned up too much, I doubt that's an easy fix and I haven't seen other apps do similarly, yet..

EDIT: It's okay - if you get staticy sound or distorted sound, check your sample rate. It should likely be up to 48,000Hz. Zdoom had this setting in it all along, and works great (if only you get it to compile) :)

---

### Post by scunc_dvl on 2007-07-16
I still need this "Easy MIDI" thread because Freepats is missing a pile of instruments. Kind of frustrating

---

### Post by mit74 on 2009-11-01
Thanks!

This totally solved my MIDI problems in Kubuntu 9.10!

---

