---
title: "Recording sound using Audacity?"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by hamstermoon on 2012-07-19
I am having problems recording sound off part of an .avi file I am running in VLC.
 
Audacity can't seem to hear what is being played in VLC. Any idea how I can sort that?

---

### Post by cortman on 2012-07-19
> **hamstermoon said:**
> I am having problems recording sound off part of an .avi file I am running in VLC.
 
Audacity can't seem to hear what is being played in VLC. Any idea how I can sort that?

How are you sending the sound from VLC to Audacity?

---

### Post by hamstermoon on 2012-07-19
I have no idea. I thought someone might be able to explain to me how to do that here (please?)

---

### Post by bryncoles on 2012-07-19
Can't remember how to do it with audacity... sorry!  But if you follow the instructions on [this page](http://stackoverflow.com/questions/7502380/streaming-pulseaudio-to-file-possibly-with-gstreamer) then you can record the audio using pulse audio, and parec in the terminal.

Check your pulseaudio sound sink using:  

```
pactl list
```

look for the line 'sink 0', and the 'Monitor Source:'.  Unmute it with:

```
pacmd
set-source-mute alsa_output.pci-0000_00_1b.0.analog-stereo.monitor false
exit
```

type the following into a terminal:

```
parec --format=s16le --device=alsa_output.pci-0000_00_1b.0.analog-stereo.monitor | lame -r - ~/Desktop/dump.mp3
```

Then start playing your file.  Anything played will be outputted to a file called 'dump' on the desktop!  

You'd finish the recording by pressing control+c

---

### Post by bryncoles on 2012-07-19
Ah!  Found where I had instructions for audacity.  Try the following:

1. Run Audacity
	1b. Go to Preferences -> Devices
	1c. Change the Playback device to "pulse".
	1d. Change the Recording device to "pulse".

2. Open PulseAudio Volume Control.  Leave it open.

The first time you use a recording program you need to to edit the recording settings of PulseAudio Volume Control. It should remember your settings after rebooting.

3. Open Audacity and hit the "Record" button.

4. While Audacity is recording, open PulseAudio Volume Control and select the "Recording" tab. It will show "Alsa plug-in Audacity. Alsa capture from" and a combo-box. Choose the "Monitor of internal audio..." if you use an internal sound card.

That should do it...

---

### Post by irv on 2012-07-19
I just tried this. I started playing some music on Pithos Radio, started Audacity hit record and it records the sound coming from my speaker. Of course it will pickup room noise.

---

### Post by bryncoles on 2012-07-19
> **irv said:**
> I just tried this. I started playing some music on Pithos Radio, started Audacity hit record and it records the sound coming from my speaker. Of course it will pickup room noise.

It does that to me too, if I have the wrong device set in pavcontrol.  In Pavcontrol's recording tab, there is nothing until you start audacity recording.  Then you can select 'capture from...' and play with the options until you find the soundcard rather than the mic.  That's what I did, anyway!

Once I have set 'capture from' to 'monitor of built in blah blah blah', it no longer records ambient room sound.  

Otherwise, does using parec form the CLI work for you?

---

### Post by cortman on 2012-07-19
One way I've recorded sound from audio play to Audacity is to simply run a 3.5 mm audio cable from the headphones port on my laptop to the mic port. No room noise at all- as far as I'm concerned no loss of sound quality either.

---

### Post by irv on 2012-07-19
> **cortman said:**
> One way I've recorded sound from audio play to Audacity is to simply run a 3.5 mm audio cable from the headphones port on my laptop to the mic port. No room noise at all- as far as I'm concerned no loss of sound quality either.

I will have to try this when I get home. I'm on the road at the moment.
I do sound recording at the chapel and this is how I do that:
1. Hook a cable from the output of the PA system into a Analog/Digital converter.
2. Run a cable from the converter to a USB port on a laptop.
3. Capture that port in Audacity.
4. Record any sound coming from any mic hook to the PA.
Works great.

I just upgraded the laptop to Ubuntu Studio 12.04 and for some reason I have started to pick up a small interference noise in my recordings. I need to do some investigating when I have some time. I can clean up the noise with Audacity, but that just add more work for me.

---

### Post by eriktheblu on 2012-07-19
Wouldn't it make more sense (speed, fidelity) to simply extract the audio using ffmpeg?

---

### Post by irv on 2012-07-19
> **eriktheblu said:**
> Wouldn't it make more sense (speed, fidelity) to simply extract the audio using ffmpeg?

I believe you are right. I used ffmpeg for video, but you sure can use it for audio. Playing around with video I ran across this howto video that helped me understand using ffmpeg to pull out parts of a video.
[http://www.linuxjournal.com/video/linux-howto-video-editing-magic-ffmpeg]("http://www.linuxjournal.com/video/linux-howto-video-editing-magic-ffmpeg")

---

### Post by lhb1142 on 2012-07-19
I assume you wish to record Internet Radio or similar. It's easy to do this from within VLC itself.

Open VLC, go to View, click on Advanced Controls.

You will see a new control bar above the normal one.

To pick a station, find the URL it uses for its *actual stream*, copy it, go to VLC's Media tab, and enter (paste) the URL into Open Network Stream.

When the program you wish to record is about to begin, merely click on VLC's record button (the red one at the far left of the new control bar).

Your program will be recorded in the same format as it is being transmitted (MP3, aac, whatever).

To make any adjustments (remove extraneous announcements, etc.) *then* I use Audacity.

The only time I use Audacity to make an original recording is when I plug in an analog source (most often a cassette tape deck) into my microphone input. Of course "live" performances can also be recorded with Audacity.

I hope this helps you.

Lawrence

---

### Post by jmfal on 2012-07-19
I haven't used audacity for a whole ,but I remember there being a setting for "floor noise",
or "floor level".

It should cut down on the extra/unwanted noises.

---

### Post by irv on 2012-07-19
Audacity has Tutorials for things like this, here is one:
[SIZE="3"]**[Tutorial - Recording audio playing on the computer]("http://manual.audacityteam.org/man/Tutorial_-_Recording_audio_playing_on_the_computer")**[/SIZE]

---

### Post by Rodney9 on 2012-07-19
[http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3](http://www.omgubuntu.co.uk/2011/03/audio-recorder-for-linux-easily-record-audio-streams-to-mp3)

Audio Recorder will record anything playing.

Rodney

---

