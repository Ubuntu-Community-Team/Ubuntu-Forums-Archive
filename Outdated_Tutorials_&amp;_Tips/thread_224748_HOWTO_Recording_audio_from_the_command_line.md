---
title: "HOWTO: Recording audio from the command line"
date: 2006-07-28
forum: Outdated Tutorials &amp; Tips
---

### Post by jordilin on 2006-07-28
Recording any sound that goes through your computer is a feature that you don't have to miss out. Mostly if this sound is music. There are lots of internet streaming mp3 sources that stream audio that you can listen with your computer and why not, you can record to mp3 and have an enormous mp3 library. In this howto I'm going to give you powerful tools to record sound directly to an mp3 file or ogg file from the command line. So, you will be able to record for hours and hours your favourite music without having to worry about your hard disk space.
First of all you have to set up the recording channels by doing

```
**alsamixer**
```

Once there, select the capture view by typing the tab key. You'll get the next screen:

[IMG]http://personal.telefonica.terra.es/web/personalinfo/alsamixer.png[/IMG]

With the arrow keys select the column Capture and set it to the CAPTUR mode with the space key as in the screenshot. Adjust the recording volume with the arrow keys. You can also set it up with the gnome volume control panel going to the capture tab.

**Recording sound to an mp3 file**

You'll need the lame mp3 encoder. Install it by doing 

```
**sudo apt-get install lame**
```

Type the following command
```
[B]
arecord -f cd -t raw | lame -x – out.mp3[/B]
```

Arecord captures the audio that goes through your computer and pipes it to the lame encoder, so you encode the audio directly to an mp3 file. You can specify more options to the lame encoder such as the bitrate with lame -x -b bitrate. Without specifying the bitrate it encodes to 128kbps constant bit rate cbr. If you want to record for an specific amount of time then:
```
[B]
arecord -f cd -d numberofseconds -t raw | lame -x – out.mp3[/B]
```
[B]
Recording sound to an ogg file[/B]

You'll need the oggenc (the ogg encoder). Install it by doing
```
[B]
sudo apt-get install vorbis-tools[/B]
```

Type the following command
```
[B]
arecord -f cd -t raw | oggenc - -r -o out.ogg[/B]
```

And you'll get your sound recorded to an ogg file. Take into account that we record directly to a compressed file, so there's nothing in between, so you can record for hours saving an incredible amount of hard disk space.

**Ripping shoutcast audio streaming**

Streamripper allows us to rip audio streaming servers. Install it by typing

```
**sudo apt-get install streamripper**
```

You can connect to any shoutcast radio station with xmms. Once playing get the info and write down the url. Then type:

```
**streamripper url **
```

and you'll get each song in a separate mp3 file.
Enjoy recording!! :D 

**Interesting audio applications.**

Audacity-Editing mp3/ogg files
Streamripper-ripping audio streaming servers 
Streamtuner-Stream directory browser

---

### Post by unless on 2006-07-30
Nice and simple! Thanks for the info.

---

### Post by natgwil on 2007-02-03
I've tried your instructions and I have two problems.

1) I can't get it to work for recording to mp3. It comes up with the following error:-

Could not find "–".
Recording raw data 'stdout' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

And nothing happens.

2) When I record in ogg format it does record. However no matter how low I put the recording level in alsamixer it sounds distorted. Am I doing something wrong?

---

### Post by scottsd48 on 2007-02-13
> 1) could not get it to work.., error '-'
I had the same problem. Be sure you use the '-' (the 'dash' key). If you cut-and-paste from the tutorial you are liable to end up with the wrong character.
The command that worked for me was:
   $ arecord -f cd -t raw | lame -x - out.mp3
Note the space before the output file name.

HTH
Scott

---

### Post by fak3r on 2007-02-24
I cannot get this to work, Scott, thanks for your reply, that solved my initial trouble, but while it 'records' I never get anything in my audio files.  Capture is unmuted and turned up, are there any other channels that's I'm missing?  I've done everything above and convinced it's working, but no sound ever gets recorded.  What's up?  I don't see any error messages or anything, everything else is working great.  Oh, I'm running Feisty, but this didn't work for me on Edgy either.  It's an AC'97 onboard Intel card that I never have any issue with playing cds/mp3s/sound in games/desktop sounds/etc...so I can't figure this out.

Any pointers, other things to check?  Thanks.

---

### Post by chaonis on 2008-11-08
Reviving the thread:

I have a Dell D9100 with 2.6.25 kernel. lspci shows:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

L/R, rear, and surround sound channels all work. However, I have three sound devices connected to the "Line-in", front, and rear "Mic" but could not get the sounds out. 

One work-around is in the command line I do:
```
# arecord -f cd -t wav | aplay
```

I can change between the input channels with alsamixer. But I can select only one input at a time, even thought it shows two capture channels (only primary works). 

My questions are:
1) how to make the Line-in, mics sound always feedback to the audio output (real time monitor). 
2) how to enable both input capture channels? 

thanks.

By the way, my module setting is: ```
options snd-hda-intel model=auto
```

---

### Post by jnihil on 2011-08-04
This thread helped me out, so here's what I did in case others are trying the same.
I'm using 10.04LTS on a Dell Mini9 with a small mic plugged into the external mic input.

$ arecord -f cd -d 3600 -t wav | lame --preset 56 -mm - `date +%Y%m%d%H%M`.mp3

This records an hour of mic input then coverts to a mono mp3 at 56kbps since I'm just recording a business meeting on my laptop PC. I put this into my crontab since we have our weekly meeting at the same time each week. Automated recording is nice. The filename is yyyymmddhhmm.mp3, so you can archive all your meetings.

I had to use the '-t wav' option since '-t raw' made lame return an error saying 'Unsupported format'.
Also, when I first did this, I had what I thought was an empty (silent) file. When I checked the pulseaudio settings, the mic input level was way down. I changed this and all was well.

---

