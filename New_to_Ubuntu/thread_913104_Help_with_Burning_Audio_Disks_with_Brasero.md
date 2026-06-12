---
title: "Help with Burning Audio Disks with Brasero"
date: 2008-09-07
forum: New to Ubuntu
---

### Post by ksaul on 2008-09-07
I am a newbie to ubuntu and I went to burn an audio disk with Brasero yesterday. Brasero said that the disk was 1hr and 10min long with 18 tracks but after it transcoded them to .wav i could only fit 11 tracks on the 700mb CD-R.

How do I stop brasero from transcoding .mp3s to .wavs?

---

### Post by ksaul on 2008-09-07
anyone??:confused:

---

### Post by ligaguine on 2008-09-07
Try selecting a Data project instead.  This will let you burn mp3 files to the disc without converting to audio CD format.  If you intend to play these songs back on an audio CD player, however, it will need to specifically support MP3 discs.  I'm not sure if this is what you're after.

If you want to burn an audio CD that can be played in any traditional CD player, then choose an Audio project in Brasero. A 700 Mb CD-R will allow for about 80 minutes of playback in this format.

---

### Post by alienexplorers on 2008-09-07
Try burning your Audio files with K3B.  It is much more friendly and stable.

---

### Post by ksaul on 2008-09-07
> **ligaguine said:**
> Try selecting a Data project instead.  This will let you burn mp3 files to the disc without converting to audio CD format.  If you intend to play these songs back on an audio CD player, however, it will need to specifically support MP3 discs.  I'm not sure if this is what you're after.

If you want to burn an audio CD that can be played in any traditional CD player, then choose an Audio project in Brasero. A 700 Mb CD-R will allow for about 80 minutes of playback in this format.

I cant do that because Brasero keeps transcoding my .mp3 files to wav files and the wav files take up more disk space.

---

### Post by ksaul on 2008-09-08
> **alienexplorers said:**
> Try burning your Audio files with K3B.  It is much more friendly and stable.

I  get this error when I use K3B

> Unable to handle the following files due to an unsupported format:
You may manually convert these audio files to wave using another application supporting the audio format and then add the wave files to the K3b project.
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/01-what_up_whats_happnin-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/02-life_of_the_party_(feat._r._kelly)-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/03-whatever_you_like-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/04-no_matter_what-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/08-done_it_now-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/09-message_to_the_government-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/10-swagger_like_us_(feat._kanye_west_jay-z_and_lil_wayne)-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/11-livin_your_life_(feat._rihanna)-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/15-no_matter_what_(official_remix)_(feat._yung_joc)-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/16-what_up_(remix)_(feat._playaz_circle)-hms.mp3
/home/ksaul/Desktop/T.I.-Paper_Trail-Advance-2008-HMS/cover.jpg

---

### Post by MoxieAndWhimsy on 2009-06-21
In case this issue comes up again, here's a solution. 

Both Brasero and K3B use Gstreamer for codec support. It's likely that installing "Commonly used restricted packages" will fix the above issue. Do this your preferred package installation method or the use the following in the terminal:
```
sudo apt-get install ubuntu-restricted-extras
```

Note: If you haven't broken your installation's free(dom) license virginity yet, this will.

---

### Post by joolz on 2009-12-15
worked, thanks.

---

